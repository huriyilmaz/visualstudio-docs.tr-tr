---
title: XAML tasarlama
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c48e44e0488d61e3061d680962bf22e42935090
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664718"
---
# <a name="designing-xaml-in-visual-studio"></a>Visual Studio'da XAML Tasarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ve Visual Studio için Blend her ikisi de XAML tabanlı Windows Masaüstü, Web, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)ve [Windows Mağazası](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) uygulamaları için çekici Kullanıcı arabirimleri ve zengin medya deneyimleri oluşturmaya yönelik görsel araçlar sağlar. Her ikisi de ortak bir tasarım ve araç pencereleri ve bir XAML Düzenleyicisi paylaşır, ancak Visual Studio için Blend animasyon ve davranışlar gibi daha gelişmiş görevler için ek tasarım araçları sağlar.

## <a name="choosing-the-right-tool"></a>Doğru aracı seçme
 Tasarım araçları seçiminiz büyük ölçüde beceri kümesine bağlıdır. Daha fazla kod odaklı ise, gelişmiş tasarım görevlerini gerçekleştirmek için Visual Studio 'da XAML kodu yazabilirsiniz. Daha fazla tasarıma sahipseniz, Visual Studio için Blend kod yazmadan gelişmiş görevler gerçekleştirmenizi sağlar.

 Visual Studio ile Visual Studio için Blend arasında geri dönebilir ve aynı projeyi aynı anda aynı zamanda açmış olabilirsiniz. Bir IDE 'de XAML dosyalarında yapılan değişiklikler, diğer IDE 'ye geçtiğinizde otomatik yeniden yükleme yoluyla uygulanabilir. Her iki IDE 'deki **Araçlar**, **Seçenekler** iletişim kutusundaki seçenekler aracılığıyla yeniden yükleme davranışını kontrol edebilirsiniz.

### <a name="shared-capabilities"></a>Paylaşılan Özellikler
 Çoğu temel görev için, Visual Studio için IDE ve Visual Studio için Blend, bazı hafif farklılıklar ile aynı pencere ve özellik kümesini paylaşır. Bazı önemli noktalar şunlardır:

- **Tutarlı bir kullanıcı arabirimi:** Uygulamalarınızı, Visual Studio Kullanıcı arabiriminin tanıdık bağlamı içinde tasarlayabilirsiniz, bu da daha fazla Plex ve üretken bir deneyim arasında geçiş yapar. Visual Studio için Blend, içerik ve Kullanıcı arabirimi arasındaki karşıtlığı geliştirerek tasarladığınız içeriğe odaklanmanıza yardımcı olan Visual Studio koyu temasını kullanır. Bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     ![Visual Studio için Blend IDE](../designers/media/blendide.png "BlendIDE")

- **Xaml IntelliSense:** Her iki Ides de, ifade tamamlama da dahil olmak üzere IntelliSense 'den bekleyebileceğiniz tüm ortak özellikleri, yorum oluşturma ve biçimlendirme gibi ortak düzenleyici işlemlerine yönelik desteği ve kaynakları, bağlamayı ve kodu gezinmeyi destekler.

- **Temel hata ayıklama özellikleri:** Artık, çalışan uygulamanızda hata ayıklamak için kodunuzda kesme noktalarını ayarlama dahil olmak üzere Blend 'de hata ayıklaması yapabilirsiniz. Visual Studio ile tutarlı bir hata ayıklama deneyimi sağlamak için Visual Studio için Blend Visual Studio 'nun hata ayıklama pencerelerini ve araç çubuklarının çoğunu içerir. Tanılama ve kod analizi gibi gelişmiş hata ayıklama özellikleri yalnızca Visual Studio 'da kullanılabilir. Bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugging-in-visual-studio.md).

- **Dosya yeniden yükleme deneyimi:** XAML dosyalarınızı Visual Studio için Blend ya da Visual Studio 'da düzenleyebilir ve bunları aralarında geçiş yaparken düzenlenmiş dosyalarınızın otomatik olarak yeniden yüklenmesini sağlayabilirsiniz. İş akışı kesintilerini en aza indirmek için dosya yeniden yükleme iletişim kutusunda dosya yeniden yükleme tercihlerinizi ayarlayabilirsiniz.

     ![Dosya yeniden yükleme deneyimi](../designers/media/blendfilereload.png "BlendFileReload")

- **Eşitlenmiş düzenler ve Ayarlar:** Özel düzenler araç penceresi düzen özelleştirmelerini kaydetmenizi ve uygulamanıza olanak tanır. Visual Studio, aynı Microsoft hesabı oturum açtığınızda hem Visual Studio hem de makineler arasında Visual Studio için Blend için bu özelleştirmeleri ve tercihleri eşitler. Bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

- **Ortak bir Çözüm Gezgini:** Çözüm Gezgini, projelerinizi ve bunların dosyalarını düzenlenmiş bir görünüm ve bunlarla ilişkili komutlara erişim olanağı sağlar. Çözüm Gezgini, büyük kurumsal projelerle çalışmak daha kolaydır. Bkz. [çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md).

