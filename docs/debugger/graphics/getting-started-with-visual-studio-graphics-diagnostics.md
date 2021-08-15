---
title: Grafik tanılamayı | Microsoft Docs
description: İlk kez Grafik Tanılama kullanmaya hazırlanma, ardından Direct3D uygulamasından kareleri yakalama ve Bunları Grafik Çözümleyicisi'ne inceleme.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1d9c8bda4a9e8660f25830f2847da1e9037819a1a6c99ad69325df4566ae8881
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454286"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
Bu bölümde ilk kez Grafik Tanılama kullanmaya hazırlayacak, ardından Direct3D uygulamasından kareleri yakalayacak ve Bunları Grafik Çözümleyicisi'ne inceleyebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Bu Grafik Tanılama kullanmak Visual Studio, Visual Studio Enterprise, Visual Studio Professional veya Visual Studio Community.  Diğer sürümler de Visual Studio Code bu özelliği içermez.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları
 İsteğe Windows *özelliği Grafik Araçları,* uygulama üzerinde kayıttan yürütme için gereken yakalama ve kayıttan Grafik Tanılama altyapısını Windows 10.

 Grafik Araçları'nın yüklemesi hakkında bilgi için [bkz. Windows 10.](#InstallGraphicsTools)

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a>Windows 10 için Grafik Araçları'Windows 10
 Bu Windows 10, Grafik Tanılama altyapısı Grafik Araçları olarak adlandırılan isteğe bağlı Windows *özelliğiyle sağlanır.* Bu özellik, yakalanan uygulamanın önceki bir Windows sürümünü veya hangi Direct3D sürümünü kullandığına bakılmaksızın Windows 10'da grafik bilgilerini yakalamak ve oynatmak için gereklidir. Grafik Araçları özelliğini daha önce yüklemeyi seçebilirsiniz; aksi takdirde, ilk kez bir oturum başlatan isteğe bağlı olarak yüklenir Grafik Tanılama oturum Visual Studio.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için Grafik Araçları'Windows 10

1. Ara'ya **Uygulamalar ve özellikler yazın** ve uygulamalar ve **özellikler &** açın.

2. Uygulamalar ve özellikler ayarlarının sağ tarafında **İsteğe &'yi** **seçin** (Uygulamalar ve özellikler **altında) & seçin.**

   İsteğe **bağlı özellikler** ayarları görüntülenir.

3. İsteğe **bağlı özellikler ayarlarında** Özellik **ekle'yi seçin.** Yükleyebilirsiniz isteğe bağlı özelliklerin listesi görüntülenir.

4. Özellikler **listesinden** Grafik Araçları'nın ardından Yükle'yi **seçin.**

   Grafik Araçları özelliği, Windows 10 SDK'sı yük Windows 10 yüklenir.

> [!TIP]
> Windows 10'nin isteğe bağlı Grafik Araçları özelliği, geliştirici araçlarının yüklenmemiş olduğu makinelerde destek, test ve tanılama senaryolarında kullanılan komut satırı yakalama programı **dxcap.exe** gibi basit yakalama ve kayıttan yürütme işlevleri sağlar. Daha fazla bilgi için Komut [Satırı Yakalama Aracı konu başlığına](command-line-capture-tool.md) bakın.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Grafik Tanılama kez kullanma
 Artık ihtiyacınız olan her şeye sahip olduğunuza göre, Grafik Tanılama. Şu adımları izlemeniz yeterlidir.

### <a name="1---create-a-direct3d-app"></a>1 - Direct3D uygulaması oluşturma

Kendi Direct3D uygulamalarınızı keşfetmek için zaten Grafik Tanılama, harika! Aksi takdirde, aşağıdakilerden birini kullanın:

::: moniker range=">=vs-2019"
[Direct3D Oyun Örneğinden bir örnek indirin.](/samples/microsoft/windows-universal-samples/simple3dgamedx/)
::: moniker-end
::: moniker range="vs-2017"
- DirectX **11 Uygulaması (Evrensel Windows)** veya **DirectX 12 Uygulaması (Evrensel Windows)** proje şablonları Windows 10.
- [Örnek için Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) Windows 10.
::: moniker-end

