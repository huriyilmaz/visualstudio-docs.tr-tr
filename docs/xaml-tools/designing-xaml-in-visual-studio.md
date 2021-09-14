---
title: Visual Studio ve Visual Studio için Blend içinde XAML tasarlama
titleSuffix: ''
description: Visual Studio 'de görsel tasarım araçlarının özellikleri ve XAML 'de uı ve deneyimler oluşturmak için Visual Studio için Blend hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 246bcf06d72cfda39a7498075b4eb4e0b3198cf5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726056"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Visual Studio ve Visual Studio için Blend XAML tasarlama

Visual Studio ve Visual Studio için Blend her ikisi de çeşitli uygulama türleri için XAML ile etkileyici kullanıcı arabirimleri ve zengin medya deneyimleri oluşturmaya yönelik görsel araçlar sağlar. Tümleşik geliştirme ortamları (IDE), Visual XAML Düzenleyicisi (Tasarımcı) dahil olmak üzere ortak bir özellikler kümesini paylaşır. WPF ve UWP platformlarını destekleyen Visual Studio için Blend, görsel durumlar tasarlamak ve animasyonlar oluşturmak için ek araçlar sağlar.

Visual Studio ve Visual Studio için Blend arasında ileri ve geri geçiş yapabilirsiniz ve aynı proje aynı anda her iki ıdes 'de da açık olabilir. Bir IDE 'deki XAML dosyalarına kaydedilen değişiklikler, diğer IDE 'ye geçtiğinizde otomatik yeniden yükleme yoluyla uygulanabilir.   >    >    >  Her iki IDE 'deki araçlar seçenekleri ortam **belgeleri** ' ne giderek yeniden yükleme davranışını kontrol edebilirsiniz.

## <a name="installation"></a>Yükleme