- **Takım Gezgini:** Takım Gezgini ile, Ekip işbirliğini kolaylaştırmak için projelerinizi GIT veya TFS depolarıyla yönetebilirsiniz. [Takım Gezgini çalışma](https://msdn.microsoft.com/library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02)bölümüne bakın.

- **NuGet:** NuGet paketlerini hem Visual Studio hem de Visual Studio için Blend yönetebilirsiniz. NuGet, bir çözümden paketlerin yüklenmesini ve kaldırılmasını kolaylaştıran .NET Framework için bir paket yöneticisidir.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Visual Studio için Blend gelişmiş özellikleri
 Verimliliğinizi artırmak için aşağıdaki görevler için Visual Studio için Blend kullanmayı düşünün. Bunlar, Visual Studio için Blend Visual Studio Tasarımcısı veya yalnızca koddan daha fazla hız ve işlevsellik sunduğu alanlardır.

|Amaç|Visual Studio|Visual Studio için Blend|Daha fazla bilgi|
|--------|-------------------|-----------------------------|----------------------|
|**Animasyon oluşturma**|Animasyonlar için tasarım aracı yoktur; bunları programlı olarak oluşturmanız gerekir. Bu, WPF ve kapsamlı kodlama uzmanlığına yönelik animasyon ve zamanlama sisteminin anlaşılmasına gerek duyar.|Animasyonları görsel olarak oluşturur ve Visual Studio için Blend önizleme uygulayabilirsiniz. Bu, kodda animasyonlarınızı derlemeden daha hızlı ve daha doğru. Kullanıcı etkileşimini işlemek için Tetikleyiciler ekleyebilirsiniz ve olay işleyicileri ve diğer işlevleri eklemek için koda geçiş yapabilirsiniz.|[Nesnelere animasyon ekleme](../designers/animate-objects-in-xaml-designer.md)|
|**Daha kolay bir işleme için şekilleri ve metinleri yollara dönüştürün**|Desteklenmez.|Daha iyi bir Editing denetimi sağlayan yollara dönüştürerek (dikdörtgenler ve üç nokta gibi) şekillere daha zarif veya çarpıcı değişiklikler yapabilirsiniz.  Yolları yeniden şekillendirebilirsiniz veya birleştirebilir ve birden çok şekil arasından bileşik yollar oluşturabilirsiniz.<br /><br /> Ayrıca, vektör görüntüleri olarak işlemek için metin bloklarını yollara dönüştürebilirsiniz.|[Şekiller ve yollar çizin](../designers/draw-shapes-and-paths.md)|
|**UI Tasarımlarınız için etkileşim ekleme**|C#, Visual Basic veya C++ kodu gerektirir.|Statik Tasarımlarınız için etkileşim eklemek üzere davranışları sürükleyip bırakın. Davranışlar, sürükle/bırak, Yakınlaştır ve görsel durum değişiklikleri gibi işlevleri kapsayan, kullanıma yönelik kullanıma yönelik kod parçacıklarında bulunur. Aralarından seçim yapabileceğiniz büyüyen bir davranışlar kümesi vardır ve kendi kendinize de oluşturabilirsiniz.<br /><br /> Sonra Visual Studio için Blend özelliklerini değiştirerek veya kodda olay işleyicileri ekleyerek her bir davranışı özelleştirebilirsiniz.|[Denetimler ekleme ve bunların davranışlarını değiştirme](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Adobe resim kullanma**|Desteklenmez.|Adobe FXG, PhotoShop veya Illustrator resimlerini içeri aktarın ve Visual Studio için Blend içinde Kullanıcı arabirimini uygulayın.|[Resim, video ve ses klipleri ekleme](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Denetimleri, şablonları ve stilleri düzenleme**|WPF stilleri ve şablonları için kodlama ve bilgi gerektirir.|Herhangi bir görüntüyü denetime dönüştürün.<br /><br /> Yalnızca birkaç fare tıklamasıyla denetimlerde, stillerde ve şablonlarda değişiklikler yapmak için şablon Düzenle araçlarını kullanın.<br /><br /> Örneğin, yaygın WPF denetimlerini (düğmeler, liste kutuları, kaydırma çubukları, menüler vb.) uygulamak ve renk, stil veya temel şablonu doğrudan Visual Studio için Blend içinde değiştirmek için Visual Studio için Blend stil kaynaklarını kullanabilirsiniz. Daha sonra isterseniz, daha sonra sonlandırma için koda geçebilirsiniz.|[Nesnelerin stilini değiştirme](../designers/modify-the-style-of-objects-in-blend.md)|
|**Kullanıcı arabiriminizi verilerinize bağlama**|SQL Server veritabanları, WCF veya Web Hizmetleri, nesneler veya SharePoint listeleri gibi kaynaklardan bir veri kaynağı oluşturabilir ve veri kaynağını UI denetimlerinize bağlayabilirsiniz.<br /><br /> Tasarım zamanı verilerinin etkileşimli bir tasarım deneyimi için el ile oluşturulması gerekir.|Prototipleme ve test için kolayca örnek veri oluşturun. Hazırsanız canlı verilere geçiş yapın.<br /><br /> Visual Studio için Blend veri oluşturma özellikleri çok önemlidir (adları, rakamları, URL 'Leri, fotoğrafları kolayca hızlı bir şekilde ekleyebilir ve istediğiniz zaman tasarruf edebilirsiniz.<br /><br /> Canlı veriler için, UI denetimlerinizi bir XML dosyasına veya herhangi bir CLR veri kaynağına bağlayabilirsiniz.|[Verileri görüntüleme](../designers/display-data-in-blend.md)|

 Gelişmiş XAML tasarımı hakkında daha fazla bilgi için bkz.. [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
