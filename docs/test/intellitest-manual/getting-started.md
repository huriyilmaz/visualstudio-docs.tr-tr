---
title: IntelliTest'e Giriş
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 113233c985053cfe838f385a36ec59cc211bfcb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591664"
---
# <a name="get-started-with-microsoft-intellitest"></a>Microsoft IntelliTest ile başlayın

* Bu IntelliTest ile ilk kez ise:
  * Kanal [9 videosunu](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest) izleyin
  * [MSDN Dergisi hakkında](https://msdn.microsoft.com/magazine/dn904672.aspx) bu genel bakışı okuyun
  * [belgelerimizi](../../test/generate-unit-tests-for-your-code-with-intellitest.md) okuyun
* [Stack Taşma](https://stackoverflow.com/questions/tagged/intellitest) ile ilgili sorularınızı sorun
* Bu başvuru kılavuzunun geri kalanını okuyun
* Hızlı başvuru için bu sayfayı yazdırın

## <a name="important-attributes"></a>Önemli öznitelikler

* [PexClass](attribute-glossary.md#pexclass) **PUT** içeren bir türü işaretler
* [PexMethod](attribute-glossary.md#pexmethod) bir **PUT** işaretleri
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) null olmayan bir parametre işaretler

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) bir test projesini projeye bağlar
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) enstrüman için bir montaj belirtir

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a>Önemli statik yardımcı sınıflar

* [PexAssume](static-helper-classes.md#pexassume) varsayımları değerlendirir (giriş filtreleme)
* [PexAssert](static-helper-classes.md#pexassert) iddiaları değerlendirir
* [PexChoose](static-helper-classes.md#pexchoose) yeni seçenekler (ek girişler) oluşturur
* [PexObserve](static-helper-classes.md#pexobserve) oluşturulan testlere canlı değerleri günlükleri

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
