---
title: 'Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e008e3181cd7c633179f35e7639265a2495fafe2
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633804"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme

Proje dosyası, projenin nasıl oluşturulduğunu tanımlayan bir veya daha fazla `Target` öğesi içerebilir. Microsoft Build Engine (MSBuild) altyapısı, bulduğu ilk projeyi ve tüm bağımlılıkları oluşturur; proje dosyası bir `DefaultTargets` özniteliği, bir `InitialTargets` özniteliği veya **hedef anahtar kullanılarak** komut satırında belirtilir.
## <a name="use-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma

 `Project` öğesinin `InitialTargets` özniteliği, hedefler komut satırında veya `DefaultTargets` özniteliğinde belirtilmiş olsa bile önce çalıştırılacak hedefi belirtir.
`Project` öğesinin `InitialTargets` özniteliği, hedefler komut satırında veya `DefaultTargets` özniteliğinde belirtilmiş olsa bile önce çalıştırılacak hedefi belirtir.

#### <a name="to-specify-one-initial-target"></a>Bir başlangıç hedefi belirtmek için

- `Project` öğesinin `InitialTargets` özniteliğinde varsayılan hedefi belirtin. Örnek:

   `<Project InitialTargets="Clean">`

  Hedefleri sırayla listeleyerek `InitialTargets` özniteliğinde birden fazla başlangıç hedefi belirtebilir ve her hedefi ayırmak için noktalı virgül kullanabilirsiniz. Listedeki hedefler sırayla çalıştırılır.

#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için

- `Project` öğesinin `InitialTargets` özniteliğinde, noktalı virgülle ayırarak ilk hedefleri listeleyin. Örneğin, `Clean` hedefini ve sonra `Compile` hedefini çalıştırmak için şunu yazın:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>DefaultTargets özniteliğini kullanma

 `Project` öğesinin `DefaultTargets` özniteliği, bir hedef açıkça komut satırında belirtilmemişse, hangi hedefin veya hedeflerin derlenmediğini belirtir. Hedefler hem `InitialTargets` hem de `DefaultTargets` özniteliklerde belirtilirse ve komut satırında hiçbir hedef belirtilmemişse, MSBuild, `InitialTargets` özniteliğinde belirtilen hedefleri ve ardından `DefaultTargets` özniteliğinde belirtilen hedefleri çalıştırır.

#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için

- `Project` öğesinin `DefaultTargets` özniteliğinde varsayılan hedefi belirtin. Örnek:

   `<Project DefaultTargets="Compile">`

  Hedefleri sırayla listeleyerek `DefaultTargets` özniteliğinde birden fazla varsayılan hedef belirtebilir ve her hedefi ayırmak için noktalı virgül kullanabilirsiniz. Listedeki hedefler sırayla çalıştırılır.

#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için

- `Project` öğesinin `DefaultTargets` özniteliğinde, noktalı virgülle ayırarak varsayılan hedefleri listeleyin. Örneğin, `Clean` hedefini ve sonra `Compile` hedefini çalıştırmak için şunu yazın:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>-Target anahtarını kullanma

 Proje dosyasında varsayılan bir hedef tanımlanmamışsa veya bu varsayılan hedefi kullanmak istemiyorsanız, farklı bir hedef belirtmek için anahtar **-hedef** komut satırını kullanabilirsiniz. **-Target** anahtarıyla belirtilen hedef veya hedefler, `DefaultTargets` özniteliği tarafından belirtilen hedefler yerine çalıştırılır. `InitialTargets` özniteliğinde belirtilen hedefler her zaman önce çalıştırılır.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Önce varsayılan hedeften farklı bir hedef kullanmak için

- Hedefi, **-target** komut satırı anahtarını kullanarak ilk hedef olarak belirtin. Örnek:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Önce varsayılan hedefleri dışında birkaç hedefi kullanmak için

- Hedefleri, **-target** komut satırı anahtarını kullanarak noktalı virgül veya virgülle ayırarak listeleyin. Örnek:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [Hedefler](../msbuild/msbuild-targets.md)
- [Nasıl yapılır: derlemeyi Temizleme](../msbuild/how-to-clean-a-build.md)
