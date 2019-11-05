---
title: Visual Studio ve Blend’de XAML tasarlama
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9cfa2d216baf89d4b7a886ff9d7b56b8b946b8b
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73569048"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Visual Studio ve Visual Studio için Blend XAML tasarlama

Visual Studio ve Visual Studio için Blend her ikisi de birçok uygulama türü için XAML ile etkileyici kullanıcı arabirimleri ve zengin medya deneyimleri oluşturmaya yönelik görsel araçlar sağlar. Tümleşik geliştirme ortamları (IDE), Visual XAML Düzenleyicisi (Tasarımcı) dahil olmak üzere ortak bir özellikler kümesini paylaşır. WPF ve UWP platformlarını destekleyen Visual Studio için Blend, görsel durumlar tasarlamak ve animasyonlar oluşturmak için ek araçlar sağlar.

Visual Studio ile Visual Studio için Blend arasında geri dönebilir ve aynı projede her iki Ides içinde de aynı projeyi açabilmenize de sahip olabilirsiniz. Bir IDE 'deki XAML dosyalarına kaydedilen değişiklikler, diğer IDE 'ye geçtiğinizde otomatik yeniden yükleme yoluyla uygulanabilir. Yeniden yükleme davranışını, **araçlar**  > **Seçenekler** ' e gıderek, her iki ıde içindeki**Belgeler** ** >   > ** .

## <a name="installation"></a>Yükleme

- WPF uygulamaları oluşturmak için, Visual Studio 'da **.net masaüstü geliştirme** iş yükünü yüklemek. Visual Studio için Blend de yüklenecektir.
- UWP uygulamaları oluşturmak için, Visual Studio 'da **Evrensel Windows platformu geliştirme** iş yükünü yüklersiniz. Visual Studio için Blend de yüklenecektir.
- Xamarin. Forms uygulamaları oluşturmak için, Visual Studio 'da .NET iş yüküne **sahip mobil geliştirme** 'yı yüklersiniz. Visual Studio için Blend yüklü *değil* ; Blend, Xamarin. Forms uygulamalarını desteklemez.

## <a name="shared-capabilities"></a>Paylaşılan yetenekler

Çoğu temel geliştirme görevi için, Visual Studio ve Visual Studio için Blend, bazı hafif farklılıklar ile aynı Windows ve özellik kümesini paylaşır. Bazı önemli noktalar şunlardır:

- **IntelliSense:** Her iki Ides de ifade tamamlama gibi IntelliSense özelliklerini destekler.

- **Hata ayıklama:** Çalışan bir uygulamada hata ayıklamak için kod noktalarını ayarlama ve uygulama çalışırken XAML kodunuzu değiştirmek için [sık yeniden yükleme](../xaml-tools/xaml-hot-reload.md) kullanma dahil olmak üzere, [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) ve [Visual Studio için Blend](../xaml-tools/debug-xaml-in-blend.md)hata ayıklaması yapabilirsiniz. Visual Studio ile tutarlı bir hata ayıklama deneyimi sağlamak için Visual Studio için Blend Visual Studio 'nun hata ayıklama pencerelerini ve araç çubuklarının çoğunu içerir.

- **Dosya yeniden yükleme:** XAML dosyalarınızı, Visual Studio veya Visual Studio için Blend düzenleyebilirsiniz. Değiştirilmiş dosyalar, Ides 'ler arasında geçiş yaparken otomatik olarak yeniden yüklenir. Yeniden yükleme davranışını, **araçlar**  > **Seçenekler** ' e gıderek, her iki ıde içindeki**Belgeler** ** >   > ** .

