---
title: Simülatör 'de Windows Mağazası uygulamalarını çalıştırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96224b522b17ff9da520386d56d4fae7a04bd981
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144781"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Simülatörde Microsoft Store uygulamaları çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Mağazası uygulamaları için Visual Studio simülatör, bir Windows Mağazası uygulamasını taklit eden bir masaüstü uygulamasıdır. Geliştirme bilgisayarınızda uygulamalar çalıştırabilir ve ortak dokunmatik ve döndürme olaylarının benzetimini yapabilirsiniz. Ayrıca, öykünmek istediğiniz fiziksel ekran boyutunu ve çözünürlüğünü ve ağ bağlantısı özelliklerinin benzetimini seçebilirsiniz.  
  
 Simülatör, Windows Mağazası uygulamalarını tasarlama, geliştirme, hata ayıklama ve test etme işlemlerini kullanabileceğiniz bir ortam sağlar. Ancak, uygulamanızı Windows Mağazası 'na yayımlamadan önce, uygulamanızı gerçek bir cihazda test etmelisiniz.  
  
 Windows Mağazası uygulamaları için Visual Studio simülatör, yerel makinenizde yalıtılmış bir ortamda çalışmaz. Bu nedenle, kurtarılamayan sistem genelinde bir hata gibi benzeticide oluşan hatalar makinenin tamamını de etkileyebilir.  
  
 Windows Phone bilgi için bkz. [öykünücüsünde Windows Phone uygulamaları çalıştırma](../debugger/run-windows-phone-apps-in-the-emulator.md) .  
  
> [!IMPORTANT]
> Visual Studio 2015 simülatör, coğrafi konum düğmesini içermez. Bunun nedeni, Windows 10 simülatörü coğrafi konum simülasyonu içermez. Bu tür bir benzetim yapmanız gerekiyorsa, Windows 8.1 veya daha önceki işletim sistemlerinde Visual Studio 2013 simülasyonu kullanabilirsiniz.  
  
