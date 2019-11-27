---
title: 'Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a567ca32a78eb6a78aad3702a68a6e08ed122db8
ms.sourcegitcommit: b04c603ce73b993d042ebdf7f3722cf4fe2ef7f4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74316503"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme
Proje dosyası, projenin nasıl oluşturulduğunu tanımlayan bir veya daha fazla `Target` öğesi içerebilir. [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) altyapısı, bulduğu ilk projeyi ve herhangi bir bağımlılığı, proje dosyası bir `DefaultTargets` özniteliği içermiyorsa, bir `InitialTargets` özniteliği veya **hedef anahtar kullanılarak** komut satırında belirtilir.

## <a name="use-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma
 `Project` öğesinin `InitialTargets` özniteliği, hedefler komut satırında veya `DefaultTargets` özniteliğinde belirtilmiş olsa bile önce çalıştırılacak hedefi belirtir.

#### <a name="to-specify-one-initial-target"></a>Bir başlangıç hedefi belirtmek için

- `Project` öğesinin `InitialTargets` özniteliğinde varsayılan hedefi belirtin. Örneğin:

   `<Project InitialTargets="Clean">`

  Hedefleri sırayla listeleyerek `InitialTargets` özniteliğinde birden fazla başlangıç hedefi belirtebilir ve her hedefi ayırmak için noktalı virgül kullanabilirsiniz. Listedeki hedefler sırayla çalıştırılır.

#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için

- `Project` öğesinin `InitialTargets` özniteliğinde, noktalı virgülle ayırarak ilk hedefleri listeleyin. Örneğin, `Clean` hedefini ve sonra `Compile` hedefini çalıştırmak için şunu yazın:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>DefaultTargets özniteliğini kullanma
 `Project` öğesinin `DefaultTargets` özniteliği, bir hedef açıkça komut satırında belirtilmemişse, hangi hedefin veya hedeflerin derlenmediğini belirtir. Hedefler hem `InitialTargets` hem de `DefaultTargets` özniteliklerde belirtilirse ve komut satırında hiçbir hedef belirtilmemişse, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] `InitialTargets` özniteliğinde belirtilen hedefleri ve ardından `DefaultTargets` özniteliğinde belirtilen hedefleri çalıştırır.

#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için

- `Project` öğesinin `DefaultTargets` özniteliğinde varsayılan hedefi belirtin. Örneğin:

   `<Project DefaultTargets="Compile">`

  Hedefleri sırayla listeleyerek `DefaultTargets` özniteliğinde birden fazla varsayılan hedef belirtebilir ve her hedefi ayırmak için noktalı virgül kullanabilirsiniz. Listedeki hedefler sırayla çalıştırılır.

#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için

- `Project` öğesinin `DefaultTargets` özniteliğinde, noktalı virgülle ayırarak varsayılan hedefleri listeleyin. Örneğin, `Clean` hedefini ve sonra `Compile` hedefini çalıştırmak için şunu yazın:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>-Target anahtarını kullanma
 Proje dosyasında varsayılan bir hedef tanımlanmamışsa veya bu varsayılan hedefi kullanmak istemiyorsanız, farklı bir hedef belirtmek için anahtar **-hedef** komut satırını kullanabilirsiniz. **-Target** anahtarıyla belirtilen hedef veya hedefler, `DefaultTargets` özniteliği tarafından belirtilen hedefler yerine çalıştırılır. `InitialTargets` özniteliğinde belirtilen hedefler her zaman önce çalıştırılır.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Önce varsayılan hedeften farklı bir hedef kullanmak için

- Hedefi, **-target** komut satırı anahtarını kullanarak ilk hedef olarak belirtin. Örneğin:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Önce varsayılan hedefleri dışında birkaç hedefi kullanmak için

- Hedefleri, **-target** komut satırı anahtarını kullanarak noktalı virgül veya virgülle ayırarak listeleyin. Örneğin:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild](../msbuild/msbuild.md)
- [Hedefler](../msbuild/msbuild-targets.md)
- [Nasıl yapılır: derlemeyi Temizleme](../msbuild/how-to-clean-a-build.md)