- WPF uygulamaları oluşturmak için Visual Studio ' ye **.net masaüstü geliştirme** iş yükünü yüklersiniz. Visual Studio için Blend de yüklenecektir.

     ![Visual Studio Yükleyicisi .net masaüstü geliştirme iş yükünün ekran görüntüsü](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- UWP uygulamaları oluşturmak için, Visual Studio **Evrensel Windows Platformu geliştirme** iş yükünü yüklemelisiniz. Visual Studio için Blend de yüklenecektir.

     ![Visual Studio Yükleyicisi Evrensel Windows Platformu geliştirme iş yükünün ekran görüntüsü](../xaml-tools/media/uwp-workload.png)

- Xamarin. Forms uygulamaları oluşturmak için Visual Studio ' de **.NET iş yüküne sahip mobil geliştirme** 'yı yüklersiniz. Visual Studio için Blend yüklü *değil* ; Blend, Xamarin. Forms uygulamalarını desteklemez.

     ![Visual Studio Yükleyicisi .net iş yüküne sahip mobil geliştirmenin ekran görüntüsü](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Paylaşılan özellikler

en temel geliştirme görevleri için, Visual Studio ve Visual Studio için Blend aynı windows ve özellik kümesini, bazı hafif farklılıklar ile paylaşır. Bazı önemli noktalar şunlardır:

- **IntelliSense:** Her iki Ides de ifade tamamlama gibi IntelliSense özelliklerini destekler.

- **Hata ayıklama:** çalışan bir uygulamada hata ayıklamak için kod noktalarını ayarlama ve uygulama çalışırken XAML kodunuzu değiştirmek için [sık yeniden yükleme](../xaml-tools/xaml-hot-reload.md) kullanma dahil [Visual Studio](inspect-xaml-properties-while-debugging.md) ve [Visual Studio için Blend](../xaml-tools/debug-xaml-in-blend.md)hata ayıklaması yapabilirsiniz. Visual Studio ile tutarlı bir hata ayıklama deneyimi sağlamak için, Visual Studio için Blend Visual Studio hata ayıklama pencerelerinin ve araç çubuklarının çoğunu içerir.

- **Dosya yeniden yükleme:** XAML dosyalarınızı Visual Studio veya Visual Studio için Blend düzenleyebilirsiniz. Değiştirilmiş dosyalar, Ides 'ler arasında geçiş yaparken otomatik olarak yeniden yüklenir.   >    >    >  Her iki IDE 'deki araçlar seçenekleri ortam **belgeleri** ' ne giderek yeniden yükleme davranışını kontrol edebilirsiniz.

- **Eşitlenmiş düzenler ve Ayarlar:** Visual Studio veya Visual Studio için Blend için tasarım özelleştirme aracı pencere düzenleri ve ayarları tercihleri, aynı kişiselleştirme hesabıyla oturum açtığınızda cihazlarınız ve sürümleriniz arasında eşitlenir. Bkz. [birden çok bilgisayar üzerinde ayarları eşitler](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Visual Studio için Blend gelişmiş özellikleri

verimliliğinizi artırmak için aşağıdaki görevler için Visual Studio için Blend kullanmayı düşünün. bunlar, Visual Studio için Blend Visual Studio tasarımcıdan veya yalnızca koddan daha fazla işlevsellik sunduğu alanlardır.

| Görev | Visual Studio | Visual Studio için Blend | Daha fazla bilgi |
| - | - | - | - |
| **Görsel durumları tasarlama** | Görsel durumları tasarlamanıza yardımcı olacak bir araç yoktur; bunları programlı olarak oluşturmanız gerekir. | Bir denetimin görünüşünü durumuna göre değiştirmek için tasarım araçları 'nı kullanın. | [Görsel durumlar](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Animasyon oluşturma** |Animasyonlar için tasarım aracı yoktur; bunları programlı olarak oluşturmanız gerekir. Bu, WPF ve kapsamlı kodlama uzmanlığına yönelik animasyon ve zamanlama sisteminin anlaşılmasına gerek duyar.|animasyonları görsel olarak oluşturur ve Visual Studio için Blend önizleme uygulayabilirsiniz. Bu, kodda animasyonlarınızı derlemeden daha hızlı ve daha doğru. Kullanıcı etkileşimini işlemek için Tetikleyiciler ekleyebilirsiniz ve olay işleyicileri ve diğer işlevleri eklemek için koda geçiş yapabilirsiniz.|[Nesnelere animasyon ekleme](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Daha kolay bir işleme için şekilleri ve metinleri yollara dönüştürün**|Desteklenmez.|Daha iyi bir Editing denetimi sağlayan yollara dönüştürerek (dikdörtgenler ve üç nokta gibi) şekillere daha zarif veya çarpıcı değişiklikler yapabilirsiniz. Yolları yeniden şekillendirebilirsiniz veya birleştirebilir ve birden çok şekil arasından bileşik yollar oluşturabilirsiniz.<br /><br />Ayrıca, vektör görüntüleri olarak işlemek için metin bloklarını yollara dönüştürebilirsiniz.|[Şekiller ve yollar çizin](../xaml-tools/draw-shapes-and-paths.md)|
|**Denetimleri, şablonları ve stilleri düzenleme**|WPF stilleri ve şablonları için kodlama ve bilgi gerektirir.|Herhangi bir görüntüyü denetime dönüştürün.<br /><br />Yalnızca birkaç fare tıklamasıyla denetimlerde, stillerde ve şablonlarda değişiklikler yapmak için şablon Düzenle araçlarını kullanın.<br /><br />örneğin, yaygın WPF denetimlerini (düğmeler, liste kutuları, kaydırma çubukları, menüler vb.) uygulamak ve renk, stil veya temel şablonu doğrudan Visual Studio için Blend içinde değiştirmek için Visual Studio için Blend stil kaynaklarını kullanabilirsiniz. Daha sonra isterseniz, daha sonra sonlandırma için koda geçebilirsiniz.|[Nesnelerin stilini değiştirme](modify-the-style-of-objects-in-blend.md)|
|**kullanıcı arabiriminizi verilere Bağlan**|SQL Server veritabanı, WCF veya web hizmeti, nesne veya SharePoint listesi gibi kaynaklardan bir veri kaynağı oluşturabilir ve ardından veri kaynağını uı denetimleriniz ile bağlayabilirsiniz.<br /><br />Tasarım zamanı verilerinin etkileşimli bir tasarım deneyimi için el ile oluşturulması gerekir.|.NET Framework uygulamalar için, prototipleme ve test için kolayca örnek veriler oluşturun. Hazırsanız canlı verilere geçiş yapın.<br /><br />Visual Studio için Blend veri oluşturma özellikleri çok önemlidir (adları, rakamları, url 'leri ve fotoğrafları kolayca anında ekleyebilirsiniz) ve size çok zaman kazandırabilir.<br /><br />Canlı veriler için, UI denetimlerinizi bir XML dosyasına veya herhangi bir CLR veri kaynağına bağlayabilirsiniz.|[Verileri görüntüleme](display-data-in-blend.md)|

gelişmiş XAML tasarımı hakkında daha fazla bilgi için bkz. [Visual Studio için Blend kullanarak kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye genel bakış](xaml-overview.md)
- [Visual Studio için Blend genel bakış](creating-a-ui-by-using-blend-for-visual-studio.md)
