---
title: Enlazar controles de Windows Forms a datos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672985"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Enlazar controles de Windows Forms a datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para mostrar datos a los usuarios de la aplicación, puede enlazarlos a Windows Forms. Para crear estos controles enlazados a datos, puede arrastrar elementos desde la ventana **orígenes de datos** hasta el diseñador de Windows Forms en Visual Studio. En este tema se describen algunas de las tareas, herramientas y clases más comunes para crear aplicaciones de Windows Forms enlazadas a datos.

 ![Operación de arrastre de origen de datos](../data-tools/media/raddata-data-source-drag-operation.png "raddata operación de arrastre de origen de datos")

 Para obtener información general sobre cómo crear controles enlazados a datos en Visual Studio, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obtener más información sobre el enlace de datos en Windows Forms, vea [Windows Forms enlace de datos](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>En esta sección

- [Enlazar controles de Windows Forms a datos](../data-tools/bind-windows-forms-controls-to-data.md)

- [Confirmar tareas de edición en proceso en controles enlazados a datos antes de guardar los datos](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Crear tablas de búsqueda en aplicaciones de Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Crear Windows Forms para buscar datos](../data-tools/create-a-windows-form-to-search-data.md)

- [Crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Crear un control de usuario de Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Pasar datos de un formulario a otro](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource (componente)
 El componente <xref:System.Windows.Forms.BindingSource> sirve para dos propósitos. Primero, proporciona una capa de abstracción cuando se enlazan los controles de su formulario a los datos. Los controles del formulario se enlazan al componente <xref:System.Windows.Forms.BindingSource> (en lugar de enlazarlos directamente a un origen de datos).

 Segundo, puede administrar una colección de objetos. Al agregar un tipo a <xref:System.Windows.Forms.BindingSource>, se crea una lista de ese tipo.

 Para obtener más información acerca del componente <xref:System.Windows.Forms.BindingSource>, vea:

- [Componente BindingSource](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [Información general sobre el componente BindingSource](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Arquitectura del componente BindingSource](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator (control)
 Este componente proporciona una interfaz de usuario para navegar por los datos mostrados en una aplicación Windows. Para más información, consulte [Control BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView (control)
 Para mostrar y editar datos tabulares de muchos tipos diferentes de orígenes de datos, use el control <xref:System.Windows.Forms.DataGridView>. Puede enlazar datos a un <xref:System.Windows.Forms.DataGridView> mediante la propiedad <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Para obtener más información, vea [información general sobre el control DataGridView](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Vea también
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
