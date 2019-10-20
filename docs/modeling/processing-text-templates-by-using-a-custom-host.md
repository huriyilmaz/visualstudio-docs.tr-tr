---
title: Bir Özel Ana Bilgisayar kullanarak Metin Şablonlarını İşleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 171eb8810d74df5c1058ba055e598d04f9164633
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658299"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Özel bir Konak kullanarak Metin Şablonlarını İşleme

*Metin şablonu dönüştürme* işlemi, girdi olarak bir *metin şablonu* dosyası alır ve çıktı olarak bir metin dosyası üretir. Bir Visual Studio uzantısı 'ndan veya Visual Studio 'Nun yüklü olduğu bir makinede çalışan tek başına uygulamadan metin dönüştürme altyapısını çağırabilirsiniz. Ancak, bir *metin şablonu oluşturma Konağı*sağlamanız gerekir. Bu sınıf, derlemeler ve ekleme dosyaları gibi kaynakları bularak ve çıktı ve hata iletilerini işleme alarak şablonu ortama bağlar.

> [!TIP]
> Visual Studio içinde çalışacak bir paket veya uzantı yazıyorsanız, kendi ana bilgisayarınızı yazmak yerine metin şablonu oluşturma hizmetini kullanmayı göz önünde bulundurun. Daha fazla bilgi için bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Metin şablonu dönüştürmelerinin sunucu uygulamalarında kullanılması önerilmez. Metin şablonu dönüştürmelerinin tek bir iş parçacığı dışında kullanılması önerilmez. Bunun nedeni, metin şablonu oluşturma motorunun şablonları çevirmek, derlemek ve yürütmek için tek bir AppDomain öğesini yeniden kullanmasıdır. Çevrilen kod, iş parçacığı açısından güvenli olmak üzere tasarlanmamıştır. Altyapı, bir Visual Studio projesinde tasarım zamanında olduklarından dosyaları seri olarak işleyecek şekilde tasarlanmıştır.
>
> Çalışma zamanı uygulamaları için, önceden işlenmiş metin şablonlarını kullanmayı düşünün: bkz. [T4 metin şablonlarıyla çalışma zamanı metin oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).

Uygulamanız, derleme zamanında sabitlenmiş bir grup şablon kullanıyorsa, Önceden İşlenmiş Metin Şablonlarının kullanılması daha kolaydır. Uygulamanız, Visual Studio 'Nun yüklü olmadığı bir makinede çalışıyorsa de bu yaklaşımı kullanabilirsiniz. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="execute-a-text-template-in-your-application"></a>Uygulamanızda bir metin şablonu yürütün

Bir metin şablonunu yürütmek için <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> ProcessTemplate yöntemini çağırın:

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Uygulamanızın şablonu bularak sağlaması ve çıktı ile işlem yapması gerekir.

 @No__t_0 parametresinde, [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))uygulayan bir sınıf sağlamanız gerekir. Bu, Motor tarafından geri çağrılır.

 Ana bilgisayar hataları günlüğe kaydedebilmeli, derleme ve ekleme dosyalarına yapılan başvuruları çözümleyebilmeli, şablonun yürütülebileceği bir Uygulama Etki Alanı sağlayabilmeli ve her yönerge için uygun işlemciyi çağırabilmelidir.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>, **Microsoft. VisualStudio. Textşablon oluşturma. \* 0. dll**ve [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) **Microsoft. VisualStudio. textşablon. Interfaces. \*.0. dll**içinde tanımlanmıştır.

## <a name="in-this-section"></a>Bu Bölümde
 [Izlenecek yol: özel metin şablonu Konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md) Metin şablonu işlevselliğinin Visual Studio dışında kullanılabilir olmasını sağlayan bir özel metin şablonu ana bilgisayarı oluşturmayı gösterir.

## <a name="reference"></a>Başvuru
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>İlgili Bölümler

- Metin [şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md) , metin dönüşümünün nasıl çalıştığını ve hangi parçaları özelleştirebileceğinizi açıklar.
- [Özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md) , metin şablonu yönerge işlemcileri için bir genel bakış sağlar.