---
title: 'Nasıl: İlk Derleme Hedefinin Hangi | Microsoft Docs'
description: Proje dosyalarında ilk olarak derlemek için ilk hedefleri veya varsayılan hedefleri MSBuild öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 26d5c3f4095dec633b853e6cb6cd141975b9cc11
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625683"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl yapılır: Önce hangi hedefin derlemek için olduğunu belirtme

Proje dosyası, projenin nasıl inşa `Target` edildiklerini tanımlayan bir veya daha fazla öğe içerebilir. Proje Microsoft Build Engine özniteliği, özniteliği veya hedef komut satırına -target anahtarı kullanılarak belirtilmemişse, Microsoft Build Engine (MSBuild) altyapısı bulduğu ilk hedefi ve tüm bağımlılıkları `DefaultTargets` `InitialTargets` derlemez. 
## <a name="use-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma

öğesinin özniteliği, hedefler komut satırı veya öznitelikte belirtilmiş olsa bile ilk `InitialTargets` `Project` olarak çalıştıracak bir hedef `DefaultTargets` belirtir.

#### <a name="to-specify-one-initial-target"></a>İlk hedeflerden birini belirtmek için

- öğesinin özniteliğinde `InitialTargets` varsayılan hedefi `Project` belirtin. Örnek:

   `<Project InitialTargets="Clean">`

  Öznitelikleri sırasıyla listeleerek ve her hedefi ayırmak için noktalı virgül kullanarak öznitelikte birden `InitialTargets` fazla başlangıç hedefi belirtsiniz. Listede hedefler sıralı olarak ecek.

#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için

- Öğenin özniteliğinde, noktalı virgülle ayrılmış şekilde `InitialTargets` ilk hedefleri `Project` listele. Örneğin, hedefi ve ardından `Clean` hedefi çalıştırmak `Compile` için yazın:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>DefaultTargets özniteliğini kullanma

 öğesinin özniteliği, komut satırı üzerinde açıkça bir hedef belirtilmezse hangi hedeflerin veya hedeflerin `DefaultTargets` `Project` nasıl bir şekilde ekli olduğunu belirtir. Hem hem de özniteliklerinde hedefler belirtilirse ve komut satırı üzerinde hedef belirtilmezse, MSBuild özniteliğinde belirtilen hedefleri ve ardından öznitelikte belirtilen hedefleri `InitialTargets` `DefaultTargets` `InitialTargets` `DefaultTargets` çalıştırır.

#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için

- öğesinin özniteliğinde `DefaultTargets` varsayılan hedefi `Project` belirtin. Örnek:

   `<Project DefaultTargets="Compile">`

  Öznitelikleri sırasıyla listeleerek ve her hedefi ayırmak için noktalı virgül kullanarak öznitelikte birden fazla varsayılan `DefaultTargets` hedef belirtsiniz. Listede hedefler sıralı olarak ecek.

#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için

- Öğenin özniteliğinde, noktalı virgülle ayrılmış varsayılan `DefaultTargets` hedefleri `Project` listele. Örneğin, hedefi ve ardından `Clean` hedefi çalıştırmak `Compile` için yazın:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>-target Anahtarını kullanma

 Proje dosyasında varsayılan hedef tanımlanmamışsa veya bu varsayılan hedefi kullanmak istemiyorsanız, farklı bir hedef belirtmek için **-target** komut satırı anahtarını kullanabilirsiniz. -target anahtarıyla belirtilen hedef **veya hedefler,** özniteliği tarafından belirtilen hedefler yerine `DefaultTargets` çalıştır. özniteliğinde belirtilen hedefler `InitialTargets` her zaman önce çalıştırın.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Önce varsayılan hedef dışında bir hedef kullanmak için

- **-target** komut satırı anahtarını kullanarak hedefi ilk hedef olarak belirtin. Örnek:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Önce varsayılan hedefler dışında birkaç hedef kullanmak için

- -target komut satırı anahtarını kullanarak hedefleri noktalı virgül veya **virgülle ayırarak** listele. Örnek:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [Targets](../msbuild/msbuild-targets.md)
- [Nasıl: Derlemeyi temizleme](../msbuild/how-to-clean-a-build.md)
