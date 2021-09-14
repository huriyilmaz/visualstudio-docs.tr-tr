---
title: T4 Metin Dönüştürmeyi Özelleştirme
description: Metin şablonu yönerge işlemcisini veya metin şablonu ana bilgisayarlarını özelleştirerek varsayılan şablon dönüştürme işlemini nasıl genişletebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4549fbcd8f342816cec490ac6b461d3448f8827e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634401"
---
# <a name="customize-t4-text-transformation"></a>T4 Metin Dönüştürmeyi Özelleştirme

Metin şablonları, bir Visual Studio aracılığıyla program kodu veya diğer metin dosyaları oluşturmasına olanak sağlayan bir özelliktir. kullanarak, [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] metin şablonu yönerge işlemcisini veya metin şablonu ana bilgisayarlarını özelleştirerek varsayılan şablon dönüştürme işlemini genişletebilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde

 [Metin Şablonu Dönüştürme süreci](../modeling/the-text-template-transformation-process.md) Metin dönüştürmenin nasıl çalıştığını açıklar ve şablon ana bilgisayarının ve yönerge işlemcilerinin rolünü açıklar.

 [Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md) Yönerge işlemcisi, şablon derlemesi sırasında çalışır ve derlemeleri ve diğer kaynakları yükleyemediklerinde olduğu gibi, şablonunuz içinde yer alan `<#@template#>.` yönergelerle çalışır. Ayrıca çalışma zamanında kaynakları yükecek kodu da ekler. Kendi yönerge işlemcinizi tanımlayarak şablonlarınız karmaşıklığını azaltabilirsiniz.

 [VS Uzantısında Metin Dönüştürmeyi Faturalama](../modeling/invoking-text-transformation-in-a-vs-extension.md) Menü komutu veya olay Visual Studio bir uzantı yazıyorsanız, uzantınız metin şablonlarını dönüştürmek için Metin Şablon Oluşturma Hizmeti'ne sahip olabilir. Session nesnesini kullanarak parametre verilerini şablona iletir ve yönergeyi kullanarak şablonun içindeki değerleri `<#@parameter#>` elde edersiniz.

 [Özel Ana Bilgisayar Kullanarak Metin Şablonlarını İşleme](../modeling/processing-text-templates-by-using-a-custom-host.md) Metin şablonunun kodu yürütülürken, konak dış dosyalara ve uygulamanın durumuna erişim sağlar. Örneğin, içinde metin dönüştürmeleri Visual Studio ana bilgisayar, **Çözüm Gezgini.** Ayrıca hata iletisi penceresinde hataları da görüntüler. Metin dönüştürmelerini farklı bir bağlamda çalıştırmak için, bu bağlamda kullanılabilir hizmetlere erişim sağlayan kendi ana bilgisayarını tanımlayabilirsiniz.

 Bir uygulama uzantısı Visual Studio kendi ana bilgisayarını yazmak yerine mevcut metin dönüştürme hizmetini kullanmayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. VS Uzantısında Metin Dönüştürmeyi Faturalama.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

## <a name="reference"></a>Başvuru

- [T4 metin şablonu yazma,](../modeling/writing-a-t4-text-template.md) metin şablonu yönergelerinin ve denetim bloklarının söz dizimlerini sağlar.