Devam etmek için uygulamayı derlemeyi ve çalıştırmayı da sağlar. Hatasız   >  **bir şekilde derlemek** için Derleme Çözümü'lerini seçin. Ardından Hata **Ayıklama Olmadan**  >  **Başlat 'ı** (**Ctrl + F5**) seçerek doğru şekilde çalıştır olduğundan emin olun. Araçla hangi makineyi test ediyor olduğunu bağlı olarak, örnek için platform ve hata ayıklama hedefini ayarlamanız gerekir. Örneğin, ana makinenizin x64 platformuna karşı test Visual Studio çözüm platformu olarak **x64,** hata ayıklama hedefiniz olarak da Yerel Makine'yi seçin.  

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Grafik Tanılama başlatma
 Artık ilk grafik tanılama oturumlarınızı başlatmaya hazır oluruz. Bu Visual Studio ana menüde Hata Ayıkla, **Grafikler,** Grafik Hata Ayıklamayı Başlat'ı seçin veya **alt+F5 tuşlarına basın.** Bu, uygulamanıza Grafik Tanılama başlatır ve tanılama oturumu pencerelerini Visual Studio.

> [!IMPORTANT]
> Uygulamanızı Windows 10 henüz isteğe bağlı Grafik Araçları özelliğini yüklememişken çalıştırdıysanız, şimdi bunu yapmanız istenir. Grafik Tanılama'i Windows 10.

### <a name="3---capture-frames"></a>3 - Çerçeveleri Yakalama
 Uygulamanız başlar başlamaz kareleri yakalamaya hazır olursanız.

#### <a name="to-capture-single-frames"></a>Tek kareleri yakalamak için

- Bu Visual Studio Grafik araç **çubuğundan** veya tanılama oturumu penceresinden Çerçeve yakala düğmesini seçin. Veya, uygulama odağı varsa klavyenizde **Yazdırma Ekranı tuşuna** basmanız da gerekir.

#### <a name="to-capture-a-sequence-of-frames"></a>Bir kare dizisini yakalamak için

- Bu Visual Studio tanılama oturumu penceresinde, Yakalama  için Kareler'i dizide yakalamak istediğiniz kare sayısına ayarlayın ve ardından tek kareleri yakalamak için yukarıda açıklanan yöntemlerden birini kullanarak sırayı yakalayın.

   Tek kareleri yeniden yakalamak için Çerçeveler'i **yakalama olarak** *1 olarak ayarlayın.*

  Çerçeveleri yakalamayı bitirerek uygulamadan çıkmanız veya Grafik araç çubuğundan **veya** tanılama oturumu penceresinden Durdur düğmesini seçmeniz gerekir.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - Grafik Çözümleyicisinde yakalanan kareleri inceleme
 Şimdi az önce yakaladığın kareleri incelemeye hazır oluruz. Bir çerçeveyi analiz etmek için tanılama oturumu penceresinden incelemek istediğiniz çerçevenin çerçeve numarasını seçin. Bu işlem, Grafik Tanılama araçlarını kullanarak uygulamanın işleme sorunlarını izlemek için Direct3D'nin nasıl kullandığını incelemek veya performansını  anlamak için Çerçeve Analizi aracını kullanarak kullanabileceğiniz **Grafik** Çözümleyicisi'nin çerçevesini açar.

 Tanılama oturumu penceresinden yanlış çerçeveyi seçtiysanız veya farklı bir çerçeveyi incelemek için Grafik Çözümleyicisi'nin yeni bir çerçevesini seçin. Grafik **günlüğü penceresinin** İşleme Hedefi sekmesinde, işleme hedefi görüntüsünün altında Çerçeve Listesi'ne gidin ve incelenecek farklı bir çerçeve seçin. 

 Grafik Çözümleyicisi araçlarını birlikte kullanma hakkında daha fazla bilgi edinmek için Bkz. [Örnekler](graphics-diagnostics-examples.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Direct3D 12 Grafikleri](/windows/desktop/direct3d12/direct3d-12-graphics)