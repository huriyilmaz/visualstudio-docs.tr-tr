---
title: Kod Oluşturma ve T4 Metin Şablonları
description: Bir T4 metin şablonunun bir metin dosyası oluşturabilen metin blokları ve denetim mantığının nasıl karışımı olduğunu öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625754"
---
# <a name="code-generation-and-t4-text-templates"></a>Kod Oluşturma ve T4 Metin Şablonları

Visual Studio, *T4 metin şablonu* metin dosyası oluşturabilen metin blokları ve denetim mantığının bir karışımından oluşur. Denetim mantığı, veya içindeki program kodu parçaları olarak yazılır [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Visual Studio 2015 güncelleştirme 2 ve sonrasında, T4 şablonları yönergelerinde C# sürüm 6,0 özelliklerini kullanabilirsiniz. Oluşturulan dosya, bir Web sayfası veya bir kaynak dosyası gibi herhangi bir türde metin veya herhangi bir dilde program kaynak kodu olabilir.

İki tür T4 metin şablonu vardır: çalışma zamanı ve tasarım zamanı.

## <a name="run-time-t4-text-templates"></a>Çalışma zamanı T4 Metin şablonları

' Önceden işlenmiş ' şablonlar olarak da bilinen çalışma zamanı şablonları, genellikle çıktısının bir parçası olarak metin dizeleri oluşturmak için uygulamanızda yürütülür. Örneğin, bir HTML sayfası tanımlamak için bir şablon oluşturabilirsiniz:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Şablonun oluşturulan çıktıya benzediğine dikkat edin. Şablonun elde edilen çıktısına benzerliği, değiştirmek istediğinizde hatalardan kaçınmanıza yardımcı olur.

Ayrıca, şablon program kodunun parçalarını içerir. Bu parçaları, metnin bölümlerini yinelemek, koşullu bölümler yapmak ve uygulamanızdan verileri göstermek için kullanabilirsiniz.

Çıktı oluşturmak için, uygulamanız şablon tarafından oluşturulan bir işlevi çağırır. Örnek:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

uygulamanız, Visual Studio yüklü olmayan bir bilgisayarda çalışabilir.

Çalışma zamanı şablonu oluşturmak için projenize **önceden işlenmiş bir metin şablonu** dosyası ekleyin. Alternatif olarak, düz metin dosyası ekleyebilir ve **özel araç** özelliğini **Texttemplatingfileönişlemci** olarak ayarlayabilirsiniz.

Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md). Şablonların sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Tasarım zamanı T4 Metin şablonları

Tasarım zamanı şablonları, kaynak kodun ve uygulamanızın diğer kaynaklarının bir parçasını tanımlar. Genellikle, tek bir giriş dosyası veya veritabanındaki verileri okuyan çeşitli şablonlar kullanır ve *. cs*, *. vb* veya diğer kaynak dosyalarından bazılarını oluşturabilirsiniz. Her şablon bir dosya oluşturur. Visual Studio veya MSBuild içinde yürütülürler.

Örneğin, giriş verileriniz bir XML dosyası yapılandırma verileri olabilir. Geliştirme sırasında XML dosyasını düzenlediğinizde metin şablonları, uygulama kodunun bir parçasını yeniden oluşturun. Şablonlardan biri aşağıdaki örneğe benzeyebilir:

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

XML dosyasındaki değerlere bağlı olarak, oluşturulan *. cs* dosyası aşağıdakine benzer:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Başka bir örnek olarak, giriş bir iş etkinliğinde iş akışının diyagramı olabilir. Kullanıcılar iş iş akışını Değiştir, ya da farklı bir iş akışına sahip yeni kullanıcılarla çalışmaya başladığınızda, kodu yeni modele sığacak şekilde yeniden oluşturmak kolaydır.

Tasarım zamanı şablonları, gereksinimler değiştiğinde yapılandırmanın değiştirilmesini daha hızlı ve daha güvenilir hale getirir. Genellikle giriş, iş akışı örneğinde olduğu gibi iş gereksinimlerine göre tanımlanır. Bu, değişiklikleri kullanıcılarınız ile tartışmanızı kolaylaştırır. Bu nedenle, tasarım zamanı şablonları Çevik bir geliştirme sürecinde yararlı bir araçtır.

Tasarım zamanı şablonu oluşturmak için projenize bir **metin şablonu** dosyası ekleyin. Alternatif olarak, düz metin dosyası ekleyebilir ve **özel araç** özelliğini **TextTemplatingFileGenerator** olarak ayarlayabilirsiniz.

Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Şablonların sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> *Model* terimi bazen bir veya daha fazla şablon tarafından okunan verileri tanımlamakta kullanılır. Model herhangi bir biçimde herhangi bir dosya veya veritabanı türünde olabilir. Bir UML modeli veya Domain-Specific dil modeli olması gerekmez. ' Model ' yalnızca verilerin koda benzer değil iş kavramları açısından tanımlanamayacağını gösterir.

Metin şablonu dönüştürme özelliği *T4* olarak adlandırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
