---
title: Procedimiento Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6841b8a91cec24f467f6e3f684cbb27e25c9fa63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899354"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Procedimiento Desactivación de la activación de URL de aplicaciones ClickOnce

Normalmente, una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se inicia automáticamente después de que se instale desde un servidor web. Por motivos de seguridad, puede deshabilitar este comportamiento e indicar a los usuarios que, en su lugar, inicien la aplicación desde el menú **Inicio**. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.

Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede utilizar para aplicaciones solo en línea, que se pueden iniciar utilizando su dirección URL. Para obtener más información acerca de la diferencia entre las aplicaciones solo en línea e instaladas, consulte [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Este procedimiento usa la herramienta de Kit de desarrollo de Software (SDK) de Windows MageUI.exe. Para obtener más información sobre esta herramienta, consulte [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). También puede realizar este procedimiento con Visual Studio.

## <a name="procedure"></a>Procedimiento

### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación

1. Abra el manifiesto de implementación en MageUI.exe. Si aún no ha creado uno, siga los pasos descritos en [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Seleccione la pestaña **Opciones de implementación**.

3. Desactive la casilla de verificación **Ejecutar automáticamente la aplicación después de instalarla**.

4. Guarde y firme el manifiesto.

## <a name="see-also"></a>Vea también

- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)