---
title: Agregar una búsqueda a una ventana de herramientas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4414f6d907424a1abb56bccd1d1b125444e7c716
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647997"
---
# <a name="add-search-to-a-tool-window"></a>Agregar búsqueda a una ventana de herramientas
Al crear o actualizar una ventana de herramientas en la extensión, puede Agregar la misma funcionalidad de búsqueda que aparece en otra parte de Visual Studio. Esta funcionalidad incluye las siguientes características:

- Un cuadro de búsqueda que siempre se encuentra en un área personalizada de la barra de herramientas.

- Indicador de progreso que está superpuesto en el propio cuadro de búsqueda.

- La capacidad de mostrar los resultados en cuanto escriba cada carácter (búsqueda instantánea) o solo después de elegir la tecla **entrar** (buscar a petición).

- Una lista que muestra los términos que ha buscado más recientemente.

- La capacidad de filtrar búsquedas por campos específicos o aspectos de los destinos de búsqueda.

Al seguir este tutorial, aprenderá a realizar las siguientes tareas:

1. Cree un proyecto de VSPackage.

2. Cree una ventana de herramientas que contenga un control UserControl con un cuadro de texto de solo lectura.

3. Agregue un cuadro de búsqueda a la ventana de herramientas.

4. Agregue la implementación de búsqueda.

5. Habilite la búsqueda instantánea y la presentación de una barra de progreso.

6. Agregue una opción de **coincidencia de mayúsculas y minúsculas** .

7. Agregue un filtro de **solo líneas de búsqueda** .

## <a name="to-create-a-vsix-project"></a>Para crear un proyecto de VSIX

1. Cree un proyecto VSIX denominado `TestToolWindowSearch` con una ventana de herramientas denominada **TestSearch**. Si necesita ayuda para hacerlo, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Para crear una ventana de herramientas

1. En el proyecto de `TestToolWindowSearch`, abra el archivo *TestSearchControl. Xaml* .

2. Reemplace el bloque de `<StackPanel>` existente por el siguiente bloque, que agrega un <xref:System.Windows.Controls.TextBox> de solo lectura a la <xref:System.Windows.Controls.UserControl> en la ventana de herramientas.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. En el archivo *TestSearchControl.Xaml.CS* , agregue la siguiente directiva using:

    ```csharp
    using System.Text;
    ```

4. Quite el método `button1_Click()`.

     En la clase **TestSearchControl** , agregue el código siguiente.

     Este código agrega una propiedad Public <xref:System.Windows.Controls.TextBox> denominada **SearchResultsTextBox** y una propiedad de cadena pública denominada **SearchContent**. En el constructor, SearchResultsTextBox se establece en el cuadro de texto y SearchContent se inicializa en un conjunto de cadenas delimitadas por nueva línea. El contenido del cuadro de texto también se inicializa en el conjunto de cadenas.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

6. En la barra de menús, elija **ver**  > **otras ventanas**  > **TestSearch**.

     Aparece la ventana de herramientas, pero el control de búsqueda todavía no aparece.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Para agregar un cuadro de búsqueda a la ventana de herramientas

1. En el archivo *TestSearch.CS* , agregue el código siguiente a la clase `TestSearch`. El código invalida la propiedad <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> de modo que el descriptor de acceso get devuelva `true`.

     Para habilitar la búsqueda, debe invalidar la propiedad <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>. La clase <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> y proporciona una implementación predeterminada que no habilita la búsqueda.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Compile la solución y comience la depuración. Aparece la instancia experimental.

3. En la instancia experimental de Visual Studio, Abra **TestSearch**.

     En la parte superior de la ventana de herramientas, aparece un control de búsqueda con una marca de agua de **búsqueda** y un icono de lupa. Sin embargo, la búsqueda no funciona aún porque no se ha implementado el proceso de búsqueda.

