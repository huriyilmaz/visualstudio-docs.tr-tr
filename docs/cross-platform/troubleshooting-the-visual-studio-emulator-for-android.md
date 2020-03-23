---
title: Android için Visual Studio Emülatör Sorun Giderme | Microsoft Dokümanlar
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
ms.openlocfilehash: 85a7748f25e284a7c746d5779b3d177a15e1d37b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272078"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
Bu konu, Android için Visual Studio Emülatörü kullanırken karşılaşabileceğiniz sorunları çözmenize yardımcı olacak bilgiler içerir.

> [!WARNING]
> Emülatör yüklendiğinde, kurulum programı yazılımı çalıştırmak için ön koşulları denetler. Ön koşullar yoksa uyarıları görüntüler, ancak yükleme için gerekli değildir.

 Bu konuda aşağıdaki bölümler yer almaktadır.

- [Başlamadan önce](#BeforeYouStart)

- [Emülatör yüklemek için başarısız](#NoInstall)

- [Etki alanı veya şirket ağındaki ağ hedeflerine bağlanamıyor](#DomainNetwork)

- [Ağ ayarları el ile yapılandırma gerektirdiğinde ağ hedeflerine bağlanamıyor](#ManualNetworkConfig)

- [Emülatör yavaş başlar, zaman acısı nedeniyle başlayamazsa veya uygulama dağıtımı başarısız olur](#SlowStart)

- [Emülatör başlatılmaz](#NoStart2)

- [Emülatör başlatılmaz (ilk kullanım)](#NoStart)

- [Bilgisayar Emülatör yükledikten sonra önyükleme başarısız](#NoBoot)

- [Visual Studio uygulamayı emülatöre dağıtmaya çalışırken takılıp kalır veya emülatör diğer IDA'larda hata ayıklama hedefi olarak görünmez](#ADB)

- [UDP bağlantı noktasını kuramadığı için emülatör asılı](#XamarinPlayer)

- [Xamarin projesine hata ayıklayıcı ekleyemez](#Skylake)

- [Emülatör, Google Play Hizmetleri kullanan uygulamayı çalıştıramıyor](#GooglePlay)

- [Bir dosyanın sürükle ve bırak, APK veya yanıp sönebilir zip dosyası çalışmıyor](#DragAndDrop)

- [Ekran görüntüsünün çözünürlüğü yanlış](#Resolution)

- [Emülatör OpenGL içeriğini işletemedi](#OpenGL)

- [Emülatör çoklu dokunma hareketlerine yanıt vermez](#Multitouch)

- [Destek kaynakları](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a>Başlamadan önce
 Sorun gidermeye başlamadan önce aşağıdaki konuları gözden geçirmek yararlı olabilir:

- [Android için Visual Studio Emülatörü için sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a>Emülatör yüklemek için başarısız
 Hyper-V yüklü yoksa, emülatör yüklemeyi çalıştığınızda aşağıdaki iletiyi görürsünüz. HyperV'yi destekleyen bir makineniz olmalı ve bu makine etkinleştirilmelidir.

 ![Android&#95;Emu&#95;&#95;Sorunu Yükleyin](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Bu ileti hem Android için Visual Studio Emülatörü hem de Windows Phone Emülatörü için geçerlidir. Windows 8.1 ve Windows 10 emülatör desteği.

 Bu iletiyi görürseniz, emülatörçalıştırıp çalıştıramayacağınızı görmek [için Android için Visual Studio Emülatörü'nün Sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) kontrol edin.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a>Etki alanı veya şirket ağındaki ağ hedeflerine bağlanamıyor
 Android için Visual Studio Emülatörü ağda kendi IP adresine sahip ayrı bir aygıt olarak görünür. Bir Windows etki alanına katılmaz ve etki alanı veya çalışma grubu kimlik bilgilerini ana bilgisayarla paylaşmaz.

 Ağınız temel ağ ve Internet bağlantısı için etki alanı veya çalışma grubu yetkilendirmesi gerektiriyorsa, bir özel durum için BT yöneticinize başvurun. Bu özel durum, geliştirme bilgisayarınızın bir sınır makinesi olarak hizmet etmesine ve emülatör gibi etki alanına katılmayan ağ aygıtlarından gelen bağlantıları kabul etmesine olanak tanır.

 Android için Visual Studio Emülatörü de MAC adresleri kendi kümesini kullanır. Emülatörden ağ veya Internet kaynaklarına erişemiyorsanız, emülatörün MAC adreslerinin ağınızda yetkilendirilip yetkilendirildiğinden emin olmak için BT yöneticinize danışın.

#### <a name="to-view-the-emulators-mac-addresses"></a>Emülatörün MAC adreslerini görüntülemek için

1. Emülatöre ateşle.

2. Emülatör araç çubuğunda, Ek Araçlar penceresini açmak için köşeli ayraç düğmesini (>>) tıklatın.

3. Ek Araçlar penceresinde Ağ sekmesini tıklatın.

4. Ağ sayfasında Fiziksel adres girişlerini bulun.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a>Ağ ayarları el ile yapılandırma gerektirdiğinde ağ hedeflerine bağlanamıyor
 Emülatörden ağ hedeflerine bağlanmak için ağınızın aşağıdaki gereksinimleri karşılaması gerekir:

- Dhcp. Emülatör, kendisini ağüzerinde kendi IP adresine sahip ayrı bir aygıt olarak yapılandırdığı için DHCP gerektirir.

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları. DNS ve ağ geçidi ayarlarını emülatör için el ile yapılandırmak mümkün değildir.

  Ağınız el ile yapılandırılmış ayarlar gerektiriyorsa, emülatör için ağ bağlantısını nasıl etkinleştirebileceğinizi belirlemek için BT yöneticinize danışın.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a>Emülatör yavaş başlar, zaman acısı nedeniyle başlayamazsa veya uygulama dağıtımı başarısız olur
 Belirli koşullar altında, emülatörbaşlatmak için birkaç dakika sürer veya bir zaman acısı nedeniyle başlatmak için başarısız olur. Emülatör başlatıldığında aşağıdaki iletiyi görürsünüz: `App deployment failed. Please try again`. Aşağıdaki koşullar bu hataya neden olabilir.

- Önyüklemeli bir VHD'den Android için Visual Studio Emülatörü çalıştırın. Bu yapılandırma desteklenmez.

- Hatalı bir sabit disk. CHKDSK programını çalıştırmayı düşünün.

- Parçalanması gereken bir sabit disk. Sürücünün parçalanmasını düşünün.

- Neredeyse dolu bir sabit disk. Sürücüde bulunan alanı kontrol edin.

- Çalışan diğer uygulamalar nedeniyle yeterli bellek kullanılamaz. Bellek tüketen uygulama sayısını azaltın veya bellek miktarını artırın.

- Genellikle, sistemde kötü performans katkıda bulunan herhangi bir faktör. Denetim Masası'nın Performans Bilgileri ve Araçları sayfasında bulabileceğiniz Windows Deneyim Dizini'ndeki en düşük alt puana sahip bileşenle sorun gidermeye başlayın.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Emülatör başlatılmaz
 Emülatör daha önce çalışıyorsa, ancak şimdi çalışmıyorsa, aşağıdaki görevleri gözden geçirin. Emülatör'ü ilk kez kullanıyorsanız, bu adımları denemeden önce [Emülatör'ün başlatılamamasına (ilk kullanım)](#NoStart) bakın.

- Emülatörün diğer Hyper-V örneklerini kaldırın.

    1. Visual Studio’yu kapatın.

    2. Hyper-V Manager'ı açın ve emülatörün (Sanal Makineler) zaten çalışan ve muhtemelen bozuk durumda olan Hyper-V örneklerini durdurun.

    3. Hyper-V Manager'da diğer emülatör VM'leri silin.

    4. Makinenizi yeniden başlatın.

- En az 4 GB sistem belleğine sahip olduğundan ve kaynak yoğun diğer programlar ve işlemler tarafından tüketilmediğinden emin olun (örneğin, tarayıcı pencerelerini kapatmayı deneyin).

- Hyper-V Manager'da Sanal Anahtar Yöneticisi'ni açın ve iki ağ anahtarınız olup olmadığını kontrol edin; ilkinin iç anahtar, ikincisinin harici olduğunu doğrulayın.

     ![Android&#95;Emu&#95;V&#95;Anahtarı&#95;Adam](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Kurulum yanlışsa ve Windows 10 kullanıyorsanız, [netcfg -d komutunu kullanarak ağ aygıtlarını yeniden yüklemeyi](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) deneyebilirsiniz (bölüm 6).

- Bu adımlar sorunu çözmezse, [bkz.](#NoStart)

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a>Emülatör başlatılmaz (ilk kullanım)
 Emülatör başlamazsa, sorunu tanımlamak ve düzeltmek için aşağıdaki görevleri gözden geçirin.

- Minimum donanım gereksinimlerinin karşılanıp BIOS ayarlarının doğru olduğundan emin olun.

   Emülatör ve Windows 8 Hyper-V, İkinci Düzey Adres Çevirisi (SLAT) içeren 64 bit işlemci gerektirir. Intel için, aslında bir Core i3, i5 veya i7 işlemci (veya birçok Xeons biri) gerekir. AMD yongalarının bir listesini [burada](https://www.amd.com/en/support)bulabilirsiniz.

  1. Bilgisayarınızın [sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)karşıladığından emin olun.

  2. [SLAT aracının](https://slatstatuscheck.codeplex.com/) bilgisayarınızın SLAT yeteneğine sahip olduğunu bildirdiğini doğrulayın.

  3. Bilgisayarınızın BIOS ayarları nda, tüm sanallaştırma teknolojisinin etkin olduğundan emin olun. Tam BIOS açıklamaları her donanım üreticisi için değişebilir. Genel olarak, ilgili özellikleri etkinleştirin:

     - SLAT (İkinci Düzey Adres Çevirisi)

     - EPT (Genişletilmiş Sayfa Tabloları) (Intel)

     - NPT (İç içe Sayfa Tabloları) (AMD)

     - RVI (Hızlı Sanallaştırma Dizinoluşturma) (AMD)

     - VMX (donanım destekli sanallaştırma desteğini gösteren bir Intel kısaltması)

     - SVM (donanım destekli sanallaştırma desteğini gösteren bir AMD kısaltması)

     - XD (Execute Devre Dışı) (Intel); bu etkin olmalıdır

     - NX (Yürütme Yok)(AMD); bu etkin olmalıdır.

  4. BIOS'ta aşağıdaki seçenekler varsa, bunları devre dışı bırakın.

     - Intel VT-d'yi devre dışı

     - Güvenilir Yürütmeyi Devre Dışı

       Daha fazla bilgi için şu makaleye bakın: Technet: Hyper-V: Hyper-V'yi Etkinleştiren BIOS Hataları Nasıl Düzeltilir?

  5. En az 4 GB sistem belleğine sahip olduğundan ve kaynak yoğun diğer programlar ve işlemler tarafından tüketilmediğinden emin olun.

  6. Windows 8 Professional veya daha iyi çalıştırdığınızdan emin olun (Windows Server 2008 desteklenmez). Windows Server 2012 desteklenir, ancak Masaüstü Deneyimi'ni etkinleştirmeniz gerekir.

     Hypervisor hataları olup olmadığını görmek için Olay Görüntüleyicisi'ni inceleyebilirsiniz. Bunu yapmak için Olay Görüntüleyicisi'ni `eventvwr`açın ( Başlat**tuşu**+**R**, sonra yazın ) ve ardından Windows **Günlükleri,** **Sistem'i**seçin. Ardından, kaynağı **Hyper-V-Hypervisor**olarak ayarlayarak günlük leri olay kaynağına göre filtreleyin. Kök nedeni belirlemeye yardımcı olmak için hataları denetleyin.

     İşlemciniz minimum gereksinimleri karşılıyorsa ancak hipervizör hala arızadurumundaysa, bilgisayarınız için kullanılabilir bir BIOS yükseltmesi olup olmadığını öğrenin. Varsa ve yükseltmeyi seçerseniz, BIOS'u yükseltirken üreticiden gelen tüm önlemleri gözlemlediğinizden emin olun (örneğin, BIOS firmware yükseltmesinin BIOS'u kalıcı olarak bozabilecek bir güç kaybıyla kesintiye uğramamasını sağlamak gibi).

- En az 4 GB sistem belleğine sahip olduğundan ve kaynak yoğun diğer programlar ve işlemler tarafından tüketilmediğinden emin olun.

- Sanal ağa müdahale eden üçüncü taraf sürücüleri veya yazılımı kaldırın/devre dışı kaldırın.

   Windows 8'in altında yüklü olan bazı 3.

   Genel olarak, windows 8 ve Hyper-V ile uyumlu olacak şekilde yazılımlarını güncellemek bu ürünlerin geliştiricileri kadar olacaktır.

   Aşağıdaki ürünler Windows 8 uyumluluğu için yükseltme gerektirebilir: VirtualBox, Virtual PC 7, VMWare, bazı VPN istemcileri, yazılım güvenlik duvarları, Cisco VPN istemcilerinin bazı sürümleri ve diğer sanallaştırma sistemleri. Windows 8 ve Hyper-V ile uyumlu hale getirmek için yazılımı yükseltmeleri için onları teşvik etmek için şüpheli sanallaştırma yazılımının geliştiricisi ile çalışın.

   Geçici *çözüm*olarak, Visual Studio ile iletişim kurmak için Emülatör tarafından kullanılan sanal ağa müdahale eden tüm üçüncü taraf sürücüleri ve uygulamaları devre dışı kullanabilirsiniz. Bu uygulamalar şunları içerebilir:

  - Virüsten koruma uygulamaları (ağ yığınına kanca)

  - Ağ izleme araçları

  - Ağ günlüğü araçları

  - Diğer sistem izleme yazılımı

    Söz konusu ürünü (ler) kaldırmanın (ve ürün geliştiricisinin güncelleştirilmiş bir sürümü serbest bırakmasından istenmesi) kısa olan başka bir olası geçici çözüm, aşağıdaki adımları atmaktır.

  1. Ağ Bağlantıları yöneticisini başlatın (Başlangıç `View Network Connections` ekranından ağ bağlantılarını görüntülemek için bu seçeneği yazın ve seçin.)

  2. vEthernet (Internal Ethernet PortU Windows Phone Emulator Internal Switch) bağdaştırıcısı için bağlam menüsünden **Özellikler'i** seçin.

      ![Hyper&#45;V tarafından kullanılan Sanal Adaptör](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Bağdaştırıcı özellikleri burada gösterilmiştir.

      ![Sanal Bağdaştırıcı Özellikleri](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Bu bağdaştırıcı **için, Bu bağlantı** altında seçilmesi gereken tek öğe aşağıdaki öğeleri kullanmalıdır:

     - Microsoft Ağları için İstemci

     - QoS Paket Zamanlayıcısı

     - Microsoft Ağları için Dosya ve Yazıcı Paylaşımı

     - Microsoft LLDP Protokol Sürücüsü

     - Bağlantı Katmanı Topoloji Si bulma Mapper I/O Sürücüsü

     - Bağlantı Katmanı Topoloji Discovery Responder

     - Internet Protokolü Sürüm 6 (TCP/IPv6)

     - Internet Protokolü Sürüm 4 (TCP/IPv4)

  4. Diğer öğelerin select'ini seçin.

     Bu tekniği kullanmanın dezavantajı, yeni bir üçüncü taraf ürün desteklenmeyen sürücüleri yüklediğinizde veya emülatör yüklendiğinde bu adımların yinelenmesi gerekeceğidir.

     Üçüncü taraf ürünleri yükledikten sonra Windows Phone Emülatör Dahili Anahtarı'nı geri yüklemeniz gerekebilir. Bunu gerçekleştirmek için:

  - Hyper V'yi açın ve Sanal Anahtar Yöneticisi'ne gidin. "Windows Phone Emülatör Dahili Anahtar" adlı sanal bir anahtar oluşturun ve bağlantı türünü **Dahili ağa**ayarlayın.

     ![Sanal Anahtar Yöneticisi](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Şimdi emülatör başlatın. İşe yaramalı.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a>Bilgisayar Emülatör yükledikten sonra önyükleme başarısız
 Aşağıdaki koşullar doğru olduğunda bu sorun oluşabilir:

- Bilgisayarınızda Gigabyte anakartı var.

- USB3 anakartta etkindir.

  Bu sorunu çözmek için, anakartın BIOS ayarlarında USB3'ü devre dışı bırakıp bilgisayarı yeniden başlatın. Sonra Gigabyte anakart BIOS için bir güncelleştirme yayımladı olup olmadığını kontrol edin.

  Daha fazla bilgi için aşağıdaki Bilgi Bankası makalesine bakın: [Gigabyte sistemlerinde Hyper-V rolünün yüklenmesinden sonra önyükleme hatası.](https://support.microsoft.com/en-us/kb/2693144)

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a>Visual Studio uygulamayı emülatöre dağıtmaya çalışırken takılıp kalır veya emülatör diğer IDA'larda hata ayıklama hedefi olarak görünmez
 Emülatör çalışıyorsa, ancak ADB'ye (Android Hata Ayıklama Köprüsü) bağlı görünmüyorsa veya ADB'den (örneğin, Android Studio veya Eclipse) kullanan Android araçlarında görünmüyorsa, emülatörün ADB'yi aradığı yeri ayarlamanız gerekebilir. Emülatör, Android SDK'nızın temel konumunu belirlemek için bir kayıt defteri anahtarı kullanır ve bu dizinin altındaki \platform-tools\adb.exe dosyasını arar. Emülatör tarafından kullanılan Android SDK yolunu değiştirmek için:

- Başlat düğmeleri bağlam menüsünden **Çalıştır'ı** seçerek, `regedit` iletişim kutusuna yazarak ve **Tamam'ı**seçerek Kayıt Defteri Düzenleyicisi'ni açın.

- Soldaki klasör ağacında *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Araçları'na* gidin.

- **Yol** kayıt defteri değişkenini Android SDK'nuzun izle eşleşecek şekilde değiştirin.

  Emülatöryeniden başlatın ve şimdi ADB ve ilişkili Android araçlarına bağlı emülatör görmek gerekir.

## <a name="emulator-hangs-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a>UDP bağlantı noktasını kuramadığı için emülatör asılı
 Xamarin Player ile uyumsuzluk nedeniyle bu sorunu yaşayabilirsiniz. Emülatör askıda görünüyorsa veya bu hata iletisini görüyorsanız, "Emülatör aygıt işletim sistemine bağlanamıyor: UDP bağlantı noktasını ayarlayamıyor.  Bazı işlevler devre dışı bırakılmış olabilir", bu sorunla karşılaşabilirsiniz. Aşağıdaki adımları atın.

1. Xamarin Player'ı kaldırın.

2. Sanal kutunun kaldırıldığını doğrulayın (Xamarin Player sanal kutunun üstünde çalışır).

3. Aygıt yöneticisine gidin, gizli aygıtları gösterme seçeneğini seçin ve ardından fiziksel ağ kartları dışındaki her şeyi silin.

4. Fiziksel olmayan ağ bağdaştırıcılarını kaldırdıktan sonra Hyper-V'yi kaldırmayı/yeniden yüklemeyi deneyebilirsiniz.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a>Xamarin projesine hata ayıklayıcı ekleyemez
 Windows 10'u Intel Skylake işlemcilerle çalıştırıyorsanız, Xamarin uygulamaları emülatörde çalışmayabilir veya Visual Studio hata ayıklayıcısı bunlara bağlanmayabilir. Bu Hyper-V ve Skylake işlemciler ile ilgili bir sorun kaynaklanmaktadır. Geçici çözüm olarak aşağıdaki adımları izleyin.

1. Hyper-V Manager'ı açın ve kullandığınız emülatör profili için VM'yi seçin.

2. **Kayıtlı Durumu Sil'i** seçin (sağ altta).

3. **Ayarlar'ı seçin...**

4. İşlemci düğümini genişletin ve **Uyumluluk'u**seçin.

5. **Farklı işlemci sürümüne sahip fiziksel bir bilgisayara Geçir'i**etkinleştirin.

6. Hizmeti yeniden başlatın **(Eylemler**altında) ve yeniden deneyin.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emülatör, Google Play Hizmetleri kullanan uygulamayı çalıştıramıyor
 Emülatör, Google Play Hizmetleri için kitaplıklarla birlikte göndermeyapmaz. Ancak, emülatör yanıp sönen zip dosyalarının sürükle ve bırak yüklemesini destekler.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a>Bir dosyanın sürükle ve bırak, APK veya yanıp sönebilir zip dosyası çalışmıyor
 Emülatör, bir dosyayı sürükleyip ekrana bıraktığınızda dosya aktarımını kolaylaştırmak için ADB.exe kullanır. Bir dosyayı sürüklemeye ve düşürmeye çalıştığınızda bir hatayla karşılaşırsanız, bu büyük olasılıkla emülatörün ADB.exe'ye bağlı olmadığını gösterir. Çözmek için, Visual Studio'daki adımları izleyin uygulamayı [emülatöre dağıtmaya çalışırken takılıp kalır veya emülatör diğer IDA'larda hata ayıklama hedefi olarak görünmez.](#ADB)

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a>Ekran görüntüsünün çözünürlüğü yanlış
 **Ek Araçlar** penceresinde ekran görüntüsü sekmesini kullanarak bir ekran görüntüsü alırsanız ve ortaya çıkan görüntü beklenmeyen boyuttaysa, **Yakalama'yı**seçmeden önce ekranın yakınlaştırma düzeyini ayarlamanız gerekebilir. Emülatör, ana bilgisayar monitörünüzdeki ekranın çözünürlüğünde ekran görüntüleri alır.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emülatör OpenGL içeriğini işletemedi
 Emülatör, opengl içeriğini ana makinenizin GPU'unu kullanarak işler ve bu aramaları DirectX'e dönüştürmek için ANGLE projesini kullanır. Uygulamanız bir aygıtta doğru işlerken ancak emülatörde yanlış bir şekilde işlerse, aygıtın yanlış bir OpenGL çağrısını azaltması olasıdır (örneğin, eşleşmeyen gölgeli değişkenler kullanır).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a>Emülatör çoklu dokunma hareketlerine yanıt vermez
 Bazı durumlarda, emülatör, dokunmatik özellikli ekranınızdan doğrudan etkileşim yoluyla veya emülatör araç çubuğundaki Multi-Touch Aracı'nı kullanarak çoklu dokunmaya başlar ve yanıt vermez. Bu durumda, emülatör araç çubuğundaki **Döndür** düğmesini seçin ve çoklu dokunmayı yeniden kullanmayı deneyin. Sorun devam ederse, [Emülatör'ün OpenGL içerik](#OpenGL) sorununu oluşturmamasını okuyun.

## <a name="support-resources"></a><a name="Support"></a>Destek kaynakları
 Ana bilgisayarınız sistem gereksinimlerini karşılıyorsa ve bu sorun giderme kılavuzunda yer almayan bir sorunla karşılaşırsanız:

- [Android emülatörü](https://stackoverflow.com/questions/tagged/android-emulator) ve görsel stüdyo etiketlerini kullanarak StackOverflow hakkında soru sorun.

- Visual Studio'da veya Emülatör Yöneticisi'nde Gülümseme Gönder aracını kullanarak bir sorunu bildirin.