- **Eşitlenmiş düzenler ve Ayarlar:** Visual Studio veya Visual Studio için Blend için özelleştirilmiş araç penceresi düzenleri ve ayarları tercihleri, aynı kişiselleştirme hesabıyla oturum açtığınızda cihazlarınız ve sürümleriniz arasında eşitlenir. Bkz. [birden çok bilgisayar üzerinde ayarları eşitler](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Visual Studio için Blend gelişmiş özellikleri

Verimliliğinizi artırmak için aşağıdaki görevler için Visual Studio için Blend kullanmayı düşünün. Bunlar, Visual Studio için Blend Visual Studio Tasarımcısı veya yalnızca koddan daha fazla işlevsellik sunduğu alanlardır.

| Görev | Visual Studio | Visual Studio için Blend | Daha fazla bilgi |
| - | - | - | - |
| **Görsel durumları tasarlama** | Görsel durumları tasarlamanıza yardımcı olacak bir araç yoktur; bunları programlı olarak oluşturmanız gerekir. | Bir denetimin görünüşünü durumuna göre değiştirmek için tasarım araçları 'nı kullanın. | [Görsel durumlar](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Animasyon oluşturma** |Animasyonlar için tasarım aracı yoktur; bunları programlı olarak oluşturmanız gerekir. Bu, WPF ve kapsamlı kodlama uzmanlığına yönelik animasyon ve zamanlama sisteminin anlaşılmasına gerek duyar.|Animasyonları görsel olarak oluşturur ve Visual Studio için Blend önizleme uygulayabilirsiniz. Bu, kodda animasyonlarınızı derlemeden daha hızlı ve daha doğru. Kullanıcı etkileşimini işlemek için Tetikleyiciler ekleyebilirsiniz ve olay işleyicileri ve diğer işlevleri eklemek için koda geçiş yapabilirsiniz.|[Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Daha kolay bir işleme için şekilleri ve metinleri yollara dönüştürün**|Desteklenmez.|Daha iyi bir Editing denetimi sağlayan yollara dönüştürerek (dikdörtgenler ve üç nokta gibi) şekillere daha zarif veya çarpıcı değişiklikler yapabilirsiniz. Yolları yeniden şekillendirebilirsiniz veya birleştirebilir ve birden çok şekil arasından bileşik yollar oluşturabilirsiniz.<br /><br />Ayrıca, vektör görüntüleri olarak işlemek için metin bloklarını yollara dönüştürebilirsiniz.|[Şekiller ve yollar çizme](../xaml-tools/draw-shapes-and-paths.md)|
|**Denetimleri, şablonları ve stilleri düzenleme**|WPF stilleri ve şablonları için kodlama ve bilgi gerektirir.|Herhangi bir görüntüyü denetime dönüştürün.<br /><br />Yalnızca birkaç fare tıklamasıyla denetimlerde, stillerde ve şablonlarda değişiklikler yapmak için şablon Düzenle araçlarını kullanın.<br /><br />Örneğin, yaygın WPF denetimlerini (düğmeler, liste kutuları, kaydırma çubukları, menüler vb.) uygulamak ve renk, stil veya temel şablonu doğrudan Visual Studio için Blend içinde değiştirmek için Visual Studio için Blend stil kaynaklarını kullanabilirsiniz. Daha sonra isterseniz, daha sonra sonlandırma için koda geçebilirsiniz.|[Nesnelerin stilini değiştirme](modify-the-style-of-objects-in-blend.md)|
|**Kullanıcı arabiriminizi verilerinize bağlama**|SQL Server veritabanı, WCF veya Web hizmeti, nesne veya SharePoint listesi gibi kaynaklardan bir veri kaynağı oluşturabilir ve ardından veri kaynağını UI denetimleriniz ile bağlayabilirsiniz.<br /><br />Tasarım zamanı verilerinin etkileşimli bir tasarım deneyimi için el ile oluşturulması gerekir.|.NET Framework uygulamalar için, Prototipleme ve test için kolayca örnek veriler oluşturun. Hazırsanız canlı verilere geçiş yapın.<br /><br />Visual Studio için Blend veri oluşturma özellikleri çok önemlidir (adları, rakamları, URL 'Leri ve fotoğrafları kolayca anında ekleyebilirsiniz) ve size çok zaman kazandırabilir.<br /><br />Canlı veriler için, UI denetimlerinizi bir XML dosyasına veya herhangi bir CLR veri kaynağına bağlayabilirsiniz.|[Verileri görüntüleme](display-data-in-blend.md)|

Gelişmiş XAML tasarımı hakkında daha fazla bilgi için bkz. [Visual Studio için Blend kullanarak Kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).
