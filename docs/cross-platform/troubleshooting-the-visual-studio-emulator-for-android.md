---
title: Android için Visual Studio Emulator sorunlarını giderme | Microsoft Docs
description: Android için Visual Studio Emulator kullanırken karşılaşabileceğiniz sorunları çözmenize yardımcı olabilecek bilgiler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
author: conceptdev
ms.author: crdun
manager: crdun
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 867908c32cf6610c1915e554720d6c9be937dac7
ms.sourcegitcommit: ac681e983f3b217c3fd9d2a31e3a3ddcc4dd3546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "132042004"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
bu konu, Android için Visual Studio Emulator kullanırken karşılaşabileceğiniz sorunları çözmenize yardımcı olacak bilgiler içerir.

> [!WARNING]
> Öykünücü yüklendiğinde, Kurulum programı yazılımı çalıştırmaya yönelik önkoşulları denetler. Önkoşullar yoksa uyarıları görüntüler, ancak yükleme için gerekli değildir.

 Bu konuda aşağıdaki bölümler yer almaktadır.

- [Başlamadan önce](#BeforeYouStart)

- [Emulator yüklenemediğinde](#NoInstall)

- [Bir etki alanı veya şirket ağındaki ağ hedeflerine bağlanılamıyor](#DomainNetwork)

- [Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflerine bağlanılamıyor](#ManualNetworkConfig)

- [Emulator yavaş başlıyor, zaman aşımı nedeniyle başlatılamaz veya uygulama dağıtımı başarısız olur](#SlowStart)

- [Emulator başlatılamadı](#NoStart2)

- [Emulator başlatılamadı (ilk kullanım)](#NoStart)

- [Emulator yüklendikten sonra bilgisayar önyükleme yapamıyor](#NoBoot)

- [Visual Studio, uygulamayı öykünücüye dağıtmaya çalışıyor veya öykünücü diğer ıdes 'te hata ayıklama hedefi olarak görünmüyor](#ADB)

- [Emulator UDP bağlantı noktasını ayarlayamadığından yanıt vermeyi durduruyor](#XamarinPlayer)

- [Hata ayıklayıcı bir Xamarin projesine iliştirilemiyor](#Skylake)

- [Emulator Google Play Hizmetleri kullanan uygulamayı çalıştıramazsa](#GooglePlay)

- [Dosya, APK veya bıraktığınızda ZIP dosyası için sürükle ve bırak çalışmıyor](#DragAndDrop)

- [Ekran görüntüsünün çözümlenmesi yanlış](#Resolution)

- [Emulator OpenGL içeriğini işleyemeyebilir](#OpenGL)

- [Emulator, çok dokunmalı hareketlere yanıt vermez](#Multitouch)

- [Destek kaynakları](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a> Başlamadan önce
 Sorun gidermeye başlamadan önce, aşağıdaki konuları gözden geçirmek yararlı olabilir:

- [Android için Visual Studio Emulator sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a>Emulator yüklenemediğinde
 Hyper-V yüklü değilse, öykünücüyü yüklemeye çalıştığınızda aşağıdaki iletiyi görürsünüz. HyperV 'yi destekleyen bir makineniz olmalıdır ve bu makinenin etkinleştirilmesi gerekir.

 ![bilgisayar Hyper-V ' y i desteklemiyorsa, kurulum 'un Android için Microsoft Visual Studio Öykünücüsü için engellendiğini belirten bir Visual Studio iletisinin ekran görüntüsü.](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> bu ileti hem Android için Visual Studio Emulator hem de Windows Phone Emulator için geçerlidir. Windows 8.1 ve Windows 10 öykünücüyü destekler.

 bu iletiyi görürseniz, öykünücü çalıştırıp çalıştıramayacağını öğrenmek için [Android için Visual Studio Emulator sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) denetleyin.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a> Bir etki alanı veya şirket ağındaki ağ hedeflerine bağlanılamıyor
 Android için Visual Studio Emulator ağ üzerinde kendi ıp adresine sahip ayrı bir cihaz olarak görünür. Windows etki alanına katılmamış ve konak bilgisayarla etki alanı veya çalışma grubu kimlik bilgilerini paylaşmıyor.

 Ağınız, temel ağ ve Internet bağlantısı için etki alanı veya çalışma grubu yetkilendirmesi gerektiriyorsa, özel durum için BT yöneticinize başvurun. Bu özel durum, geliştirme bilgisayarınızın bir sınır makine olarak çalışmasına ve öykünücü gibi etki alanına katılmış olmayan ağ cihazlarından gelen bağlantıları kabul etmesine olanak tanır.

 Android için Visual Studio Emulator, kendi MAC adresi kümesini de kullanır. Öykünücüden ağ veya Internet kaynaklarına erişemiyorsanız, öykünücü MAC adreslerinin ağınızda yetkilendirilmiş olduğundan emin olmak için BT yöneticinize başvurun.

#### <a name="to-view-the-emulators-mac-addresses"></a>Öykünücüsünün MAC adreslerini görüntülemek için

1. Öykünücüyü başlatın.

2. Öykünücü araç çubuğunda, ek araçlar penceresini açmak için köşeli çift ayraç düğmesine (>>) tıklayın.

3. Ek Araçlar penceresinde Ağ sekmesine tıklayın.

4. Ağ sayfasında, fiziksel adres girişlerini bulun.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a> Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflerine bağlanılamıyor
 Öykünücünden ağ hedeflerine bağlanmak için ağınızın aşağıdaki gereksinimleri karşılaması gerekir:

- Bkz. Öykünücü, kendisini ağ üzerinde kendi IP adresiyle ayrı bir cihaz olarak yapılandırdığından DHCP gerektirir.

- DNS ve ağ geçidi ayarları otomatik olarak yapılandırıldı. Öykünücü için DNS ve ağ geçidi ayarlarını el ile yapılandırmak mümkün değildir.

  Ağınız el ile yapılandırılmış ayarlar gerektiriyorsa, öykünücü için ağ bağlantısını nasıl etkinleştirebileceğini öğrenmek için BT yöneticinize başvurun.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a>Emulator yavaş başlıyor, zaman aşımı nedeniyle başlatılamaz veya uygulama dağıtımı başarısız olur
 Belirli koşullar altında, öykünücü bir zaman aşımı nedeniyle başlatılması veya başlatılması birkaç dakika sürer. Öykünücü başlayamazsa şu iletiyi görürsünüz: `App deployment failed. Please try again` . Aşağıdaki koşullar bu hataya neden olabilir.

- önyüklenebilir bir VHD 'den Android için Visual Studio Emulator çalıştırma. Bu yapılandırma desteklenmez.

- Hatalı bir sabit sürücü. Chkdsk programını çalıştırmayı göz önünde bulundurun.

- Birleştirilmesi gereken bir sabit sürücü. Sürücüyü birleştirmeyi düşünün.

- Neredeyse dolu bir sabit sürücü. Sürücüdeki kullanılabilir alanı denetleyin.

- Çalışan diğer uygulamalar nedeniyle yeterli bellek yok. Belleği tüketen veya bellek miktarını artıran uygulama sayısını azaltın.

- Genellikle sistemde düşük performansa katkıda bulunan her türlü etken. denetim masası 'nın performans bilgileri ve araçlar sayfasında bulabileceğiniz Windows deneyim dizininde en düşük alt puanı olan bileşenle sorun gidermeye başlayın.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Emulator başlatılamadı
 Öykünücü daha önce çalıştıyordu, ancak şu anda çalışmazsa, aşağıdaki görevlerden geçin. emulator 'u ilk kez kullanıyorsanız, bu adımları denemeden önce [Emulator başlatılamadı (ilk kullanım)](#NoStart) bölümüne bakın.

- Öykünücüsünün diğer Hyper-V örneklerini kaldırın.

    1. Visual Studio’yu kapatın.

    2. hyper-v yöneticisi 'ni açın ve zaten çalışmakta olan ve muhtemelen bozulmuş durumda olan Emulator (sanal makineler) hyper-v örneklerini durdurun.

    3. Hyper-V Yöneticisi 'nde diğer öykünücü VM 'Leri silin.

    4. Makinenizi yeniden başlatın.

- En az 4 GB sistem belleğinizin olduğundan ve diğer kaynak yoğunluklu programlar ve süreçler tarafından tüketilmediğinden emin olun (örneğin, herhangi bir tarayıcı pencerelerini kapatmayı deneyin).

- Hyper-V Yöneticisi 'nde sanal anahtar yöneticisini açın ve iki ağ anahtarınız olup olmadığını denetleyin; birincinin iç anahtar olduğunu ve ikincisi 'nin dış olduğunu doğrulayın.

     ![Hyper-V Yöneticisi 'nde sanal anahtar Yöneticisi ekran görüntüsü. Yeni bir sanal anahtar vurgulanır ve bu özellikler bir dış ağ anahtarı olduğunu gösterir.](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     kurulum yanlışsa ve Windows 10 kullanıyorsanız, [netcfg-d komutunu (bölüm 6) kullanarak ağ aygıtlarını yeniden yüklemeyi](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) deneyebilirsiniz.

- bu adımlar sorunu çözmezse, öykünücüyü etkileyebilecek üçüncü taraf yazılımlar hakkında bilgi için [Emulator başlatılamadı (ilk kullanım)](#NoStart) konusuna bakın.

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a>Emulator başlatılamadı (ilk kullanım)
 Öykünücü başlamazsa, sorunu tanımlamak ve onarmak için aşağıdaki görevleri gözden geçin.

- En düşük donanım gereksinimlerinin yerine getirildiğini ve BIOS ayarlarının doğru olduğundan emin olun.

   Emulator ve Windows 8 Hyper-V, ikinci düzey adres çevirisi (SLAT) ile 64 bitlik bir işlemci gerektirir. Intel için temel bir i3, i5 veya i7 İşlemciye (veya birçok Xeons) ihtiyacınız vardır. AMD yongaları listesine [buradan](https://www.amd.com/en/support)ulaşabilirsiniz.

  1. Bilgisayarınızın [sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)karşıladığından emin olun.

  2. [Coreınfo aracının](/sysinternals/downloads/coreinfo) bilgisayarınızın SLAT özellikli olduğunu raporluyor olduğunu doğrulayın.

  3. Bilgisayarınızın BIOS ayarları içinde tüm sanallaştırma teknolojisinin etkinleştirildiğinden emin olun. Tam BIOS açıklamaları her donanım üreticisi için farklılık gösterebilir. Genel olarak, şununla ilgili özellikleri etkinleştirin:

     - SLAT (Ikinci düzey adres çevirisi)

     - EPT (genişletilmiş sayfa tabloları) (Intel)

     - NPT (Iç Içe sayfa tabloları) (AMD)

     - RVI (Hızlı sanallaştırma dizin oluşturma) (AMD)

     - VMX (donanım yardımlı sanallaştırma desteğini gösteren bir Intel kısaltması)

     - SVM (donanım yardımlı sanallaştırma desteğini gösteren bir AMD kısaltması)

     - XD (yürütmeyi devre dışı bırak) (Intel); Bunun etkinleştirilmesi gerekir

     - NX (Yürütme Yok)(AMD); bu etkinleştirilmelidir.

  4. BIOS'ta aşağıdaki seçenekler varsa bunları devre dışı bırakmanız gerekir.

     - Intel VT-d'yi devre dışı bırakma

     - Güvenilen Yürütmeyi Devre Dışı Bırakma

       Daha fazla bilgi için şu makaleye bakın: Technet: Hyper-V: Hyper-V Etkinleştirme BIOS Hatalarını Düzeltme

  5. En az 4 GB sistem belleğine sahip olduğundan ve bunun yoğun kaynak kullanımlı diğer programlar ve işlemler tarafından tüketilmemesi gerekir.

  6. Veya daha iyi bir Windows 8 Professional emin olun (Windows Server 2008 desteklenmiyor). Windows Server 2012, ancak Masaüstü Deneyimini etkinleştirmeniz gerekir.

     Hipervizör Olay Görüntüleyicisi olup ola bir hata olup ola bir şey olup ola bir denetime gerek yok. Bunu yapmak için Olay Görüntüleyicisi **(** Başlangıç anahtarı + **R,** ardından yazın) açın ve `eventvwr` **günlükler , Sistem Windows 'yi** **seçin.** Ardından günlüğü olay kaynağına göre filtrele ve kaynağı **Hyper-V-Hypervisor olarak ayarlar.** Kök nedeni belirlemeye yardımcı olması için hataları denetleyin.

     İşlemciniz en düşük gereksinimleri karşılıyor ancak hipervizör hala başarısız oluyorsa, bilgisayarınızda kullanılabilir bir BIOS yükseltmesi olup ola bir şey olup değildir. Bir tane varsa ve yükseltmeyi seçerseniz, BIOS'u yükseltirken üreticinin tüm önlemlerini (BIOS üretici yazılımı yükseltmenin bios'u kalıcı olarak bozacak bir güç kaybı tarafından kesintiye uğramaması gibi) gözlemleyenin.

- En az 4 GB sistem belleğine sahip olduğundan ve bunun yoğun kaynak kullanımlı diğer programlar ve işlemler tarafından tüketilmemesi gerekir.

- Sanal ağ ile engel olan üçüncü taraf sürücüleri veya yazılımları kaldırın/devre dışı bırakma.

   Hyper-V ağ yığınıyla tam olarak uyumlu olmayan ağ sürücüleri/protokolleri gibi Windows 8 bazı 3. taraf ürünlerle ilgili bilinen bazı sorunlar vardır.

   Genel olarak, yazılımlarını Windows 8 ve Hyper-V ile uyumlu olacak şekilde güncelleştirmeleri, bu ürünlerin geliştiricilerine açık olur.

   Aşağıdaki ürünler, Windows 8 uyumluluğu için yükseltmeyi gerekli olabilir: VirtualBox, Virtual PC 7, VMWare, bazı VPN istemcileri, yazılım güvenlik duvarları, Cisco VPN istemcilerinin bazı sürümleri ve diğer sanallaştırma sistemleri. Şüpheli sanallaştırma yazılımının geliştiricisi ile birlikte çalışarak yazılım ve Hyper-V ile uyumlu hale Windows 8 yükseltmelerini teşvik edin.

   Geçici bir *çözüm* olarak, sanal makine tarafından sanal ağ ile iletişim kurmak için kullanılan sanal ağa engel olan tüm Emulator sürücüleri ve uygulamaları Visual Studio. Bu uygulamalar şunları içerebilir:

  - Virüsten koruma uygulamaları (ağ yığınına kanca)

  - Ağ izleme araçları

  - Ağ günlüğü araçları

  - Diğer sistem izleme yazılımı

    Söz konusu ürünleri kaldırmanın (ve ürün geliştiricinin güncelleştirilmiş bir sürümü serbest bırakmalarını talep etmek) başka bir olası geçici çözüm de aşağıdaki adımların atılmasıdır.

  1. Ağ Bağlantıları yöneticisini başlatma (Başlangıç ekranı ağ bağlantılarını görüntülemek için bu seçeneği yazın `View Network Connections` ve seçin.)

  2. vEthernet (İç Ethernet Bağlantı Noktası Windows Phone Emulator İç Anahtar) bağdaştırıcısı için bağlam **menüsünden** Özellikler'i seçin.

      ![Hyper&#45;V tarafından kullanılan Sanal Bağdaştırıcı](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Bağdaştırıcı özellikleri burada gösterilir.

      ![Sanal Bağdaştırıcı Özellikleri](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Bu bağdaştırıcı için, Bu bağlantı altında yalnızca aşağıdaki öğeleri kullanır **altında seçili olması gereken öğeler** aşağıdakiler olabilir:

     - Microsoft Ağları için İstemci

     - QoS Paket Zamanlaması

     - Microsoft Ağları için Dosya ve Yazıcı Paylaşımı

     - Microsoft LLDP Protokol Sürücüsü

     - Bağlantı Katmanı Topolojisi Bulma EşleciSi/O Sürücüsü

     - Bağlantı Katmanı Topoloji Bulma Yanıtlayanı

     - İnternet Protokolü Sürüm 6 (TCP/IPv6)

     - İnternet Protokolü Sürüm 4 (TCP/IPv4)

  4. Diğer öğelerin seçimini kaldırın.

     Bu tekniği kullanmanın dezavantajı, yeni bir 3. taraf ürününün desteklenmeyen sürücüleri yüklemesi veya öykünücü yüklendikten sonra bu adımların yinelenmeleri gerektirmektedir.

     Üçüncü taraf ürünleri kaldırdikten sonra, şirket içi anahtarı Windows Phone Emulator gerekir. Bunu gerçekleştirmek için:

  - Hyper V'i açın ve Sanal Anahtar Yöneticisi'ne gidin. "İç Anahtar Windows Phone Emulator adlı bir sanal anahtar oluşturun ve bağlantı türünü İç ağ **olarak ayarlayın.**

     ![Sanal Anahtar Yöneticisi](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Şimdi öykünücüsü başlat. Çalışması gerekir.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a>Bilgisayar, Emulator'yi yükledikten sonra önyükleme Emulator
 Bu sorun aşağıdaki koşullar doğru olduğunda oluşabilir:

- Bilgisayarınızda Gigabayt ana kart var.

- USB3, anakartta etkindir.

  Bu sorunu çözmek için anakartın BIOS ayarlarında USB3'ü devre dışı bırakarak bilgisayarı yeniden başlatın. Ardından Gigabyte'ın anakartınızın BIOS'u için bir güncelleştirme yayınıp yayınlayamamış olup olmadığını kontrol edin.

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a>Visual Studio öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer IDE'lerde hata ayıklama hedefi olarak görünmüyor
 Öykünücü çalışıyor ancak ADB'ye bağlı görünmüyorsa (Android Debug Bridge) veya ADB kullanan Android araçlarında görünmüyorsa (örneğin, Android Studio veya Eclipse), öykünücüsünün ADB'yi nerede aramasını ayarlamanız gerekir. Öykünücü, dosyanın temel konumunu belirlemek için bir kayıt Android SDK kullanır ve \platform-tools\adb.exe altındaki dosyanın yerini tespit eder. Öykünücü tarafından Android SDK yolu değiştirmek için:

- Başlat düğmeleri bağlam menüsünde **Çalıştır'ı** seçerek, iletişim kutusuna yazarak ve Tamam'ı `regedit` seçerek Kayıt Defteri Düzenleyicisi'ni **açın.**

- Sol *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools* klasör ağacında yer alan klasöre gidin.

- Yol kayıt **defteri** değişkenini, dosyanıza giden yol ile eş Android SDK.

  Öykünücüsü yeniden başlatın; artık ADB'ye ve ilişkili Android araçlarına bağlı öykünücüsü görüyor olun.

## <a name="emulator-stops-responding-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a>Emulator UDP bağlantı noktasını ayarlayamaması nedeniyle yanıt vermiyor
 Xamarin Player ile uyumsuzluk nedeniyle bu sorunla karşınız olabilir. Öykünücü yanıt vermiyor gibi görünüyorsa veya şu hata iletisini görüyorsanız: "Öykünücü cihaz işletim sistemine bağlanamıyor: UDP bağlantı noktası ayar yapamadı.  Bazı işlevler devre dışı bırakılmış olabilir" gibi bir durumla karşılaşıyor olabilir. Aşağıdaki adımları uygulayın.

1. Xamarin Player'ı kaldırın.

2. Sanal kutunun kaldırılmış olduğunu doğrulayın (Xamarin Player sanal kutunun üzerinde çalışır).

3. Cihaz yöneticisine gidin, gizli cihazları gösterme seçeneğini belirleyin ve ardından fiziksel ağ kartları dışındaki her şeyi silin.

4. Fiziksel olmayan ağ bağdaştırıcılarını kaldırdikten sonra Hyper-V'yi kaldırmayı/yeniden yüklemeyi çalışabilirsiniz.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a> Xamarin projesine hata ayıklayıcı ek olama
 Intel Skylake işlemcileriyle Windows 10 çalıştırıyorsanız, Xamarin uygulamaları öykünücüde çalıştırılamayabilirsiniz veya Visual Studio hata ayıklayıcısı bu uygulamalara eklenemeyebilirsiniz. Bunun nedeni Hyper-V ve Skylake işlemcileriyle ilgili bir sorundur. Geçici çözüm olarak aşağıdaki adımları uygulayın.

1. Hyper-V Yöneticisi'ni açın ve kullanmakta olan öykünücü profili için VM'yi seçin.

2. Kaydedilen **Durumu Sil (sağ alt)** öğesini seçin.

3. Seçim **Ayarlar...**

4. İşlemci düğümünü genişletin ve **Uyumluluk'ı seçin.**

5. Farklı **bir işlemci sürümüne sahip fiziksel bir bilgisayara geçişi etkinleştirin.**

6. Hizmeti yeniden başlatın (Eylemler **altında)** ve yeniden deneyin.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emulator kullanan uygulama çalıştır Google Play Hizmetleri
 Öykünücü, iş için kitaplıklarla birlikte Google Play Hizmetleri. Ancak öykünücü, değiştirilebilir zip dosyalarının sürükle ve bırak ile yüklemesini destekler.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a> Bir dosyanın, APK'nin veya flashable zip dosyasının sürüklenip bırakı çalışmıyor
 Öykünücü, ADB.exe sürükleyip ekrana bırakarak dosya aktarımını kolaylaştırmak için ADB.exe kullanır. Bir dosyayı sürükleyip bırakmayı deneerek hatayla karşılaşırsanız, bu büyük olasılıkla öykünücüsünün bir dosyaya ADB.exe. Sorunu çözmek için, Visual Studio öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer IDE'lerde hata ayıklama hedefi [olarak görünmüyor.](#ADB)

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a> Ekran görüntüsünün çözünürlüğü yanlış
 Ek Araçlar penceresindeki Ekran Görüntüsü  sekmesini kullanarak ekran görüntüsü alırsanız ve elde edilen görüntü beklenmedik boyuttasa, Yakala'yi seçmeden önce ekranın yakınlaştırma düzeyini ayarlamanız **gerekir.** Öykünücü, ana bilgisayar izleyicinizin ekran çözünürlüğünde ekran görüntülerini alır.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emulator OpenGL içeriğini işleyemezse
 Öykünücü, ana makinenizin GPU'larını kullanarak OpenGL içeriğini işler ve BU çağrıları DirectX'e ve DirectX'e dönüştürmek için ANGLE projesini kullanır. Uygulamanız bir cihazda doğru ancak öykünücüde hatalı bir şekilde işlemesi, cihazın yanlış bir OpenGL çağrısını azaltması olasıdır (örneğin, eşleşmeen gölgelendirici değişkenleri kullanarak).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a>Emulator dokunma hareketlerine yanıt vermiyor
 Bazı durumlarda öykünücü, dokunmatik ekrandan doğrudan etkileşim aracılığıyla veya öykünücü araç çubuğunda Multi-Touch Aracını kullanarak çoklu dokunmaya başlar ve yanıt vermez. Bu durumda öykünücü **araç** çubuğundaki Döndür düğmesini seçin ve çoklu dokunmayı yeniden kullanmayı deneyin. Sorun devam ederse [OpenGL](#OpenGL) içerik Emulator başarısız olduğunda sorunu okuyun.

## <a name="support-resources"></a><a name="Support"></a> Destek kaynakları
 Ana bilgisayarınız sistem gereksinimlerini karşılıyorsa ve bu sorun giderme kılavuzunda kapsanmayan bir sorunla karşılaşırsanız:

- [Android-Emulator](https://stackoverflow.com/questions/tagged/android-emulator) ve Visual-Studio etiketlerini kullanarak StackOverflow 'de soru sorun.

- Visual Studio veya Emulator yöneticisi 'nde gülümseme gönder aracını kullanarak bir sorun bildirin.
