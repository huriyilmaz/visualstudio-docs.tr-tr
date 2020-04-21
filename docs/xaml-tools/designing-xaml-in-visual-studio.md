---
title: Tasarım XAML Visual Studio ve Visual Studio için Blend
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: eb18a2face5d9f1831bec35379a423f272c3e6ce
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649819"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Tasarım XAML Visual Studio ve Blend Visual Studio için

Visual Studio ve Blend for Visual Studio, çeşitli uygulama türleri için XAML ile ilgi çekici kullanıcı arayüzleri ve zengin medya deneyimleri oluşturmak için görsel araçlar sağlar. Her iki tümleşik geliştirme ortamı (IDE), görsel bir XAML düzenleyicisi (tasarımcı) dahil olmak üzere ortak bir özellik kümesini paylaşır. WPF ve UWP platformlarını destekleyen Blend for Visual Studio, görsel durumlar tasarlamak ve animasyonlar oluşturmak için ek araçlar sağlar.

Visual Studio ve Blend for Visual Studio arasında ileri geri geçiş yapabilir ve hatta aynı projeyi aynı anda her iki IDE'de de açabilirsiniz. Bir IDE'de XAML dosyalarına kaydedilen değişiklikler, diğer IDE'ye geçtiğinızda otomatik yeniden yükleme yoluyla uygulanabilir. Her iki IDE'de **Araçlar** > **Seçenekleri** > **Çevre** > **Belgeleri'ne** yönlendirerek yeniden yükleme davranışını denetleyebilirsiniz.

## <a name="installation"></a>Yükleme

