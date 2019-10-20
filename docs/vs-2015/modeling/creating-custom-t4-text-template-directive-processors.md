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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651210"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Metin şablonu dönüştürme işlemi* , girdi olarak bir *metin şablonu* dosyası alır ve çıktı olarak bir metin dosyası üretir. *Metin şablonu dönüştürme altyapısı* işlemi denetler ve motor bir metin şablonu dönüştürme konağından ve bir veya daha fazla metin şablonu *yönerge işlemcisiyle* etkileşime geçerek işlemi tamamlar. Daha fazla bilgi için bkz. [metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md).

 Özel bir yönerge işlemcisi oluşturmak için <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ya da <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> devralan bir sınıf oluşturursunuz.

 Bu iki arasındaki fark, <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> kullanıcıdan parametreleri almak ve şablon çıkış dosyasını üreten kodu oluşturmak için gerekli olan en düşük arabirimi uygular. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>, tasarım deseninin gerektirdiği/sağladığı şekilde uygular. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>, `requires` ve `provides` iki özel parametreyi işler.  Örneğin, özel bir yönerge işlemcisi kullanıcıdan bir dosya adı kabul edebilir, dosyayı açıp okuyabilir ve sonra dosyanın metnini `fileText` adlı bir değişkende saklayabilir. @No__t_0 sınıfının bir alt sınıfı, kullanıcıdan `requires` parametresinin değeri olarak bir dosya adı ve `provides` parametresinin değeri olarak metnin kaydedileceği değişkenin adını alabilir. Bu işlemci dosyayı açıp okuyabilir ve sonra dosyanın metnini belirtilen değişkende depolar.

 @No__t_0 bir metin şablonundan özel yönerge işlemcisini çağırabilmeniz için önce onu kaydetmeniz gerekir.

 Kayıt defteri anahtarını ekleme hakkında daha fazla bilgi için bkz. [özel yönerge Işlemcisi dağıtma](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Özel yönergeler
 Özel bir yönerge şöyle görünür:

 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`

 Bir metin şablonundan dış verilere veya kaynaklara erişmek istediğinizde özel bir yönerge işlemcisi kullanabilirsiniz.

 Farklı metin şablonları, tek bir yönerge işlemcisinin sağladığı işlevselliği paylaşabilir, bu nedenle yönerge işlemcileri yeniden kullanım için kodu çarpanlara yönelik bir yol sağlar. Kodu çarpanlara ayırmak ve farklı metin şablonları arasında paylaşmak için kullanabileceğiniz yerleşik `include` yönergesi benzerdir. Fark, `include` yönergesinin sağladığı işlevlerin düzeltilme ve parametreleri kabul etmesinin gerektiğidir. Bir metin şablonuna ortak işlevsellik sağlamak ve şablonun parametreleri geçmesine izin vermek istiyorsanız, özel bir yönerge işlemcisi oluşturmanız gerekir.

 Bazı özel yönerge işlemcileri örnekleri şunlar olabilir:

- Bir Kullanıcı adı ve parolayı parametre olarak kabul eden bir veritabanından veri döndürmek için yönerge işlemcisi.

- Dosya adını bir parametre olarak kabul eden bir dosyayı açmak ve okumak için yönerge işlemcisi.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Özel yönerge işlemcisinin asıl kısımları
 Bir yönerge işlemcisi geliştirmek için, <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> veya <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> devralan bir sınıf oluşturmanız gerekir.

 Uygulamanız gereken en önemli `DirectiveProcessor` yöntemler aşağıdaki gibidir.

- `bool IsDirectiveSupported(string directiveName)`-yönerge işlemcinizin adlandırılmış yönergeyle uğraşmak için `true` döndürün.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`-şablon altyapısı, şablondaki her bir yönerge oluşumu için bu yöntemi çağırır. İşlemcinizin sonuçları kaydetmesi gerekir.

  ProcessDirective () tüm çağrılarından sonra, şablon oluşturma altyapısı bu yöntemleri çağırır:

- `string[] GetReferencesForProcessingRun()`-şablon kodunun gerektirdiği derlemelerin adlarını döndürün.

- `string[] GetImportsForProcessingRun()`-Şablon kodunda kullanılabilecek ad alanlarını döndürün.

- `string GetClassCodeForProcessingRun()`-şablon kodu tarafından kullanılabilecek yöntemlerin, özelliklerin ve diğer bildirimlerin kodunu döndürün. Bunu yapmanın en kolay yolu, C# veya Visual Basic kodunu içeren bir dize oluşturur. Yönerge işlemcinizi herhangi bir CLR dili kullanan bir şablondan çağrılabilir hale getirmek için, deyimlerini bir CodeDom ağacı olarak oluşturabilir ve sonra ağacı seri hale getirme sonucunu şablon tarafından kullanılan dilde döndürebilirsiniz.

- Daha fazla bilgi için bkz. [Izlenecek yol: özel yönerge Işlemcisi oluşturma](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="in-this-section"></a>Bu Bölümde
 [Özel yönerge Işlemcisi dağıtma](../modeling/deploying-a-custom-directive-processor.md) Özel bir yönerge işlemcisinin nasıl kaydedileceği açıklanmaktadır.

 [Izlenecek yol: özel yönerge Işlemcisi oluşturma](../modeling/walkthrough-creating-a-custom-directive-processor.md) Özel bir yönerge işlemcisinin nasıl oluşturulduğunu, yönerge işlemcisinin nasıl kaydedileceği ve test edileceğini ve çıktı dosyasının HTML olarak nasıl biçimlendirileceğini açıklar.
