---
title: XAML'i Visual Studio ve Visual Studio için Blend
titleSuffix: ''
description: XAML'de kullanıcı arabirimi ve deneyimler Visual Studio Visual Studio için Blend görsel tasarım araçlarının özellikleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 3367574ab52f02d3c6d4c8316eb6f616e5ca80540e5ed8874b8aad60280cd7a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351614"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>XAML'i Visual Studio ve Visual Studio için Blend

Visual Studio Visual Studio için Blend, çeşitli uygulama türleri için XAML ile etkileşimli kullanıcı arabirimleri ve zengin medya deneyimleri oluşturmak için görsel araçlar sağlar. Her iki tümleşik geliştirme ortamları da (IDE), görsel XAML düzenleyicisi (tasarımcı) dahil olmak üzere ortak bir özellik kümesi paylaşır. Visual Studio için Blend WPF ve UWP platformlarını destekleyen bir uygulama, görsel durumları tasarlamaya ve animasyon oluşturmaya yönelik ek araçlar sağlar.

Visual Studio ile Visual Studio için Blend arasında geçiş Visual Studio için Blend ve hatta aynı projenin aynı anda her iki IDE'de de açılmasını sabilirsiniz. Bir IDE'de XAML dosyalarına kaydedilen değişiklikler, diğer IDE'ye geçiş yaptığınız zaman otomatik yeniden yükleme yoluyla uygulanabilir. IDE'den herhangi bir IDE'de Araçlar Seçenekler Ortam   >    >  **Belgeleri'ne**  >  **giderek yeniden** yükleme davranışını kontrol edin.

## <a name="installation"></a>Yükleme

