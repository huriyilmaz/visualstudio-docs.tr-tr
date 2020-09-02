---
title: Öykünücüde Windows Phone uygulamaları çalıştırın | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683535"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Öykünücüde Windows Phone uygulamaları çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Phone öykünücüsü, fiziksel bir cihaz olmadan bilgisayarınızda hata ayıklamanıza ve Windows Phone uygulamalarda test yapabilmeniz için sanallaştırılmış bir ortam sağlar. Ortak dokunma ve döndürme olaylarının benzetimini yapabilir ve fiziksel ekran boyutunu ve öykünmek istediğiniz çözünürlüğü seçebilirsiniz. Konum, ağ, bildirimler, sensör, ivme ölçer ve isteğe bağlı SD kart gibi yaygın olarak kullanılan birçok özelliği de test edebilirsiniz.  
  
 Öykünücüde test ettiğiniz özellikler hakkında daha fazla bilgi için bkz. [Windows Phone öykünücüsü 'Nde test uygulaması özellikleri](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Öykünücü, Visual Studio ile birlikte Windows Phone uygulamaları tasarlayabileceğiniz, geliştirebileceğiniz, hata ayıklamanın ve test etmekte kullanabileceğiniz bir ortam sunar.  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> Öykünücüde bir Windows Phone uygulaması çalıştırma  
 Windows Phone bir uygulama geliştirirken uygulamanızı hızlı bir şekilde dağıtmak ve test etmek için Windows Phone öykünücüsü 'nü kullanabilirsiniz. Uygulamanızı Windows Phone deposunda yayımlamadan önce, uygulamanızı gerçek bir Windows Phone cihazında test etmenizi öneririz. Bu, kullanıcılara karşılaşması için uygulamanızı görmenizi sağlar.  
  
 Windows Phone öykünücüsü içinde ilk kez bir Windows Phone uygulaması çalıştırdığınızda, aşağıdaki olaylar gerçekleşir:  
  
1. Öykünücü başlatılır.  
  
2. Öykünücü, Windows Phone işletim sistemini yükler.  
  
3. Öykünücü Windows Phone Başlangıç ekranını görüntüler.  
  
4. Uygulamanız öykünücüye dağıtılır.  
  
5. Uygulamanız öykünücü üzerinde çalışır.  
  
   Seçili öykünücü zaten çalışıyorsa, uygulamanız çalışan öykünücüsünde dağıtılır ve başlatılır. Her bir öykünücü için tek bir örnek çalıştırılabilir.  
  
> [!TIP]
> Uygulamanızı Öykünücüde test ederken, uygulamanızı hızlı bir şekilde çalıştırmak için hata ayıklama oturumları arasında öykünücüsü açık bırakın.  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> Visual Studio 'dan bir uygulama çalıştırma  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Visual Studio 'dan bir uygulama dağıtmak ve çalıştırmak için  
  
1. Visual Studio 'da bir Windows Phone projesi açın.  
  
2. **Standart** araç çubuğunda öykünücü seçeneklerinden birini seçin.  
  
     ![Windows Phone öykünücü görüntülerinin listesi](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Uygulamanızı hata ayıklama ile dağıtmak ve çalıştırmak için, **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın veya F5 tuşuna basın.  
  
     Uygulamanızı hata ayıklamadan dağıtmak ve çalıştırmak için, **hata** ayıklama menüsünde **hata ayıklama olmadan Başlat**' a tıklayın veya CTRL + F5 ' e basın.  
  
     Uygulamanız dağıtıldı ve başlatıldı.  
  
     Uygulamanızı çalıştırmadan dağıtmak için, **Yapı** menüsünde **Çözümü dağıt**' a tıklayın.  
  
##### <a name="to-stop-a-running-app"></a>Çalışan bir uygulamayı durdurmak için  
  
- Çalışan bir uygulamayı durdurmak için aşağıdakilerden birini yapın:  
  
  - Visual Studio 'da **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' a tıklayın veya SHIFT + F5 tuşlarına basın.  
  
  - Öykünücüde, uygulamadan çıkmak için **geri** düğmesine basın. Uygulamanın etkin sayfası uygulamanın başlangıç sayfası değilse, **geri** düğmesine birden çok kez basmanız gerekebilir.  
  
    Uygulama çıkar ve başlangıç ekranı açılır. Bu, geçerli hata ayıklama oturumunu sonlandırır.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Bir uygulamayı hata ayıklama olmadan yeniden başlatmak için  
  
1. Öykünücüsünde, başlangıç ekranında, uygulama listesini görüntülemek için sola kaydırın.  
  
2. Uygulama listesinde uygulama simgesine dokunun. Uygulama hata ayıklama olmadan yeniden başlatılır.  
  
##### <a name="to-deactivate-a-running-app"></a>Çalışan bir uygulamayı devre dışı bırakmak için  
  
1. Uygulamanızı çalıştırmadan önce, Visual Studio 'da Çözüm Gezgini ' de projeye sağ tıklayın ve ardından **Özellikler** ' i seçerek **Proje Tasarımcısı**' nı açın.  
  
2. **Proje Tasarımcısı**' nda, **hata** ayıklama sayfasında, hata **ayıklama** sırasında devre dışı bırak onay kutusunun işaretini kaldırın. Devre dışı bırakıldığında uygulamanın kaldırıldı olarak işaretlenmiş olmasını istiyorsanız onay kutusunu işaretleyin.  
  
3. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın veya F5 ' e basarak uygulamayı çalıştırın.  
  
4. Öykünücüde **Başlat** düğmesine basın. Başlangıç ekranı görünür ve uygulama devre dışı bırakılır. Uygulama, **hata ayıklama sırasında devre dışı bırakıldıktan sonra kaldırılma** ayarına bağlı olarak, etkin olmayan bir duruma geçer ya da kaldırıldı.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Etkinliği olmayan veya kaldırıldı olarak işaretlenmiş uygulamayı yeniden etkinleştirmek için  
  
- Öykünücüde, uygulamaya geri dönmek için **geri** düğmesine basın. Başka sayfalara gezindiyseniz veya başka bir uygulamayı açtıysanız, uygulamayı yeniden etkinleştirmek için **geri** düğmesine birden çok kez basmanız gerekebilir.  
  
     Hata ayıklama oturumu devam ettirir. Hata ayıklayıcı uygulamadan ayrılmışsa, hata ayıklama oturumunu sürdürmeniz için F5 tuşuna basmanız gerekebilir.  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> Uygulama dağıtım aracı ile uygulama çalıştırma  
 Uygulamanızı Öykünücüde çalıştırmak için Windows Phone uygulama dağıtım aracı 'nı (**AppDeploy.exe**) de kullanabilirsiniz. Bu araç, Windows Phone geliştirme araçlarını yüklediğinizde yüklü olan tek başına bir uygulamadır.  
  
 Daha fazla bilgi için bkz. [uygulama dağıtım aracı ile Windows Phone 8,1 uygulamaları dağıtma](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> Öykünücü araç çubuğuyla Windows Phone öykünücüsünü yapılandırma  
 Bu tabloda, öykünücü araç çubuğunda kullanılabilen yapılandırma düğmeleri gösterilmektedir.  
  
|Araç çubuğu düğmeleri|Yapılandırma seçenekleri|  
|---------------------|---------------------------|  
|![Windows Phone öykünücü araç çubuğundaki giriş seçenekleri](../debugger/media/wp-emulator.png "WP_Emulator_")|**Tek nokta veya çok noktalı girişi yapılandırma**<br /><br /> Çok noktalı girişi etkinleştirdiğinizde, dokunmatik noktaları ekrana dokunmadan taşımak için sağ tıklayabilirsiniz. Ardından, her iki dokunma noktasını eşzamanlı olarak taşımak için sol tıklayabilirsiniz.|  
|![Windows Phone öykünücü araç çubuğunda yönlendirme](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Öykünücü yönünü yapılandırma**<br /><br /> Windows Phone öykünücüsünde yönü üç yönden birine değiştirebilirsiniz: dikey, yatay sol veya yatay sağ. Yönlendirmeyi değiştirdiğinizde öykünücü boyutu değişmez.<br /><br /> Yönü değiştirmek için **Sola Döndür** düğmesine veya **sağ Döndür** düğmesine tıklayın.|  
|![Windows Phone öykünücü araç çubuğundaki boyut seçenekleri](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Öykünücü boyutunu yapılandırma**<br /><br /> Konak bilgisayar ekranında öykünücü boyutunu değiştirebilirsiniz. Öykünücü için inç başına nokta (DPı), yakınlaştırma değerinden bağımsız olarak konak İzleyicisi DPI 'sını temel alır.<br /><br /> -Öykünücüyü ekrana sığdırmak için **ekrana sığdır** düğmesine tıklayın.<br />-Yakınlaştırma ayarını değiştirmek için **Yakınlaştır** düğmesine tıklayın. **Yakınlaştır** iletişim kutusu açılır. **Yakınlaştır** iletişim kutusunda 33 ve 100 arasında bir yakınlaştırma değeri girin.|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> Öykünücü üzerinde sanal donanım düğmelerini kullanma  
 Öykünücü ekranının sağ tarafındaki sanal donanım düğmelerini kullanarak bir telefonun donanım düğmelerinin kullanımına benzetim yapın.  
  
- Görüntüyü kapatmak ve açık yapmak için **Güç** düğmesine tıklayın. Telefonu kapatma benzetimini yapmak için tıklayın ve basılı tutun.  
  
- Telefon görüşmeleri ve bildirimler için telefon konuşmacının hacminin değiştirilmesini taklit etmek üzere **hacim yukarı** veya **hacim aşağı** düğmesine tıklayın.  
  
- Kamera **düğmesi kamera** uygulamasını başlatır. Kamera uygulamasındaki denetimleri kullanarak fotoğraf veya video alma benzetimi yapabilirsiniz.  
  
  Aşağıdaki ekran görüntüsünde, sanal donanım düğmeleri gösterilmektedir.  
  
1. Sol görüntüde öykünücü üzerindeki başlangıç ekranı görüntülenir.  
  
2. Ortadaki görüntüde, görüntüyü kapatmak için **Güç** düğmesine dokunduktan sonra öykünücü görüntülenir.  
  
3. Doğru görüntüde, birimi artırmak için **birim yukarı** düğmesine dokunduktan sonra öykünücü ekran görüntülenir.  
  
   ![Windows Phone öykünücüsünün düğmeleri](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> Öykünücü ile bilgisayar klavyesini kullanma  
 Öykünücü, geliştirme bilgisayarınızdaki donanım klavyesi Windows Phone klavye ile eşlemeyi destekler. Anahtarların davranışı, Windows Phone cihazındaki ile aynıdır.  
  
 Varsayılan olarak, donanım klavyesi etkin değildir. Bu uygulama, kullanabilmeniz için dağıtılması gereken bir kayan klavyeye eşdeğerdir. Donanım klavyesini etkinleştirmeden önce, öykünücü anahtar girişi yalnızca denetim anahtarlarından kabul eder.  
  
 Windows geliştirme bilgisayarının yerelleştirilmiş bir sürümünün klavyesindeki özel karakterler öykünücü tarafından desteklenmez. Yerelleştirilmiş klavyede bulunan özel karakterler girmek için, bunun yerine yazılım giriş paneli 'ni (SIP) kullanın.  
  
 Bilgisayarınızın klavye öykünücüsünde kullanılması için, sayfa yukarı tuşu veya duraklatma/kesme anahtarı (Windows 8/8.1 öykünücüsü) veya F4 (Windows 10 öykünücüsü) tuşlarına basın.  
  
 Öykünücüsünde bilgisayarınızın klavye kullanımını durdurmak için, sayfa aşağı tuşuna veya duraklatma/kesme anahtarına (Windows 8/8.1 öykünücüsü) veya F4 (Windows 10 Emulator) tuşuna basın.  
  
 Aşağıdaki tabloda, bir Windows Phone düğmeleri ve diğer denetimleri bir benzemek için kullanabileceğiniz bir donanım klavyesindeki anahtarlar listelenmektedir.  
  
|Bilgisayar donanım anahtarı|Windows Phone donanım düğmesi|Notlar|  
|---------------------------|-----------------------------------|-----------|  
|F1|Geri|Uzun basma, beklendiği gibi çalışır.|  
|F2|BAŞıNDAN|Uzun basma, beklendiği gibi çalışır.|  
|F3|SEARCH||  
|F4|Windows 10 öykünücüsünde yerel bilgisayarın klavyesi kullanılarak değil, yerel bilgisayarın klavyesi kullanılarak geçiş yapar.|Windows 8/8.1 öykünücüsünde geçerli değildir.|  
|F5|Geçerli değildir.||  
|F6|KAMERA YARıSı|Yarı bir şekilde basılan, ayrılmış bir kamera düğmesi.|  
|F7|TAM KAMERA|Ayrılmış bir kamera düğmesi.|  
|F8|Geçerli değildir.||  
|F9|BIRIM YUKARı||  
|F10|BIRIM AŞAĞı||  
| F11|Geçerli değildir.||  
|F12|POWER|Kilit ekranını etkinleştirmek için F12 tuşuna iki kez basın.<br /><br /> Uzun basma, beklendiği gibi çalışır.|  
|LARıNA|Geri|Uzun basma, beklendiği gibi çalışır.|  
|DURAKLAT/KES|Klavyeyi değiştirme (yalnızca Windows 8/8.1 öykünücüsü).|Windows 10 öykünücüsü için geçerli değildir.|  
|SAYFA YUKARı|Donanım klavye (yalnızca Windows 8/8.1 öykünücüsü) etkinleştirilir.|Windows 10 öykünücüsü için geçerli değildir.|  
|SAYFA AŞAĞı|Donanım klavyesini devre dışı bırakır (yalnızca Windows 8/8.1 öykünücüsü).|Windows 10 öykünücüsü için geçerli değildir.|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> Özel kontrol noktalarını kaydetme ve yükleme  
 Öykünücü 'un **ek araçlarının** **denetim noktaları** sekmesini kullanarak öykünücü durumunun bir anlık görüntüsünü kaydedin. Uygulamanızı aynı veri ve ayarlarla sıklıkla test ediyorsanız bu özellik faydalıdır.  
  
 Örneğin, uygulamanız birkaç kişi gerektiriyorsa, kişi kayıtlarını bir kez oluşturabilir ve öykünücünün anlık görüntüsünü kaydedebilirsiniz. Aksi takdirde, öykünücüyü her başlattığınızda kişi kayıtlarını yeniden oluşturmanız gerekir.  
  
- Daha sonra uygulamanızı test etmek için gereken veri ve ayarlarla öykünücü durumunun yeni bir anlık görüntüsünü yakalamak için **Yeni denetim noktası** ' na tıklayın. Yeni denetim noktası **denetim noktaları** listesine eklenir.  
  
   Hata ayıklayıcı öykünücüye iliştirirken bir denetim noktası yakalayamazsınız.  
  
- Denetim noktası hakkındaki bilgileri görüntülemek için Denetim **noktaları** listesinde bir kontrol noktası seçin.  
  
- **Varsayılan** sütunda, etkin öykünücü için varsayılan denetim noktası olarak kaydedilmiş bir kontrol noktası oluşturmak için radyo düğmesini seçin.  
  
- Öykünücü üzerinde Windows Phone işletim sistemini yeniden başlatmak ve seçilen anlık görüntüyü yüklemek için **geri yükle** ' ye tıklayın.  
  
- Artık ihtiyacınız olmayan bir anlık görüntüyü silmek için **Sil** ' e tıklayın.  
  
  Özgün öykünücü görüntüsü, her zaman **kontrol noktaları** listesindeki ilk öğe olarak görünür ve değiştirilemez ya da silinemez. Bununla birlikte, varsayılan öykünücü görüntüsü olarak farklı bir anlık görüntü seçebilirsiniz.  
  
  ![Windows Phone öykünücüsünün denetim noktaları sekmesi](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> Öykünücüde ekran görüntülerini yakala  
 Ek araçlar penceresinden ekran görüntüsü aracını kullanarak, Windows Phone uygulamalarınızın ekran görüntülerini oluşturabilirsiniz. Araç, çalışan öykünücü çözümüyle eşleşen PNG dosyaları oluşturur.  
  
 ![Windows Phone öykünücüsünde ekran görüntüleri](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Yerleşik öykünücü ekran görüntüsü aracını kullanarak bir uygulama ekran görüntüsü oluşturmak için  
  
1. Ekran görüntülerinin kalitesini iyileştirmek için öykünücünün yakınlaştırma düzeyini yüzde 100 olarak ayarlayın. Yakınlaştırma düzeyini ne kadar yükseğe ayarlarsanız ekran görüntüsünün kalitesi de artar.  
  
2. Uygulamanızı öykünücüsünde başlatın.  
  
3. Öykünücü araç çubuğunda Genişlet düğmesine tıklayarak **ek araçlar** penceresini açın.  
  
4. **Ekran görüntüsü** sekmesine tıklayın.  
  
5. Uygulamanız hazırsanız **yakala** düğmesine tıklayın.  
  
    Ekran görüntüsü çalışma alanında görüntülenir.  
  
6. **Farklı kaydet** iletişim kutusunu açmak için **Kaydet** düğmesine tıklayın.  
  
7. İstediğiniz konum ve **dosya adını** seçin ve ardından **Kaydet**' e tıklayın.  
  
8. İsteğe bağlı olarak, uygulamanızdaki diğer sayfalara gidin ve ek ekran görüntüleri yakalayın.  
  
9. Farklı bir çözünürlükte aynı ekran görüntülerini yakalamak için farklı ekran çözünürlüğüyle bir öykünücü başlatın. Uygulamanızı hata ayıklama ile çalıştırdıysanız, başka bir öykünücü üzerinde yeniden çalıştırmadan önce hata ayıklamayı durdurmanız gerekir.  
  
   Windows Phone deposuna gönderilecek ekran görüntülerini yakalamadan önce öykünücü ekranındaki kare hızı sayaçlarını devre dışı bırakın.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Ekran görüntülerini yakalamaya başlamadan önce öykünücüsünde kare hızı sayaçlarını devre dışı bırakmak için  
  
- Visual Studio 'da bir yayın derlemesi belirtin. Bir yayın derlemesi belirttikten sonra, **derleme** menüsündeki **Dağıt _[uygulama adı]_ ** bağlantısını seçerek uygulamanızı başlatın.  
  
- Alternatif olarak, değerini olarak ayarlayan app.xaml.cs veya App. xaml. vb dosyasındaki kod satırını açıklama olarak ayarlayabilirsiniz `EnableFrameRateCounter` `true` .
