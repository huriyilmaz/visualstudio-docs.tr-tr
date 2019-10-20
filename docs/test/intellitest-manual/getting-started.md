---
title: IntelliTest 'e giriş
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Get started
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 0d0d681c59935bbbb4591438f538d0c800cba489
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653214"
---
# <a name="get-started-with-microsoft-intellitest"></a>Microsoft IntelliTest ile çalışmaya başlama

* IntelliTest ile ilk kez bu ise:
  * [Channel 9 videosunu](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest) izleyin
  * [MSDN Magazine 'te bu genel bakışı](https://msdn.microsoft.com/magazine/dn904672.aspx) okuyun
  * [belgelerimizi](../../test/generate-unit-tests-for-your-code-with-intellitest.md) okuyun
* [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest) sorularınızı sorun
* Bu başvurunun geri kalanını okuyun
* Bu sayfayı hızlı başvuru için Yazdır

## <a name="important-attributes"></a>Önemli öznitelikler

* [PexClass](attribute-glossary.md#pexclass) , **PUT** içeren bir türü işaretler
* [PexMethod](attribute-glossary.md#pexmethod) bir **PUT** 'i işaretler
* [Pexassumenotnull](attribute-glossary.md#pexassumenotnull) , null olmayan bir parametreyi işaretler

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

* [Pexassemblyundertest](attribute-glossary.md#pexassemblyundertest) bir test projesini bir projeye bağlar
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) , işaretlemek için bir derlemeyi belirtir

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a>Önemli statik yardımcı sınıfları

* [Pexvarsay](static-helper-classes.md#pexassume) varsayımları değerlendirir (giriş filtresi)
* [Pexonaylama](static-helper-classes.md#pexassert) onayları değerlendirir
* [PexChoose](static-helper-classes.md#pexchoose) yeni seçimler oluşturur (ek girişler)
* [Pexgözlemleme](static-helper-classes.md#pexobserve) , canlı değerleri oluşturulan testlere kaydeder

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

## <a name="got-feedback"></a>Geri bildirim alındı mı?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)' na gönderin.
