---
title: Bir Özel Ana Bilgisayar kullanarak Metin Şablonlarını İşleme
description: Metin şablonu dönüştürme işleminin giriş olarak bir metin şablonu dosyası alır ve çıkış olarak bir metin dosyası ürettiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: ed2f7b273948bac1ba07322ed079dd5cbd92711a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637598"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Özel bir Konak kullanarak Metin Şablonlarını İşleme

Metin *şablonu dönüştürme* işlemi, giriş olarak bir *metin* şablonu dosyası alır ve çıkış olarak bir metin dosyası oluşturur. Metin dönüştürme altyapısını bir Visual Studio uzantısından veya uygulamanın yüklü olduğu bir makinede çalışan tek başına Visual Studio çağırabilirsiniz. Ancak, bir metin *templating ana bilgisayarı sağlanız gerekir.* Bu sınıf, derlemeler ve ekleme dosyaları gibi kaynakları bularak ve çıktı ve hata iletilerini işleme alarak şablonu ortama bağlar.

> [!TIP]
> Uygulama içinde çalıştıracak bir paket veya uzantı Visual Studio, kendi ana bilgisayarını yazmak yerine metin templating hizmetini kullanmayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. VS Uzantısında Metin Dönüştürmeyi Faturalama.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

> [!NOTE]
> Metin şablonu dönüştürmelerinin sunucu uygulamalarında kullanılması önerilmez. Metin şablonu dönüştürmelerinin tek bir iş parçacığı dışında kullanılması önerilmez. Bunun nedeni, metin şablonu oluşturma motorunun şablonları çevirmek, derlemek ve yürütmek için tek bir AppDomain öğesini yeniden kullanmasıdır. Çevrilen kod, iş parçacığı açısından güvenli olmak üzere tasarlanmamıştır. Altyapı, dosyaları tasarım zamanında bir Visual Studio olarak işley için tasarlanmıştır.
>
> Çalışma zamanı uygulamaları için önceden işlenmemiş metin şablonları kullanmayı göz önünde bulundurabilirsiniz: bkz. [T4 Metin Şablonları ile](../modeling/run-time-text-generation-with-t4-text-templates.md)Çalışma Zamanı Metin Oluşturma.

Uygulamanız, derleme zamanında sabitlenmiş bir grup şablon kullanıyorsa, Önceden İşlenmiş Metin Şablonlarının kullanılması daha kolaydır. Ayrıca, bu yaklaşımı, uygulamanın yüklü olduğu bir makinede Visual Studio da kullanabilirsiniz. Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="execute-a-text-template-in-your-application"></a>Uygulamanıza Metin Şablonu Yürütme

Bir metin şablonu yürütmek için ProcessTemplate yöntemini <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> çağırabilirsiniz:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Uygulamanızın şablonu bularak sağlaması ve çıktı ile işlem yapması gerekir. 

 `host` [parametresinde, ITextTemplatingEngineHost uygulayan bir sınıf sağlanız gerekir.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) Bu, Motor tarafından geri çağrılır.

 Ana bilgisayar hataları günlüğe kaydedebilmeli, derleme ve ekleme dosyalarına yapılan başvuruları çözümleyebilmeli, şablonun yürütülebileceği bir Uygulama Etki Alanı sağlayabilmeli ve her yönerge için uygun işlemciyi çağırabilmelidir.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>**Microsoft.VisualStudio.TextTemplating. içinde \* tanımlanır. . 0.dll**, [ve ITextTemplatingEngineHost,](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) **Microsoft.VisualStudio.TextTemplating.Interfaces. içinde \* tanımlanır. . 0.dll.**

## <a name="in-this-section"></a>Bu Bölümde
 [Adım adım kılavuz: Özel Metin Şablonu Ana Bilgisayarı Oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md) Metin şablonu işlevselliğini uygulama dışında kullanılabilir yapan özel bir metin şablonu ana bilgisayarının nasıl Visual Studio.

## <a name="reference"></a>Başvuru
 [Itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>İlgili Bölümler

- [Metin Şablonu Dönüştürme Süreci,](../modeling/the-text-template-transformation-process.md) metin dönüştürmenin nasıl çalıştığını ve hangi bölümleri özelleştirebileceğinizi açıklar.
- [Özel T4 Metin Şablonu Yönerge İşlemcileri oluşturma,](../modeling/creating-custom-t4-text-template-directive-processors.md) metin şablonu yönerge işlemcileri için genel bir bakış sağlar.
