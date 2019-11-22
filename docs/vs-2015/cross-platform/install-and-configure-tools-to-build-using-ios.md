---
title: İOS kullanarak derlemek için Araçlar yükleyip yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 695cbeaba5a108c61b5e81078a9651c0df9237f5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299816"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>iOS Kullanarak Derlemeye Yönelik Araçları Yükleme ve Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İOS kodu ile iOS C++ simülatörünü veya bir iOS cihazını düzenlemek, hatalarını ayıklamak ve dağıtmak için Visual, platformlar arası mobil geliştirme için kullanabilirsiniz, ancak lisanslama kısıtlamaları nedeniyle kodun bir Mac üzerinde oluşturulması ve uzaktan çalıştırılması gerekir. Visual Studio kullanarak iOS uygulamaları derlemek ve çalıştırmak için, Mac 'inizde [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)uzak aracısını ayarlamanız ve yapılandırmanız gerekir. Uzak Aracı, Visual Studio 'dan derleme isteklerini işler ve uygulamayı Mac 'e bağlı iOS cihazında veya Mac üzerindeki iOS simülatörü üzerinde çalıştırır.  
  
> [!NOTE]
> Mac yerine bulutta barındırılan Mac Hizmetleri kullanma hakkında daha fazla bilgi için bkz. [bulutta IOS oluşturma ve benzetimi](https://taco.visualstudio.com/docs/build_ios_cloud/)yapma. Yönergeler, Apache Cordova için Visual Studio Araçları kullanarak oluşturma içindir. Platformlar arası mobil geliştirme için Visual C++ kullanarak oluşturma yönergelerini kullanmak için, vs-MDA-Remote için vcremote yerine koyun.  
  
 İOS kullanarak derlemek için araçları yükledikten sonra, Visual Studio ve Mac 'te iOS geliştirmesi için uzak aracıyı hızlı bir şekilde yapılandırmak ve güncellemek üzere bu konuya bakın.  
  
 [Önkoşullar](#Prerequisites)  
  
 [İOS için uzak aracıyı yükler](#Install)  
  
 [Uzak aracıyı başlatma](#Start)  
  
 [Visual Studio 'da uzak Aracıyı yapılandırma](#ConfigureVS)  
  
 [Yeni bir güvenlik PIN 'ı oluştur](#GeneratePIN)  
  
 [Yeni bir sunucu sertifikası oluştur](#GenerateCert)  
  
 [Mac 'te uzak Aracıyı yapılandırma](#ConfigureMac)  
  
## <a name="Prerequisites"></a> Önkoşullar  
 İOS için kod geliştirmek üzere uzak aracıyı yüklemek ve kullanmak için, önce aşağıdaki önkoşullara sahip olmanız gerekir:  
  
- OS X Mavericks veya üstünü çalıştıran bir Mac bilgisayar  
  
- Bir [Apple Kimliği](https://appleid.apple.com/)  
  
- Apple ile etkin bir [IOS geliştirici programı](https://developer.apple.com/programs/ios/) hesabı  
  
- [Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Xcode 6, App Store 'dan indirilebilir.  
  
- Xcode komut satırı araçları  
  
     Xcode komut satırı araçlarını yüklemek için, Mac 'inizde Terminal uygulamasını açın ve şu komutu girin:  
  
     `xcode-select --install`  
  
- Xcode 'da yapılandırılmış bir iOS imzalama kimliği  
  
     İOS Imzalama kimliği alma hakkında ayrıntılı bilgi için bkz. [Imza kimliklerinizi ve sertifikalarınızı](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) IOS geliştirici kitaplığı 'nda koruma. Xcode 'da imzalama kimliğinizi görmek veya ayarlamak için **Xcode** menüsünü açın ve **Tercihler**' i seçin. **Hesaplar** ' ı seçin ve Apple Kimliğinizi seçin ve ardından **Ayrıntıları görüntüle** düğmesini seçin.  
  
- Geliştirme için bir iOS cihazı kullanıyorsanız, cihazınız için Xcode 'da yapılandırılmış bir sağlama profili  
  
     Sağlama profilleri oluşturma hakkında ayrıntılı bilgi için bkz. iOS Geliştirici kitaplığındaki [üye merkezini kullanarak sağlama profilleri oluşturma](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) .  
  
- [Node.js](https://nodejs.org/en/)  
  
- Güncelleştirilmiş NPM sürümü  
  
     Node. js ile birlikte gelen NPM sürümü vcremote yüklemek için yeterince yeni olmayabilir. NPM 'yi güncelleştirmek için Mac 'inizde Terminal uygulamasını açın ve şu komutu girin:  
  
     `sudo npm install -g npm@latest`  
  
## <a name="Install"></a>İOS için uzak aracıyı yükler  
 Platformlar arası mobil geliştirme C++ için Visual yüklediğinizde, Visual Studio [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)Ile iletişim kurabilir, Mac 'inizde çalışan uzak bir aracı, dosyaları aktarmak, iOS uygulamanızı derlemek ve çalıştırmak ve hata ayıklama komutları göndermek için kullanılabilir.  
  
 Uzak aracıyı yüklemeden önce, [platformlar arası mobil geliştirme C++ için](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools) [önkoşulları](#Prerequisites) ve yüklü görseli karşıladığınızdan emin olun.  
  
### <a name="DownloadInstall"></a>Uzak aracıyı indirmek ve yüklemek için  
  
- Mac inizdeki Terminal uygulamasından şunu girin:  
  
   `sudo npm install -g --unsafe-perm vcremote`  
  
   Genel yükleme ( **-g**) anahtarı önerilir, ancak gerekli değildir.  
  
   Yükleme sırasında vcremote yüklenir ve geliştirici modu Mac 'inizde etkinleştirilir. [Homebrew](https://brew.sh/) ve iki NPM paketi vcremote-lib ve vcremote-utils da yüklüdür.  
  
  > [!NOTE]
  > Homebrew 'yi yüklemek için sudo (yönetici) erişiminizin olması gerekir. Sudo olmadan vcremote ' i yüklemeniz gerekiyorsa, el ile bir usr/yerel konuma homebrew yükleyebilir ve bin klasörünü yolunuza ekleyebilirsiniz. Daha fazla bilgi için [homebrew belgelerine](https://github.com/Homebrew/homebrew/wiki/Installation)bakın. Geliştirici modunu el ile etkinleştirmek için bu komutu Terminal uygulamasına girin: `DevToolsSecurity –enable`  
  
  Visual Studio 'nun yeni bir sürümüne güncelleştirirseniz, uzak aracının geçerli sürümüne de güncelleştirmeniz gerekir. Uzak aracıyı güncelleştirmek için uzak aracıyı indirme ve yükleme adımlarını yineleyin.  
  
## <a name="Start"></a>Uzak aracıyı başlatma  
 İOS kodunuzu derlemek ve çalıştırmak için uzak aracının Visual Studio için çalışıyor olması gerekir. İletişim kurabilmesi için, Visual Studio 'Nun uzak aracıyla eşleştirilmiş olması gerekir. Varsayılan olarak, uzak Aracı, Visual Studio ile eşleştirmek için PIN gerektiren güvenli bağlantı modunda çalışır.  
  
### <a name="RemoteAgentStartServer"></a>Uzak aracıyı başlatmak için  
  
- Mac inizdeki Terminal uygulamasından şunu girin:  
  
   `vcremote`  
  
   Bu, uzak aracıyı ~/vcremotevarsayılan derleme diziniyle başlatır. Ek yapılandırma seçenekleri için bkz. [Mac üzerinde uzak Aracıyı yapılandırma](#ConfigureMac).  
  
  Aracıyı ilk kez başlattığınızda ve yeni bir istemci sertifikası oluşturduğunuzda, ana bilgisayar adı, bağlantı noktası ve PIN dahil olmak üzere Visual Studio 'da aracıyı yapılandırmak için gerekli bilgiler sunulur.  
  
  ![Güvenli PIN oluşturmak için vcremote kullanın](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
  Visual Studio 'da ana bilgisayar adını kullanarak uzak aracıyı yapılandırmak istiyorsanız, erişilebilir olduğunu doğrulamak için ana bilgisayar adını kullanarak Windows 'dan Mac 'e ping gönderin. Aksi takdirde, bunun yerine IP adresini kullanmanız gerekebilir.  
  
  Oluşturulan PIN bir kerelik kullanım içindir ve yalnızca sınırlı bir süre için geçerlidir. Zaman sona ermeden önce Visual Studio 'Yu uzak aracı ile eşleştirmeyin, yeni bir PIN oluşturmanız gerekecektir. Daha fazla bilgi için bkz. [Yeni bir güvenlik PIN 'ı oluşturma](#GeneratePIN).  
  
  Uzak aracıyı güvenli olmayan modda kullanabilirsiniz. Güvenli olmayan modda uzak Aracı, PIN olmadan Visual Studio ile eşleştirilebilir.  
  
#### <a name="to-disable-secured-connection-mode"></a>Güvenli bağlantı modunu devre dışı bırakmak için  
  
- Vcremote 'da güvenli bağlantı modunu devre dışı bırakmak için, aşağıdaki komutu Mac 'inizde Terminal uygulamasına girin:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Güvenli bağlantı modunu etkinleştirmek için  
  
- Güvenli bağlantı modunu etkinleştirmek için şu komutu girin:  
  
   `vcremote --secure true`  
  
  Uzak aracıyı başlattığınızda, bunu durdurmadan, Visual Studio 'dan kullanabilirsiniz.  
  
#### <a name="to-stop-the-remote-agent"></a>Uzak aracıyı durdurmak için  
  
- Terminal penceresinde vcremote ' de çalışıyor `Control+C`girin.  
  
## <a name="ConfigureVS"></a>Visual Studio 'da uzak Aracıyı yapılandırma  
 Visual Studio 'dan uzak aracıya bağlanmak için, Visual Studio seçeneklerinde uzak yapılandırmayı belirtmeniz gerekir.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Uzak aracıyı Visual Studio 'dan yapılandırmak için  
  
1. Aracı Mac 'inizde zaten çalışmıyorsa, [uzak aracıyı başlatma](#Start)bölümündeki adımları izleyin. Projenizi başarıyla eşleştirmek, bağlanmak ve derlemek için Mac 'inizde Visual Studio için vcremote çalışıyor olmalıdır.  
  
2. Mac 'inizde, Mac 'nizin ana bilgisayar adını veya IP adresini alın.  
  
    Terminal penceresinde **ifconfig** komutunu kullanarak IP adresini alabilirsiniz. Etkin ağ arabirimi altında listelenen Inet adresini kullanın.  
  
3. Visual Studio menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.  
  
4. **Seçenekler** iletişim kutusunda **platformlar arası**, **C++** **iOS**' ı genişletin.  
  
5. **Ana bilgisayar adı** ve **bağlantı noktası** alanlarında, uzak aracı tarafından başlatıldığında belirtilen değerleri girin. Ana bilgisayar adı, Mac 'nizin DNS adı veya IP adresi olabilir. Varsayılan bağlantı noktası 3030 ' dir.  
  
   > [!NOTE]
   > Ana bilgisayar adını kullanarak Mac 'e ping yapamadıysanız IP adresini kullanmanız gerekebilir.  
  
6. Uzak aracıyı varsayılan güvenli bağlantı modunda kullanıyorsanız, **güvenli** onay kutusunu işaretleyin, sonra **PIN** alanına uzak aracı tarafından belirtilen PIN değerini girin. Uzak aracıyı güvenli olmayan bağlantı modunda kullanıyorsanız, **güvenli** onay kutusunu temizleyip **sabitle** alanını boş bırakın.  
  
7. Eşleştirmeyi etkinleştirmek için **çift** seçin.  
  
    ![İOS derlemeleri için vcremote bağlantısını yapılandırma](../cross-platform/media/cppmdd-options-ios.PNG "CPPMDD_Options_iOS")  
  
    Eşleştirme, ana bilgisayar adı veya bağlantı noktası değiştirilene kadar devam ettirir. **Seçenekler** iletişim kutusunda ana bilgisayar adını veya bağlantı noktasını değiştirirseniz, değişikliği geri almak için, önceki eşleştirmeye geri dönmek Için **geri al** düğmesini seçin.  
  
    Eşleştirme başarılı olmazsa uzak [aracıyı başlatma](#Start)bölümündeki adımları izleyerek uzak aracının çalıştığını doğrulayın. Uzak aracı PIN 'ı oluşturulduktan sonra çok fazla zaman geçtiyse, Mac üzerinde [Yeni bir güvenlik PIN 'ı oluşturma](#GeneratePIN) ' daki adımları izleyin ve sonra yeniden deneyin. Mac 'nizin ana bilgisayar adını kullanıyorsanız, bunun yerine **ana bilgisayar adı** alanındaki IP adresini kullanmayı deneyin.  
  
8. Uzak **kök** alanındaki klasör adını, Mac 'teki giriş (~) dizininizde bulunan uzak aracı tarafından kullanılan klasörü belirlemek için güncelleştirin. Varsayılan olarak, uzak aracı uzak kök olarak/Users/`username`/vcremote kullanır.  
  
9. Uzaktan eşleştirme bağlantı ayarlarını kaydetmek için **Tamam ' ı** seçin.  
  
   Visual Studio, kullandığınız her seferinde Mac 'inizde uzak aracıya bağlanmak için aynı bilgileri kullanır. Mac 'inizde yeni bir güvenlik sertifikası oluşturmadığınız veya ana bilgisayar adı veya IP adresi değiştiği takdirde, Visual Studio 'Yu uzak aracıyla yeniden eşleştirmenizi gerektirmez.  
  
## <a name="GeneratePIN"></a>Yeni bir güvenlik PIN 'ı oluştur  
 Uzak aracıyı ilk kez başlattığınızda, oluşturulan PIN, varsayılan olarak 10 dakika boyunca sınırlı bir süre için geçerlidir. Zaman sona ermeden önce Visual Studio 'Yu uzak aracıya eşleştirmezseniz, yeni bir PIN oluşturmanız gerekir.  
  
#### <a name="to-generate-a-new-pin"></a>Yeni bir PIN oluşturmak için  
  
1. Aracıyı durdurun veya Mac 'inizde ikinci bir Terminal uygulaması penceresi açın ve bunu kullanarak komutu girin.  
  
2. Terminal uygulamasına şu komutu girin:  
  
     `vcremote generateClientCert`  
  
     Uzak aracı yeni bir geçici PIN oluşturur. Visual Studio 'Yu yeni PIN kullanarak eşleştirmek için, [Visual Studio 'da uzak Aracıyı yapılandırma](#ConfigureVS)bölümündeki adımları yineleyin.  
  
## <a name="GenerateCert"></a>Yeni bir sunucu sertifikası oluştur  
 Güvenlik nedeniyle, Visual Studio 'Yu uzak aracıyla eşleştirmeyen sunucu sertifikaları, Mac 'nizin IP adresine veya ana bilgisayar adına bağlıdır. Bu değerler değiştiğinde, yeni bir sunucu sertifikası oluşturmanız ve ardından Visual Studio 'Yu yeni değerlerle yeniden yapılandırmanız gerekir.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Yeni bir sunucu sertifikası oluşturmak için  
  
1. Vcremote Aracısı 'nı durdurun.  
  
2. Terminal uygulamasına şu komutu girin:  
  
     `vcremote resetServerCert`  
  
3. Onay istendiğinde `Y`girin.  
  
4. Terminal uygulamasına şu komutu girin:  
  
     `vcremote generateClientCert`  
  
     Bu, yeni bir geçici PIN oluşturur.  
  
5. Visual Studio 'Yu yeni PIN kullanarak eşleştirmek için, [Visual Studio 'da uzak Aracıyı yapılandırma](#ConfigureVS)bölümündeki adımları yineleyin.  
  
## <a name="ConfigureMac"></a>Mac 'te uzak Aracıyı yapılandırma  
 Uzak aracıyı çeşitli komut satırı seçeneklerini kullanarak yapılandırabilirsiniz. Örneğin, derleme isteklerini dinlemek için bağlantı noktasını belirtebilir ve dosya sisteminde korunacak en fazla derleme sayısını belirtebilirsiniz. Varsayılan olarak, sınır 10 derlemedir. Uzak Aracı, kapatırken en fazla uzunluğu aşan yapıları kaldırır.  
  
#### <a name="to-configure-the-remote-agent"></a>Uzak aracıyı yapılandırmak için  
  
- Uzak aracı komutlarının tüm listesini görmek için, Terminal uygulamasında şunu girin:  
  
     `vcremote --help`  
  
- Güvenli modu devre dışı bırakmak ve basit HTTP tabanlı bağlantıları etkinleştirmek için şunu girin:  
  
     `vcremote --secure false`  
  
     Bu seçeneği kullandığınızda, aracıyı Visual Studio 'da yapılandırırken **güvenli** onay kutusunun işaretini kaldırın ve **PIN** alanını boş bırakın.  
  
- Uzak Aracı dosyaları için bir konum belirtmek üzere şunu girin:  
  
     `vcremote --serverDir directory_path`  
  
     Burada *directory_path* , günlük dosyalarının, derlemelerin ve sunucu sertifikalarının yerleştirileceği Mac 'inizde yer alır. Varsayılan olarak, bu konum/Users/*UserName*/vcremote. Derlemeler, bu konumda yapı numarasına göre düzenlenir.  
  
- `stdout` yakalamak ve Server. log adlı bir dosyaya `stderr` bir arka plan işlemi kullanmak için şunu girin:  
  
     `vcremote > server.log 2>&1 &`  
  
     Server. log dosyası, derleme sorunlarını gidermeye yardımcı olabilir.  
  
- Aracıyı komut satırı parametreleri yerine bir yapılandırma dosyası kullanarak çalıştırmak için şunu girin:  
  
     `vcremote --config config_file_path`  
  
     Burada *config_file_path* , JSON biçimindeki bir yapılandırma dosyasının yoludur. Başlangıç seçenekleri ve değerleri tire içermemelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Platformlar Arası Mobil Geliştirme için Visual C++’ı yükleme](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
