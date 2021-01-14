---
title: Eski dil hizmeti temelleri | Microsoft Docs
description: Bir programlama dilini Visual Studio ile tümleştirmenize olanak tanıyan eski dil hizmetlerinde sunulan temel özellikler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa21b619ef17be3fa649732a2b6e3bcd700dda6
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205157"
---
# <a name="legacy-language-service-essentials"></a>Eski Dil Hizmeti Temel Bileşenleri
Programlama dilini Visual Studio ile tümleştirebilmek için bir dil hizmeti sağlamanız gerekir. Bu konuda, eski dil hizmetlerinde kullanılabilen özellikler açıklanmaktadır.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Eski dil Hizmetleri aşağıdaki özellikleri sağlar:

|Özellik|Açıklama|
|-------------|-----------------|
|Sözdizimi renklendirme|Düzenleyici görünümünün, dilin farklı öğeleri için farklı renkler ve yazı tipi stilleri görüntülemesine neden olur. Bu ayrım, dosyaları okumayı ve düzenlemeyi kolaylaştırabilir.<br /><br /> Genel bilgiler için, bkz. [eski dil hizmetindeki sözdizimi renklendirme](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Bu özellik hakkında daha fazla bilgi için, bkz. [eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Ekstre tamamlama|Kullanıcının yazmaya başladığı bir ifadeyi veya anahtar sözcüğü tamamlar. Deyim tamamlama, kullanıcıların daha az yazma ve hata için daha az olasısız zor deyimleri daha kolay girmesine yardımcı olur.<br /><br /> Genel bilgi için, bkz. [eski dil hizmetinde deyimin tamamlanması](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> MPF 'deki bu özellik hakkında daha fazla bilgi için bkz. [eski dil hizmetinde sözcük tamamlama](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Ayraç eşleştirme|Parantez gibi eşleştirilmiş karakterleri vurgular. Kullanıcı "}" gibi bir kapanış karakteri yazdığında, parantez eşleştirme, karşılık gelen "{" gibi açma karakterini vurgular. Birçok kapsayan karakter düzeyi olduğunda, bu özellik kullanıcıların kapsayan karakterlerin doğru şekilde eşleştirildiğini onaylamasını sağlar.<br /><br /> MPF 'deki bu özellik hakkında daha fazla bilgi için bkz. [eski dil hizmetinde küme ayracı eşleme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Parametre bilgileri araç ipuçları|Kullanıcının şu anda yazmakta olduğu aşırı yüklenmiş yöntem için olası imzaların bir listesini görüntüler.<br /><br /> Genel bilgiler için, [eski dil hizmetindeki parametre bilgilerine](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)bakın.<br /><br /> MPF 'deki bu özellik hakkında daha fazla bilgi için, [eski dil hizmetindeki parametre bilgilerine](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)bakın.|
|Hata işaretçileri|Sözdizimsel olarak da bilinen dalgalı kırmızı alt çizgiyi, sözdizimsel olarak yanlış olan metin altında görüntüler. Hata işaretçileri genellikle, kullanıcıların yanlış yazılmış anahtar sözcüklerin, kapatılmamış parantezler, geçersiz karakterlerden ve benzer hataların farkında olması için kullanılır.<br /><br /> MPF sınıflarında, hata işaretçileri, sınıfının yönteminde otomatik olarak işlenir <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> .|

 Bu özelliklerin birçoğu, kaynak kodu ayrıştırmak için dil hizmetinin kullanılmasını gerektirir. Genellikle derleyici veya yorumlayıcı için simgeleme ve ayrıştırma kodunu yeniden kullanabilirsiniz.

 Aşağıdaki özellikler programlama dilleri desteğiyle ilgilidir ancak dil hizmetlerinin bir parçası değildir:

| Özellik | Açıklama |
|-----------------------| - |
| İfade değerlendiricileri | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kesme noktalarını doğrulayarak ve **oto** hata ayıklama penceresinde görüntülenecek ifadelerin bir listesini sağlayarak hata ayıklayıcıyı destekler.<br /><br /> Daha fazla bilgi için bkz. [hata ayıklama Için dil hizmeti desteği](../../extensibility/internals/language-service-support-for-debugging.md). |
| Sembol tarama araçları | **Nesne tarayıcısı**, **sınıf görünümü**, **çağrı tarayıcısı** destekler ve **sembol sonuçlarını bulur**. |
