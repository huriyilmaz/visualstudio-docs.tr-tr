---
title: Visual Studio ve Blend’de XAML tasarlama
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 97946fc2ed79b83fbc7d3ce3c3dc4960934eb5ab
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592982"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Visual Studio ve Visual Studio için Blend XAML tasarlama

Visual Studio ve Visual Studio için Blend kullanıcı arabirimlerinin ilgi çekici yapı için görsel araçların sağlanmasına ve çeşitli uygulama türleri için XAML ile zengin medya deneyimlerini. Tümleşik geliştirme ortamları (IDE), Visual XAML Düzenleyicisi (Tasarımcı) dahil olmak üzere ortak bir özellikler kümesini paylaşır. WPF ve UWP platformlarını destekleyen Visual Studio için Blend, görsel durumlar tasarlamak ve animasyonlar oluşturmak için ek araçlar sağlar.

Visual Studio ile Visual Studio için Blend arasında geri dönebilir ve aynı projede her iki Ides içinde de aynı projeyi açabilmenize de sahip olabilirsiniz. Bir IDE 'deki XAML dosyalarına kaydedilen değişiklikler, diğer IDE 'ye geçtiğinizde otomatik yeniden yükleme yoluyla uygulanabilir. Yeniden yükleme davranışını, **araçlar** > **Seçenekler** ' e gıderek, her iki ıde içindeki **Belgeler** ** >  > ** .

## <a name="installation"></a>Yükleme

- WPF uygulamaları oluşturmak için, Visual Studio 'da **.net masaüstü geliştirme** iş yükünü yüklemek. Visual Studio için Blend de yüklenecektir.
- UWP uygulamaları oluşturmak için, Visual Studio 'da **Evrensel Windows platformu geliştirme** iş yükünü yüklersiniz. Visual Studio için Blend de yüklenecektir.
- Xamarin. Forms uygulamaları oluşturmak için, Visual Studio 'da .NET iş yüküne **sahip mobil geliştirme** 'yı yüklersiniz. Visual Studio için Blend yüklü *değil* ; Blend, Xamarin. Forms uygulamalarını desteklemez.

## <a name="shared-capabilities"></a>Paylaşılan özellikler

Çoğu temel geliştirme görevi için, Visual Studio ve Visual Studio için Blend, bazı hafif farklılıklar ile aynı Windows ve özellik kümesini paylaşır. Bazı önemli noktalar şunlardır:

- **IntelliSense:** Her iki Ides de ifade tamamlama gibi IntelliSense özelliklerini destekler.

- **Hata ayıklama:** Çalışan bir uygulamada hata ayıklamak için kod noktalarını ayarlama ve uygulama çalışırken XAML kodunuzu değiştirmek için [sık yeniden yükleme](../xaml-tools/xaml-hot-reload.md) kullanma dahil olmak üzere, [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) ve [Visual Studio için Blend](../xaml-tools/debug-xaml-in-blend.md)hata ayıklaması yapabilirsiniz. Visual Studio ile hata ayıklama tutarlı bir deneyim sağlamak için Visual Studio için Blend çoğu Visual Studio hata ayıklama windows ve araç çubuklarını içerir.

- **Dosya yeniden yükleme:** XAML dosyalarınızı, Visual Studio veya Visual Studio için Blend düzenleyebilirsiniz. Değiştirilmiş dosyalar, Ides 'ler arasında geçiş yaparken otomatik olarak yeniden yüklenir. Yeniden yükleme davranışını, **araçlar** > **Seçenekler** ' e gıderek, her iki ıde içindeki **Belgeler** ** >  > ** .

