---
title: 'Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178332"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl Yapılır: Önce Hangi Hedefin Derleneceğini Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje dosyası, projenin nasıl oluşturulduğunu tanımlayan bir veya daha fazla `Target` öğe içerebilir. [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)]( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) Altyapısı, bulduğu ilk projeyi ve tüm bağımlılıkları oluşturur, çünkü proje dosyası bir `DefaultTargets` öznitelik, bir öznitelik `InitialTargets` veya bir hedef, komut satırında **/target** anahtarı kullanılarak belirtilir.  
  
## <a name="using-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma  
 `InitialTargets`Öğesinin özniteliği, `Project` hedefler komut satırında veya özniteliğinde belirtilmiş olsa bile, ilk olarak çalıştırılacak hedefi belirtir `DefaultTargets` .  
  
#### <a name="to-specify-one-initial-target"></a>Bir başlangıç hedefi belirtmek için  
  
- Öğesinin özniteliğinde varsayılan hedefi belirtin `InitialTargets` `Project` . Örneğin:  
  
   `<Project InitialTargets="Clean">`  
  
  `InitialTargets`Hedefleri sırayla listeleyerek ve her hedefi ayırmak için noktalı virgül kullanarak öznitelikte birden fazla başlangıç hedefi belirtebilirsiniz. Listedeki hedefler sırayla çalıştırılır.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için  
  
- Öğe özniteliğinde noktalı virgülle ayırarak ilk hedefleri listeleyin `InitialTargets` `Project` . Örneğin, `Clean` hedefi ve sonra hedefi çalıştırmak için `Compile` şunu yazın:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>DefaultTargets özniteliğini kullanma  
 `DefaultTargets`Öğesinin özniteliği, `Project` bir hedef açık olarak komut satırında belirtilmemişse, hangi hedefin veya hedeflerin derlenmediğini belirtir. Hedefler hem `InitialTargets` hem de `DefaultTargets` özniteliklerde belirtilirse ve komut satırında hiçbir hedef belirtilmemişse, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özniteliğinde belirtilen hedefleri ve `InitialTargets` ardından özniteliğinde belirtilen hedefleri çalıştırır `DefaultTargets` .  
  
#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için  
  
- Öğesinin özniteliğinde varsayılan hedefi belirtin `DefaultTargets` `Project` . Örneğin:  
  
   `<Project DefaultTargets="Compile">`  
  
  `DefaultTargets`Hedefleri sırasıyla listeleyerek ve her hedefi ayırmak için noktalı virgül kullanarak öznitelikte birden fazla varsayılan hedef belirtebilirsiniz. Listedeki hedefler sırayla çalıştırılır.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için  
  
- Öğesinin özniteliğinde, varsayılan hedefleri noktalı virgülle ayırarak listeleyin `DefaultTargets` `Project` . Örneğin, `Clean` hedefi ve sonra hedefi çalıştırmak için `Compile` şunu yazın:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>/Target anahtarını kullanma  
 Proje dosyasında varsayılan bir hedef tanımlanmamışsa veya bu varsayılan hedefi kullanmak istemiyorsanız, farklı bir hedef belirtmek için komut satırı anahtarı **/target** komutunu kullanabilirsiniz. **/Target** anahtarıyla belirtilen hedef veya hedefler, özniteliği tarafından belirtilen hedefler yerine çalıştırılır `DefaultTargets` . Öznitelikte belirtilen hedefler `InitialTargets` her zaman önce çalıştırılır.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Önce varsayılan hedeften farklı bir hedef kullanmak için  
  
- Hedefi, **/target** komut satırı anahtarını kullanarak ilk hedef olarak belirtin. Örneğin:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Önce varsayılan hedefleri dışında birkaç hedefi kullanmak için  
  
- **/Target** komut satırı anahtarını kullanarak, hedefleri noktalı virgül veya virgülle ayırarak listeleyin. Örneğin:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Ayrıca Bkz.
  [MSBUILD](msbuild.md)  
 [Lerden](../msbuild/msbuild-targets.md)   
 [Nasıl Yapılır: Derlemeyi Temizleme](../msbuild/how-to-clean-a-build.md)
