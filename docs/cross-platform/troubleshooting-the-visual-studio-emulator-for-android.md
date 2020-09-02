---
title: Android için Visual Studio öykünücüsü sorunlarını giderme | Microsoft Docs
ms.custom: ''
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
ms.openlocfilehash: cfcae9ac15292a52a79c97b5b67e758b9dc0dcde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386309"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
Bu konu, Android için Visual Studio öykünücüsü 'nü kullanırken karşılaşabileceğiniz sorunları çözmenize yardımcı olacak bilgiler içerir.

> [!WARNING]
> Öykünücü yüklendiğinde, Kurulum programı yazılımı çalıştırmaya yönelik önkoşulları denetler. Önkoşullar yoksa uyarıları görüntüler, ancak yükleme için gerekli değildir.

 Bu konuda aşağıdaki bölümler yer almaktadır.

- [Başlamadan önce](#BeforeYouStart)

- [Öykünücü yüklenemiyor](#NoInstall)

- [Bir etki alanı veya şirket ağındaki ağ hedeflerine bağlanılamıyor](#DomainNetwork)

- [Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflerine bağlanılamıyor](#ManualNetworkConfig)

- [Öykünücü yavaş başlıyor, zaman aşımı nedeniyle başlatılamaz veya uygulama dağıtımı başarısız olur](#SlowStart)

- [Öykünücü başlatılamadı](#NoStart2)

- [Öykünücü başlatılamadı (ilk kullanım)](#NoStart)

- [Öykünücü yüklendikten sonra bilgisayar önyükleme yapamıyor](#NoBoot)

- [Visual Studio, uygulamayı öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer Ides 'te hata ayıklama hedefi olarak görünmüyor](#ADB)

- [Öykünücü UDP bağlantı noktasını ayarlayamadığından yanıt vermiyor](#XamarinPlayer)

- [Hata ayıklayıcı bir Xamarin projesine iliştirilemiyor](#Skylake)

- [Öykünücü Google Play Hizmetleri kullanan uygulamayı çalıştıramıyor](#GooglePlay)

- [Dosya, APK veya bıraktığınızda ZIP dosyası için sürükle ve bırak çalışmıyor](#DragAndDrop)

- [Ekran görüntüsünün çözümlenmesi yanlış](#Resolution)

- [Öykünücü OpenGL içeriğini işlemesini başaramazsa](#OpenGL)

- [Öykünücü çok dokunmalı hareketlere yanıt vermiyor](#Multitouch)

- [Destek kaynakları](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a> Başlamadan önce
 Sorun gidermeye başlamadan önce, aşağıdaki konuları gözden geçirmek yararlı olabilir:

- [Android için Visual Studio öykünücüsü sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a> Öykünücü yüklenemiyor
 Hyper-V yüklü değilse, öykünücüyü yüklemeye çalıştığınızda aşağıdaki iletiyi görürsünüz. HyperV 'yi destekleyen bir makineniz olmalıdır ve bu makinenin etkinleştirilmesi gerekir.

 ![Android&#95;EMU&#95;Install&#95;sorunu](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Bu ileti hem Android için Visual Studio öykünücüsü hem de Windows Phone öykünücüsü için geçerlidir. Windows 8.1 ve Windows 10 öykünücüsü destekler.

 Bu iletiyi görürseniz, öykünücüyü çalıştırıp çalıştıramayacağını öğrenmek için [Android Için Visual Studio öykünücüsü sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) denetleyin.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a> Bir etki alanı veya şirket ağındaki ağ hedeflerine bağlanılamıyor
 Android için Visual Studio öykünücüsü, ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür. Windows etki alanına katılmamış ve ana bilgisayar ile etki alanı veya çalışma grubu kimlik bilgilerini paylaşmıyor.

 Ağınız, temel ağ ve Internet bağlantısı için etki alanı veya çalışma grubu yetkilendirmesi gerektiriyorsa, özel durum için BT yöneticinize başvurun. Bu özel durum, geliştirme bilgisayarınızın bir sınır makine olarak çalışmasına ve öykünücü gibi etki alanına katılmış olmayan ağ cihazlarından gelen bağlantıları kabul etmesine olanak tanır.

 Android için Visual Studio öykünücüsü, kendi MAC adresi kümesini de kullanır. Öykünücüden ağ veya Internet kaynaklarına erişemiyorsanız, öykünücü MAC adreslerinin ağınızda yetkilendirilmiş olduğundan emin olmak için BT yöneticinize başvurun.

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

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a> Öykünücü yavaş başlıyor, zaman aşımı nedeniyle başlatılamaz veya uygulama dağıtımı başarısız olur
 Belirli koşullar altında, öykünücü bir zaman aşımı nedeniyle başlatılması veya başlatılması birkaç dakika sürer. Öykünücü başlayamazsa şu iletiyi görürsünüz: `App deployment failed. Please try again` . Aşağıdaki koşullar bu hataya neden olabilir.

- Önyüklenebilir bir VHD 'den Android için Visual Studio öykünücüsü 'nü çalıştırma. Bu yapılandırma desteklenmez.

- Hatalı bir sabit sürücü. Chkdsk programını çalıştırmayı göz önünde bulundurun.

- Birleştirilmesi gereken bir sabit sürücü. Sürücüyü birleştirmeyi düşünün.

- Neredeyse dolu bir sabit sürücü. Sürücüdeki kullanılabilir alanı denetleyin.

- Çalışan diğer uygulamalar nedeniyle yeterli bellek yok. Belleği tüketen veya bellek miktarını artıran uygulama sayısını azaltın.

- Genellikle sistemde düşük performansa katkıda bulunan her türlü etken. Denetim Masası 'nın performans bilgileri ve araçlar sayfasında bulabileceğiniz Windows Deneyim dizininde en düşük alt puanı olan bileşenle sorun gidermeye başlayın.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a> Öykünücü başlatılamadı
 Öykünücü daha önce çalıştıyordu, ancak şu anda çalışmazsa, aşağıdaki görevlerden geçin. Emulator 'u ilk kez kullanıyorsanız, bu adımları denemeden önce [öykünücü başlatılamadı (ilk kullanım)](#NoStart) .

- Öykünücüsünün diğer Hyper-V örneklerini kaldırın.

    1. Visual Studio’yu kapatın.

    2. Hyper-V Yöneticisi 'Ni açın ve zaten çalışmakta olan ve muhtemelen bozulmuş durumda olan öykünücü (sanal makineler) Hyper-V örneklerini durdurun.

    3. Hyper-V Yöneticisi 'nde diğer öykünücü VM 'Leri silin.

    4. Makinenizi yeniden başlatın.

- En az 4 GB sistem belleğinizin olduğundan ve diğer kaynak yoğunluklu programlar ve süreçler tarafından tüketilmediğinden emin olun (örneğin, herhangi bir tarayıcı pencerelerini kapatmayı deneyin).

- Hyper-V Yöneticisi 'nde sanal anahtar yöneticisini açın ve iki ağ anahtarınız olup olmadığını denetleyin; birincinin iç anahtar olduğunu ve ikincisi 'nin dış olduğunu doğrulayın.

     ![Android&#95;EMU&#95;V&#95;Switch&#95;Man](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Kurulum yanlışsa ve Windows 10 kullanıyorsanız, [netcfg-d komutunu (Bölüm 6) kullanarak ağ aygıtlarını yeniden yüklemeyi](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) deneyebilirsiniz.

- Bu adımlar sorunu çözmezse, öykünücüyü etkileyebilecek üçüncü taraf yazılımlar hakkında bilgi için bkz. [öykünücü başlatılamadı (ilk kullanım)](#NoStart) .

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a> Öykünücü başlatılamadı (ilk kullanım)
 Öykünücü başlamazsa, sorunu tanımlamak ve onarmak için aşağıdaki görevleri gözden geçin.

- En düşük donanım gereksinimlerinin yerine getirildiğini ve BIOS ayarlarının doğru olduğundan emin olun.

   Öykünücü ve Windows 8 Hyper-V, Ikinci düzey adres çevirisi (SLAT) ile 64 bitlik bir işlemci gerektirir. Intel için temel bir i3, i5 veya i7 İşlemciye (veya birçok Xeons) ihtiyacınız vardır. AMD yongaları listesine [buradan](https://www.amd.com/en/support)ulaşabilirsiniz.

  1. Bilgisayarınızın [sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)karşıladığından emin olun.

  2. [SLAT aracının](https://slatstatuscheck.codeplex.com/) bilgisayarınızın SLAT özellikli olduğunu raporluyor olduğunu doğrulayın.

  3. Bilgisayarınızın BIOS ayarları içinde tüm sanallaştırma teknolojisinin etkinleştirildiğinden emin olun. Tam BIOS açıklamaları her donanım üreticisi için farklılık gösterebilir. Genel olarak, şununla ilgili özellikleri etkinleştirin:

     - SLAT (Ikinci düzey adres çevirisi)

     - EPT (genişletilmiş sayfa tabloları) (Intel)

     - NPT (Iç Içe sayfa tabloları) (AMD)

     - RVI (Hızlı sanallaştırma dizin oluşturma) (AMD)

     - VMX (donanım yardımlı sanallaştırma desteğini gösteren bir Intel kısaltması)

     - SVM (donanım yardımlı sanallaştırma desteğini gösteren bir AMD kısaltması)

     - XD (yürütmeyi devre dışı bırak) (Intel); Bunun etkinleştirilmesi gerekir

     - NX (yürütme yok) (AMD); Bu, etkin olmalıdır.

  4. BIOS 'ta aşağıdaki seçenekler varsa, bunları devre dışı bırakın.

     - Intel VT-d 'yi devre dışı bırak

     - Güvenilen yürütmeyi devre dışı bırak

       Daha fazla bilgi için şu makaleye bakın: TechNet: Hyper-V: Hyper-V ' yi etkinleştirme BIOS hataları nasıl düzeltilir

  5. En az 4 GB sistem belleğinizin olduğundan ve Kaynak yoğunluklu diğer programlar ve süreçler tarafından tüketilmediğinden emin olun.

  6. Windows 8 Professional veya daha iyi bir sürümü çalıştırdığınızdan emin olun (Windows Server 2008 desteklenmez). Windows Server 2012 desteklenir, ancak masaüstü deneyimini etkinleştirmeniz gerekir.

     Herhangi bir hiper yönetici hatası olup olmadığını görmek için Olay Görüntüleyicisi inceleyebilirsiniz. Bunu yapmak için Olay Görüntüleyicisi açın (**anahtar** + **R**'yi başlatın, sonra yazın `eventvwr` ) ve ardından **Windows günlükleri**, **sistem**' i seçin. Ardından, günlüğü olay kaynağına göre filtreleyin, kaynağı **Hyper-V-hiper yönetici**olarak ayarlar. Kök nedeni belirlemenize yardımcı olması için hata olup olmadığını denetleyin.

     İşlemcinizin en düşük gereksinimleri karşılaması ancak hiper yönetici hala başarısız olursa, bilgisayarınız için bir BIOS yükseltmesi olup olmadığını bulmayı göz önünde bulundurun. Bir tane varsa ve yükseltmeyi seçerseniz, BIOS 'U yükseltirken üreticiden tüm önlemleri gözlemlediğinizden emin olun (BIOS üretici yazılımı yükseltmesinin, BIOS 'un kalıcı olarak bozulmasına neden olabilecek bir güç kaybı nedeniyle kesilmediğinden emin olma gibi).

- En az 4 GB sistem belleğinizin olduğundan ve Kaynak yoğunluklu diğer programlar ve süreçler tarafından tüketilmediğinden emin olun.

- Sanal ağ ile müdahale eden üçüncü taraf sürücüleri veya yazılımları kaldırın/devre dışı bırakın.

   Windows 8 altında, Hyper-V ağ yığınında tam olarak uyumlu olmayan ağ sürücüleri/protokolleri gibi bazı üçüncü taraf ürünlerle birlikte yüklenmiş bazı bilinen sorunlar vardır.

   Genel olarak, bu ürünlerin geliştiricileri, Windows 8 ve Hyper-V ile uyumlu olmak üzere yazılımlarını güncelleştirmelerdir.

   Aşağıdaki ürünler Windows 8 uyumluluğu için yükseltme gerektirebilir: VirtualBox, Virtual PC 7, VMWare, bazı VPN istemcileri, yazılım güvenlik duvarları, Cisco VPN istemcilerinin bazı sürümleri ve diğer sanallaştırma sistemleri. Şüpheli sanallaştırma yazılımının geliştiriciyle birlikte çalışarak, yazılımı Windows 8 ve Hyper-V ile uyumlu hale getirmek üzere yükseltmeyi teşvik edin.

   Geçici bir *çözüm*olarak, öykünücü tarafından Visual Studio ile iletişim kurmak için kullanılan sanal ağla kesintiye uğraabilecek tüm üçüncü taraf sürücüleri ve uygulamaları devre dışı bırakabilirsiniz. Bu uygulamalar şunlar olabilir:

  - Virüsten koruma uygulamaları (ağ yığınına kanca)

  - Ağ izleme araçları

  - Ağ günlüğü araçları

  - Diğer sistem izleme yazılımı

    Bu olası bir geçici çözüm olan, söz konusu ürünlerin (ve güncelleştirilmiş bir sürümü serbest bırakmaya yönelik ürün geliştiricisinin) kaldırılmasından kısa bir süre için aşağıdaki adımları gerçekleştirmeniz gerekir.

  1. Ağ bağlantıları Yöneticisini başlatın (Başlangıç ekranından, `View Network Connections` ağ bağlantılarını görüntülemek için yazın ve bu seçeneği belirleyin.)

  2. VEthernet (Iç Ethernet bağlantı noktası Windows Phone öykünücü Iç anahtar) bağdaştırıcısı için bağlam menüsünden **Özellikler** ' i seçin.

      ![Hyper&#45;V tarafından kullanılan sanal bağdaştırıcı](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Bağdaştırıcı özellikleri burada gösterilir.

      ![Sanal bağdaştırıcı özellikleri](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Bu bağdaştırıcı için, bu bağlantı altında seçilmesi gereken tek öğeler aşağıdaki **öğeleri kullanır** :

     - Microsoft Ağları için İstemci

     - QoS Paket Zamanlayıcısı

     - Microsoft Ağları için Dosya ve Yazıcı Paylaşımı

     - Microsoft LLDP protokol sürücüsü

     - Bağlantı katmanı topolojisi bulma Eşleyici g/ç sürücüsü

     - Bağlantı Katmanı Topolojisi Bulma Yanıtlayıcısı

     - Internet Protokolü sürüm 6 (TCP/IPv6)

     - Internet Protokolü sürüm 4 (TCP/IPv4)

  4. Diğer tüm öğelerin seçimini kaldırın.

     Bu tekniği kullanmanın alt tarafında, yeni bir 3. taraf ürünün desteklenmeyen sürücüleri yüklemesi veya öykünücü her yüklendiğinde bu adımların tekrarlanması gerekir.

     Üçüncü taraf ürünleri kaldırdıktan sonra, Windows Phone öykünücü Iç anahtarını geri yüklemeniz gerekebilir. Bunu gerçekleştirmek için:

  - Hyper V ' i açın ve sanal anahtar Yöneticisi ' ne gidin. "Windows Phone öykünücü Iç anahtarı" adlı bir sanal anahtar oluşturun ve bağlantı türünü **iç ağ**olarak ayarlayın.

     ![Sanal Anahtar Yöneticisi](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Şimdi öykünücüsü başlatın. Çalışması gerekir.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a> Öykünücü yüklendikten sonra bilgisayar önyükleme yapamıyor
 Bu sorun, aşağıdaki koşullar doğru olduğunda oluşabilir:

- Bilgisayarınızda gigabayt ana kartı bulunur.

- USB3, anakart üzerinde etkindir.

  Bu sorunu çözmek için, ana kartın BIOS ayarlarında USB3 devre dışı bırakın ve bilgisayarı yeniden başlatın. Ardından, gigabayttan kartın BIOS 'U için bir güncelleştirme yayımlamışsa emin olun.

  Daha fazla bilgi için aşağıdaki Bilgi Bankası makalesine bakın: [gigabayt sistemlerine Hyper-V rolü yüklendikten sonra önyükleme hatası](https://support.microsoft.com/en-us/kb/2693144).

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a> Visual Studio, uygulamayı öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer Ides 'te hata ayıklama hedefi olarak görünmüyor
 Öykünücü çalışıyorsa, ancak ADB 'ye (Android Debug Bridge) bağlı görünmüyor veya ADB (örneğin, Android Studio veya tutulma) kullanan Android araçları 'nda görünmüyorsa, öykünücüsünün ADB 'yi nerede aradığı üzerinde ayarlamanız gerekebilir. Öykünücü, Android SDK temel konumunu tanımlamak için bir kayıt defteri anahtarı kullanır ve bu dizin altında \platform-tools\adb.exe dosyasını arar. Öykünücü tarafından kullanılan Android SDK yolunu değiştirmek için:

- Başlat düğmeleri bağlam menüsünden **Çalıştır** ' ı seçerek Kayıt Defteri Düzenleyicisi 'ni açın, `regedit` iletişim kutusuna yazın ve **Tamam**' ı seçin.

- Soldaki klasör ağacında *\SOFTWARE\Wow6432Node\Android SDK Tools HKEY_LOCAL_MACHINE* gidin.

- **Yol** kayıt defteri değişkenini Android SDK yolu ile eşleşecek şekilde değiştirin.

  Öykünücüyü yeniden başlatın ve şimdi ADB ve ilişkili Android araçlarına bağlı olan öykünücüyü görmeniz gerekir.

## <a name="emulator-stops-responding-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a> Öykünücü UDP bağlantı noktasını ayarlayamadığından yanıt vermiyor
 Xamarin Player ile uyumsuzluk nedeniyle bu sorunla karşılaşabilirsiniz. Öykünücü yanıt vermeyi durdur olarak görünüyorsa veya bu hata iletisini görürseniz, "öykünücü cihaz işletim sistemine bağlanamıyor: UDP bağlantı noktası ayarlanamadı.  Bazı işlevler devre dışı bırakılabilir ", bu sorunu yaşıyor olabilirsiniz. Aşağıdaki adımları uygulayın.

1. Xamarin Player 'ı kaldırın.

2. Sanal kutunun kaldırıldığını doğrulayın (Xamarin Player, sanal kutudan en üstünde çalışır).

3. Cihaz Yöneticisi ' ne gidin, gizli cihazları gösterme seçeneğini belirleyin ve ardından fiziksel ağ kartları dışındaki her şeyi silin.

4. Fiziksel olmayan ağ bağdaştırıcılarını kaldırdıktan sonra, Hyper-V ' yi kaldırmayı/yeniden yüklemeyi deneyebilirsiniz.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a> Hata ayıklayıcı bir Xamarin projesine iliştirilemiyor
 Intel ufuk Gölü işlemcilerle Windows 10 çalıştırıyorsanız, Xamarin uygulamaları öykünücüsünde çalışmayabilir veya Visual Studio hata ayıklayıcısı bunlara iliştirilemeyebilir. Bunun nedeni, Hyper-V ve ufuk Gölü işlemcileriyle ilgili bir sorundur. Geçici bir çözüm olarak aşağıdaki adımları uygulayın.

1. Hyper-V Yöneticisi 'Ni açın ve kullanmakta olduğunuz öykünücü profili için VM 'yi seçin.

2. **Kaydedilmiş durumu Sil** (sağ alt) seçeneğini belirleyin.

3. **Ayarları Seç...**

4. İşlemci düğümünü genişletin ve **Uyumluluk**' i seçin.

5. **Farklı bir işlemci sürümü olan fiziksel bir bilgisayara geçişi**etkinleştirin.

6. Hizmeti yeniden başlatın ( **Eylemler**altında) ve yeniden deneyin.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a> Öykünücü Google Play Hizmetleri kullanan uygulamayı çalıştıramıyor
 Öykünücü, Google Play Hizmetleri kitaplıklarıyla birlikte gelmez. Ancak öykünücü, düz ZIP dosyalarını sürükleyip bırakma yüklemesini destekler.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a> Dosya, APK veya bıraktığınızda ZIP dosyası için sürükle ve bırak çalışmıyor
 Öykünücü, bir dosyayı sürükleyip ekrana bıraktığınızda dosya aktarımını kolaylaştırmak için ADB.exe kullanır. Bir dosyayı sürükleyip bırakmaya çalıştığınızda bir hatayla karşılaşırsanız, bu büyük olasılıkla öykünücüsünün ADB.exe bağlı olmadığını gösterir. Sorunu gidermek için, [Visual Studio 'da uygulamayı öykünücüye dağıtmaya çalışmak için takılmış veya öykünücü diğer Ides 'te hata ayıklama hedefi olarak görünmüyor](#ADB).

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a> Ekran görüntüsünün çözümlenmesi yanlış
 **Ek araçlar** penceresinde ekran görüntüsü sekmesini kullanarak bir ekran görüntüsü alırsanız ve sonuçta elde edilen görüntü beklenmeyen bir Boyutladır, **yakalama**'yı seçmeden önce ekranın yakınlaştırma düzeyini ayarlamanız gerekebilir. Öykünücü ekran görüntülerini ana bilgisayar izleyicinizdeki ekran çözünürlüğünde alır.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a> Öykünücü OpenGL içeriğini işlemesini başaramazsa
 Öykünücü, ana bilgisayar makinenizin GPU 'SU kullanılarak OpenGL içeriği işler ve bu çağrıları DirectX 'e ve DirectX 'e dönüştürmek için AÇıLı projeyi kullanır. Uygulamanız bir cihazda düzgün şekilde çalışıyorsa, ancak öykünücüsünde yanlış bir OpenGL çağrısını (örneğin, eşleşmeyen gölgelendirici değişkenlerini kullanarak) azaltılmış olabilir.

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a> Öykünücü çok dokunmalı hareketlere yanıt vermiyor
 Bazı durumlarda, öykünücü dokunma etkin görüntüinizden doğrudan etkileşim aracılığıyla ya da öykünücü araç çubuğundaki çok dokunmalı aracı kullanarak çok dokunmadan başlar ve yanıt vermez. Bu durumda, öykünücü araç çubuğunda **Döndür** düğmesini seçin ve çoklu Touch 'ı kullanmayı deneyin. Sorun devam ederse, [Emulator 'un OpenGL içerik sorununu oluşturabileceği başarısız](#OpenGL) olup olmadığını okuyun.

## <a name="support-resources"></a><a name="Support"></a> Destek kaynakları
 Ana bilgisayarınız sistem gereksinimlerini karşılıyorsa ve bu sorun giderme kılavuzunda kapsanmayan bir sorunla karşılaşırsanız:

- [Android-Emulator](https://stackoverflow.com/questions/tagged/android-emulator) ve Visual-Studio etiketlerini kullanarak StackOverflow 'de soru sorun.

- Visual Studio 'da veya öykünücü yöneticisinde gülümseme Gönder aracını kullanarak bir sorun bildirin.
