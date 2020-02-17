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
ms.openlocfilehash: 85a7748f25e284a7c746d5779b3d177a15e1d37b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272078"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Android için Visual Studio Öykünücüsü’nde Sorun Giderme
Bu konu, Android için Visual Studio öykünücüsü 'nü kullanırken karşılaşabileceğiniz sorunları çözmenize yardımcı olacak bilgiler içerir.

> [!WARNING]
> Öykünücü yüklendikten sonra Kurulum programı yazılımı çalıştıran önkoşulları denetler. Önkoşulları mevcut değildir, ancak bunları yükleme için gerekli olmadığı uyarıları görüntüler.

 Bu konuda aşağıdaki bölümleri içerir.

- [Başlamadan önce](#BeforeYouStart)

- [Öykünücü yüklenemiyor](#NoInstall)

- [Bir etki alanı veya şirket ağındaki ağ hedeflerine bağlanılamıyor](#DomainNetwork)

- [Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflerine bağlanılamıyor](#ManualNetworkConfig)

- [Öykünücü yavaş başlıyor, zaman aşımı nedeniyle başlatılamaz veya uygulama dağıtımı başarısız olur](#SlowStart)

- [Öykünücü başlatılamadı](#NoStart2)

- [Öykünücü başlatılamadı (ilk kullanım)](#NoStart)

- [Öykünücü yüklendikten sonra bilgisayar önyükleme yapamıyor](#NoBoot)

- [Visual Studio, uygulamayı öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer Ides 'te hata ayıklama hedefi olarak görünmüyor](#ADB)

- [Öykünücü, UDP bağlantı noktasını ayarlayamadığından askıda kalıyor](#XamarinPlayer)

- [Hata ayıklayıcı bir Xamarin projesine iliştirilemiyor](#Skylake)

- [Öykünücü Google Play Hizmetleri kullanan uygulamayı çalıştıramıyor](#GooglePlay)

- [Dosya, APK veya bıraktığınızda ZIP dosyası için sürükle ve bırak çalışmıyor](#DragAndDrop)

- [Ekran görüntüsünün çözümlenmesi yanlış](#Resolution)

- [Öykünücü OpenGL içeriğini işlemesini başaramazsa](#OpenGL)

- [Öykünücü çok dokunmalı hareketlere yanıt vermiyor](#Multitouch)

- [Destek kaynakları](#Support)

## <a name="BeforeYouStart"></a>Başlamadan önce
 Sorun gidermeye başlamadan önce aşağıdaki konuları gözden geçirmeniz faydalı olabilir:

- [Android için Visual Studio öykünücüsü sistem gereksinimleri](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="NoInstall"></a>Öykünücü yüklenemiyor
 Hyper-V yüklü yoksa öykünücü yüklemeye çalıştığınızda şu iletiyi görürsünüz. HyperV destekleyen bir makine olmalıdır ve etkinleştirilmesi gerekir.

 ![Android&#95;EMU&#95;yüklemesi&#95;sorunu](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Bu ileti, hem Visual Studio öykünücüsü Android ve Windows Phone öykünücüsü için geçerlidir. Öykünücü, Windows 8.1 ve Windows 10'u destekler.

 Bu iletiyi görürseniz, öykünücüyü çalıştırıp çalıştıramayacağını öğrenmek için [Android Için Visual Studio öykünücüsü sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) denetleyin.

## <a name="DomainNetwork"></a>Bir etki alanı veya şirket ağındaki ağ hedeflerine bağlanılamıyor
 Android için Visual Studio öykünücüsü ağ üzerinde kendi IP adresine sahip ayrı bir cihaz olarak görünür. Bir Windows etki alanına katılmamışsa ve ana bilgisayar ile etki alanı veya çalışma grubu kimlik bilgileri paylaşmaz.

 Ağınızın temel ağ ve Internet bağlantısı için etki alanı veya çalışma grubu yetkilendirme gerektiriyorsa, özel durum için BT yöneticinize başvurun. Bu özel durumun geliştirme bilgisayarınıza bir sınır makine olarak görev yapacak ve öykünücü gibi ağ etki alanı ile birleşik olmayan cihazlardan gelen bağlantıları kabul etmek üzere sağlar.

 Android için Visual Studio öykünücüsü, ayrıca kendi MAC adresleri kümesini kullanır. Öykünücüden ağ veya Internet kaynaklarına erişemiyorsanız, öykünücü MAC adreslerinin ağınızda yetkilendirilmiş olduğundan emin olmak için BT yöneticinize başvurun.

#### <a name="to-view-the-emulators-mac-addresses"></a>Öykünücüsünün MAC adreslerini görüntülemek için

1. Öykünücüyü başlatın.

2. Öykünücü araç çubuğunda köşeli çift ayraç düğmesini (>>) ek araçları penceresini açın.

3. Ek araçlar penceresine, ağ sekmesini tıklatın.

4. Ağ sayfasında, fiziksel adres girdilerini bulun.

## <a name="ManualNetworkConfig"></a>Ağ ayarları el ile yapılandırma gerektirirken ağ hedeflerine bağlanılamıyor
 Öykünücüsünden ağ hedeflerine bağlamak için ağınıza aşağıdaki gereksinimleri karşılaması gerekir:

- DHCP. Kendi IP adresini ağ üzerinde ayrı bir cihaz olarak kendisini yapılandırır için öykünücü DHCP gerektirir.

- Otomatik olarak yapılandırılan DNS ve ağ geçidi ayarları. Öykünücü için DNS ve ağ geçidi ayarlarını el ile yapılandırmak mümkün değildir.

  Ağınız el ile yapılandırılan ayarların gerektiriyorsa ve öykünücüsü için ağ bağlantısını nasıl olanak sağlayabileceğiniz belirlemek için BT yöneticinize danışın.

## <a name="SlowStart"></a>Öykünücü yavaş başlıyor, zaman aşımı nedeniyle başlatılamaz veya uygulama dağıtımı başarısız olur
 Belirli koşullar altında öykünücü başlatmak için birkaç dakika sürer veya bir zaman aşımı nedeniyle başlatılamıyor. Öykünücü başlayamazsa şu iletiyi görürsünüz: `App deployment failed. Please try again`. Aşağıdaki koşullar Bu hataya neden.

- Visual Studio öykünücüsü Android için önyüklenebilir bir VHD'den çalıştırılıyor. Bu yapılandırma desteklenmez.

- Hatalı sabit sürücü. Chkdsk programı çalıştırmayı göz önünde bulundurun.

- Bir sabit sürücü birleştirilmesi gerekir. Sürücü birleştirmeyi göz önünde bulundurun.

- Bir sabit sürücü dolmak üzere. Sürücüde kullanılabilir alan kontrol edin.

- Yetersiz bellek nedeniyle çalışan diğer uygulamaları kullanılabilir. Bellek miktarını artırın veya bellek kullanan uygulamaların sayısını azaltın.

- Genellikle, sistemdeki zayıf performansa katkıda bulunan tüm faktörü. En düşük alt Denetim Masası'nın performans bilgi ve araçları sayfasında bulabilirsiniz Windows Deneyimi Dizini olan bileşeni ile sorun giderme başlar.

## <a name="NoStart2"></a>Öykünücü başlatılamadı
 Öykünücü daha önce çalışıyor olsa da artık çalışmaz, aşağıdaki görevleri gidin. Emulator 'u ilk kez kullanıyorsanız, bu adımları denemeden önce [öykünücü başlatılamadı (ilk kullanım)](#NoStart) .

- Öykünücü diğer Hyper-V örneklerini kaldırın.

    1. Visual Studio’yu kapatın.

    2. Hyper-V Yöneticisi'ni açın ve herhangi bir Hyper-V örneği zaten çalışıyor öykünücüsü (sanal makineler) ve muhtemelen bozuk bir durumda durdurun.

    3. Hyper-V Yöneticisi'nde, diğer bir öykünücü tüm sanal makineleri silin.

    4. Makinenizi yeniden başlatın.

- En az 4 GB sistem belleği ve bunu diğer yoğun kaynak programlar ve işlemler (örneğin, tüm tarayıcı pencerelerini kapatmayı deneyin) tarafından Tüketilmekte olan değil, sahip olduğunuzdan emin olun.

- Sanal Anahtar Yöneticisi ve denetim, iki ağ anahtarları olduğunu görmek için Hyper-V Yöneticisi'nde açın; ilk iç anahtar ve ikinci dış olduğundan emin olun.

     ![Android&#95;EMU&#95;V&#95;anahtar&#95;Man](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Kurulum yanlışsa ve Windows 10 kullanıyorsanız, [netcfg-d komutunu (Bölüm 6) kullanarak ağ aygıtlarını yeniden yüklemeyi](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) deneyebilirsiniz.

- Bu adımlar sorunu çözmezse, öykünücüyü etkileyebilecek üçüncü taraf yazılımlar hakkında bilgi için bkz. [öykünücü başlatılamadı (ilk kullanım)](#NoStart) .

## <a name="NoStart"></a>Öykünücü başlatılamadı (ilk kullanım)
 Öykünücü başlatılmazsa belirlemek ve sorunu gidermek için aşağıdaki görevleri gidin.

- En düşük donanım gereksinimleri karşılandıktan ve BIOS ayarları doğru olduğundan emin olun.

   Öykünücü ve Windows 8 Hyper-V, ikinci düzey adres çevirisi (SLAT) ile 64-bit işlemci gerektirir. Intel, temelde çekirdek ı3 i5 veya i7 işlemci (ya da birçok Xeon birini) gerekir. AMD yongaları listesine [buradan](https://www.amd.com/en/support)ulaşabilirsiniz.

  1. Bilgisayarınızın [sistem gereksinimlerini](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)karşıladığından emin olun.

  2. [SLAT aracının](https://slatstatuscheck.codeplex.com/) bilgisayarınızın SLAT özellikli olduğunu raporluyor olduğunu doğrulayın.

  3. Bilgisayarınızın BIOS ayarları içinde tüm sanallaştırma teknolojisini etkin olduğundan emin olun. Tam BIOS açıklamaları için her bir donanım üreticisinin farklılık gösterebilir. Genel olarak, ilgili özellikleri sağlar:

     - SLAT (ikinci düzey adres çevirisi)

     - (Genişletilmiş sayfa tabloları) kabul et (Intel)

     - NPT (iç içe sayfa tabloları) (AMD)

     - (Hızlı sanallaştırma dizini) RVI (AMD)

     - VMX (bir Intel harflendirme belirten donanım Yardımlı sanallaştırma desteği)

     - SVM (donanım Yardımlı sanallaştırma desteği belirten bir AMD kısaltması)

     - XD (yürütmeyi devre dışı bırak) (Intel); Bu etkinleştirilmelidir

     - NX (Execute)(AMD) yok; Bu etkinleştirilmesi gerekir.

  4. Aşağıdaki seçenekler BIOS'ta varsa, bunları devre dışı bırakın.

     - Intel VT-d devre dışı bırak

     - Güvenilir yürütme devre dışı bırak

       Bu makalede daha fazla bilgi için bkz: Technet: Hyper-V: nasıl düzeltme BIOS hataları etkinleştirme Hyper-V'ye

  5. En az 4 GB sistem belleği ve bunu diğer yoğun kaynak programlar ve süreçler tarafından Tüketilmekte olan değil, sahip olduğunuzdan emin olun.

  6. Daha iyi veya Windows 8 Professional çalıştırdığınızdan emin olun (Windows Server 2008 desteklenmez). Windows Server 2012 desteklenir, ancak masaüstü deneyimi etkinleştirmeniz gerekir.

     Hiper yönetici hataları olup olmadığını görmek için Olay Görüntüleyicisi'ni inceleyebilirsiniz. Bunu yapmak için Olay Görüntüleyicisi açın (**key**+**R**' yi başlatın, sonra da `eventvwr`) ve ardından **Windows günlükleri**, **sistem**' i seçin. Ardından, günlüğü olay kaynağına göre filtreleyin, kaynağı **Hyper-V-hiper yönetici**olarak ayarlar. Kök nedeni belirlemenize yardımcı olması hata olup olmadığını denetleyin.

     En düşük gereksinimler ancak hiper yönetici hala başarısız, işlemci karşıladığını gerçekleştiriliyorsa, bulma olmadığını öğrenmek için bilgisayarınızın BIOS yükseltme yok. Varsa, yükseltme, üreticinin tüm önlemler (örneğin, BIOS üretici yazılımı yükseltme BIOS kalıcı olarak bozabilir ve güç kaybı tarafından engellenmez sağlamaktan) BIOS yükseltirken gözlemlemek mutlaka seçin.

- En az 4 GB sistem belleği ve bunu diğer yoğun kaynak programlar ve süreçler tarafından Tüketilmekte olan değil, sahip olduğunuzdan emin olun.

- Kaldır/devre dışı bırak üçüncü taraf sürücüler veya yazılımlar ile sanal ağ iletişimi engelliyor olabilir.

   Ağ sürücüleri/Hyper-V ağ yığınını ile tam olarak uyumlu olmayan protokolleri gibi Windows 8'altında yüklü 3 bazı taraf ürünler ile ilgili bazı bilinen sorunlar vardır.

   Genel olarak, geliştiricilerin bu ürün Windows 8 ve Hyper-V ile uyumlu olacak şekilde, yazılım güncelleştirme kadar olacaktır.

   Aşağıdaki ürünler için Windows 8 Uyumluluk yükseltme gerektirebilir: VirtualBox, sanal bilgisayar 7, VMWare, bazı VPN istemcileri yazılım güvenlik duvarları, Cisco VPN istemcileri ve diğer sanallaştırma sistemlerinin bazı sürümlerinde. Windows 8 ve Hyper-V ile uyumlu hale getirmek için yazılım yükseltmelerini teşvik etmek için sorgulanabilir sanallaştırma yazılımı geliştiricisi çalışın.

   Geçici bir *çözüm*olarak, öykünücü tarafından Visual Studio ile iletişim kurmak için kullanılan sanal ağla kesintiye uğraabilecek tüm üçüncü taraf sürücüleri ve uygulamaları devre dışı bırakabilirsiniz. Bu uygulamalar şunları içerebilir:

  - (Ağ yığınına kanca) virüsten koruma uygulamaları

  - Ağ izleme araçları

  - Ağ günlük araçları

  - Diğer sistem izleme yazılımı

    Heyecan verici ürünlerle ilgilenmeleri kaldırma kısıtlıysa, başka bir olası çözüm soru (ve güncelleştirilmiş bir sürümünü yayımlamayı ürün Geliştirici isteyen), aşağıdaki adımları sağlamaktır.

  1. Ağ bağlantıları Yöneticisini başlatın (Başlangıç ekranından `View Network Connections` yazın ve ağ bağlantılarını görüntülemek için bu seçeneği belirleyin.)

  2. VEthernet (Iç Ethernet bağlantı noktası Windows Phone öykünücü Iç anahtar) bağdaştırıcısı için bağlam menüsünden **Özellikler** ' i seçin.

      ![Hyper&#45;V tarafından kullanılan sanal bağdaştırıcı](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Bağdaştırıcı özellikleri burada gösterilir.

      ![Sanal bağdaştırıcı özellikleri](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Bu bağdaştırıcı için, bu bağlantı altında seçilmesi gereken tek öğeler aşağıdaki **öğeleri kullanır** :

     - Microsoft Ağları için istemci

     - QoS Paket Zamanlayıcısı

     - Dosya ve yazıcı paylaşımı Microsoft Ağları için

     - Microsoft LLDP protokol sürücüsüne

     - Bağlantı-katman Topoloji Bulma Eşleyicisi g/ç sürücüsü

     - Bağlantı-katman Topoloji Bulma Yanıtlayıcı

     - Internet Protokolü sürüm 6 (TCP/IPv6)

     - Internet Protokolü sürüm 4 (TCP/IPv4)

  4. Diğer öğeleri kaldırın.

     İçin bu teknik kullanılarak dezavantajı, dilediğiniz zaman yeni bir 3. taraf ürün desteklenmeyen sürücüleri yükler veya öykünücü yüklendikten, dilediğiniz zaman bu adımları yinelenmesi gerekir ' dir.

     Üçüncü taraf ürünleri kaldırıldıktan sonra Windows Phone öykünücüsü iç anahtar geri yüklemek gerekebilir. Bunu yapmak için:

  - Hyper V açın ve sanal Anahtar Yöneticisi'ne gidin. "Windows Phone öykünücü Iç anahtarı" adlı bir sanal anahtar oluşturun ve bağlantı türünü **iç ağ**olarak ayarlayın.

     ![Sanal Anahtar Yöneticisi](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Artık öykünücüyü başlatın. Çalışmalıdır.

## <a name="NoBoot"></a>Öykünücü yüklendikten sonra bilgisayar önyükleme yapamıyor
 Aşağıdaki koşullar doğru olduğunda bu sorun oluşabilir:

- Bilgisayarınızda bir gigabayt anakart vardır.

- USB3 anakart üzerinde etkindir.

  Bu sorunu çözmek için USB3 anakart BIOS ayarları devre dışı bırakın ve bilgisayarı yeniden başlatın. Ardından, gigabayttan kartın BIOS 'U için bir güncelleştirme yayımlamışsa emin olun.

  Daha fazla bilgi için aşağıdaki Bilgi Bankası makalesine bakın: [gigabayt sistemlerine Hyper-V rolü yüklendikten sonra önyükleme hatası](https://support.microsoft.com/en-us/kb/2693144).

## <a name="ADB"></a>Visual Studio, uygulamayı öykünücüye dağıtmaya çalışırken takılıyor veya öykünücü diğer Ides 'te hata ayıklama hedefi olarak görünmüyor
 Öykünücünün çalıştığından, ancak ADB (Android hata ayıklama köprüsü) bağlanması görünmez ya da (örneğin, Android Studio veya Eclipse) ADB kullanan Android araçları görünmüyor öykünücü için ADB nerede arar ayarlamak gerekebilir. Öykünücü, Android SDK'nızı temel konumunu tanımlamak için bir kayıt defteri anahtarını kullanır ve bu dizin altında \platform-tools\adb.exe dosyasını arar. Öykünücüsü tarafından kullanılan Android SDK yolu değiştirmek için:

- Başlat düğmeleri bağlam menüsünden **Çalıştır** ' ı seçerek Kayıt Defteri Düzenleyicisi 'ni açın, iletişim kutusuna `regedit` yazın ve **Tamam**' ı seçin.

- Soldaki klasör ağacında *\SOFTWARE\Wow6432Node\Android SDK Tools HKEY_LOCAL_MACHINE* gidin.

- **Yol** kayıt defteri değişkenini Android SDK yolu ile eşleşecek şekilde değiştirin.

  Öykünücü yeniden başlatın ve artık öykünücü ADB bağlı ve Android araçları ilişkili görüyor olmanız gerekir.

## <a name="XamarinPlayer"></a>Öykünücü, UDP bağlantı noktasını ayarlayamadığından askıda kalıyor
 Xamarin Player ile uyumsuzluğu nedeniyle bu sorunla karşılaşabilirsiniz. Öykünücü askıda görünüyorsa veya bu hata iletisini görürseniz, "öykünücü cihaz işletim sistemine bağlanamıyor: UDP bağlantı noktası ayarlanamadı.  Bazı işlevler devre dışı bırakılabilir", bu sorunu yaşıyor olabilirsiniz. Aşağıdaki adımları uygulayın.

1. Xamarin Player kaldırın.

2. Kaldırılan (Xamarin Player çalıştırması sanal kutusunun üstünde) olan sanal kutunun doğrulayın.

3. Cihaz Yöneticisi'ne gidin, gizli aygıtları göster seçeneğini belirleyin ve ardından fiziksel ağ kartları dışında her şeyi silin.

4. Kaldırma/Hyper-V olmayan fiziksel ağ bağdaştırıcısı kaldırdıktan sonra yeniden yüklemeyi deneyebilirsiniz.

## <a name="Skylake"></a>Hata ayıklayıcı bir Xamarin projesine iliştirilemiyor
 Intel Skylake işlemcilere sahip Windows 10 çalıştırıyorsanız, Xamarin uygulamaları öykünücüde çalıştırma başarısız olabilir veya Visual Studio için hata ayıklayıcının değil. Hyper-V ve Skylake işlemciler ile ilgili bir sorun nedeniyle budur. Geçici bir çözüm olarak aşağıdaki adımları uygulayın.

1. Hyper-V Yöneticisi'ni açın ve öykünücü profil için VM'yi seçin olduğunuz kullanarak.

2. **Kaydedilmiş durumu Sil** (sağ alt) seçeneğini belirleyin.

3. **Ayarları Seç...**

4. İşlemci düğümünü genişletin ve **Uyumluluk**' i seçin.

5. **Farklı bir işlemci sürümü olan fiziksel bir bilgisayara geçişi**etkinleştirin.

6. Hizmeti yeniden başlatın ( **Eylemler**altında) ve yeniden deneyin.

## <a name="GooglePlay"></a>Öykünücü Google Play Hizmetleri kullanan uygulamayı çalıştıramıyor
 Öykünücü, Google Play Hizmetleri'ni kitaplıklarıyla gelmez. Ancak öykünücü sürükle ve bırak açılıp dosyaların yüklenmesini destekler.

## <a name="DragAndDrop"></a>Dosya, APK veya bıraktığınızda ZIP dosyası için sürükle ve bırak çalışmıyor
 Öykünücü ADB.exe ekrana bir dosya sürükleyip zaman dosya aktarımı kolaylaştırmak için kullanır. Bir dosya sürükleyip denediğinizde bir hatayla karşılaşırsanız, bu büyük olasılıkla öykünücü ADB.exe için bağlı olmadığını gösterir. Sorunu gidermek için, [Visual Studio 'da uygulamayı öykünücüye dağıtmaya çalışmak için takılmış veya öykünücü diğer Ides 'te hata ayıklama hedefi olarak görünmüyor](#ADB).

## <a name="Resolution"></a>Ekran görüntüsünün çözümlenmesi yanlış
 **Ek araçlar** penceresinde ekran görüntüsü sekmesini kullanarak bir ekran görüntüsü alırsanız ve sonuçta elde edilen görüntü beklenmeyen bir Boyutladır, **yakalama**'yı seçmeden önce ekranın yakınlaştırma düzeyini ayarlamanız gerekebilir. Öykünücü ekran görüntüleri, ana bilgisayar İzleyicisi ekranın çözünürlükte alır.

## <a name="OpenGL"></a>Öykünücü OpenGL içeriğini işlemesini başaramazsa
 Öykünücü, ana bilgisayar makinenizin GPU 'SU kullanılarak OpenGL içeriği işler ve bu çağrıları DirectX 'e ve DirectX 'e dönüştürmek için AÇıLı projeyi kullanır. Bir cihazda, ancak yanlış öykünücü uygulamanızın doğru şekilde işlediğinden, cihaz yanlış bir OpenGL çağrı (örneğin, eşleşmeyen gölgelendirici değişkenleri kullanarak) için Azaltıcı olasıdır.

## <a name="Multitouch"></a>Öykünücü çok dokunmalı hareketlere yanıt vermiyor
 Bazı durumlarda, öykünücüyü başlatın ve çok noktalı dokunma için ya da ile doğrudan etkileşim-dokunmatik ekran veya öykünücü araç çubuğunda çok noktalı dokunma aracını kullanarak yanıt değil. Bu durumda, öykünücü araç çubuğunda **Döndür** düğmesini seçin ve çoklu Touch 'ı kullanmayı deneyin. Sorun devam ederse, [Emulator 'un OpenGL içerik sorununu oluşturabileceği başarısız](#OpenGL) olup olmadığını okuyun.

## <a name="Support"></a>Destek kaynakları
 Ana bilgisayarınızın sistem gereksinimlerini karşıladığından ve bu sorun giderme Kılavuzu'nda ele alınmayan bir sorunla karşılaşırsanız varsa:

- [Android-Emulator](https://stackoverflow.com/questions/tagged/android-emulator) ve Visual-Studio etiketlerini kullanarak StackOverflow 'de soru sorun.

- Visual Studio'da veya öykünücü Yöneticisi'nde gönderme gülümseme aracını kullanarak bir sorun bildirin.
