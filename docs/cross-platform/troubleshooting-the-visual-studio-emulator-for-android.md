---
title: Android Visual Studio Emulator sorun giderme | Microsoft Docs
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
ms.openlocfilehash: 6d4f1c7007b21fd3580ffcde0d22ba2f92f5841f
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129560873"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
Bu konu, Android için bir uygulama kullanırken karşılaşılan sorunları çözmenize yardımcı olacak Visual Studio Emulator içerir.

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

- [Emulator, Google Play Hizmetleri kullanan bir uygulama çalıştıramaz](#GooglePlay)

- [Bir dosyanın, APK'nin veya flashable zip dosyasının sürüklenip bırakı çalışmıyor](#DragAndDrop)

- [Ekran görüntüsünün çözünürlüğü yanlış](#Resolution)

- [Emulator OpenGL içeriği iş başarısız oluyor](#OpenGL)

- [Emulator dokunma hareketlerine yanıt vermiyor](#Multitouch)

- [Destek kaynakları](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a> Başlamadan önce
 Sorun gidermeye başlamadan önce aşağıdaki konuları gözden geçirmek yararlı olabilir:

- [Android için Visual Studio Emulator gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a>Emulator başarısız oluyor
 Hyper-V yüklüyse öykünücüsünü yüklemeye çalışırsanız aşağıdaki iletiyi alırsınız. HyperV'i destekleyen bir makineye sahip olmalı ve etkinleştirilmelidir.

 ![Bilgisayarın Hyper-V Visual Studio i engellemesi nedeniyle Android için Microsoft Visual Studio Öykünücüsü engellenmiş olduğunu söyleyen bir hata iletisi ekran görüntüsü.](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Bu ileti hem Android hem de Visual Studio Emulator için Windows Phone Emulator. Windows 8.1 ve Windows 10 öykünücü desteği sağlar.

 Bu iletiyi görüyorsanız öykünücü çalıştırıp [Visual Studio Emulator Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) için sistem gereksinimleri'ne bakın.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a> Etki alanı veya kurumsal ağ üzerinde ağ hedeflere bağlanamıyor
 Android Visual Studio Emulator, ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür. Bir etki alanına katılmaz Windows etki alanı veya çalışma grubu kimlik bilgilerini konak bilgisayarla paylaşmaz.

 Ağınız temel ağ ve İnternet bağlantısı için etki alanı veya çalışma grubu yetkilendirmesi gerektiriyorsa, özel durum için IT yöneticinize başvurun. Bu özel durum, geliştirme bilgisayarınızın bir sınır makinesi olarak hizmet etmelerini ve öykünücü gibi etki alanına katılmayan ağ aygıtlarından gelen bağlantıları kabul etmelerini sağlar.

 Android Visual Studio Emulator kendi MAC adresleri kümesi de kullanılır. Öykünücüden ağ veya İnternet kaynaklarına erişe değilseniz, öykünücüsünün MAC adreslerinin ağ üzerinde yetkilendirilmiş olduğundan emin olmak için IT yöneticinize başvurun.

#### <a name="to-view-the-emulators-mac-addresses"></a>Öykünücüsünün MAC adreslerini görüntülemek için

1. Öykünücü'ünü başlatma.

2. Öykünücü araç çubuğunda köşeli çift ayraç düğmesine (>>) tıklayarak Ek Araçlar penceresini açın.

3. Ek Araçlar penceresinde Ağ sekmesine tıklayın.

4. Ağ sayfasında Fiziksel adres girdilerini bulun.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a> Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflere bağlanamıyor
 Öykünücüden ağ hedeflerine bağlanmak için ağ aşağıdaki gereksinimleri karşılamalıdır:

- DHCP. Öykünücü, kendisini ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak yapılandıran DHCP gerektirir.

- DNS ve ağ geçidi ayarlarını otomatik olarak yapılandırdı. Öykünücü için DNS ve ağ geçidi ayarlarını el ile yapılandırmak mümkün değildir.

  Ağınız el ile yapılandırılmış ayarlar gerektiriyorsa, öykünücü için ağ bağlantısını nasıl etkinleştirebilirsiniz belirlemek üzere IT yöneticinize başvurun.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a>Emulator yavaş başlatılır, zaman aşımı nedeniyle başlatamaz veya uygulama dağıtımı başarısız olur
 Belirli koşullar altında öykünücünin başlaması birkaç dakika sürer veya zaman aşımı nedeniyle başlatılamaz. Öykünücü başlatılamayamazsa şu iletiyi alırsınız: `App deployment failed. Please try again` . Aşağıdaki koşullar bu hataya neden olabilir.

- Android için Visual Studio Emulator önyüklenebilir BIR VHD'den çalıştırma. Bu yapılandırma desteklenmez.

- Hatalı bir sabit sürücü. chkdsk programını çalıştırmayı göz önünde bulundurabilirsiniz.

- Birleştirmesi gereken bir sabit sürücü. Sürücüyü birleştirmeyi göz önünde bulundurabilirsiniz.

- Neredeyse dolu bir sabit sürücü. Sürücüde kullanılabilir alanı kontrol edin.

- Çalışan diğer uygulamalar nedeniyle yeterli bellek yok. Bellek tüketen uygulama sayısını azaltma veya bellek miktarını artırma.

- Genellikle sistemde düşük performansa katkıda bulunan faktörler. Windows Deneyimi Dizini'nin Performans Bilgileri ve Araçlar sayfasında en düşük alt çizgiye sahip bileşenle ilgili sorun gidermeye Denetim Masası.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Emulator başlatıla
 Öykünücü daha önce çalışıyor ancak şimdi çalışmıyorsa aşağıdaki görevleri gerçekleştirin. Öykünücüsü ilk kez kullanıyorsanız, bu adımları denemeden önce Emulator başlatılamayabilirsiniz [(ilk kullanım)](#NoStart) bkz.

- Öykünücüsünün diğer Tüm Hyper-V örneklerini kaldırın.

    1. Visual Studio’yu kapatın.

    2. Hyper-V Yöneticisi'ni açın ve zaten çalışan ve bozuk durumda Emulator sanal makinelerin (Sanal Makineler) Hyper-V örneklerini durdurun.

    3. Hyper-V Yöneticisi'nde diğer öykünücü VM'leri silin.

    4. Makinenizi yeniden başlatın.

- En az 4 GB sistem belleğine sahip olduğundan ve bunun yoğun kaynak kullanımı olan diğer programlar ve işlemler tarafından tüketilmemesi (örneğin, tarayıcı pencerelerini kapatmayı deneyin) emin olun.

- Hyper-V Yöneticisi'nde Sanal Anahtar Yöneticisi'ni açın ve iki ağ anahtarına sahip olup olamayabilirsiniz; birinci anahtarın iç anahtar, ikinci anahtarın ise dış anahtar olduğunu doğrulayın.

     ![Hyper-V Yöneticisi'nde Sanal Anahtar Yöneticisi'nin ekran görüntüsü. Yeni bir sanal anahtar vurgulanmış ve özellikleri bunun bir dış ağ anahtarı olduğunu gösterir.](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Kurulum yanlışsa ve Windows 10 kullanıyorsanız [netcfg -d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) komutunu kullanarak ağ cihazlarını yeniden yüklemeyi denemeniz gerekebilir (bölüm 6).

- Bu adımlar sorunu çözmezse, [öykünücüye](#NoStart) engel Emulator üçüncü taraf yazılım hakkında bilgi için bkz. Emulator başlatılamayamaz (ilk kullanım).

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a>Emulator başlatıla (ilk kullanım)
 Öykünücü başlamazsa, sorunu tanımlamak ve düzeltmek için aşağıdaki görevleri gerçekleştirin.

- En düşük donanım gereksinimlerinin karşı olduğundan ve BIOS ayarlarının doğru olduğundan emin olun.

   Hyper-V Emulator ve Windows 8, İkinci Düzey Adres Çevirisi (SLAT) ile 64 bit işlemci gerektirir. Intel için çekirdek i3, i5 veya i7 işlemciye (veya birçok Xeon'a) ihtiyacınız vardır. AMD yongalarının listesini burada [edinebilirsiniz.](https://www.amd.com/en/support)

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

     - NX (yürütme yok) (AMD); Bu, etkin olmalıdır.

  4. BIOS 'ta aşağıdaki seçenekler varsa, bunları devre dışı bırakın.

     - Intel VT-d 'yi devre dışı bırak

     - Güvenilen yürütmeyi devre dışı bırak

       Daha fazla bilgi için şu makaleye bakın: TechNet: Hyper-V: Hyper-V ' yi etkinleştirme BIOS hataları nasıl düzeltilir

  5. En az 4 GB sistem belleğinizin olduğundan ve Kaynak yoğunluklu diğer programlar ve süreçler tarafından tüketilmediğinden emin olun.

  6. Windows 8 Professional veya daha iyi çalıştırdığınızdan emin olun (Windows Server 2008 desteklenmez). Windows Server 2012 desteklenir, ancak masaüstü deneyimini etkinleştirmeniz gerekir.

     Herhangi bir hiper yönetici hatası olup olmadığını görmek için Olay Görüntüleyicisi inceleyebilirsiniz. bunu yapmak için Olay Görüntüleyicisi açın (**anahtar** + **R**'yi başlatın, sonra yazın `eventvwr` ) ve sonra **Windows günlükler**, **sistem**' i seçin. Ardından, günlüğü olay kaynağına göre filtreleyin, kaynağı **Hyper-V-hiper yönetici** olarak ayarlar. Kök nedeni belirlemenize yardımcı olması için hata olup olmadığını denetleyin.

     İşlemcinizin en düşük gereksinimleri karşılaması ancak hiper yönetici hala başarısız olursa, bilgisayarınız için bir BIOS yükseltmesi olup olmadığını bulmayı göz önünde bulundurun. Bir tane varsa ve yükseltmeyi seçerseniz, BIOS 'U yükseltirken üreticiden tüm önlemleri gözlemlediğinizden emin olun (BIOS üretici yazılımı yükseltmesinin, BIOS 'un kalıcı olarak bozulmasına neden olabilecek bir güç kaybı nedeniyle kesilmediğinden emin olma gibi).

- En az 4 GB sistem belleğinizin olduğundan ve Kaynak yoğunluklu diğer programlar ve süreçler tarafından tüketilmediğinden emin olun.

- Sanal ağ ile müdahale eden üçüncü taraf sürücüleri veya yazılımları kaldırın/devre dışı bırakın.

   Hyper-V ağ yığınına tamamen uyumlu olmayan ağ sürücüleri/protokolleri gibi Windows 8 altında yüklü bazı üçüncü taraf ürünlerle ilgili bazı bilinen sorunlar vardır.

   genel olarak, bu ürünlerin geliştiricilerine Windows 8 ve Hyper-V ile uyumlu olacak şekilde güncelleştirilmesi gerekir.

   aşağıdaki ürünler Windows 8 uyumluluk için yükseltme gerektirebilir: virtualbox, Virtual PC 7, VMWare, bazı VPN istemcileri, yazılım güvenlik duvarları, Cisco VPN istemcilerinin bazı sürümleri ve diğer sanallaştırma sistemleri. şüpheli sanallaştırma yazılımının geliştiriciyle birlikte çalışarak, Windows 8 ve Hyper-V ' d e uyumlu hale getirmek üzere yazılımı yükseltmesine teşvik edin.

   geçici bir *çözüm* olarak, Visual Studio iletişim kurmak için Emulator tarafından kullanılan sanal ağla kesintiye uğraabilecek tüm üçüncü taraf sürücüleri ve uygulamaları devre dışı bırakabilirsiniz. Bu uygulamalar şunlar olabilir:

  - Virüsten koruma uygulamaları (ağ yığınına kanca)

  - Ağ izleme araçları

  - Ağ günlüğü araçları

  - Diğer sistem izleme yazılımı

    Bu olası bir geçici çözüm olan, söz konusu ürünlerin (ve güncelleştirilmiş bir sürümü serbest bırakmaya yönelik ürün geliştiricisinin) kaldırılmasından kısa bir süre için aşağıdaki adımları gerçekleştirmeniz gerekir.

  1. Ağ bağlantıları Yöneticisini başlatın (Başlangıç ekranından, `View Network Connections` ağ bağlantılarını görüntülemek için yazın ve bu seçeneği belirleyin.)

  2. vethernet (iç Ethernet bağlantı noktası Windows Phone Emulator iç anahtar) bağdaştırıcısı için bağlam menüsünden **özellikler** ' i seçin.

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

     üçüncü taraf ürünleri kaldırdıktan sonra, Windows Phone iç anahtarı Emulator geri yüklemeniz gerekebilir. Bunu gerçekleştirmek için:

  - Hyper V ' i açın ve sanal anahtar Yöneticisi ' ne gidin. "Windows Phone Emulator iç anahtarı" adlı bir sanal anahtar oluşturun ve bağlantı türünü **iç ağ** olarak ayarlayın.

     ![Sanal Anahtar Yöneticisi](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Şimdi öykünücüsü başlatın. Çalışması gerekir.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a>Emulator yüklendikten sonra bilgisayar önyükleme yapamıyor
 Bu sorun, aşağıdaki koşullar doğru olduğunda oluşabilir:

- Bilgisayarınızda gigabayt ana kartı bulunur.

- USB3, anakart üzerinde etkindir.

  Bu sorunu çözmek için, ana kartın BIOS ayarlarında USB3 devre dışı bırakın ve bilgisayarı yeniden başlatın. Ardından, gigabayttan kartın BIOS 'U için bir güncelleştirme yayımlamışsa emin olun.

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a>Visual Studio, uygulamayı öykünücüye dağıtmaya çalışıyor veya öykünücü diğer ıdes 'te hata ayıklama hedefi olarak görünmüyor
 Öykünücü çalışıyorsa, ancak ADB 'ye (Android Debug Bridge) bağlı görünmüyor veya ADB (örneğin, Android Studio veya tutulma) kullanan Android araçları 'nda görünmüyorsa, öykünücüsünün ADB 'yi nerede aradığı üzerinde ayarlamanız gerekebilir. Öykünücü, Android SDK temel konumunu tanımlamak için bir kayıt defteri anahtarı kullanır ve bu dizin altında \platform-tools\adb.exe dosyasını arar. Öykünücü tarafından kullanılan Android SDK yolunu değiştirmek için:

- Başlat düğmeleri bağlam menüsünden **Çalıştır** ' ı seçerek Kayıt Defteri Düzenleyicisi 'ni açın, `regedit` iletişim kutusuna yazın ve **Tamam**' ı seçin.

- Soldaki klasör ağacında *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools* gidin.

- **Yol** kayıt defteri değişkenini Android SDK yolu ile eşleşecek şekilde değiştirin.

  Öykünücüyü yeniden başlatın ve şimdi ADB ve ilişkili Android araçlarına bağlı olan öykünücüyü görmeniz gerekir.

## <a name="emulator-stops-responding-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a>Emulator UDP bağlantı noktasını ayarlayamadığından yanıt vermeyi durduruyor
 Xamarin Player ile uyumsuzluk nedeniyle bu sorunla karşılaşabilirsiniz. Öykünücü yanıt vermeyi durdur olarak görünüyorsa veya bu hata iletisini görürseniz, "öykünücü cihaz işletim sistemine bağlanamıyor: UDP bağlantı noktası ayarlanamadı.  Bazı işlevler devre dışı bırakılabilir ", bu sorunu yaşıyor olabilirsiniz. Aşağıdaki adımları uygulayın.

1. Xamarin Player 'ı kaldırın.

2. Sanal kutunun kaldırıldığını doğrulayın (Xamarin Player, sanal kutudan en üstünde çalışır).

3. Cihaz Yöneticisi ' ne gidin, gizli cihazları gösterme seçeneğini belirleyin ve ardından fiziksel ağ kartları dışındaki her şeyi silin.

4. Fiziksel olmayan ağ bağdaştırıcılarını kaldırdıktan sonra, Hyper-V ' yi kaldırmayı/yeniden yüklemeyi deneyebilirsiniz.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a> Hata ayıklayıcı bir Xamarin projesine iliştirilemiyor
 ıntel ufuk gölü işlemcilerle Windows 10 çalıştırıyorsanız, Xamarin uygulamaları öykünücüsünde çalışmayabilir veya Visual Studio hata ayıklayıcı bunlara iliştirilemeyebilir. Bunun nedeni, Hyper-V ve ufuk Gölü işlemcileriyle ilgili bir sorundur. Geçici bir çözüm olarak aşağıdaki adımları uygulayın.

1. Hyper-V Yöneticisi 'Ni açın ve kullanmakta olduğunuz öykünücü profili için VM 'yi seçin.

2. **Kaydedilmiş durumu Sil** (sağ alt) seçeneğini belirleyin.

3. **Ayarlar seçin...**

4. İşlemci düğümünü genişletin ve **Uyumluluk**' i seçin.

5. **Farklı bir işlemci sürümü olan fiziksel bir bilgisayara geçişi** etkinleştirin.

6. Hizmeti yeniden başlatın ( **Eylemler** altında) ve yeniden deneyin.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emulator Google Play Hizmetleri kullanan uygulamayı çalıştıramazsa
 Öykünücü, Google Play Hizmetleri kitaplıklarıyla birlikte gelmez. Ancak öykünücü, düz ZIP dosyalarını sürükleyip bırakma yüklemesini destekler.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a> Dosya, APK veya bıraktığınızda ZIP dosyası için sürükle ve bırak çalışmıyor
 Öykünücü, bir dosyayı sürükleyip ekrana bıraktığınızda dosya aktarımını kolaylaştırmak için ADB.exe kullanır. Bir dosyayı sürükleyip bırakmaya çalıştığınızda bir hatayla karşılaşırsanız, bu büyük olasılıkla öykünücüsünün ADB.exe bağlı olmadığını gösterir. sorunu çözmek için [Visual Studio, uygulamayı öykünücüsüne dağıtmaya çalışırken takılırken veya öykünücü diğer ıdes 'te hata ayıklama hedefi olarak görünmediğinden](#ADB), ' daki adımları izleyin.

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a> Ekran görüntüsünün çözümlenmesi yanlış
 **Ek araçlar** penceresinde ekran görüntüsü sekmesini kullanarak bir ekran görüntüsü alırsanız ve sonuçta elde edilen görüntü beklenmeyen bir Boyutladır, **yakalama**'yı seçmeden önce ekranın yakınlaştırma düzeyini ayarlamanız gerekebilir. Öykünücü ekran görüntülerini ana bilgisayar izleyicinizdeki ekran çözünürlüğünde alır.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emulator OpenGL içeriğini işleyemeyebilir
 Öykünücü, ana bilgisayar makinenizin GPU 'SU kullanılarak OpenGL içeriği işler ve bu çağrıları DirectX 'e ve DirectX 'e dönüştürmek için AÇıLı projeyi kullanır. Uygulamanız bir cihazda düzgün şekilde çalışıyorsa, ancak öykünücüsünde yanlış bir OpenGL çağrısını (örneğin, eşleşmeyen gölgelendirici değişkenlerini kullanarak) azaltılmış olabilir.

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a>Emulator, çok dokunmalı hareketlere yanıt vermez
 Bazı durumlarda, öykünücü dokunma etkin görüntüinizden doğrudan etkileşim aracılığıyla ya da öykünücü araç çubuğundaki çok dokunmalı aracı kullanarak çok dokunmadan başlar ve yanıt vermez. Bu durumda, öykünücü araç çubuğunda **Döndür** düğmesini seçin ve çoklu Touch 'ı kullanmayı deneyin. sorun devam ederse, [OpenGL içerik sorununu işlemek Emulator](#OpenGL) okuyun.

## <a name="support-resources"></a><a name="Support"></a> Destek kaynakları
 Ana bilgisayarınız sistem gereksinimlerini karşılamıyorsa ve bu sorun giderme kılavuzunda yer alan bir sorunla karşılaşırsanız:

- stackOverflow'da [android-emulator ve visual-studio](https://stackoverflow.com/questions/tagged/android-emulator) etiketlerini kullanarak bir soru sorun.

- Visual Studio veya Emulator Manager'da Gülümseme Gönder aracını kullanarak bir Emulator bildirme.
