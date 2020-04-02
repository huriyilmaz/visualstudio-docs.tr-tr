---
title: 'Nasıl Yapılsın: İlk Hangi Hedefin Oluşturulabildiğini Belirt | Microsoft Dokümanlar'
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
ms.openlocfilehash: c679b2a43ec799035f9bafb6a03a546808498342
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543981"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Nasıl yapılır: İlk hangi hedefi oluşturacaklarını belirtin

Proje dosyası, projenin nasıl `Target` oluşturulabileceğini tanımlayan bir veya daha fazla öğe içerebilir. Microsoft Build Engine (MSBuild) altyapısı, proje dosyası bir `DefaultTargets` öznitelik, öznitelik `InitialTargets` veya hedef **-hedef** anahtarı nı kullanarak komut satırında belirtilmediği sürece bulduğu ilk projeyi ve herhangi bir bağımlılık oluşturur.
## <a name="use-the-initialtargets-attribute"></a>InitialTargets özniteliğini kullanma

Hedefkomut `InitialTargets` satırında `Project` veya öznitelikte `DefaultTargets` belirtilmiş olsa bile, öğenin özniteliği ilk çalışacak bir hedef belirtir.

#### <a name="to-specify-one-initial-target"></a>Bir ilk hedef belirtmek için

- Öğenin özniteliği `InitialTargets` içinde varsayılan hedefi belirtin. `Project` Örnek:

   `<Project InitialTargets="Clean">`

  Hedefleri sırayla listeleyerek ve `InitialTargets` her hedefi ayırmak için bir yarı sütun kullanarak öznitelikte birden fazla ilk hedef belirtebilirsiniz. Listedeki hedefler sırayla çalıştırılacaktır.

#### <a name="to-specify-more-than-one-initial-target"></a>Birden fazla ilk hedef belirtmek için

- İlk hedefleri, yarı iki nokta ile `InitialTargets` ayrılmış, öğenin özniteliği listele. `Project` Örneğin, `Clean` hedefi çalıştırmak için ve `Compile` ardından hedefi, yazın:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Varsayılan Hedefler özniteliğini kullanma

 Bir `DefaultTargets` hedef komut `Project` satırında açıkça belirtilmemişse, öğenin özniteliği hangi hedefin veya hedeflerin oluşturulmadığını belirtir. Hedefler `InitialTargets` hem `DefaultTargets` özniteliklerde hem de özniteliklerde belirtilirse ve komut satırında `InitialTargets` hedef belirtilmemişse, MSBuild öznitelikte `DefaultTargets` belirtilen hedeflertarafından izlenen öznitelikte belirtilen hedefleri çalıştırUr.

#### <a name="to-specify-one-default-target"></a>Bir varsayılan hedef belirtmek için

- Öğenin özniteliği `DefaultTargets` içinde varsayılan hedefi belirtin. `Project` Örnek:

   `<Project DefaultTargets="Compile">`

  Hedefleri sırayla listeleyerek ve `DefaultTargets` her hedefi ayırmak için bir yarı sütun kullanarak öznitelikte birden fazla varsayılan hedef belirtebilirsiniz. Listedeki hedefler sırayla çalıştırılacaktır.

#### <a name="to-specify-more-than-one-default-target"></a>Birden fazla varsayılan hedef belirtmek için

- Öğenin özniteliği olarak, `DefaultTargets` yarı iki nokta ile ayrılmış varsayılan hedefleri listele. `Project` Örneğin, `Clean` hedefi çalıştırmak için ve `Compile` ardından hedefi, yazın:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Hedef Anahtarını kullanma

 Proje dosyasında varsayılan bir hedef tanımlanmamışsa veya bu varsayılan hedefi kullanmak istemiyorsanız, farklı bir hedef belirtmek için komut satırı anahtarı **-hedefini** kullanabilirsiniz. **Öznitelik** te `DefaultTargets` belirtilen hedefler yerine -hedef anahtarı ile belirtilen hedef veya hedefler çalıştırılır. Öznitelikte `InitialTargets` belirtilen hedefler her zaman önce çalışır.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Önce varsayılan hedef dışında bir hedef kullanmak için

- **-target** komut satırı anahtarını kullanarak hedefi ilk hedef olarak belirtin. Örnek:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Önce varsayılan hedefler dışında birkaç hedef kullanmak için

- **-target** komut satırı anahtarını kullanarak, yarı kolon veya virgülle ayrılan hedefleri listele. Örnek:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [Hedef](../msbuild/msbuild-targets.md)
- [Nasıl yapılsın: Yapıyı temizleme](../msbuild/how-to-clean-a-build.md)
