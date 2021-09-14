---
title: Android Visual Studio Emulator için sorun giderme | Microsoft Docs
description: Android için yeni bir uygulama kullanırken karşılaşılan sorunları çözmenize yardımcı Visual Studio Emulator öğrenin.
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
ms.openlocfilehash: 62c2b69edf6868d1559df2a861a85e286f8ffa15
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631659"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
Bu konu, Android için yeni bir uygulama kullanırken karşılaşılan sorunları çözmenize yardımcı olacak Visual Studio Emulator içerir.

> [!WARNING]
> Öykünücü yüklendikten sonra kurulum programı, yazılımı çalıştırma önkoşullarını denetler. Önkoşullar yoksa ancak yükleme için gerekli olmazsa uyarılar görüntüler.

 Bu konuda aşağıdaki bölümler yer almaktadır.

- [Başlamadan önce](#BeforeYouStart)

- [Emulator başarısız oluyor](#NoInstall)

- [Etki alanı veya kurumsal ağ üzerinde ağ hedeflere bağlanamıyor](#DomainNetwork)

- [Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflere bağlanamıyor](#ManualNetworkConfig)

- [Emulator yavaş başlatılır, zaman aşımı nedeniyle başlatamaz veya uygulama dağıtımı başarısız olur](#SlowStart)

- [Emulator başlatıla](#NoStart2)

- [Emulator başlatıla (ilk kullanım)](#NoStart)

- [Bilgisayar, Emulator'yi yükledikten sonra önyükleme Emulator](#NoBoot)

- [Visual Studio öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer IDE'lerde hata ayıklama hedefi olarak görünmüyor](#ADB)

- [Emulator UDP bağlantı noktasını ayarlayamaması nedeniyle yanıt vermiyor](#XamarinPlayer)

- [Xamarin projesine hata ayıklayıcı ek olama](#Skylake)

- [Emulator kullanan bir uygulama çalıştır Google Play Hizmetleri](#GooglePlay)

- [Bir dosyanın, APK'nin veya flashable zip dosyasının sürükleyip bırakması çalışmıyor](#DragAndDrop)

- [Ekran görüntüsünün çözünürlüğü yanlış](#Resolution)

- [Emulator OpenGL içeriğini işleyemezse](#OpenGL)

- [Emulator çok dokunmalı hareketlere yanıt vermiyor](#Multitouch)

- [Destek kaynakları](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a> Başlamadan önce
 Sorun gidermeye başlamadan önce aşağıdaki konuları gözden geçirmek yararlı olabilir:

- [Android için Visual Studio Emulator gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a>Emulator başarısız oluyor
 Hyper-V yüklüyse öykünücüsünü yüklemeye çalışırsanız aşağıdaki iletiyi alırsınız. HyperV'i destekleyen bir makineye sahip olmalı ve etkinleştirilmelidir.

 ![Bilgisayar Hyper-V Visual Studio için kurulumun engellenmiş olduğunu Android için Microsoft Visual Studio Öykünücüsü iletinin ekran görüntüsü.](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Bu ileti hem Android hem de Visual Studio Emulator için Windows Phone Emulator. Windows 8.1 ve Windows 10 öykünücüsü destekler.

 Bu iletiyi görüyorsanız öykünücü çalıştırıp [Visual Studio Emulator android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) için sistem gereksinimleri'ne bakın.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a> Etki alanı veya kurumsal ağ üzerinde ağ hedeflere bağlanamıyor
 Android Visual Studio Emulator, ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür. Etki alanı veya çalışma Windows katılmaz ve konak bilgisayarla etki alanı veya çalışma grubu kimlik bilgilerini paylaşmaz.

 Ağınız temel ağ ve İnternet bağlantısı için etki alanı veya çalışma grubu yetkilendirmesi gerektiriyorsa, özel durum için IT yöneticinize başvurun. Bu özel durum, geliştirme bilgisayarınızın bir sınır makinesi olarak hizmet etmelerini ve öykünücü gibi etki alanına katılmayan ağ aygıtlarından gelen bağlantıları kabul etmelerini sağlar.

 Android Visual Studio Emulator kendi MAC adresleri kümesi de kullanılır. Öykünücüden ağ veya İnternet kaynaklarına erişe değilseniz, öykünücüsünün MAC adreslerinin ağ üzerinde yetkilendirilmiş olduğundan emin olmak için IT yöneticinize başvurun.

#### <a name="to-view-the-emulators-mac-addresses"></a>Öykünücüsünün MAC adreslerini görüntülemek için

1. Öykünücü'ünü başlatma.

2. Öykünücü araç çubuğunda köşeli çift ayraç düğmesine (>>) tıklayarak Ek Araçlar penceresini açın.

3. Ek Araçlar penceresinde Ağ sekmesine tıklayın.

4. Ağ sayfasında Fiziksel adres girişlerini bulun.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a> Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflere bağlanamıyor
 Öykünücüden ağ hedeflerine bağlanmak için ağ aşağıdaki gereksinimleri karşılamalıdır:

- DHCP. Öykünücü, kendisini ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak yapılandıran DHCP gerektirir.

- DNS ve ağ geçidi ayarlarını otomatik olarak yapılandırdı. Öykünücü için DNS ve ağ geçidi ayarlarını el ile yapılandırmak mümkün değildir.

  Ağınız el ile yapılandırılmış ayarlar gerektiriyorsa, öykünücü için ağ bağlantısını nasıl etkinleştirebilirsiniz belirlemek üzere IT yöneticinize danışın.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a>Emulator yavaş başlatılır, zaman aşımı nedeniyle başlatamaz veya uygulama dağıtımı başarısız olur
 Belirli koşullar altında öykünücünin başlaması birkaç dakika sürer veya zaman aşımı nedeniyle başlatılamaz. Öykünücü başlatılamayamazsa şu iletiyi alırsınız: `App deployment failed. Please try again` . Aşağıdaki koşullar bu hataya neden olabilir.

- Android için Visual Studio Emulator önyüklenebilir BIR VHD'den çalıştırma. Bu yapılandırma desteklenmez.

- Hatalı bir sabit sürücü. chkdsk programını çalıştırmayı göz önünde bulundurabilirsiniz.

- Birleştirmesi gereken bir sabit sürücü. Sürücüyü birleştirmeyi göz önünde bulundurabilirsiniz.

- Neredeyse dolu bir sabit sürücü. Sürücüde kullanılabilir alanı kontrol edin.

- Çalışan diğer uygulamalar nedeniyle yeterli bellek yok. Bellek tüketen veya bellek miktarını artıran uygulama sayısını azaltabilirsiniz.

- Genellikle sistemde düşük performansa katkıda bulunan faktörler. Windows Experience Index'de en düşük alt çizgiye sahip olan bileşenle ilgili sorun gidermeye başlayabilirsiniz. Bu sorun giderme adımlarını uygulamanın Performans Bilgileri ve Araçlar sayfasında Denetim Masası.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Emulator başlatıla
 Öykünücü daha önce çalışıyor ancak şimdi çalışmıyorsa aşağıdaki görevleri gerçekleştirin. Öykünücüsü ilk kez kullanıyorsanız, bu [adımları denemeden önce Emulator başlatılamayabilirsiniz (ilk kullanım).](#NoStart)

- Öykünücüsünün diğer Tüm Hyper-V örneklerini kaldırın.

    1. Visual Studio’yu kapatın.

    2. Hyper-V Yöneticisi'ni açın ve zaten çalışan ve bozuk durumda Emulator (Sanal Makineler) hyper-V örneklerini durdurun.

    3. Hyper-V Yöneticisi'nde diğer öykünücü VM'leri silin.

    4. Makinenizi yeniden başlatın.

- En az 4 GB sistem belleğine sahip olduğundan ve bunun yoğun kaynak kullanımı olan diğer programlar ve işlemler tarafından tüketilmemesi (örneğin, tarayıcı pencerelerini kapatmayı deneyin) emin olun.

- Hyper-V Yöneticisi'nde Sanal Anahtar Yöneticisi'ni açın ve iki ağ anahtarına sahip olup olamayabilirsiniz; birinci anahtarın iç anahtar, ikinci anahtarın ise dış anahtar olduğunu doğrulayın.

     ![Hyper-V Yöneticisi'nde Sanal Anahtar Yöneticisi'nin ekran görüntüsü. Yeni bir sanal anahtar vurgulanmış ve özellikleri bunun bir dış ağ anahtarı olduğunu gösterir.](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Kurulum yanlışsa ve ağ Windows 10 kullanıyorsanız [netcfg -d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) komutunu kullanarak ağ cihazlarını yeniden yüklemeyi denemeniz gerekebilir (bölüm 6).

- Bu adımlar sorunu çözmezse, [öykünücüye](#NoStart) engel Emulator üçüncü taraf yazılım hakkında bilgi için bkz. Emulator başlatılamaz (ilk kullanım).

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a>Emulator başlatıla (ilk kullanım)
 Öykünücü başlamazsa, sorunu tanımlamak ve düzeltmek için aşağıdaki görevleri gerçekleştirin.

- En düşük donanım gereksinimlerinin karşı olduğundan ve BIOS ayarlarının doğru olduğundan emin olun.

   Hyper-V Emulator Windows 8, İkinci Düzey Adres Çevirisi (SLAT) ile 64 bit işlemci gerektirir. Intel için çekirdek i3, i5 veya i7 işlemciye (veya birçok Xeon'a) ihtiyacınız vardır. AMD yongalarının listesi burada [mevcuttur.](https://www.amd.com/en/support)

  1. Bilgisayarınızın sistem gereksinimlerini karşılaya [olduğundan emin olun.](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

  2. [SLAT aracının bilgisayarınızın](https://slatstatuscheck.codeplex.com/) SLAT özellikli olduğunu raporlayalı olduğunu doğrulayın.

  3. Bilgisayarınızın BIOS ayarlarında tüm sanallaştırma teknolojisinin etkinleştirildiğinden emin olun. Bios açıklamaları her donanım üreticisi için farklılık gösterebilir. Genel olarak, şunlarla ilgili özellikleri etkinleştirin:

     - SLAT (İkinci Düzey Adres Çevirisi)

     - EPT (Genişletilmiş Sayfa Tabloları) (Intel)

     - NPT (İç İçe Sayfa Tabloları) (AMD)

     - RVI (Hızlı Sanallaştırma Dizin Oluşturma) (AMD)

     - VMX (donanım destekli sanallaştırma desteğini gösteren bir Intel kısaltması)

     - SVM (donanım destekli sanallaştırma desteğini gösteren bir AMD kısaltması)

     - XD (Yürütme Devre Dışı Bırak) (Intel); bu etkinleştirilmelidir

     - NX (Yürütme Yok)(AMD); bu etkinleştirilmelidir.

  4. BIOS'ta aşağıdaki seçenekler varsa bunları devre dışı bırakabilirsiniz.

     - Intel VT-d'yi devre dışı bırakma

     - Güvenilen Yürütmeyi Devre Dışı Bırakma

       Daha fazla bilgi için şu makaleye bakın: Technet: Hyper-V: Hyper-V Etkinleştirme BIOS Hatalarını Düzeltme

  5. En az 4 GB sistem belleğine sahip olduğundan ve bunun diğer yoğun kaynak kullanımlı programlar ve işlemler tarafından tüketilmemesi gerekir.

  6. Veya daha iyi bir Windows 8 Professional emin olun (Windows Server 2008 desteklenmiyor). Windows Server 2012, ancak Masaüstü Deneyimini etkinleştirmeniz gerekir.

     Hipervizör Olay Görüntüleyicisi olup ola bir hata olup olamaylarını inceleysiniz. Bunu yapmak için Olay Görüntüleyicisi **(** Başlangıç anahtarı + **R,** yazın) açın ve `eventvwr` **günlükler , Sistem Windows** **seçin.** Ardından günlüğü olay kaynağına göre filtrele ve kaynağı **Hyper-V-Hypervisor olarak ayarlar.** Kök nedeni belirlemeye yardımcı olması için hataları denetleyin.

     İşlemciniz en düşük gereksinimleri karşılıyor ancak hipervizör hala başarısız oluyorsa, bilgisayarınızda kullanılabilir bir BIOS yükseltmesi olup ola bir şey olup değildir. Bir tane varsa ve yükseltmeyi seçerseniz, BIOS'u yükseltirken üreticinin tüm önlemlerini (BIOS üretici yazılımı yükseltmenin bios'u kalıcı olarak bozan bir güç kaybı tarafından kesintiye uğramaması gibi) gözlemek için emin olun.

- En az 4 GB sistem belleğine sahip olduğundan ve bunun diğer yoğun kaynak kullanımlı programlar ve işlemler tarafından tüketilmemesi gerekir.

- Sanal ağ ile engel olan üçüncü taraf sürücüleri veya yazılımları kaldırın/devre dışı bırakma.

   Hyper-V ağ yığınıyla tam olarak uyumlu olmayan ağ sürücüleri/protokolleri Windows 8 altında yüklü olan bazı üçüncü taraf ürünlerle ilgili bilinen bazı sorunlar vardır.

   Genel olarak, yazılımlarını Windows 8 ve Hyper-V ile uyumlu olacak şekilde güncelleştirmek, bu ürünlerin geliştiricilerine açık olur.

   Aşağıdaki ürünler, Windows 8 uyumluluğu için yükseltmeyi gerekli olabilir: VirtualBox, Virtual PC 7, VMWare, bazı VPN istemcileri, yazılım güvenlik duvarları, Cisco VPN istemcilerinin bazı sürümleri ve diğer sanallaştırma sistemleri. Şüpheli sanallaştırma yazılımının geliştiricisi ile birlikte çalışarak yazılımı Windows 8 ve Hyper-V ile uyumlu hale Windows 8 yükseltmelerini teşvik edin.

   Geçici bir *çözüm* olarak, sanal makine tarafından sanal ağ ile iletişim kurmak için kullanılan sanal ağa engel olan tüm üçüncü taraf Emulator ve uygulamaları devre Visual Studio. Bu uygulamalar şunları içerebilir:

  - Virüsten koruma uygulamaları (ağ yığınına kanca)

  - Ağ izleme araçları

  - Ağ günlüğü araçları

  - Diğer sistem izleme yazılımı

    Söz konusu ürünleri kaldırmanın (ve ürün geliştiricinin güncelleştirilmiş bir sürümü serbest bırakmasini talep etmek) başka bir olası geçici çözüm de aşağıdaki adımların atılmasıdır.

  1. Ağ Bağlantıları yöneticisini başlatma (Başlangıç ekranı ağ bağlantılarını görüntülemek için bu seçeneği yazın `View Network Connections` ve seçin.)

  2. vEthernet (İç Ethernet Bağlantı Noktası Windows Phone Emulator İç Anahtar) bağdaştırıcısı için bağlam **menüsünden** Özellikler'i seçin.

      ![Hyper&#45;V tarafından kullanılan Sanal Bağdaştırıcı](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Bağdaştırıcı özellikleri burada gösterilir.

      ![Sanal Bağdaştırıcı Özellikleri](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Bu bağdaştırıcı için, Bu bağlantı altında yalnızca aşağıdaki öğeleri kullanır **altında seçili olması gereken** öğeler aşağıdakiler olabilir:

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

  Daha fazla bilgi için şu Bilgi Bankası bakın: [Gigabayt sistemlerinde Hyper-V](https://support.microsoft.com/en-us/kb/2693144)rolü yüklemesi sonrasında önyükleme hatası.

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a>Visual Studio öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer IDE'lerde hata ayıklama hedefi olarak görünmüyor
 Öykünücü çalışıyorsa ama ADB'ye (Android Debug Bridge) bağlı görünmüyorsa veya ADB kullanan Android araçlarında görünmüyorsa (örneğin, Android Studio veya Eclipse) öykünücüsünün ADB'yi nerede aramasını ayarlamanız gerekir. Öykünücü, kayıt defteri anahtarıyla kayıt defterinizin temel konumunu Android SDK ve bu dizin \platform-tools\adb.exe dosyanın yerini tespit eder. Öykünücü Android SDK yolu değiştirmek için:

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
 Intel Skylake işlemcileriyle Windows 10 çalıştırıyorsanız Xamarin uygulamaları öykünücüde çalıştırılamayabilirsiniz veya Visual Studio hata ayıklayıcısı bu uygulamalara eklenemeyebilirsiniz. Bunun nedeni Hyper-V ve Skylake işlemcileriyle ilgili bir sorundur. Geçici çözüm olarak aşağıdaki adımları uygulayın.

1. Hyper-V Yöneticisi'ni açın ve kullanmakta olan öykünücü profili için VM'yi seçin.

2. Kaydedilen **Durumu Sil (sağ alt)** öğesini seçin.

3. Seç **Ayarlar...**

4. İşlemci düğümünü genişletin ve **Uyumluluk'ı seçin.**

5. Farklı **bir işlemci sürümüne sahip fiziksel bir bilgisayara geçişi etkinleştirin.**

6. Hizmeti yeniden başlatın (Eylemler **altında)** ve yeniden deneyin.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emulator kullanan bir uygulama çalıştır Google Play Hizmetleri
 Öykünücü, iş için kitaplıklarla birlikte Google Play Hizmetleri. Ancak öykünücü, değiştirilebilir zip dosyalarının sürükle ve bırak ile yüklemesini destekler.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a> Bir dosyanın, APK'nin veya flashable zip dosyasının sürükleyip bırakması çalışmıyor
 Öykünücü, ADB.exe sürükleyip ekrana bırakarak dosya aktarımını kolaylaştırmak için ADB.exe kullanır. Bir dosyayı sürükleyip bırakmayı deneerek bir hatayla karşılaşırsanız, bu büyük olasılıkla öykünücüsünün bir dosyaya ADB.exe. Sorunu çözmek için, Visual Studio öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer IDE'lerde hata ayıklama hedefi [olarak görünmüyor.](#ADB)

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a> Ekran görüntüsünün çözünürlüğü yanlış
 Ek Araçlar penceresindeki Ekran Görüntüsü  sekmesini kullanarak ekran görüntüsü alırsanız ve elde edilen görüntü beklenmedik boyuttasa, Yakala'yi seçmeden önce ekranın yakınlaştırma düzeyini ayarlamanız **gerekir.** Öykünücü, ana bilgisayar izleyicinizin ekran çözünürlüğünde ekran görüntülerini alır.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emulator OpenGL içeriğini işleyemezse
 Öykünücü, ana makinenizin GPU'larını kullanarak OpenGL içeriğini işler ve BU çağrıları DirectX'e ve DirectX'e dönüştürmek için ANGLE projesini kullanır. Uygulamanız bir cihazda doğru ancak öykünücüde hatalı bir şekilde işlemesi, cihazın yanlış bir OpenGL çağrısını azaltması olasıdır (örneğin, eşleşmeen gölgelendirici değişkenleri kullanarak).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a>Emulator çok dokunmalı hareketlere yanıt vermiyor
 Bazı durumlarda öykünücü, dokunmatik ekrandan doğrudan etkileşim aracılığıyla veya öykünücü araç çubuğunda Multi-Touch Aracını kullanarak çoklu dokunmaya başlar ve yanıt vermez. Bu durumda öykünücü **araç** çubuğundaki Döndür düğmesini seçin ve çoklu dokunmayı yeniden kullanmayı deneyin. Sorun devam ederse [OpenGL](#OpenGL) içerik Emulator başarısız olduğunda sorunu okuyun.

## <a name="support-resources"></a><a name="Support"></a> Destek kaynakları
 Ana bilgisayarınız sistem gereksinimlerini karşılamıyorsa ve bu sorun giderme kılavuzunda yer alan bir sorunla karşılaşırsanız:

- stackOverflow'da [android-emulator ve visual-studio](https://stackoverflow.com/questions/tagged/android-emulator) etiketlerini kullanarak bir soru sorun.

- Visual Studio'de veya Emulator Manager'da Gülümseme Gönder aracını kullanarak sorun bildirebilirsiniz.
