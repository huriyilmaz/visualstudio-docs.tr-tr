---
title: T4 metin dönüşümünü özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654961"
---
# <a name="customizing-t4-text-transformation"></a>T4 Metin Dönüştürmeyi Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonları, bir dönüştürme işlemi aracılığıyla program kodu veya diğer metin dosyaları oluşturmanıza olanak sağlayan bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] özelliğidir. @No__t_0 kullanarak, metin şablonu yönerge işlemcisini veya metin şablonu konağını özelleştirerek varsayılan şablon dönüşüm işlemini genişletebilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde
 [Metin şablonu dönüştürme işlemi](../modeling/the-text-template-transformation-process.md) Metin dönüşümünün nasıl çalıştığını açıklar ve şablon konağının ve yönerge işlemcilerin rolünü açıklar.

 [Özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md) Yönerge işlemcisi, şablonunuzda, şablonun derlenmesi sırasında çalıştığı ve derleme ve diğer kaynakları yükleyen `<#@template#>.` gibi yönergeler ile ilgilidir. Ayrıca, çalışma zamanında kaynakları yükleyecek kodu da ekleyebilir. Kendi yönerge işlemcinizi tanımlayarak, şablonlarınızın karmaşıklığını azaltabilirsiniz.

 [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md) Bir menü komutu veya olay işleyicisi gibi bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı yazıyorsanız, uzantınızın metin şablonu dönüştürmek için metin şablonu oluşturma hizmetini kullanabilirsiniz. Oturum nesnesini kullanarak parametre verilerini şablona geçirebilir ve `<#@parameter#>` yönergesini kullanarak değerleri şablon içinden alabilirsiniz.

 [Özel bir konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md) Metin şablonunun kodu yürütüldüğünde, ana bilgisayar dış dosyalara ve uygulamanın durumuna erişim sağlar. Örneğin, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 'de metin dönüştürmeleri çalıştıran ana bilgisayar Çözüm Gezgini 'ne erişim sağlayabilir. Hata iletisi penceresindeki hataları da görüntüler. Metin dönüşümlerini farklı bir bağlamda çalıştırmak istiyorsanız, bu bağlamda kullanılabilen hizmetlere erişim sağlayan kendi ana bilgisayarınızı tanımlayabilirsiniz.

 @No__t_0 uzantısı yazıyorsanız, kendi ana bilgisayarınızı yazmak yerine var olan metin dönüştürme hizmetini kullanmayı düşünün. Daha fazla bilgi için bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Başvuru
 [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)

 Metin şablonu yönergelerinin ve denetim bloklarının sözdizimini sağlar.
