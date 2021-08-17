---
title: T4 Metin Dönüştürmeyi Özelleştirme
description: Metin şablonu yönerge işlemcisini veya metin şablonu konağını özelleştirerek varsayılan şablon dönüştürme işlemini nasıl genişletebileceğinizi öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027766"
---
# <a name="customize-t4-text-transformation"></a>T4 Metin Dönüştürmeyi Özelleştirme

metin şablonları, bir dönüştürme işlemi aracılığıyla program kodu veya diğer metin dosyaları oluşturmanıza olanak sağlayan bir Visual Studio özelliğidir. Kullanarak [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] , metin şablonu yönerge işlemcisini veya metin şablonu konağını özelleştirerek varsayılan şablon dönüştürme işlemini genişletebilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde

 [Metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md) Metin dönüşümünün nasıl çalıştığını açıklar ve şablon konağının ve yönerge işlemcilerin rolünü açıklar.

 [Özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md) Yönerge işlemcisi, şablonun derlenmesi sırasında çalıştığı gibi, şablonunuzda bulunan yönergelerden oluşur `<#@template#>.` ve derlemeleri ve diğer kaynakları yükleyebilir. Ayrıca, çalışma zamanında kaynakları yükleyecek kodu da ekleyebilir. Kendi yönerge işlemcinizi tanımlayarak, şablonlarınızın karmaşıklığını azaltabilirsiniz.

 [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md) bir menü komutu veya olay işleyicisi gibi bir Visual Studio uzantısı yazıyorsanız, uzantınızın metin şablonu dönüştürmek için metin şablonu oluşturma hizmetini kullanabilirsiniz. Oturum nesnesini kullanarak parametre verilerini şablona geçirebilir ve yönergesini kullanarak değerleri şablon içinden alabilirsiniz `<#@parameter#>` .

 [Özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md) Metin şablonunun kodu yürütüldüğünde, ana bilgisayar dış dosyalara ve uygulamanın durumuna erişim sağlar. örneğin, Visual Studio ' de metin dönüşümleri çalıştıran ana bilgisayar **Çözüm Gezgini** erişim sağlayabilir. Hata iletisi penceresindeki hataları da görüntüler. Metin dönüşümlerini farklı bir bağlamda çalıştırmak istiyorsanız, bu bağlamda kullanılabilen hizmetlere erişim sağlayan kendi ana bilgisayarınızı tanımlayabilirsiniz.

 Visual Studio uzantısı yazıyorsanız, kendi ana bilgisayarınızı yazmak yerine var olan metin dönüştürme hizmetini kullanmayı düşünün. Daha fazla bilgi için bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Başvuru

- [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md) metin şablonu yönergelerinin ve denetim bloklarının sözdizimini sağlar.
