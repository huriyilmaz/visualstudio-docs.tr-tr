---
title: Grafik Tanılama ile çalışmaya başlama | Microsoft Docs
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 575b0254768ac359e43cd5b04c23a220549ac973
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557922"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
Bu bölümde, grafik Tanılama'yı ilk kez kullanmak hazırlarsınız ve ardından bir Direct3D uygulamasından kareleri yakalayın ve grafik Çözümleyicisi'nde inceleyebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Visual Studio grafik tanılama kullanmak için Visual Studio Enterprise, Visual Studio Professional veya Visual Studio Community kullanmanız gerekir.  Visual Studio Code dahil olmak üzere diğer sürümleri, bu özelliği içermez.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları
 İsteğe bağlı Windows özelliği *grafik araçları* , Windows 10 ' da grafik Tanılama için gereken yakalama ve kayıttan yürütme altyapısını sağlar.

 Grafik araçları 'nı yükleme hakkında bilgi için bkz. [Windows 10 Için grafik araçları 'Nı yükleme](#InstallGraphicsTools).

## <a name="InstallGraphicsTools"></a>Windows 10 için grafik araçları 'nı yükler
 Windows 10 ' da, Grafik Tanılama altyapısı, *grafik araçları*adlı Windows 'un isteğe bağlı bir özelliği tarafından sağlanır. Bu özellik, yakalama ve hedefleri olan uygulama olup olmadığını yakalanan ne olursa olsun, grafik bilgilerini Windows 10, windows veya kullandığı Direct3D'ın hangi sürümünün önceki bir sürümünü oynatmak için gereklidir. Grafik araçları özelliğinin önceden yüklemeyi seçebilirsiniz; Aksi durumda, Visual Studio'dan bir grafik Tanılama oturumu başlatın yüklü üzerine ilk zaman olur.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için grafik araçları yüklemek için

1. Ara bölümünde **uygulamalar ve Özellikler** yazın ve ardından **uygulamalar & özellikleri** ayarları ' nı açın.

2. **Uygulamalar & özellikleri** ayarlarının sağ tarafında **isteğe bağlı özellikler** ' i ( **uygulamalar & Özellikler**altında) seçin.

   **Isteğe bağlı özellikler** ayarları görüntülenir.

3. **Isteğe bağlı özellikler** ayarları ' nda **Özellik Ekle**' yi seçin. Yükleyebileceğiniz isteğe bağlı özelliklerin bir listesi görüntülenir.

4. Özellikler listesinden **grafik araçları** ' nı seçin ve ardından **Install**' ı seçin.

   Grafik araçları özelliğinin de, Windows 10 SDK'yı yüklediğinizde otomatik olarak yüklenir.

> [!TIP]
> Windows 10 ' un isteğe bağlı grafik araçları özelliği, Geliştirici araçlarının yüklü olmadığı makinelerde destek, test ve tanılama senaryolarında kullanılabilen, basit yakalama ve kayıttan yürütme işlevleri (komut satırı yakalama programı **DXCap. exe**gibi) sağlar. Daha fazla bilgi için, bkz. [komut satırı yakalama aracı](command-line-capture-tool.md) konusu.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>İlk kez grafik tanılamayı kullanma
 İhtiyacınız olan her şey sahip olduğunuza göre grafik Tanılama'yı kullanmaya başlamak hazırsınız. Şu adımları izlemeniz yeterlidir.

### <a name="1---create-a-direct3d-app"></a>1 - bir Direct3D uygulaması oluşturma
 Grafik Tanılama, harika keşfetmek için kendi Direct3D uygulaması zaten varsa! Aksi takdirde, aşağıdakilerden birini kullanın:

- Windows 10 için **DirectX 11 uygulaması (Evrensel Windows)** veya **DirectX 12 uygulaması (Evrensel Windows)** proje şablonları.
- Windows 10 için [Direct3D 12 UAP örneği](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) .

  Geçmeden önce uygulamanın oluşturduğunuzdan emin olun.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - bir grafik Tanılama oturumu başlatın
 Artık ilk grafik tanılama oturumunuzu başlamak hazırsınız. Visual Studio 'da, ana menüdeki **Hata Ayıkla, grafikler, grafik hata ayıklamayı Başlat**' ı seçin veya **alt + F5**tuşlarına basın. Bu, uygulamanızı grafik tanılama altında başlar ve Visual Studio'da Tanılama oturumu windows görüntüler.

> [!IMPORTANT]
> Uygulamanızı Windows 10'da çalıştırıyorsanız ve isteğe bağlı grafik araçları özelliğinin henüz yüklemediyseniz, bunu şimdi yapmak istenir. Windows 10'da grafik tanılama kullanmadan önce yüklemeniz gerekir.

### <a name="3---capture-frames"></a>3 - kareleri yakalayın
 Uygulamanız başlar başlamaz kareleri yakalayın hazırsınız demektir.

#### <a name="to-capture-single-frames"></a>Tek çerçeve yakalama

- Visual Studio 'da grafik araç çubuğundan veya Tanılama oturumu penceresinden **kare yakala** düğmesini seçin. Ya da uygulamanız odağa sahipse, klavyenizde **PRINT Screen** tuşuna basmanız yeterlidir.

#### <a name="to-capture-a-sequence-of-frames"></a>Bir dizi kare yakalamak için

- Visual Studio 'da, Tanılama oturumu penceresinde, çerçeveleri sırayla yakalamak istediğiniz çerçeve sayısına **yakalamaya** göre ayarlayın ve ardından tek çerçeveleri yakalamak için yukarıda açıklanan yöntemlerden herhangi birini kullanarak sırayı yakalayın.

   Tek kareleri yeniden yakalamak için **kareleri yakalamaya** *1*olarak ayarlayın.

  Çerçeveleri yakalamayı tamamladığınızda uygulamadan çıkmak veya grafik araç çubuğundan veya Tanılama oturumu penceresinden **Durdur** düğmesini seçmeniz yeterlidir.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - Grafik Çözümleyicisi yakalanan karelerde inceleyin
 Artık yalnızca yakalanan çerçeveleri incelemek hazırsınız. Çerçeveyi analiz etmeye başlamak için tanılama oturumu penceresinden incelemek istediğiniz çerçeve çerçeve sayısını seçin. Bu, uygulamanızın işleme sorunlarını izlemek için Direct3D 'yi nasıl kullandığını incelemek için Grafik Tanılama araçlarını kullanabileceğiniz veya performansını anlamak için **Çerçeve Analizi** aracını kullanmanın **grafik Çözümleyicisi**' nde çerçeveyi açar.

 Tanılama oturumu penceresinden yanlış çerçeve seçtiğiniz ya da farklı bir çerçeveyi incelemek istediğiniz yeni bir grafik Çözümleyicisi'ni seçebilirsiniz. Grafik günlüğü penceresinin **Işleme hedefi** sekmesinde, işleme hedefi görüntüsü altında, **çerçeve listesini** genişletin ve ardından incelemek üzere farklı bir çerçeve seçin.

 Grafik Çözümleyicisi araçlarının birlikte nasıl kullanılacağı hakkında daha fazla bilgi edinmek için [örneklere](graphics-diagnostics-examples.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Direct3D 12 grafik](/windows/desktop/direct3d12/direct3d-12-graphics)