- WPF uygulamaları oluşturmak için **.NET** masaüstü geliştirme iş yükünü Visual Studio. Visual Studio için Blend da yüklenir.

     ![Uygulamanın .NET Masaüstü Geliştirme iş yükünün ekran Visual Studio Yükleyicisi](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- UWP uygulamaları oluşturmak için Universal **Windows Platform geliştirme iş yükünü** Visual Studio. Visual Studio için Blend da yüklenir.

     ![Visual Studio Yükleyicisi'den Universal Windows Platform Geliştirme iş yükünün ekran Visual Studio Yükleyicisi](../xaml-tools/media/uwp-workload.png)

- Xamarin.Forms uygulamaları oluşturmak için.NET ile **mobil geliştirme iş yükünü** Visual Studio. Visual Studio için Blend *yüklü* değil; Blend, Xamarin.Forms uygulamalarını desteklemez.

     ![.NET iş yüküyle Mobil Geliştirme'nin ekran görüntüsü Visual Studio Yükleyicisi](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Paylaşılan özellikler

Çoğu temel geliştirme görevi için Visual Studio ve Visual Studio için Blend, bazı küçük farklılıklarla aynı pencere ve özellikler kümesi paylaşır. Bazı önemli noktalar şunlardır:

- **IntelliSense:** Her iki IDE de deyim tamamlama gibi IntelliSense özelliklerini destekler.

- **Hata ayıklama:** Visual Studio ve [Visual Studio için Blend'da](inspect-xaml-properties-while-debugging.md) hata [](../xaml-tools/debug-xaml-in-blend.md)ayıklar, çalışan bir uygulamada hata ayıklamak için kodda kesme noktaları ayarlama ve [Çalışırken Yeniden Yükleme](../xaml-tools/xaml-hot-reload.md) çalışırken XAML kodunuzu değiştirmek için Çalışırken Yeniden Yükleme kullanma da dahil olmak üzere hata ayıklar. Visual Studio ile tutarlı bir hata Visual Studio için Blend sağlamak için Visual Studio pencere ve araç çubuklarının çoğunu içerir.

- **Dosya yeniden yükleme:** XAML dosyalarınızı Visual Studio veya Visual Studio için Blend. IDE'ler arasında geçiş yapılırken, kaydedilen dosyalar otomatik olarak yeniden yüklenir. IDE'den herhangi bir IDE'de Araçlar Seçenekler Ortam   >    >  **Belgeleri'ne**  >  **giderek yeniden** yükleme davranışını kontrol edin.

- **Eşitlenmiş düzenler ve ayarlar:** Aynı kişiselleştirme hesabıyla oturum Visual Studio veya Visual Studio için Blend için özelleştirme aracı penceresi düzenleri ve ayar tercihleri cihazlarınız ve sürümleriniz arasında eşitlenir. Bkz. [Birden çok bilgisayarda ayarları eşitleme.](../ide/synchronized-settings-in-visual-studio.md)

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Visual Studio için Blend'daki gelişmiş özellikler

Üretkenliğinizi artırmak için, aşağıdaki Visual Studio için Blend için Visual Studio için Blend kullanmayı göz önünde bulundurabilirsiniz. Bunlar, tek başına Visual Studio için Blend veya koddan daha fazla işlev Visual Studio alandır.

| Görev | Visual Studio | Visual Studio için Blend | Daha fazla bilgi |
| - | - | - | - |
| **Görsel durumları tasarlama** | Görsel durumları tasarlamanıza yardımcı olacak bir araç yoktur; bunları program aracılığıyla oluşturmanız gerekir. | Bir denetimin durumunu temel alarak görünümünü değiştirmek için tasarım araçlarını kullanın. | [Görsel durumlar](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Animasyon oluşturma** |Animasyonlar için tasarım aracı yoktur; bunları program aracılığıyla oluşturmanız gerekir. Bunun için WPF'de animasyon ve zamanlama sisteminin anlaşılması ve kapsamlı kodlama uzmanlığı gerekir.|Animasyonları görsel olarak oluşturabilir ve görsel olarak önizleme Visual Studio için Blend. Bu, animasyonlarınızı kodda oluşturmaktan daha hızlı ve daha kesindir. Kullanıcı etkileşimini işlemek için tetikleyiciler ekleyebilir ve olay işleyicileri ve diğer işlevler eklemek için koda geçebilirsiniz.|[Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Daha kolay işleme için şekilleri ve metni yollara dönüştür**|Desteklenmez.|Şekiller üzerinde (dikdörtgenler ve üç nokta gibi) daha iyi düzenleme denetimi sağlayan yollara dönüştürerek küçük veya çarpıcı değişiklikler yapabilirsiniz. Yolları yeniden şekillendirebilirsiniz veya birleştirebilirsiniz ve birden çok şekilde bileşik yollar oluşturabilirsiniz.<br /><br />Metin bloklarını vektör görüntüleri olarak işlemek için yollara da dönüştürebilirsiniz.|[Şekiller ve yollar çizin](../xaml-tools/draw-shapes-and-paths.md)|
|**Denetimleri, şablonları ve stilleri düzenleme**|WPF stilleri ve şablonları için kodlama ve bilgi gerektirir.|Herhangi bir görüntüyü denetime dönüştürebilirsiniz.<br /><br />Yalnızca birkaç fare tıklaması ile denetimlerde, stillerde ve şablonlarda değişiklik yapmak için şablon düzenleme araçlarını kullanın.<br /><br />Örneğin, yaygın WPF denetimlerini (düğmeler, liste kutuları, kaydırma çubukları, menüler vb.) uygulamak için Visual Studio için Blend stil kaynaklarını kullanabilir ve renklerini, stillerini veya temel alınan şablonlarını doğrudan Visual Studio için Blend. Daha sonra gerektirdikten sonra dokunmaları sonlandırmak için koda geçebilirsiniz.|[Nesnelerin stilini değiştirme](modify-the-style-of-objects-in-blend.md)|
|**Bağlan kullanıcı arabiriminizi veriye göre özelleştirme**|SQL Server veritabanı, WCF veya web hizmeti, nesne veya SharePoint listesi gibi kaynaklardan bir veri kaynağı oluşturabilir ve ardından veri kaynağını kullanıcı arabirimi denetimlerinize bekleyebilirsiniz.<br /><br />Etkileşimli bir tasarım deneyimi için tasarım zamanı verileri el ile oluşturulacak.|Örnek .NET Framework için, örnek verileri kolayca oluşturma ve test etme. Hazır olduğunda canlı verilere geçiş.<br /><br />Visual Studio için Blend oluşturma özellikleri olağanüstüdir (adları, sayıları, URL'leri ve fotoğrafları kolayca ekleyebilir) ve çok zaman tasarrufu yapabilirsiniz.<br /><br />Canlı veriler için kullanıcı arabirimi denetimlerinizi bir XML dosyasına veya herhangi bir CLR veri kaynağına bebilirsiniz.|[Verileri görüntüleme](display-data-in-blend.md)|

Gelişmiş XAML tasarımı hakkında daha fazla bilgi için [bkz.](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)Visual Studio için Blend.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye genel bakış](xaml-overview.md)
- [Visual Studio için Blend genel bakış](creating-a-ui-by-using-blend-for-visual-studio.md)
