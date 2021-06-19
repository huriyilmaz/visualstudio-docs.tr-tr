---
title: Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma
description: Metin şablonu dönüştürme işlemi ve özel bir T4 metin şablonu yönerge işlemcisi oluşturma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59644275f17eac197074351a777959bb1826a5de
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389507"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma

Metin *şablonu dönüştürme işlemi,* giriş *olarak bir metin* şablonu dosyası alır ve çıkış olarak bir metin dosyası oluşturur. Metin *şablonu dönüştürme altyapısı* işlemi kontrol eder ve altyapı, işlemi tamamlamak için bir  metin şablonu dönüştürme ana bilgisayarı ve bir veya daha fazla metin şablonu yönerge işlemcisi ile etkileşime girin. Daha fazla bilgi için [bkz. Metin Şablonu Dönüştürme İşlemleri.](../modeling/the-text-template-transformation-process.md)

Özel yönerge işlemcisi oluşturmak için veya 'den devralan bir sınıf <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> oluşturun.

Bu ikisi arasındaki fark, kullanıcıdan parametreleri almak ve şablon çıkış dosyasını üreten kodu oluşturmak için gereken en düşük arabirimi <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> uygulamadır. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> , tasarım desenini gerektirir/sağlar. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> iki özel parametreyi (ve ) `requires` `provides` işler.  Örneğin, özel yönerge işlemcisi kullanıcıdan bir dosya adı kabul eder, dosyayı açıp okur ve ardından dosyanın metnini adlı bir değişkende `fileText` depolar. Sınıfın bir alt sınıfı, parametrenin değeri olarak kullanıcıdan bir dosya adı ve metnin parametresinin değeri olarak <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> `requires` depolandırı değişkenin adını `provides` alır. Bu işlemci dosyayı açıp okur ve ardından dosyanın metnini belirtilen değişkende depolar.

Bir metin şablonundan özel yönerge işlemcisini çağırmadan önce Visual Studio kaydetmeniz gerekir.

Kayıt defteri anahtarını ekleme hakkında daha fazla bilgi için [bkz. Özel Yönerge İşlemcisi Dağıtma.](../modeling/deploying-a-custom-directive-processor.md)

## <a name="custom-directives"></a>Özel Yönergeler

Özel bir yönerge şu şekildedir:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Bir metin şablonundan dış verilere veya kaynaklara erişmek istediğiniz zaman özel yönerge işlemcisi kullanabilirsiniz.

Farklı metin şablonları tek bir yönerge işlemcisinin sağladığı işlevselliği paylaşabilir, bu nedenle yönerge işlemcileri kodu yeniden kullanmak üzere çarpanlara eklemek için bir yol sağlar. Yerleşik yönerge benzerdir çünkü kodu çarpanlara alıp farklı metin şablonları arasında `include` paylaşabilirsiniz. Aradaki fark, yönergenin sağladığı işlevler `include` sabittir ve parametreleri kabul etmez. Bir metin şablonuna ortak işlevsellik sağlamak ve şablonun parametreleri geçmesine izin vermek için özel yönerge işlemcisi oluşturmanız gerekir.

Özel yönerge işlemcilerinin bazı örnekleri:

- Parametre olarak kullanıcı adı ve parola kabul eden bir veritabanından veri iade etmek için yönerge işlemcisi.

- Parametre olarak dosyanın adını kabul eden bir dosyayı açmak ve okumak için yönerge işlemcisi.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Özel yönerge işlemcisinin temel parçaları

Bir yönerge işlemcisi geliştirmek için veya 'den devralan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gerekir.

Uygulamanız `DirectiveProcessor` gereken en önemli yöntemler aşağıdaki gibidir.

- `bool IsDirectiveSupported(string directiveName)` - Yönerge `true` işlemciniz adlandırılmış yönergeyle ilgileneninse dönüş.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` - Şablon altyapısı, şablonda bir yönergenin her oluşum için bu yöntemi arar. İşlemcinizin sonuçları kaydetmesi gerekir.

ProcessDirective() çağrısının ardından, templating altyapısı şu yöntemleri çağıracak:

- `string[] GetReferencesForProcessingRun()` - Şablon kodunun gerektirdiği derlemelerin adlarını dönüş.

- `string[] GetImportsForProcessingRun()` - Şablon kodunda kullanılan ad alanlarını geri girin.

- `string GetClassCodeForProcessingRun()` - Şablon kodunun kullanabileceği yöntemlerin, özelliklerin ve diğer bildirimlerin kodunu dönüş. Bunu yapmanın en kolay yolu C# veya kod içeren bir dize Visual Basic oluşturmaktır. Yönerge işlemcinizin herhangi bir CLR dilini kullanan bir şablondan çağrılabilir hale getirmesi için deyimlerini CodeDom ağacı olarak oluşturabilir ve ardından ağacı şablon tarafından kullanılan dilde seri hale getirmenin sonucu getirebilirsiniz.

- Daha fazla bilgi için [bkz. Adım adım yönergeler: Özel Yönerge İşlemcisi Oluşturma.](../modeling/walkthrough-creating-a-custom-directive-processor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Yönerge İşlemcisi Dağıtma,](../modeling/deploying-a-custom-directive-processor.md) özel yönerge işlemcisinin nasıl kaydediliyor olduğunu açıklar.
- [Kılavuz: Özel Yönerge](../modeling/walkthrough-creating-a-custom-directive-processor.md) İşlemcisi Oluşturma, özel yönerge işlemcisi oluşturma, yönerge işlemcisini kaydetme ve test etmek ve çıkış dosyasını HTML olarak biçimlendirmeyi açıklar.