- **Eşitlenmiş düzenler ve Ayarlar:** Visual Studio veya Visual Studio için Blend için özelleştirilmiş araç penceresi düzenleri ve ayarları tercihleri, aynı kişiselleştirme hesabıyla oturum açtığınızda cihazlarınız ve sürümleriniz arasında eşitlenir. Bkz: [birden fazla bilgisayara ayarları senkronize](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Visual Studio için Blend gelişmiş özellikleri

Üretkenliğinizi artırmak için aşağıdaki görevler için Visual Studio için Blend kullanarak göz önünde bulundurun. Bunlar, Visual Studio için Blend Visual Studio Tasarımcısı veya yalnızca koddan daha fazla işlevsellik sunduğu alanlardır.

| Görev | {1&gt;Visual Studio&lt;1} | Visual Studio için Blend | Daha fazla bilgi |
| - | - | - | - |
| **Görsel durumları tasarlama** | Görsel durumları tasarlamanıza yardımcı olacak bir araç yoktur; bunları programlı olarak oluşturmanız gerekir. | Bir denetimin görünüşünü durumuna göre değiştirmek için tasarım araçları 'nı kullanın. | [Görsel durumlar](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Animasyonlar oluşturma** |Animasyon için tasarım aracı yoktur; bunları programlı olarak oluşturmanız gerekir. Bu, animasyon ve zamanlama sistemine WPF ve kodlama kapsamlı uzmanlığını'nın bilinmesini gerektirir.|Görsel animasyonlar oluşturur ve bunları Visual Studio için blend'de önizlemesini görebilirsiniz. Bu daha hızlı ve kod içinde animasyonları oluşturmak daha kesin değildir. Kullanıcı etkileşimi işlemek için Tetikleyiciler ekleyebilir ve olay işleyicileri ve diğer işlevler eklemek için kod geçiş yapabilirsiniz.|[Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Şekil ve metinler yolları daha kolay düzenlemesi için dönüştürün**|Desteklenmez.|Daha iyi düzenleme denetimi sağlayan yollar dönüştürerek (örneğin, dikdörtgenler ve elipsler) şekillere ince veya çarpıcı değişiklikler yapabilirsiniz. Şekillendirmek veya yolları birleştirme ve birden çok şekillerden bileşik yollar oluşturabilir.<br /><br />Ayrıca metin blokları vektör görüntüleri yönetileceğini yolları dönüştürebilirsiniz.|[Şekiller ve yollar çizme](../xaml-tools/draw-shapes-and-paths.md)|
|**Denetimleri, şablonlar ve stiller Düzenle**|Kodlama ve WPF stilleri ve şablonları bilinmesini gerektirir.|Herhangi bir görüntü denetime açın.<br /><br />Denetimleri, stilleri ve şablonları ile yalnızca birkaç tıklamayla değişiklik yapmak için şablon düzenleme araçlarını kullanın.<br /><br />Örneğin, Visual Studio stili kaynak için Blend (örneğin, düğmeler, liste kutuları, kaydırma çubukları, menüler, vb.) ortak WPF denetimleri uygulayın ve bunların renk, stil veya doğrudan Visual Studio için blend'de temel alınan şablonu değiştirmek için kullanabilirsiniz. İsterseniz daha sonra Son dokunuşları kodunu geçiş yapabilirsiniz.|[Nesnelerin stilini değiştirme](modify-the-style-of-objects-in-blend.md)|
|**Kullanıcı Arabirimi verilere bağlanma**|SQL Server veritabanı, WCF veya Web hizmeti, nesne veya SharePoint listesi gibi kaynaklardan bir veri kaynağı oluşturabilir ve ardından veri kaynağını UI denetimleriniz ile bağlayabilirsiniz.<br /><br />Tasarım zamanı veri bir etkileşimli bir tasarımı deneyimi için el ile oluşturulması gerekir.|.NET Framework uygulamalar için, Prototipleme ve test için kolayca örnek veriler oluşturun. Hazır olduğunuzda Canlı verilere geçme.<br /><br />Visual Studio'nun veri oluşturma özellikleri bekleyen için Blend (adlar, sayılar, URL'ler ve fotoğraf kolayca anında ekleyebilirsiniz), çok zaman tasarruf edebilirsiniz.<br /><br />Canlı verileri için bir XML dosyasına veya herhangi bir CLR veri kaynağı için kullanıcı Arabirimi denetimleri bağlayabilirsiniz.|[Verileri görüntüleme](display-data-in-blend.md)|

Gelişmiş XAML tasarımı hakkında daha fazla bilgi için bkz. [Visual Studio için Blend'i kullanarak kullanıcı Arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).