- WPF uygulamaları oluşturmak için Visual Studio'da **.NET masaüstü geliştirme** iş yükünü yükleyin. Visual Studio için Blend da kurulacak.

     ![Visual Studio Installer'dan .NET Masaüstü Geliştirme iş yükünün ekran görüntüsü](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- UWP uygulamaları oluşturmak için Visual Studio'da **Evrensel Windows Platformu geliştirme** iş yükünü yükleyin. Visual Studio için Blend da kurulacak.

     ![Visual Studio Installer'dan Evrensel Windows Platform Geliştirme iş yükünün ekran görüntüsü](../xaml-tools/media/uwp-workload.png)

- Xamarin.Forms uygulamaları oluşturmak için Visual Studio'da .NET iş **yüküyle Mobil geliştirmeyi** yükleyin. Visual Studio için Blend yüklü *değildir;* Blend Xamarin.Forms uygulamalarını desteklemez.

     ![Visual Studio Installer'dan .NET iş yükü ile Mobil Geliştirme ekran görüntüsü](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Paylaşılan özellikler

En temel geliştirme görevleri için Visual Studio ve Blend for Visual Studio, bazı ince farklılıklarla aynı pencere ve yetenek kümesini paylaşır. Bazı önemli noktalar şunlardır:

- **IntelliSense:** Her iki IDe'ler de bildirim tamamlama gibi IntelliSense yeteneklerini destekler.

- **Hata ayıklama:** Çalışan bir uygulamayı hata ayıklamak için kodda kesme noktaları ayarlamak ve uygulama çalışırken XAML kodunuzu değiştirmek için [Hot Reload'ı](../xaml-tools/xaml-hot-reload.md) kullanmak da dahil olmak üzere [Visual Studio](inspect-xaml-properties-while-debugging.md) ve Blend for [Visual Studio'da](../xaml-tools/debug-xaml-in-blend.md)hata ayıklama yapabilirsiniz. Visual Studio ile tutarlı bir hata ayıklama deneyimi sürdürmek için, Visual Studio için Blend Visual Studio'nun hata ayıklama pencerelerinin ve araç çubuklarının çoğunu içerir.

- **Dosya yeniden yükleme:** XAML dosyalarınızı Visual Studio veya Blend for Visual Studio'da edinebilirsiniz. IDA'lar arasında geçiş yaptığınızda kaydedilen düzenlenmiş dosyalar otomatik olarak yeniden yüklenir. Her iki IDE'de **Araçlar** > **Seçenekleri** > **Çevre** > **Belgeleri'ne** yönlendirerek yeniden yükleme davranışını denetleyebilirsiniz.

- **Senkronize düzenler ve ayarlar:** Tasarım özelleştirme aracı pencere düzenleri ve Visual Studio veya Karma for Visual Studio için ayarlar tercihleri, aynı kişiselleştirme hesabıyla oturum açtığınızda aygıtlarınız ve sürümleriniz arasında senkronize edilir. Bkz. [Birden çok bilgisayarda ayarları eşitle.](../ide/synchronized-settings-in-visual-studio.md)

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Visual Studio için Blend'te gelişmiş yetenekler

Üretkenliğinizi artırmak için aşağıdaki görevler için Visual Studio için Blend'i kullanmayı düşünün. Bu alanlar Blend for Visual Studio'nun visual studio tasarımcısından veya koddan daha fazla işlevsellik sunduğu alanlardır.

| Görev | Visual Studio | Visual Studio için Blend | Daha fazla bilgi |
| - | - | - | - |
| **Görsel durumları tasarla** | Görsel durumları tasarlamanıza yardımcı olacak bir araç yoktur; bunları programlı olarak oluşturmanız gerekir. | Durumuna göre denetimin görünümünü değiştirmek için tasarım araçlarını kullanın. | [Görsel durumlar](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Animasyonlar oluşturma** |Animasyonlar için tasarım aracı yoktur; bunları programlı bir şekilde oluşturmanız gerekir. Bu, WPF'deki animasyon ve zamanlama sisteminin anlaşılmasını ve kapsamlı kodlama uzmanlığını gerektirir.|Animasyonları görsel olarak oluşturursunuz ve bunları Karma for Visual Studio'da önizleyebilirsiniz. Bu, animasyonlarınızı kod halinde oluşturmaktan daha hızlı ve daha doğrudur. Kullanıcı etkileşimini işlemek için tetikleyiciler ekleyebilir ve olay işleyicileri ve diğer işlevler eklemek için koda geçebilirsiniz.|[Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Daha kolay manipülasyon için şekilleri ve metni yollara dönüştürme**|Desteklenmiyor.|Şekillerde (dikdörtgenler ve elipsler gibi) ince veya dramatik değişiklikler yaparak, bunları daha iyi düzenleme denetimi sağlayan yollara dönüştürebilirsiniz. Yolları yeniden şekillendirebilir veya birleştirebilir ve birden çok şekilde bileşik yollar oluşturabilirsiniz.<br /><br />Ayrıca, metin bloklarını vektör görüntüsü olarak işlemek için yollara dönüştürebilirsiniz.|[Şekiller ve yollar çizin](../xaml-tools/draw-shapes-and-paths.md)|
|**Denetimleri, şablonları ve stilleri edin**|WPF stilleri ve şablonları hakkında kodlama ve bilgi gerektirir.|Herhangi bir görüntüyü kontrole dönüştürün.<br /><br />Yalnızca birkaç fare tıklamasıyla denetimlerde, stillerde ve şablonlarda değişiklik yapmak için şablon düzenleme araçlarını kullanın.<br /><br />Örneğin, ortak WPF denetimleri (düğmeler, liste kutuları, kaydırma çubukları, menüler, vb. gibi) uygulamak ve renklerini, stillerini veya temel şablonlarını doğrudan Visual Studio için Karışım'da değiştirmek için Visual Studio stili kaynaklarını blend olarak kullanabilirsiniz. Daha sonra isterseniz son rötuşlar için koda geçebilirsiniz.|[Nesnelerin stilini değiştirme](modify-the-style-of-objects-in-blend.md)|
|**UI'nizi verilere bağlama**|SQL Server veritabanı, WCF veya web hizmeti, nesne veya SharePoint listesi gibi kaynaklardan bir veri kaynağı oluşturabilir ve ardından veri kaynağını UI denetimlerinize bağlayabilirsiniz.<br /><br />Etkileşimli bir tasarım deneyimi için tasarım zamanı verileri elle oluşturulmalıdır.|.NET Framework uygulamaları için prototip oluşturma ve test etmek için kolayca örnek veriler oluşturun. Hazır olduğunuzda canlı verilere geçin.<br /><br />Visual Studio'nun veri oluşturma özellikleri için Blend olağanüstüdür (anında kolayca isim, sayı, URL ve fotoğraf ekleyebilirsiniz) ve size çok zaman kazandırabilirsiniz.<br /><br />Canlı veriler için, UI denetimlerinizi bir XML dosyasına veya herhangi bir CLR veri kaynağına bağlayabilirsiniz.|[Verileri görüntüleme](display-data-in-blend.md)|

Gelişmiş XAML tasarımı hakkında daha fazla bilgi için Visual [Studio için Blend'i kullanarak bir kullanıcı arabirimi oluşturma bölümüne](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye genel bakış](xaml-overview.md)
- [Visual Studio için Blend genel bakış](creating-a-ui-by-using-blend-for-visual-studio.md)
