---
title: Procedimiento Incluir un archivo de datos en una aplicación ClickOnce | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd2db09937ad76c0ea4c990fcdba5c34a0f8f66c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898641"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Procedimiento Inclusión de un archivo de datos en una aplicación ClickOnce
Cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que se instala se asigna a un directorio de datos en el disco local del equipo de destino donde la aplicación puede administrar sus propios datos. Los archivos de datos pueden incluir cualquier tipo de archivo: archivos de texto, archivos XML o incluso bases de datos de Microsoft Access (*.mdb*) los archivos. Los procedimientos siguientes muestran cómo agregar un archivo de datos de cualquier tipo en su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Para incluir un archivo de datos mediante Mage.exe

1. Agregue el archivo de datos en el directorio de aplicación con el resto de los archivos de la aplicación.

    Normalmente, será el directorio de la aplicación a un directorio etiquetado con la versión actual de la implementación, por ejemplo, v1.0.0.0.

2. Actualice el manifiesto de aplicación a la lista el archivo de datos.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Llevar a cabo esta tarea vuelve a crea la lista de archivos en el manifiesto de aplicación y también genera automáticamente las firmas hash.

3. Abra el manifiesto de aplicación en el editor XML o texto que prefiera y busque el `file` (elemento) para el archivo agregado recientemente.

    Si agrega un archivo XML denominado `Data.xml`, el archivo tendrá un aspecto similar al siguiente ejemplo de código.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Agregue el atributo `type` a este elemento y proporcionarla con un valor de `data`.

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Volver a firmar el manifiesto de aplicación con el par de claves o un certificado y, a continuación, volver a firmar el manifiesto de implementación.

    Deberá volver a firmar el manifiesto de implementación porque ha cambiado su hash del manifiesto de aplicación.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Para incluir un archivo de datos mediante MageUI.exe

1. Agregue el archivo de datos en el directorio de aplicación con el resto de los archivos de la aplicación.

2. Normalmente, será el directorio de la aplicación a un directorio etiquetado con la versión actual de la implementación, por ejemplo, v1.0.0.0.

3. En el **archivo** menú, haga clic en **abrir** para abrir el manifiesto de aplicación.

4. Seleccione el **archivos** ficha.

5. En el cuadro de texto en la parte superior de la ficha, escriba el directorio que contiene los archivos de la aplicación y, a continuación, haga clic en **rellenar**.

     El archivo de datos aparecerá en la cuadrícula.

6. Establecer el **tipo de archivo** valor del archivo de datos a **datos**.

7. Guarde el manifiesto de aplicación y, a continuación, volver a firmar el archivo.

     *MageUI.exe* le solicitará que vuelva a firmar el archivo.

8. Volver a firmar el manifiesto de implementación

     Deberá volver a firmar el manifiesto de implementación porque ha cambiado su hash del manifiesto de aplicación.

## <a name="see-also"></a>Vea también
- [Acceso a datos locales y remotos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)