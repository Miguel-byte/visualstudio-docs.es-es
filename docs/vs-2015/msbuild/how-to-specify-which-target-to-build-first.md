---
title: Procedimiento Especificar qué destino usar primero al compilar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178340"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Procedimiento Especificar qué destino se compila primero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un archivo del proyecto puede contener uno o vario elementos `Target` que definen cómo se compila el proyecto. El motor [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) compila el primer proyecto que encuentra, así como las dependencias, a menos que el archivo del proyecto contenga un atributo `DefaultTargets`, un atributo `InitialTargets` o que un destino se especifique en la línea de comandos mediante el modificador **/target**.  
  
## <a name="using-the-initialtargets-attribute"></a>Usar el atributo InitialTargets  
 El atributo `InitialTargets` del elemento `Project` especifica un destino que se ejecutará en primer lugar, incluso si los destinos se especifican en la línea de comandos o en el atributo `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Para especificar un destino inicial  
  
- Especifique el destino predeterminado en el atributo `InitialTargets` del elemento `Project`. Por ejemplo:  
  
   `<Project InitialTargets="Clean">`  
  
  Puede especificar más de un destino inicial en el atributo `InitialTargets` enumerando los destinos en orden y utilizando un punto y coma para separar cada destino. Los objetivos de la lista se ejecutarán secuencialmente.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Para especificar más de un destino inicial  
  
- Enumere los destinos iniciales, separados por punto y coma, en el atributo `InitialTargets` del elemento `Project`. Por ejemplo, para ejecutar el destino `Clean` y, a continuación, el destino `Compile`, escriba:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Usar el atributo DefaultTargets  
 El atributo `DefaultTargets` del elemento `Project` especifica qué destinos se compilan si un destino no se especifica explícitamente en la línea de comandos. Si se especifican los destinos en los atributos `InitialTargets` y `DefaultTargets` y no se especifica ningún destino en la línea de comandos, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ejecuta los destinos especificados en el atributo `InitialTargets` seguido por los destinos especificados en el atributo `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Para especificar un destino predeterminado  
  
- Especifique el destino predeterminado en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo:  
  
   `<Project DefaultTargets="Compile">`  
  
  Puede especificar más de un destino predeterminado en el atributo `DefaultTargets` enumerando los destinos en orden y utilizando un punto y coma para separar cada destino. Los objetivos de la lista se ejecutarán secuencialmente.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Para especificar más de un destino predeterminado  
  
- Enumere los destinos predeterminados, separados por punto y coma, en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo, para ejecutar el destino `Clean` y, a continuación, el destino `Compile`, escriba:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Usar el modificador /target  
 Si un destino predeterminado no está definido en el archivo del proyecto, o si no quiere utilizar ese destino predeterminado, puede utilizar el modificador de línea de comandos **/target** para especificar un destino diferente. Los destinos especificados con el modificador **/target** se ejecutan en lugar de los destinos especificados por el atributo `DefaultTargets`. Los destinos especificados en el atributo `InitialTargets` siempre se ejecutan primero.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Para utilizar primero un destino distinto del destino predeterminado  
  
- Especifique el destino como el primer destino mediante el modificador de línea de comandos **/target**. Por ejemplo:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Para utilizar primero varios destinos distintos de los destinos predeterminados  
  
- Enumere los destinos, separados por punto y coma o comas, mediante el conmutador de línea de comandos **/target**. Por ejemplo:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Vea también
  [MSBuild](msbuild.md)  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Procedimientos: Limpiar una compilación](../msbuild/how-to-clean-a-build.md)
