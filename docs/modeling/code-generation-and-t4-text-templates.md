---
title: Kod Oluşturma ve T4 Metin Şablonları
description: T4 metin şablonunun metin blokları ile metin dosyası oluşturan denetim mantığının bir karışımı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: e862500f8e8518cc4f2b47402544431ef6706c25
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061447"
---
# <a name="code-generation-and-t4-text-templates"></a>Kod Oluşturma ve T4 Metin Şablonları

Bu Visual Studio *T4 metin şablonu,* metin dosyası oluşturan metin bloklarının ve denetim mantığının bir karışımıdır. Denetim mantığı, veya içinde program kodunun parçaları olarak [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] yazılır. 2015 Visual Studio 2 ve sonraki sürümlerde, T4 şablonları yönergelerinde C# sürüm 6.0 özelliklerini kullanabilirsiniz. Oluşturulan dosya, web sayfası veya kaynak dosyası ya da herhangi bir dilde program kaynak kodu gibi herhangi bir türden metin olabilir.

İki tür T4 metin şablonu vardır: çalışma zamanı ve tasarım zamanı.

## <a name="run-time-t4-text-templates"></a>Çalışma zamanı T4 metin şablonları

'Önceden işlenmemiş' şablonlar olarak da bilinen çalışma zamanı şablonları, genellikle çıkışının bir parçası olarak metin dizeleri oluşturmak için uygulamanıza yürütülür. Örneğin, HTML sayfası tanımlamak için bir şablon oluşturabilirsiniz:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Şablonun, oluşturulan çıkışa benzeye dikkat ediyor. Şablonun sonuçta elde edilen çıkışla benzerliği, şablonu değiştirmek istediğiniz zaman hatalardan kaçınmanıza yardımcı olur.

Ayrıca, şablon program kodu parçalarını içerir. Metin bölümlerini yinelemek, koşullu bölümler oluşturmak ve uygulamanıza gelen verileri göstermek için bu parçaları kullanabilirsiniz.

Çıktıyı oluşturmak için, uygulamanız şablon tarafından oluşturulan bir işlevi çağırıyor. Örnek:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Uygulamanız, yüklü yüklü bir Visual Studio çalıştırabilirsiniz.

Çalışma zamanı şablonu oluşturmak için projenize **önceden işlenmemiş bir metin** şablonu dosyası ekleyin. Alternatif olarak, bir düz metin dosyası  ekleyebilir ve Özel Araç özelliğini **TextTemplatingFilePreprocessor olarak ayarlayın.**

Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md) Şablonların söz dizimi hakkında daha fazla bilgi için [bkz. T4 Metin Şablonu Yazma.](../modeling/writing-a-t4-text-template.md)

## <a name="design-time-t4-text-templates"></a>Tasarım zamanı T4 metin şablonları

Tasarım zamanı şablonları, kaynak kodunun bir bölümünü ve uygulamanın diğer kaynaklarını tanımlar. Genellikle, tek bir giriş dosyasındaki veya veritabanındaki verileri okumak ve *.cs*, *.vb* veya diğer kaynak dosyalarınızı oluşturan birkaç şablon kullanırsınız. Her şablon bir dosya oluşturur. Bu komutlar, Visual Studio veya MSBuild.

Örneğin, giriş verileriniz yapılandırma verilerini bir XML dosyası olabilir. Geliştirme sırasında XML dosyasını düzenlemeniz sırasında metin şablonları uygulama kodunun bir bölümünü yeniden oluşturur. Şablonlardan biri aşağıdaki örnekteki gibi olabilir:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

XML dosyasındaki değerlere bağlı olarak, oluşturulan *.cs* dosyası aşağıdakine benzer:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Başka bir örnek olarak, giriş bir iş etkinliğinde iş akışının diyagramı olabilir. Kullanıcılar iş iş akışlarını değiştir yaptıklarında veya farklı bir iş akışına sahip yeni kullanıcılarla çalışmaya başsanız, kodu yeni modele uyacak şekilde kolayca yeniden üretebilirsiniz.

Tasarım zamanı şablonları, gereksinimler değiştiklerde yapılandırmayı daha hızlı ve daha güvenilir bir şekilde değiştirmenizi sağlar. Giriş genellikle iş akışı örneğinde olduğu gibi iş gereksinimleri açısından tanımlanır. Bu, değişiklikleri kullanıcılarınız ile tartışmanızı kolaylaştırır. Bu nedenle, tasarım zamanı şablonları çevik bir geliştirme sürecinde kullanışlı bir araçtır.

Tasarım zamanı şablonu oluşturmak için projenize **bir Metin Şablonu** dosyası ekleyin. Alternatif olarak, bir düz metin dosyası  ekleyebilir ve Özel Araç özelliğini **TextTemplatingFileGenerator olarak ayarlayın.**

Daha fazla bilgi için [bkz. T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)Metin Şablonları kullanarak Tasarım Zamanı Kodu Oluşturma. Şablonların söz dizimi hakkında daha fazla bilgi için [bkz. T4 Metin Şablonu Yazma.](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> Model terimi *bazen* bir veya daha fazla şablon tarafından okunan verileri açıklamak için kullanılır. Model herhangi bir biçimde, herhangi bir dosya veya veritabanı biçiminde olabilir. Bir UML modeli veya Domain-Specific Dil modeli olması gerek değildir. 'Model', verilerin koda benzer şekilde değil, yalnızca iş kavramları açısından tanımlanabilirsiniz olduğunu gösterir.

Metin şablonu dönüştürme özelliği *T4 olarak adlandırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
