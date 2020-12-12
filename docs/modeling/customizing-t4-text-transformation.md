---
title: T4 Metin Dönüştürmeyi Özelleştirme
description: Metin şablonu yönerge işlemcisini veya metin şablonu konağını özelleştirerek varsayılan şablon dönüştürme işlemini nasıl genişletebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b168e0e66b7704c3e78a241f76ee4122278c9ed
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362918"
---
# <a name="customize-t4-text-transformation"></a>T4 Metin Dönüştürmeyi Özelleştirme

Metin şablonları, bir dönüştürme işlemi aracılığıyla program kodu veya diğer metin dosyaları oluşturmanıza olanak sağlayan bir Visual Studio özelliğidir. Kullanarak [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] , metin şablonu yönerge işlemcisini veya metin şablonu konağını özelleştirerek varsayılan şablon dönüştürme işlemini genişletebilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde

 [Metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md) Metin dönüşümünün nasıl çalıştığını açıklar ve şablon konağının ve yönerge işlemcilerin rolünü açıklar.

 [Özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md) Yönerge işlemcisi, şablonun derlenmesi sırasında çalıştığı gibi, şablonunuzda bulunan yönergelerden oluşur `<#@template#>.` ve derlemeleri ve diğer kaynakları yükleyebilir. Ayrıca, çalışma zamanında kaynakları yükleyecek kodu da ekleyebilir. Kendi yönerge işlemcinizi tanımlayarak, şablonlarınızın karmaşıklığını azaltabilirsiniz.

 [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md) Bir menü komutu veya olay işleyicisi gibi bir Visual Studio uzantısı yazıyorsanız, uzantınız metin şablonunu dönüştürmek için metin şablon oluşturma hizmetini kullanabilir. Oturum nesnesini kullanarak parametre verilerini şablona geçirebilir ve yönergesini kullanarak değerleri şablon içinden alabilirsiniz `<#@parameter#>` .

 [Özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md) Metin şablonunun kodu yürütüldüğünde, ana bilgisayar dış dosyalara ve uygulamanın durumuna erişim sağlar. Örneğin, Visual Studio 'da metin dönüştürmeleri çalıştıran ana bilgisayar **Çözüm Gezgini** erişim sağlayabilir. Hata iletisi penceresindeki hataları da görüntüler. Metin dönüşümlerini farklı bir bağlamda çalıştırmak istiyorsanız, bu bağlamda kullanılabilen hizmetlere erişim sağlayan kendi ana bilgisayarınızı tanımlayabilirsiniz.

 Visual Studio uzantısı yazıyorsanız, kendi ana bilgisayarınızı yazmak yerine var olan metin dönüştürme hizmetini kullanmayı düşünün. Daha fazla bilgi için bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Başvuru

- [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md) metin şablonu yönergelerinin ve denetim bloklarının sözdizimini sağlar.
