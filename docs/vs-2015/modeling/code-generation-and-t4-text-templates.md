---
title: Kod oluşturma ve T4 Metin şablonları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667916"
---
# <a name="code-generation-and-t4-text-templates"></a>Kod Oluşturma ve T4 Metin Şablonları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' De, bir *T4 metin şablonu* , metin dosyası oluşturabilen bir metin blokları ve Denetim mantığı karışımından oluşur. Denetim mantığı, veya içindeki program kodu parçaları olarak yazılır [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Visual Studio 2015 güncelleştirme 2 ve sonrasında, T4 şablonları yönergelerinde C# sürüm 6,0 özelliklerini kullanabilirsiniz. Oluşturulan dosya, bir Web sayfası veya bir kaynak dosyası gibi herhangi bir türde metin veya herhangi bir dilde program kaynak kodu olabilir.

 İki tür T4 metin şablonu vardır:

 **Çalışma zamanı T4 Metin şablonları** (' önceden işlenmiş ' şablonlar) uygulamanızda, genellikle çıktısının bir parçası olarak metin dizeleri oluşturmak için yürütülür.
Örneğin, bir HTML sayfası tanımlamak için bir şablon oluşturabilirsiniz:

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

 Uygulamanız, yüklü olmayan bir bilgisayarda çalışabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Çalışma zamanı şablonu oluşturmak için projenize **önceden işlenmiş bir metin şablonu** dosyası ekleyin. Alternatif olarak, düz metin dosyası ekleyebilir ve **özel araç** özelliğini **Texttemplatingfileönişlemci**olarak ayarlayabilirsiniz.

 Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md). Şablonların sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

 **Tasarım zamanı T4 Metin şablonları** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kaynak kodun ve uygulamanızın diğer kaynaklarının bir kısmını tanımlamak için içinde yürütülür.
Genellikle, tek bir giriş dosyası veya veritabanındaki verileri okuyan çeşitli şablonlar kullanır ve bazı `.cs` , `.vb` veya diğer kaynak dosyalarından bazılarını oluşturabilirsiniz. Her şablon bir dosya oluşturur. Veya içinde yürütülür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .

 Örneğin, giriş verileriniz bir XML dosyası yapılandırma verileri olabilir. Geliştirme sırasında XML dosyasını düzenlediğinizde metin şablonları, uygulama kodunun bir parçasını yeniden oluşturacak. Şablonlardan biri aşağıdaki örneğe benzeyebilir:

```
<#@ output extension=".txt" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}

```

 XML dosyasındaki değerlere bağlı olarak, oluşturulan `.cs` dosya aşağıdakine benzer:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

 Başka bir örnek olarak, giriş bir iş etkinliğinde iş akışının diyagramı olabilir. Kullanıcılar iş iş akışını Değiştir, ya da farklı bir iş akışına sahip yeni kullanıcılarla çalışmaya başladığınızda, kodu yeni modele sığacak şekilde yeniden oluşturmak kolaydır.

 Tasarım zamanı şablonları, gereksinimler değiştiğinde yapılandırmanın değiştirilmesini daha hızlı ve daha güvenilir hale getirir. Genellikle giriş, iş akışı örneğinde olduğu gibi iş gereksinimlerine göre tanımlanır. Bu, değişiklikleri kullanıcılarınız ile tartışmanızı kolaylaştırır. Bu nedenle, tasarım zamanı şablonları Çevik bir geliştirme sürecinde yararlı bir araçtır.

 Tasarım zamanı şablonu oluşturmak için projenize bir **metin şablonu** dosyası ekleyin. Alternatif olarak, düz metin dosyası ekleyebilir ve **özel araç** özelliğini **TextTemplatingFileGenerator**olarak ayarlayabilirsiniz.

 Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Şablonların sözdizimi hakkında daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> *Model* terimi bazen bir veya daha fazla şablon tarafından okunan verileri tanımlamakta kullanılır. Model herhangi bir biçimde herhangi bir dosya veya veritabanı türünde olabilir. Bir UML modeli veya etki alanına özgü dil modeli olması gerekmez. ' Model ' yalnızca verilerin koda benzer değil iş kavramları açısından tanımlanamayacağını gösterir.

 Metin şablonu dönüştürme özelliği *T4*olarak adlandırılır.

## <a name="in-this-section"></a>Bu Bölümde
 [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md) Metin dosyaları üreten herhangi bir uygulamada, önceden derlenmiş metin şablonları, metni tanımlamaya yönelik kolay ve güvenilir bir yöntemdir. Ancak, bu yöntem çalışma zamanında değişen metin şablonları için kullanılamaz.

 [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Bir modelden kod ve diğer kaynakların oluşturulması, modeli güncelleştirerek uygulamanızı güncelleştirmenizi sağlar.

 [Derleme Işleminde kod üretimi](../modeling/code-generation-in-a-build-process.md) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Görselleştirme ve modelleme SDK 'sını yüklediyseniz, oluşturulan yazılımın modeldeki değişikliklerle güncel kalmasını sağlayabilirsiniz.

 [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md) Metin şablonu dosyasının sözdizimi.

 [Izlenecek yol: metin şablonları kullanarak kod oluşturma](../modeling/walkthrough-generating-code-by-using-text-templates.md) Kod oluşturmayı kullanmanın bir yolu gösterimi.

 [T4 metin şablonunda hata ayıklama](../modeling/debugging-a-t4-text-template.md) Metin şablonlarındaki hata ayıklama ve bazı yaygın metin şablonu hataları.

 [TextTransform yardımcı programıyla dosyalar oluşturma](../modeling/generating-files-with-the-texttransform-utility.md) Metin şablonu dönüşümlerini çalıştırmak için kullanabileceğiniz komut satırı aracı.

 [T4 metin dönüşümünü özelleştirme](../modeling/customizing-t4-text-transformation.md) Kendi veri kaynaklarınız için yönerge işlemcileri ve özel şablon oluşturma Konakları yazma.

## <a name="see-also"></a>Ayrıca Bkz.
 [Etki alanına özgü dilden kod üreten](../modeling/generating-code-from-a-domain-specific-language.md) [UML modelden dosya oluşturma](../modeling/generate-files-from-a-uml-model.md)