## <a name="to-add-the-search-implementation"></a>Para agregar la implementación de búsqueda
 Cuando se habilita la búsqueda en un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, como en el procedimiento anterior, la ventana de herramientas crea un host de búsqueda. Este host configura y administra los procesos de búsqueda, que siempre se producen en un subproceso en segundo plano. Dado que la clase <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> administra la creación del host de búsqueda y la configuración de la búsqueda, solo necesita crear una tarea de búsqueda y proporcionar el método de búsqueda. El proceso de búsqueda se produce en un subproceso en segundo plano y las llamadas al control de la ventana de herramientas se producen en el subproceso de la interfaz de usuario. Por lo tanto, debe usar el método [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) para administrar las llamadas que realice para tratar con el control.

1. En el archivo *TestSearch.CS* , agregue las siguientes directivas de `using`:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. En la clase `TestSearch`, agregue el código siguiente, que realiza las acciones siguientes:

    - Invalida el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> para crear una tarea de búsqueda.

    - Invalida el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> para restaurar el estado del cuadro de texto. Se llama a este método cuando un usuario cancela una tarea de búsqueda y cuando un usuario establece o desestablece opciones o filtros. En el subproceso de la interfaz de usuario se llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> y a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>. Por lo tanto, no es necesario tener acceso al cuadro de texto mediante el método [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Crea una clase denominada `TestSearchTask` que hereda de <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, que proporciona una implementación predeterminada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.

         En `TestSearchTask`, el constructor establece un campo privado que hace referencia a la ventana de herramientas. Para proporcionar el método de búsqueda, invalide los métodos <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> y <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>. El método <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> es donde se implementa el proceso de búsqueda. Este proceso incluye la realización de la búsqueda, la visualización de los resultados de la búsqueda en el cuadro de texto y la llamada a la implementación de la clase base de este método para informar de que la búsqueda se ha completado.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Realice los pasos siguientes para probar la implementación de la búsqueda:

    1. Vuelva a compilar el proyecto e iniciar la depuración.

    2. En la instancia experimental de Visual Studio, vuelva a abrir la ventana de herramientas, escriba el texto de búsqueda en la ventana de búsqueda y haga clic en **entrar**.

         Deberían aparecer los resultados correctos.

## <a name="to-customize-the-search-behavior"></a>Para personalizar el comportamiento de búsqueda
 Al cambiar la configuración de búsqueda, puede realizar una serie de cambios en el modo en que aparece el control de búsqueda y cómo se lleva a cabo la búsqueda. Por ejemplo, puede cambiar la marca de agua (el texto predeterminado que aparece en el cuadro de búsqueda), el ancho mínimo y máximo del control de búsqueda y si desea mostrar una barra de progreso. También puede cambiar el punto en el que los resultados de la búsqueda empiezan a aparecer (a petición o búsqueda instantánea) y si se muestra una lista de términos para los que se ha buscado recientemente. Puede encontrar la lista completa de valores en la clase <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>.

1. En el archivo * TestSearch.cs *, agregue el siguiente código a la clase `TestSearch`. Este código habilita la búsqueda instantánea en lugar de la búsqueda a petición (lo que significa que el usuario no tiene que hacer clic en **entrar**). El código invalida el método `ProvideSearchSettings` de la clase `TestSearch`, que es necesario para cambiar la configuración predeterminada.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Pruebe la nueva configuración volviendo a compilar la solución y reiniciando el depurador.

     Los resultados de la búsqueda aparecen cada vez que se escribe un carácter en el cuadro de búsqueda.

3. En el método `ProvideSearchSettings`, agregue la línea siguiente, que habilita la presentación de una barra de progreso.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Para que aparezca la barra de progreso, se debe informar del progreso. Para notificar el progreso, quite el comentario del código siguiente en el método `OnStartSearch` de la clase `TestSearchTask`:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Para ralentizar el procesamiento suficiente para que la barra de progreso esté visible, quite la marca de comentario de la siguiente línea en el método `OnStartSearch` de la clase `TestSearchTask`:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Pruebe la nueva configuración volviendo a compilar la solución y empezando a depurar.

     La barra de progreso aparece en la ventana Buscar (como una línea azul debajo del cuadro de texto Buscar) cada vez que realiza una búsqueda.

## <a name="to-enable-users-to-refine-their-searches"></a>Para permitir que los usuarios definan sus búsquedas
 Puede permitir que los usuarios definan sus búsquedas por medio de opciones como **coincidencia de mayúsculas y minúsculas** o **palabras completas**. Las opciones pueden ser booleanas, que aparecen como casillas de verificación o comandos, que aparecen como botones. En este tutorial, creará una opción booleana.

1. En el archivo *TestSearch.CS* , agregue el código siguiente a la clase `TestSearch`. El código invalida el método de `SearchOptionsEnum`, que permite a la implementación de búsqueda detectar si una opción determinada está activada o desactivada. El código de `SearchOptionsEnum` agrega una opción para buscar coincidencias de mayúsculas y minúsculas en un enumerador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>. La opción de coincidencia de mayúsculas y minúsculas también está disponible como la propiedad `MatchCaseOption`.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. En la clase `TestSearchTask`, quite la marca de comentario de la siguiente línea en el método `OnStartSearch`:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Pruebe la opción:

    1. Compile la solución y comience la depuración. Aparece la instancia experimental.

    2. En la ventana de herramientas, elija la flecha abajo situada a la derecha del cuadro de texto.

         Aparece la casilla **Coincidir mayúsculas y minúsculas** .

    3. Active la casilla **Coincidir mayúsculas y minúsculas** y realice algunas búsquedas.

## <a name="to-add-a-search-filter"></a>Para agregar un filtro de búsqueda
 Puede Agregar filtros de búsqueda que permitan a los usuarios restringir el conjunto de destinos de búsqueda. Por ejemplo, puede filtrar los archivos en el explorador de archivos por las fechas en las que se modificaron más recientemente y sus extensiones de nombre de archivo. En este tutorial, agregará un filtro solo para las líneas pares. Cuando el usuario elige ese filtro, el host de búsqueda agrega las cadenas que especifique a la consulta de búsqueda. A continuación, puede identificar estas cadenas dentro del método de búsqueda y filtrar los destinos de búsqueda en consecuencia.

1. En el archivo *TestSearch.CS* , agregue el código siguiente a la clase `TestSearch`. El código implementa `SearchFiltersEnum` agregando un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> que especifica que se filtren los resultados de la búsqueda para que solo aparezcan las líneas pares.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Ahora, el control de búsqueda muestra el filtro de búsqueda `Search even lines only`. Cuando el usuario elige el filtro, la cadena `lines:"even"` aparece en el cuadro de búsqueda. Otros criterios de búsqueda pueden aparecer al mismo tiempo que el filtro. Las cadenas de búsqueda pueden aparecer antes del filtro, después del filtro o ambos.

2. En el archivo *TestSearch.CS* , agregue los siguientes métodos a la clase `TestSearchTask`, que se encuentra en la clase `TestSearch`. Estos métodos admiten el método `OnStartSearch`, que se modificará en el paso siguiente.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. En la clase `TestSearchTask`, actualice el método `OnStartSearch` con el código siguiente. Este cambio actualiza el código para admitir el filtro.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Pruebe el código.

5. Compile la solución y comience la depuración. En la instancia experimental de Visual Studio, abra la ventana de herramientas y, a continuación, elija la flecha abajo en el control de búsqueda.

     Las casillas **Coincidir mayúsculas y minúsculas** y **Buscar solo líneas de búsqueda** aparecen.

6. Elija el filtro.

     El cuadro de búsqueda contiene **líneas: "par"** y aparecen los siguientes resultados:

     2 bueno

     4 bueno

     6 adiós

7. Elimine `lines:"even"` en el cuadro de búsqueda, active la casilla **Coincidir mayúsculas y minúsculas** y escriba `g` en el cuadro de búsqueda.

     Aparecen los siguientes resultados:

     1 Go

     2 bueno

     5 Adiós

8. Elija la X que se encuentra en el lado derecho del cuadro de búsqueda.

     La búsqueda se borra y el contenido original aparece. Sin embargo, la casilla **Coincidir mayúsculas y minúsculas** sigue activada.