## <a name="BKMK_Set_the_simulator_as_the_target"></a>Simülatör 'ı hedef olarak ayarlayın  
 Windows mağazası uygulamanızı simülatör 'da çalıştırmak için hata ayıklayıcı **Standart** araç çubuğunda **hata ayıklamayı Başlat** düğmesinin yanındaki aşağı açılan listeden **simülatör** ' ı seçin.  
  
 ![Simülatör 'da çalıştırma](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="BKMK_Choose_an_interaction_mode"></a>Etkileşim modu seçin  
 Aşağıdaki etkileşim modlarını seçebilirsiniz  
  
- ![Fare modu düğmesi](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") Fare modu: etkileşim modunu fare hareketleri olarak ayarlar. Tıklama, Çift tıklama ve sürüklendiğinde fare hareketleri vardır.  
  
- ![Touch öykünme düğmesine başla](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Dokunma öykünmesini Başlat: etkileşim modunu, tek bir parmakla dokunma hareketlerine ayarlar. Tek parmakla olaylar arasında dokunma, sürükleme ve çekme dahildir.  
  
     ![Simülatör bir parmak hedefi](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") Tek hedef simgesi simülatör içindeki olayların konumunu gösterir. İşaretçiyi konumlandırmak için fareyi kullanın.  
  
     ![Bir Finger Touch hedefi](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") Dokunma modunu etkinleştirmek için sol fare düğmesine basın. Örneğin, bir dokunun benzetimini yapmak için düğmeye tıklayın veya sürüklerken ya da çekerek düğmeye basın ve basılı tutun.  
  
## <a name="pinch-and-zoom"></a>Pinç ve zoom  
 Etkileşim modunu iki parmağınızla bir Pinç ve yakınlaştırma hareketlerine ayarlar.  
  
- ![Simülatör iki parmak hedefi](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - Çift hedef simgesi, Cihaz ekranındaki iki parmağınızla konumunu gösterir.  

  - Simgeleri Cihaz ekranındaki nesnenin üzerine konumlandırmak için fareyi taşıyın.  

  - Bir veya daha fazla yakınlaştırma yapmadan önce iki parmağınızla oluşan sanal mesafeyi değiştirmek için fare tekerleğini geri veya ileri döndürün.  

- ![Pinç, yakınlaştırma ve döndürme hedefleri](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - Sol düğmesine basın ve tekerleği yakınlaştırmak için geri döndürün (Pinç).  

  - Sol düğmesine basın ve fare tekerleğini (yakınlaştırmadan uzağa) uzaklaştırmak için (yakınlaştırma) döndürün.  
  
## <a name="object-rotation"></a>Nesne döndürme  
 **Dokunma öykünmesi döndürme** düğmesi, etkileşim modunu iki parmağınızı kullanarak döndürme hareketlerine ayarlar.  
  
- Simgeleri Cihaz ekranındaki nesnenin üzerine konumlandırmak için fareyi taşıyın.  
  
  - Nesneyi döndürmeden önce iki parmağınızla oluşan sanal yönlendirmeyi değiştirmek için fare tekerleğini geri veya ileri döndürün.  

- Nesne sayacını saat yönünde döndürmek için sol düğmesine basın ve tekerleği geriye doğru döndürün (sizin için). Fare tekerleğini döndürürken, iki hedef simgenin biri diğerinin etrafında dönerek dönüşün göreli boyutunu gösterir.  

  - Sol düğmeye basın ve fare tekerleğini ileri döndürün (uygulamadan uzağa), nesneyi saat yönünde döndürün.  

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a>Always on üstteki modu etkinleştir veya devre dışı bırak  
 Simülatör penceresini her zaman diğer pencerelerin üstünde olacak şekilde ayarlayabilirsiniz. **En üstteki pencereyi aç** düğmesi simülatör penceresinin **Always on üstteki** modunu sunar veya devre dışı bırakır.  
  
## <a name="BKMK_Change_the_device_orientation"></a>Cihaz yönünü değiştirme  
 Simülatör 90 derece bir yöne döndürerek dikey ve yatay arasındaki cihaz yönünü değiştirebilirsiniz.  
  
> [!NOTE]
> Simülatör bir projenin [DisplayProperties. oto Rotationpreferences](https://go.microsoft.com/fwlink/?LinkId=249460) özelliğini dikkate almaz. Örneğin, projeniz yönü `Landscape`olarak ayarlarsa ve simülatörü dikey yönlendirmeye döndürdüğünüzde simülatör görüntü görüntüsü de döndürülür ve yeniden boyutlandırılır. Bu ayarları gerçek bir cihazda test edin.  
  
> [!NOTE]
> Simülatör 'in bir kenarının, üzerinde görüntülenen ekrandan daha büyük olması için simülatörü döndürdüğünüzde, simülatör ekran içine sığacak şekilde otomatik olarak yeniden boyutlandırılır. Yeniden döndürürseniz simülatör özgün boyutuna yeniden boyutlandırılmaz.  
  
## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a>Sanal ekran boyutunu ve çözünürlüğünü değiştirme  
 Sanal ekran boyutunu ve çözünürlüğünü değiştirmek için paletteki **çözümü Değiştir** düğmesini seçin ve listeden yeni bir boyut ve çözünürlük seçin.  
  
 Ekran boyutu ve çözümlemesi *, ekran genişliği inç, piksel genişliği X piksel yüksekliği*olarak listelenir. Hem ekran boyutunun hem de çözümlemenin benzetildiğini unutmayın. Simülatörde birlikte bulunan konum, seçilen cihaz boyutunun ve çözünürlüğündeki ortak ordinına çevrilir.  
  
> [!NOTE]
> Uygulamanıza bit eşlem görüntülerinin ölçeklendirilen sürümlerini kaydedebilir ve Windows geçerli ölçek için doğru görüntüyü yükler. Daha fazla bilgi için bkz. [yanıt veren tasarım 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Ancak, Windows 'un çözünürlüğe uyacak şekilde farklı bir görüntü görebilmesi için simülatör çözünürlüğünü değiştirirseniz, yeni görüntüyü görüntülemek için hata ayıklama oturumunuzu durdurup yeniden başlatmanız gerekir.  
  
## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Windows Mağazası 'na göndermek için uygulamanızın ekran görüntüsünü yakalayın  
 Windows uygulama mağazası 'na bir uygulama gönderdiğinizde, uygulamanın ekran görüntülerini dahil etmeniz gerekir.  
  
> [!NOTE]
> Ekran görüntüsü, simülatör 'ın geçerli çözümüne kaydedilir. Çözünürlüğü değiştirmek için, **çözümü Değiştir** düğmesini seçin.  
  
- Simülatörden uygulamanızın ekran görüntülerini oluşturmak için **ekran görüntüsünü panoya yakala** düğmesini seçin.  
  
- Ekran görüntülerinin bulunduğu konumu ayarlamak için **ekran görüntüsü ayarları** düğmesini seçin ve kısayol menüsünden konumu seçin.  
  
     ![Ekran görüntüsü ayarları bağlam menüsü](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="BKMK_Simulate_network_connection_properties"></a>Ağ bağlantısı özelliklerinin benzetimini yap  
 Ağ bağlantısı maliyetinin veya veri planı durum değişikliklerinin farkında olmadan ve uygulamanızın bu bilgileri kullanarak dolaşım veya bir yandan bu bilgileri aşmasını önlemek için bu bilgileri kullanmasını sağlayarak uygulamanızın kullanıcılarına tarifeli ağ bağlantısı maliyetini yönetmesine yardımcı olabilirsiniz. Belirtilen veri aktarımı sınırı. [Windows. Networking. Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) API 'leri, oturum açmak Için [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) ve [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) olaylarına yanıt vermenizi sağlar. Bkz. [hızlı başlangıç: tarifeli ağ maliyeti kısıtlamalarını yönetme](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Ağ maliyetinizi algılayan kodunuzun hatalarını ayıklamak veya test etmek için simülatör, [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)tarafından döndürülen [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) nesnesi aracılığıyla kullanıma sunulan bir ağın özelliklerini taklit edebilir.  
  
 Ağ özelliklerinin benzetimini yapmak için:  
  
1. Simülatör araç çubuğunda **ağ özelliklerini değiştir** düğmesini seçin.  
  
2. **Ağ özelliklerini ayarla** iletişim kutusunda, **sanal ağ özelliklerini kullan**' ı seçin.  
  
    Benzetimi kaldırmak ve şu anda bağlı olan arabirimin Ağ özelliklerine dönmek için onay kutusunu temizleyin.  
  
3. Sanal ağ için bir **profil adı** girin. [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) nesnesinin [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) özelliğinde benzetimi tanımlamak için kullanabileceğiniz benzersiz bir ad kullanmanızı öneririz.  
  
4. **Ağ maliyet türü** listesinden profil Için [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) değerini seçin.  
  
5. **Veri sınırı durum bayrağı** listesinden, [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) özelliğini veya [oververiııt](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)özelliğini true olarak ayarlayabilir ya da her iki değeri de false olarak ayarlamak için **veri sınırı altında** seçeneğini belirleyebilirsiniz.  
  
6. **Dolaşım durumu** listesinden [dolaşım](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) özelliğini ayarlayın.  
  
7. Ön plan [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) olayını tetikleyerek ve **NetworkStateChange**türünde bir arka plan [sistem tetikleyicisi](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) Ile ağ özelliklerinin benzetimini yapmak için **Özellikleri ayarla** ' yı seçin.  
  
   **Ağ bağlantılarını yönetme hakkında daha fazla bilgi**  
  
   [Hızlı başlangıç: tarifeli ağ maliyeti kısıtlamalarını yönetme](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ağ bilgileri örneği](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Enerji kullanımını çözümleme](../profiling/analyze-energy-use-in-store-apps.md)  
    
   [Windows. Networking. Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Arka plan görevleriyle sistem olaylarına yanıt verme](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Windows Mağazası uygulamalarında askıya alma, sürdürülme ve arka plan olaylarını tetikleme](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a>Klavyeye Benzetici ile gezinme  
 Simülatör penceresi simülatör araç çubuğuna odaklanmak için **Ctrl + Alt + Yukarı ok** tuşlarına basarak simülatör araç çubuğuna gidebilirsiniz. Araç çubuğu düğmeleri arasında gezinmek için **yukarı oku** ve **aşağı oku** kullanın.  
  
 **Ctrl + Alt + F4**tuşlarına basarak simülatörü kapatabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md)
