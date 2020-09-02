---
title: Özel T4 metin şablonu yönerge Işlemcileri oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eef9fd14dc78ff1f377ffb94bcf76fde0c401783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651210"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Metin şablonu dönüştürme işlemi* , girdi olarak bir *metin şablonu* dosyası alır ve çıktı olarak bir metin dosyası üretir. *Metin şablonu dönüştürme altyapısı* işlemi denetler ve motor bir metin şablonu dönüştürme konağından ve bir veya daha fazla metin şablonu *yönerge işlemcisiyle* etkileşime geçerek işlemi tamamlar. Daha fazla bilgi için bkz. [metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md).

 Özel bir yönerge işlemcisi oluşturmak için ya da veya ' den devralan bir sınıf oluşturursunuz <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

 Bu iki arasındaki fark, <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> kullanıcıdan parametreleri almak ve şablon çıkış dosyasını üreten kodu oluşturmak için gereken en düşük arabirimi uygular. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> , tasarım deseninin gerektirdiği/sağladığı bir uygular. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> , ve olmak üzere iki özel parametreyi işler `requires` `provides` .  Örneğin, özel bir yönerge işlemcisi kullanıcıdan bir dosya adı kabul edebilir, dosyayı açıp okuyabilir ve sonra adlı bir değişkende dosyanın metnini depolar `fileText` . Sınıfının bir alt sınıfı <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> , kullanıcıdan parametrenin değeri olarak bir dosya adı `requires` ve parametrenin değeri olarak metnin kaydedileceği değişkenin adını alabilir `provides` . Bu işlemci dosyayı açıp okuyabilir ve sonra dosyanın metnini belirtilen değişkende depolar.

 İçindeki bir metin şablonundan özel bir yönerge işlemcisini çağırabilmeniz için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , onu kaydetmeniz gerekir.

 Kayıt defteri anahtarını ekleme hakkında daha fazla bilgi için bkz. [özel yönerge Işlemcisi dağıtma](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Özel yönergeler
 Özel bir yönerge şöyle görünür:

 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`

 Bir metin şablonundan dış verilere veya kaynaklara erişmek istediğinizde özel bir yönerge işlemcisi kullanabilirsiniz.

 Farklı metin şablonları, tek bir yönerge işlemcisinin sağladığı işlevselliği paylaşabilir, bu nedenle yönerge işlemcileri yeniden kullanım için kodu çarpanlara yönelik bir yol sağlar. `include`Kodu çarpanlara ayırmak ve farklı metin şablonları arasında paylaşmak için kullanabileceğiniz yerleşik yönerge benzerdir. Fark, `include` yönergenin sağladığı işlevlerin düzeltilme ve parametreleri kabul etmesinin gerektiğidir. Bir metin şablonuna ortak işlevsellik sağlamak ve şablonun parametreleri geçmesine izin vermek istiyorsanız, özel bir yönerge işlemcisi oluşturmanız gerekir.

 Bazı özel yönerge işlemcileri örnekleri şunlar olabilir:

- Bir Kullanıcı adı ve parolayı parametre olarak kabul eden bir veritabanından veri döndürmek için yönerge işlemcisi.

- Dosya adını bir parametre olarak kabul eden bir dosyayı açmak ve okumak için yönerge işlemcisi.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Özel yönerge işlemcisinin asıl kısımları
 Bir yönerge işlemcisi geliştirmek için ya da veya ' den devralan bir sınıf oluşturmanız gerekir <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

 `DirectiveProcessor`Uygulamanız gereken en önemli yöntemler aşağıdaki gibidir.

- `bool IsDirectiveSupported(string directiveName)` - `true` Yönerge işlemciniz adlandırılmış yönergeyle uğraşmışsa döndürün.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Şablon altyapısı, şablondaki her bir yönerge oluşumu için bu yöntemi çağırır. İşlemcinizin sonuçları kaydetmesi gerekir.

  ProcessDirective () tüm çağrılarından sonra, şablon oluşturma altyapısı bu yöntemleri çağırır:

- `string[] GetReferencesForProcessingRun()` -Şablon kodunun gerektirdiği derlemelerin adlarını döndürün.

- `string[] GetImportsForProcessingRun()` -Şablon kodunda kullanılabilecek ad alanlarını döndürün.

- `string GetClassCodeForProcessingRun()` -Şablon kodunun kullanabileceği yöntemlerin, özelliklerin ve diğer bildirimlerin kodunu döndürün. Bunu yapmanın en kolay yolu, C# veya Visual Basic kodunu içeren bir dize derlemenize olanak sağlar. Yönerge işlemcinizi herhangi bir CLR dili kullanan bir şablondan çağrılabilir hale getirmek için, deyimlerini bir CodeDom ağacı olarak oluşturabilir ve sonra ağacı seri hale getirme sonucunu şablon tarafından kullanılan dilde döndürebilirsiniz.

- Daha fazla bilgi için bkz. [Izlenecek yol: özel yönerge Işlemcisi oluşturma](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="in-this-section"></a>Bu Bölümde
 [Özel yönerge Işlemcisi dağıtma](../modeling/deploying-a-custom-directive-processor.md) Özel bir yönerge işlemcisinin nasıl kaydedileceği açıklanmaktadır.

 [Izlenecek yol: özel yönerge Işlemcisi oluşturma](../modeling/walkthrough-creating-a-custom-directive-processor.md) Özel bir yönerge işlemcisinin nasıl oluşturulduğunu, yönerge işlemcisinin nasıl kaydedileceği ve test edileceğini ve çıktı dosyasının HTML olarak nasıl biçimlendirileceğini açıklar.
