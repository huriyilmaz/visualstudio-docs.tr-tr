---
title: Eski Dil Hizmeti Temelleri | Microsoft Dokümanlar
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
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707420"
---
# <a name="legacy-language-service-essentials"></a>Eski Dil Hizmeti Temel Bileşenleri
Bir programlama dilini Visual Studio'ya entegre etmek için bir dil hizmeti sağlamanız gerekir. Bu konu, eski dil hizmetlerinde bulunan özellikleri açıklar.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Bir dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Editör ve Dil Hizmeti Uzantıları'na](../../extensibility/editor-and-language-service-extensions.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Eski dil hizmetleri aşağıdaki özellikleri sağlar:

|Özellik|Açıklama|
|-------------|-----------------|
|Sözdizimi boyama|Düzenleyici görünümünün bir dilin farklı öğeleri için farklı renkler ve yazı tipi stillerini görüntülemesine neden olur. Bu farklılaşma, dosyaların okunmasını ve daha kolay bir şekilde okunmasını ve düzelmesini sağlayabilir.<br /><br /> Genel bilgi için, [Eski Dil Hizmetinde Sözdizimi Boyama'ya](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)bakın.<br /><br /> Yönetilen paket çerçevesindeki (MPF) bu özellik hakkında bilgi için, [Eski Dil Hizmetinde Sözdizimi Renklendirme'ye](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)bakın.|
|İfade tamamlama|Kullanıcının yazmaya başladığı bir ifadeyi veya anahtar kelimeyi tamamlar. Ekstre tamamlama, kullanıcıların daha az yazma ve daha az hata şansı yla zor ifadeleri daha kolay girmenize yardımcı olur.<br /><br /> Genel bilgi için, [Eski Dil Hizmetinde İfade Tamamlama'ya](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)bakın.<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi için, [Eski Dil Hizmetinde Sözcük Tamamlama'ya](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)bakın.|
|Ayraç eşleştirme|Ayraçlar gibi eşleştirilmiş karakterleri vurgular. Kullanıcı "}" gibi bir kapanış karakteri yazdığında, ayraç eşleştirmesi "{" gibi karşılık gelen açılış karakterini vurgular. Çevreleyen karakterlerin çeşitli düzeyleri olduğunda, bu özellik kullanıcıların çevreleyen karakterlerin doğru eşlenediğini onaylamalarına yardımcı olur.<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi [için, Eski Dil Hizmetinde Ayraç Eşleştirme'ye](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)bakın.|
|Parametre bilgi araç ipuçları|Kullanıcının şu anda yazmakta olduğu aşırı yüklenilen yöntem için olası imzaların listesini görüntüler.<br /><br /> Genel bilgi için, [Eski Dil Hizmetindeki Parametre Bilgileri'ne](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)bakın.<br /><br /> MPF'deki bu özellik hakkında daha fazla bilgi [için, Eski Dil Hizmetinde Parametre Bilgileri'ne](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)bakın.|
|Hata işaretleri|Sözdizimsel olarak yanlış olan metnin altında kıvrımlı olarak da bilinen dalgalı kırmızı bir alt çizgi yi görüntüler. Hata işaretçileri genellikle kullanıcıların yanlış yazılmış anahtar kelimeler, kapalı olmayan parantezler, geçersiz karakterler ve benzer hatalar hakkında bilgi vermek için kullanılır.<br /><br /> MPF sınıflarında hata işaretçileri <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfın yönteminde otomatik olarak işlenir.|

 Bu özelliklerin çoğu, kaynak kodu ayrışdırmak için dil hizmeti gerektirir. Derleyiciniz veya yorumlayıcınız için belirteç ve ayrıştırma kodunu sık sık yeniden kullanabilirsiniz.

 Aşağıdaki özellikler programlama dillerini desteklemekle ilgilidir, ancak dil hizmetlerinin bir parçası değildir:

| Özellik | Açıklama |
|-----------------------| - |
| İfade değerlendiriciler | Kesme noktalarını doğrulayarak ve Otomatik Ler hata ayıklama penceresinde görüntülenecek ifadelerin listesini sağlayarak hata ayıklayıcıyı destekler. **Autos** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]<br /><br /> Daha fazla bilgi için Hata [Ayıklama için Dil Hizmeti Desteği'ne](../../extensibility/internals/language-service-support-for-debugging.md)bakın. |
| Sembol tarama araçları | **Nesne Tarayıcısını**Destekler , **Sınıf Görünümü**, **Çağrı Tarayıcısı**, ve **Sembol Sonuçlarını Bul**. |
