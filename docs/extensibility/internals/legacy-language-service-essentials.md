---
title: Eski Dil Hizmeti Temel | Microsoft Docs
description: Eski dil hizmetlerinde bulunan ve programlama dilini bir programlama diliyle tümleştiren temel özellikleri Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dda53c2ea5c282e67b3ed0ec86112a2a69d64cab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049915"
---
# <a name="legacy-language-service-essentials"></a>Eski Dil Hizmeti Temel Bileşenleri
Programlama dilini programlama diliyle tümleştiren bir dil hizmeti Visual Studio. Bu konu başlığında, eski dil hizmetlerinde kullanılabilen özellikler açıklanmıştır.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi için bkz. [Düzenleyici ve Dil Hizmeti Uzantıları.](../../extensibility/editor-and-language-service-extensions.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Eski dil hizmetleri aşağıdaki özellikleri sağlar:

|Özellik|Açıklama|
|-------------|-----------------|
|Söz dizimi renklendirme|Düzenleyici görünümünün bir dilin farklı öğeleri için farklı renkler ve yazı tipi stilleri görüntülemelerine neden olur. Bu fark, dosyaları okumayı ve düzenlemeyi kolaylaştırabilirsiniz.<br /><br /> Genel bilgi için bkz. [Eski Dil Hizmeti'de Söz Dizimi Renklendirmesi.](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)<br /><br /> Yönetilen paket çerçevesinde (MPF) bu özellik hakkında bilgi için bkz. Eski Dil Hizmeti'de [Söz Dizimi Renklendirme.](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)|
|Deyim tamamlama|Kullanıcının yazmaya başladığı bir deyimi veya anahtar sözcüğü tamamlar. Deyim tamamlama, kullanıcıların zor deyimleri daha kolay bir şekilde girmelerine ve daha az yazma ve hata olasılığına sahip olmalarına yardımcı olur.<br /><br /> Genel bilgi için [bkz. Eski Dil Hizmeti'de Deyim Tamamlama.](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)<br /><br /> MPF'deki bu özellik hakkında bilgi için bkz. [Eski Dil Hizmeti'de Sözcük Tamamlama.](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)|
|Küme ayracı eşleştirme|Küme ayraçları gibi eşleştirilmiş karakterleri vurgular. Kullanıcı "}" gibi bir kapatma karakteri türetirse, küme ayracı eşleştirme ilgili açılış karakterini (örneğin, "{" ) vurgular. Birkaç kapsayan karakter düzeyi olduğunda, bu özellik kullanıcıların kapsayan karakterlerin doğru eşleştirilmiş olduğunu onaylamanıza yardımcı olur.<br /><br /> MPF'deki bu özellik hakkında bilgi için [bkz. Eski Dil Hizmeti'de Küme Ayracı Eşleştirme.](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)|
|Parametre bilgileri araç ipucu|Kullanıcının şu anda yazmakta olduğu aşırı yüklenmiş yöntem için olası imzaların listesini görüntüler.<br /><br /> Genel bilgi için [bkz. Eski Dil Hizmeti'ne Parametre Bilgileri.](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi için [bkz. Eski Dil Hizmeti'deki Parametre Bilgileri.](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)|
|Hata işaretçileri|Dalgalı çizgi olarak da bilinen dalgalı kırmızı bir alt çizgi, metnin altında, var olan ve yanlış olan bir dalgalı çizgi görüntüler. Hata işaretçileri genellikle kullanıcıların yanlış yazılmış anahtar sözcükler, açık olmayan parantezler, geçersiz karakterler ve benzer hatalardan haberdar olması için kullanılır.<br /><br /> MPF sınıflarında, hata işaretçileri sınıfının yönteminde <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> otomatik olarak <xref:Microsoft.VisualStudio.Package.AuthoringSink> işlenir.|

 Bu özelliklerin çoğu, kaynak kodunu ayrıştırmak için dil hizmetini gerektirir. Genellikle derleyiciniz veya yorumlayıcınız için belirteçlerileştirme ve ayrıştırma kodunu yeniden kullanabilirsiniz.

 Aşağıdaki özellikler programlama dillerini desteklemeyle ilgilidir ancak dil hizmetlerinin bir parçası değildir:

| Özellik | Açıklama |
|-----------------------| - |
| İfade değerlendiricileri | Kesme noktaları doğrular ve Otomatik hata ayıklama penceresinde görüntülenecek ifadelerin listesini belirterek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **hata ayıklayıcıyı** destekler.<br /><br /> Daha fazla bilgi için [bkz. Hata Ayıklama için Dil Hizmeti Desteği.](../../extensibility/internals/language-service-support-for-debugging.md) |
| Sembol tarama araçları | Object **Browser ,** **Sınıf Görünümü**, **Çağrı Tarayıcısı** ve **Find Symbol Results 'ı destekler.** |
