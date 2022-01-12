---
title: Kod Oluşturma ve T4 Metin Şablonları
description: Bir T4 metin şablonunun bir metin dosyası oluşturabilen metin blokları ve denetim mantığının nasıl karışımı olduğunu öğrenin.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.date: 12/28/2021
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
ms.openlocfilehash: 950cadad3444fa62f272bb6ea64eb8317fe43a62
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803888"
---
# <a name="code-generation-and-t4-text-templates"></a>Kod Oluşturma ve T4 Metin Şablonları

Visual Studio, *T4 metin şablonu* metin dosyası oluşturabilen metin blokları ve denetim mantığının bir karışımından oluşur. Denetim mantığı, veya içindeki program kodu parçaları olarak yazılır [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Visual Studio 2015 güncelleştirme 2 ve sonrasında, T4 şablonları yönergelerinde C# sürüm 6,0 özelliklerini kullanabilirsiniz. Oluşturulan dosya, bir Web sayfası veya bir kaynak dosyası gibi bir metin veya herhangi bir dilde program kaynak kodu olabilir.

Belirli bir sorun alanında ifade ifade etmek için tasarlanan, etki alanına özgü dil (DSL) için [Domain-Specific dilinden kod oluşturmayı](../modeling/generating-code-from-a-domain-specific-language.md) öğrenin

İki tür T4 metin şablonu vardır: [çalışma zamanı](#run-time-t4-text-templates) ve [Tasarım zamanı](#design-time-t4-text-templates)

## <a name="run-time-t4-text-templates"></a>Çalışma zamanı T4 Metin şablonları

Çalışma zamanı şablonları ' önceden işlenmiş ' şablonlar olarak da bilinir. Uygulamasındaki şablonları, çıktısının bir parçası olarak metin dizeleri oluşturacak şekilde çalıştırırsınız. Örneğin, bir HTML sayfası tanımlamak için bir şablon oluşturabilirsiniz:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Şablonun oluşturulan çıktıya benzediğine dikkat edin. Şablonun elde edilen çıktısına benzerliği, değiştirmek istediğinizde hatalardan kaçınmanıza yardımcı olur.

Ayrıca, şablon program kodunun parçalarını içerir. Bu parçaları, metnin bölümlerini yinelemek, koşullu bölümler yapmak ve uygulamanızdan verileri göstermek için kullanabilirsiniz.

Çıktı oluşturmak için, uygulamanız şablon tarafından oluşturulan bir işlevi çağırır. Örneğin:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

uygulamanız, Visual Studio yüklü olmayan bir bilgisayarda çalışabilir.

Çalışma zamanı şablonu oluşturmak için projenize **önceden işlenmiş bir metin şablonu** dosyası ekleyin. Ayrıca, düz metin dosyası ekleyebilir ve **özel araç** özelliğini **Texttemplatingfileönişlemci** olarak ayarlayabilirsiniz.

Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md). Şablonların sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Tasarım zamanı T4 Metin şablonları

Tasarım zamanı şablonları, kaynak kodun ve uygulamanızın diğer kaynaklarının bir parçasını tanımlar. Genellikle, tek bir giriş dosyası veya veritabanındaki verileri okuyan çeşitli şablonlar kullanır ve *. cs*, *. vb* veya diğer kaynak dosyalarından bazılarını oluşturabilirsiniz. her şablon bir dosya oluşturur ve Visual Studio veya MSBuild içinde oluşturulur.

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

Oluşturulan *. cs* dosyası XML dosyası değerlerine göre aşağıdaki biçimdedir:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Başka bir örnek olarak, giriş bir iş etkinliğinde iş akışının diyagramı olabilir. Kullanıcılar iş iş akışını Değiştir, ya da farklı bir iş akışına sahip yeni kullanıcılarla çalışmaya başladığınızda, kodu yeni modele sığacak şekilde yeniden oluşturmak kolaydır.

> [!NOTE]
> *Model* terimi bazen bir veya daha fazla şablon tarafından okunan verileri tanımlamakta kullanılır. Model herhangi bir biçimde herhangi bir dosya veya veritabanı türünde olabilir. Bir UML modeli veya Domain-Specific dil modeli olması gerekmez. ' Model ' yalnızca verilerin koda benzer değil iş kavramları açısından tanımlanamayacağını gösterir.
Gereksinimler değiştikçe yapılandırma değiştirilirken tasarım zamanı şablonları daha hızlı ve daha güvenilirdir. Genellikle, giriş iş açısından iş gereksinimlerine göre tanımlanır, iş akışı örneğinde olduğu gibi. Tasarım zamanı şablonları, çevik bir geliştirme sürecinde yararlı araçlardır.

Tasarım zamanı şablonu oluşturmak için projenize bir **metin şablonu** dosyası ekleyin. Alternatif olarak, düz metin dosyası ekleyebilir ve **özel araç** özelliğini **TextTemplatingFileGenerator** olarak ayarlayabilirsiniz.

Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Şablonların sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

Metin şablonu dönüştürme özelliği *T4* olarak adlandırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
