---
title: Grafik Tanılama kullanmaya başlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9056fdae9d0eff55c572d8e38503d88269dbde3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704701"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde Grafik Tanılama ilk kez kullanmaya hazırlarsınız, sonra Direct3D uygulamasından çerçeveler yakalayıp grafik Çözümleyicisi 'nde inceleyebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Visual Studio 2015 ' de Grafik Tanılama kullanmak için şu sürümlerden birine sahip olmanız gerekir:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Visual Studio 2015 Community

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları
 İsteğe bağlı Windows özelliği *grafik araçları* , Windows 10 ' da grafik Tanılama için gereken yakalama ve kayıttan yürütme altyapısını sağlar.

 Grafik araçları 'nı yükleme hakkında bilgi için bkz. [Windows 10 Için grafik araçları 'Nı yükleme](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Windows 8.1 önkoşulları
 Windows 8.1 için Windows yazılım geliştirme seti (SDK), Windows 8.1 Grafik Tanılama gereken yakalama ve kayıttan yürütme altyapısını sağlar ve Windows 8.1 ve Windows 8 için geliştirmeyi destekler.

 [Windows 8.1 için Windows yazılım geliştirme seti 'Ni (SDK) indirin](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Windows 8.1 çalıştıran bir geliştirme makinesinden Windows 10 çalıştıran bir uzak kayıttan yürütme makinesini kullanmak için, geliştirme makinesine Windows 10 SDK 'yı ve kayıttan yürütme makinesinde isteğe bağlı grafik araçları özelliğini yüklemelisiniz.

## <a name="install-graphics-tools-for-windows-10"></a><a name="InstallGraphicsTools"></a> Windows 10 için grafik araçları 'nı yükler
 Windows 10 ' da, Grafik Tanılama altyapısı, *grafik araçları*adlı Windows 'un isteğe bağlı bir özelliği tarafından sağlanır. Yakalanan uygulamanın Windows 'un önceki bir sürümünü veya hangi Direct3D sürümünü kullandığını bağımsız olarak Windows 10 ' da grafik bilgilerini yakalamak ve oynatmak için bu özellik gereklidir. Grafik araçları özelliğini bir süre önce yüklemeyi seçebilirsiniz; Aksi takdirde, Visual Studio 'dan Grafik Tanılama oturumu ilk kez başlattığınızda isteğe bağlı olarak yüklenir.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için grafik araçları 'nı yüklemek için

1. **Başlat** menüsünde **Ayarlar**' ı seçin. **Ayarlar** iletişim kutusu görüntülenir.

2. **Ayarlar** Iletişim kutusunda **sistem**' i seçin ve ardından Sistem Ayarları listesinden **yüklü uygulamalar** ' ı seçin.

3. **Ayarlar** iletişim kutusunun sağ tarafında, **yüklü uygulamalar ve Özellikler**altında **isteğe bağlı özellikleri yönet** ' i seçin. **İsteğe bağlı özellikleri yönet** iletişim kutusu görüntülenir.

4. **İsteğe bağlı özellikleri yönet** iletişim kutusunda **Özellik Ekle**' yi seçin. Yükleyebileceğiniz isteğe bağlı özelliklerin bir listesi görüntülenir.

5. Özellikler listesinden **grafik araçları** ' nı seçin ve ardından **Install**' ı seçin.

   Grafik araçları özelliği, Windows 10 SDK 'Yı yüklediğinizde de otomatik olarak yüklenir.

> [!TIP]
> Windows 10 ' un isteğe bağlı grafik araçları özelliği, Geliştirici araçlarının yüklü olmadığı makinelerde destek, test ve tanılama senaryolarında kullanılabilecek, komut satırı yakalama programı **dxcap.exe**gibi basit yakalama ve kayıttan yürütme işlevleri sağlar. Daha fazla bilgi için, bkz. [komut satırı yakalama aracı](../debugger/command-line-capture-tool.md) konusu.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>Grafik Tanılama ilk kez kullanma
 Artık ihtiyacınız olan her şeye sahip olduğunuza göre Grafik Tanılama kullanmaya başlamaya hazırsınız. Şu adımları izlemeniz yeterlidir.

### <a name="1---create-a-direct3d-app"></a>1-Direct3D uygulaması oluşturma
 İle Grafik Tanılama araştırmak için kendi Direct3D uygulamanızı zaten aldıysanız harika! Aksi takdirde, kod galerisinde bulunan Direct3D örneklerinden birini kullanabilirsiniz.

- Visual Studio 2015 kullanarak Windows 10 ' da Direct3D 12 ile Grafik Tanılama denemek için, Windows 10 için [Direct3D 12 UAP örneğini](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) deneyin.

- Windows 10 veya Windows 8.1 'de Direct3D 11 ile Grafik Tanılama denemek için **DirectX uygulaması (Windows Evrensel)** veya  **directx uygulama (Windows 8.1)** proje şablonlarını kullanabilirsiniz. Ya da daha ilgi çekici bir şeyler için, Windows 8.1 için [DirectX mermer Maze oyun örneğini](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) deneyin.

  Uygulamasına geçmeden önce uygulamayı derlediğinizden emin olun.

### <a name="2---start-a-graphics-diagnostics-session"></a>2-Grafik Tanılama oturumu başlatma
 Şimdi ilk grafik tanılama oturumunuzu başlatmaya hazırsınız. Visual Studio 'da, ana menüden **Hata Ayıkla, grafikler, Tanılamayı Başlat**' ı seçin veya **alt + F5**tuşlarına basın. Bu, uygulamanızı Grafik Tanılama altında başlatır ve Tanılama oturumu pencerelerini Visual Studio 'da görüntüler.

> [!IMPORTANT]
> Uygulamanızı Windows 10 ' da çalıştırıyorsanız ve isteğe bağlı grafik araçları özelliğini henüz yüklemediyseniz, bunu şimdi yapmanız istenir. Windows 10 ' da Grafik Tanılama kullanabilmeniz için önce bu uygulamayı yüklemelisiniz.

### <a name="3---capture-frames"></a>3-çerçeveleri yakala
 Uygulamanız başladıktan hemen sonra çerçeveler yakalamaya hazırsınız.

##### <a name="to-capture-single-frames"></a>Tek çerçeveleri yakalamak için

- Visual Studio 'da grafik araç çubuğundan veya Tanılama oturumu penceresinden **kare yakala** düğmesini seçin. Ya da uygulamanız odağa sahipse **PRINT Screen**tuşuna basın.

##### <a name="to-capture-a-sequence-of-frames"></a>Çerçeve dizisini yakalamak için

- Visual Studio 'da, Tanılama oturumu penceresinde, çerçeveleri sırayla yakalamak istediğiniz çerçeve sayısına **yakalamaya** göre ayarlayın ve ardından tek çerçeveleri yakalamak için yukarıda açıklanan yöntemlerden herhangi birini kullanarak sırayı yakalayın.

   Tek kareleri yeniden yakalamak için, **yakalama yapılacak kareleri** olarak ayarlayın `1` .

  Çerçeveleri yakalamayı tamamladığınızda uygulamadan çıkmak veya grafik araç çubuğundan veya Tanılama oturumu penceresinden **Durdur** düğmesini seçmeniz yeterlidir.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 – grafik çözümleyici 'de yakalanan çerçeveleri İnceleme
 Şimdi, az önce yakaladığınız çerçeveleri incelemek için hazırsınız. Bir çerçeveyi çözümlemeye başlamak için, Tanılama oturumu penceresinden incelemek istediğiniz çerçevenin kare numarasını seçin. Bu, uygulamanızın işleme sorunlarını izlemek için Direct3D 'yi nasıl kullandığını incelemek için Grafik Tanılama araçlarını kullanabileceğiniz veya performansını anlamak için **Çerçeve Analizi** aracını kullanmanın **grafik Çözümleyicisi**' nde çerçeveyi açar.

 Tanılama oturumu penceresinden yanlış çerçeveyi seçtiyseniz veya farklı bir çerçeveyi incelemek istiyorsanız grafik çözümleyicisinden yeni bir tane seçebilirsiniz. Grafik günlüğü penceresinin **Işleme hedefi** sekmesinde, işleme hedefi görüntüsü altında, **çerçeve listesini** genişletin ve ardından incelemek üzere farklı bir çerçeve seçin.

 Grafik Çözümleyicisi araçlarının birlikte nasıl kullanılacağı hakkında daha fazla bilgi edinmek için [örneklere](../debugger/graphics-diagnostics-examples.md)bakın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Direct3D 12 grafik](https://msdn.microsoft.com/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
