---
title: Procedimiento Crear un manifiesto de producto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68f3006104b50876f6d2716ff4eb1efe0a705284
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928372"
---
# <a name="how-to-create-a-product-manifest"></a>Procedimiento Crear un manifiesto de producto
Para implementar los requisitos previos para la aplicación, puede crear un paquete de arranque. Un paquete de arranque contiene un archivo de manifiesto de producto único, pero un manifiesto del paquete para cada configuración regional. El manifiesto del paquete contiene aspectos específicos de la localización del paquete. Esto incluye cadenas, contratos de licencia del usuario final y los paquetes de idioma.

 Para obtener más información acerca de los manifiestos de paquete, vea [Cómo: Creación de un manifiesto de paquete](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Crear el manifiesto del producto

#### <a name="to-create-the-product-manifest"></a>Para crear el manifiesto del producto

1. Cree un directorio para el paquete de programa previo. Este ejemplo utiliza C:\package.

2. En Visual Studio, cree un nuevo archivo XML denominado *product.xml*y guárdelo en el *C:\package* carpeta.

3. Agregue el siguiente código XML para describir el código de producto y el espacio de nombres XML para el paquete. Reemplace el código de producto con un identificador único para el paquete.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Agregue el código XML para especificar que el paquete tiene una dependencia. Este ejemplo utiliza una dependencia en Microsoft Windows Installer 3.1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Agregue el código XML para mostrar todos los archivos que se encuentran en el paquete de arranque. Este ejemplo usa el nombre del archivo de paquete *CorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Copiar o mover el *CorePackage.msi* del archivo a la *C:\package* carpeta.

7. Agregue el código XML para instalar el paquete mediante los comandos del programa previo. El programa previo se agrega automáticamente el **/qn** marca a la *.msi* archivo, que se instalará de forma silenciosa. Si el archivo es un *.exe*, se ejecuta el programa previo del *.exe* archivo mediante el shell. El siguiente XML no muestra ningún argumento *CorePackage.msi*, pero puede colocar el argumento de línea de comandos en el `Arguments` atributo.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Agregue el siguiente código XML para comprobar si está instalado este paquete de programa previo. Reemplace el código de producto con el GUID del componente redistribuible.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Agregue el código XML para cambiar el comportamiento del programa previo dependiendo de si ya está instalado el componente de programa previo. Si el componente está instalado, el paquete de arranque no se ejecuta. El siguiente código XML comprueba si el usuario actual es un administrador porque este componente requiere privilegios administrativos.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Agregue el código XML para establecer los códigos de salida si la instalación es correcta y si es necesario un reinicio. El siguiente XML muestra que el error y FailReboot códigos, que indican que el programa previo no continuará la instalación de paquetes de salida.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Agregue el siguiente código XML para finalizar la sección para los comandos del programa previo.

    ```xml
        </Command>
    </Commands>
    ```

12. Mover el *C:\package* carpeta en el directorio de programa previo de Visual Studio. Para Visual Studio 2010, este es el *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* directory.

## <a name="example"></a>Ejemplo
 El manifiesto del producto contiene instrucciones de instalación de requisitos previos personalizados.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Custom.Bootstrapper.Package">

  <RelatedProducts>
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
  </RelatedProducts>

  <PackageFiles>
    <PackageFile Name="CorePackage.msi"/>
  </PackageFiles>

  <InstallChecks>
    <MsiProductCheck Product="IsMsiInstalled"
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
  </InstallChecks>

  <Commands>
    <Command PackageFile="CorePackage.msi" Arguments="">

      <InstallConditions>
        <BypassIf Property="IsMsiInstalled"
          Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
          Compare="ValueNotEqualTo" Value="True"
         String="NotAnAdmin"/>
      </InstallConditions>

      <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
      </ExitCodes>
    </Command>
  </Commands>
</Product>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)