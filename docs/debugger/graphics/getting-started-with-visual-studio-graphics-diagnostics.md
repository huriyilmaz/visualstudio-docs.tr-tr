---
title: Grafik tanılama 'yı kullanmaya başlama | Microsoft Docs
description: Grafik Tanılama ilk kez kullanmaya hazırlanın, sonra Direct3D uygulamasından çerçeveler yakalayın ve bunları grafik Çözümleyicisi 'nde inceleyin.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 88ccd8ea443092e3d22c4266bbecd2a56efb6dd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074318"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
Bu bölümde Grafik Tanılama ilk kez kullanmaya hazırlarsınız, sonra Direct3D uygulamasından çerçeveler yakalayıp grafik Çözümleyicisi 'nde inceleyebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Visual Studio Grafik Tanılama kullanmak için Visual Studio Enterprise, Visual Studio Professional veya Visual Studio Community kullanmanız gerekir.  Visual Studio Code dahil diğer sürümler bu özelliği içermez.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları
 isteğe bağlı Windows özelliği *grafik araçları* , Windows 10 Grafik Tanılama gereken yakalama ve kayıttan yürütme altyapısını sağlar.

 Grafik araçları 'nı yükleme hakkında daha fazla bilgi için bkz. [Windows 10 Için grafik araçları 'Nı yükleme](#InstallGraphicsTools).

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a>Windows 10 için grafik araçları 'nı yükler
 Windows 10, Grafik Tanılama altyapısı, *grafik araçları* adlı Windows isteğe bağlı bir özelliği tarafından sağlanır. bu özellik, yakalanan uygulamanın Windows 'un önceki bir sürümünü mi yoksa hangi Direct3D sürümünü kullandığını mı hedeflediğinden bağımsız olarak Windows 10 grafik bilgilerini yakalayıp çalmak için gereklidir. Grafik araçları özelliğini bir süre önce yüklemeyi seçebilirsiniz; Aksi takdirde, Visual Studio Grafik Tanılama oturumu ilk kez başlattığınızda isteğe bağlı olarak yüklenir.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için grafik araçları 'nı yüklemek için

1. Ara bölümünde **uygulamalar ve Özellikler** yazın ve ardından **uygulamalar & özellikleri** ayarları ' nı açın.

2. **Uygulamalar & özellikleri** ayarlarının sağ tarafında **isteğe bağlı özellikler** ' i ( **uygulamalar & Özellikler** altında) seçin.

   **Isteğe bağlı özellikler** ayarları görüntülenir.

3. **Isteğe bağlı özellikler** ayarları ' nda **Özellik Ekle**' yi seçin. Yükleyebileceğiniz isteğe bağlı özelliklerin bir listesi görüntülenir.

4. Özellikler listesinden **grafik araçları** ' nı seçin ve ardından **Install**' ı seçin.

   grafik araçları özelliği, Windows 10 SDK 'yı yüklediğinizde de otomatik olarak yüklenir.

> [!TIP]
> Windows 10 'nin isteğe bağlı grafik araçları özelliği, geliştirici araçlarının yüklü olmadığı makinelerde destek, test ve tanılama senaryolarında kullanılabilen bir komut satırı yakalama programı **dxcap.exe** gibi basit yakalama ve kayıttan yürütme işlevleri sağlar. Daha fazla bilgi için, bkz. [komut satırı yakalama aracı](command-line-capture-tool.md) konusu.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Grafik Tanılama ilk kez kullanma
 Artık ihtiyacınız olan her şeye sahip olduğunuza göre Grafik Tanılama kullanmaya başlamaya hazırsınız. Şu adımları izlemeniz yeterlidir.

### <a name="1---create-a-direct3d-app"></a>1-Direct3D uygulaması oluşturma

İle Grafik Tanılama araştırmak için kendi Direct3D uygulamanız zaten varsa harika! Aksi takdirde, aşağıdakilerden birini kullanın:

::: moniker range=">=vs-2019"
[Direct3D oyun örneğinden](/samples/microsoft/windows-universal-samples/simple3dgamedx/)bir örnek indirin.
::: moniker-end
::: moniker range="vs-2017"
- Windows 10 için **directx 11 uygulaması (evrensel Windows)** veya **directx 12 uygulaması (evrensel Windows)** proje şablonları.
- Windows 10 için [Direct3D 12 UAP örneği](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) .
::: moniker-end

Üzerinde geçiş yapmadan önce uygulamayı derleyebilir ve çalıştıradığınızdan emin olun.   >  Hata olmadan oluşturulduğundan emin olmak için derleme **Yapı çözümünü** seçin. Doğru çalıştığından   >  emin olmak için hata ayıklama **olmadan Başlat** ' ı (**CTRL + F5**) seçin. Araçla test ettiğiniz makineye bağlı olarak, örnek için platformu ve hata ayıklama hedefini ayarlamanız gerekebilir. örneğin, Visual Studio ana makinenizde x64 platformunda test etmek için, çözüm platformu olarak **x64** ve hata ayıklama hedefi olarak **yerel makine** ' yi seçin. 

### <a name="2---start-a-graphics-diagnostics-session"></a>2-Grafik Tanılama oturumu başlatma
 Şimdi ilk grafik tanılama oturumunuzu başlatmaya hazırsınız. Visual Studio, ana menüden **hata ayıkla, grafikler, grafik hata ayıklamayı başlat**' ı seçin veya **Alt + F5** tuşlarına basın. Bu, uygulamanızı Grafik Tanılama altında başlatır ve Tanılama oturumu pencerelerini Visual Studio görüntüler.

> [!IMPORTANT]
> uygulamanızı Windows 10 çalıştırıyorsanız ve isteğe bağlı grafik araçları özelliğini henüz yüklemediyseniz, bunu şimdi yapmanız istenir. Windows 10 Grafik Tanılama kullanabilmeniz için önce bu uygulamayı yüklemelisiniz.

### <a name="3---capture-frames"></a>3-çerçeveleri yakala
 Uygulamanız başladıktan hemen sonra çerçeveler yakalamaya hazırsınız.

#### <a name="to-capture-single-frames"></a>Tek çerçeveleri yakalamak için

- Visual Studio, grafik araç çubuğundan veya tanılama oturumu penceresinden **çerçeve yakala** düğmesini seçin. Ya da uygulamanız odağa sahipse, klavyenizde **PRINT Screen** tuşuna basmanız yeterlidir.

#### <a name="to-capture-a-sequence-of-frames"></a>Çerçeve dizisini yakalamak için

- Visual Studio, tanılama oturumu penceresinde, çerçeveleri sırayla yakalamak istediğiniz çerçeve sayısına **yakalamaya** göre ayarlayın ve ardından tek çerçeveleri yakalamak için yukarıda açıklanan yöntemlerden herhangi birini kullanarak sırayı yakalayın.

   Tek kareleri yeniden yakalamak için **kareleri yakalamaya** *1* olarak ayarlayın.

  Çerçeveleri yakalamayı tamamladığınızda uygulamadan çıkmak veya grafik araç çubuğundan veya Tanılama oturumu penceresinden **Durdur** düğmesini seçmeniz yeterlidir.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4-grafik çözümleyici 'de yakalanan çerçeveleri İnceleme
 Şimdi, az önce yakaladığınız çerçeveleri incelemek için hazırsınız. Bir çerçeveyi çözümlemeye başlamak için, Tanılama oturumu penceresinden incelemek istediğiniz çerçevenin kare numarasını seçin. Bu, uygulamanızın işleme sorunlarını izlemek için Direct3D 'yi nasıl kullandığını incelemek için Grafik Tanılama araçlarını kullanabileceğiniz veya performansını anlamak için **Çerçeve Analizi** aracını kullanmanın **grafik Çözümleyicisi**' nde çerçeveyi açar.

 Tanılama oturumu penceresinden yanlış çerçeveyi seçtiyseniz veya farklı bir çerçeveyi incelemek istiyorsanız grafik çözümleyicisinden yeni bir tane seçebilirsiniz. Grafik günlüğü penceresinin **Işleme hedefi** sekmesinde, işleme hedefi görüntüsü altında, **çerçeve listesini** genişletin ve ardından incelemek üzere farklı bir çerçeve seçin.

 Grafik Çözümleyicisi araçlarının birlikte nasıl kullanılacağı hakkında daha fazla bilgi edinmek için [örneklere](graphics-diagnostics-examples.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Direct3D 12 grafik](/windows/desktop/direct3d12/direct3d-12-graphics)