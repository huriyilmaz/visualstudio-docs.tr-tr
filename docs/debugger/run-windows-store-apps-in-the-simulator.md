---
title: Simülatörde UWP uygulamaları çalıştırma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9b46abc4d22ddfdc551669d3bcd4cba5acf7cce4
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599522"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Simülatörde UWP uygulamaları çalıştırma

UWP uygulamaları için Visual Studio simülatör, UWP uygulamasını taklit eden bir masaüstü uygulamasıdır. Genellikle, yerel makinede, bağlı bir cihazda veya uzak makinede hata ayıklaması yapmanız gerekir. Ancak, bazı senaryolarda, farklı bir fiziksel ekran boyutu ve çözümüne öykünmek için Visual Studio simülatörü kullanmak isteyebilirsiniz. Ayrıca, ortak dokunma ve döndürme olaylarının benzetimini yapabilir ve ağ bağlantısı özelliklerinin benzetimini yapabilirsiniz.

Simülatör, UWP uygulamalarını tasarlamak, geliştirmek, hatalarını ayıklamak ve test etmek için kullanabileceğiniz bir ortam sağlar. Ancak, uygulamanızı Microsoft Store için yayımlamadan önce, uygulamanızı gerçek bir cihazda test etmelisiniz.

UWP uygulamaları için Visual Studio simülatörü, yerel makinenizde yalıtılmış bir ortamda çalışmaz. Bu nedenle, kurtarılamayan sistem genelinde bir hata gibi benzeticide oluşan hatalar makinenin tamamını de etkileyebilir.

> [!IMPORTANT]
> Visual Studio 2015 simülatör, coğrafi konum düğmesini içermez. Bunun nedeni, Windows 10 simülatörü coğrafi konum simülasyonu içermez.

## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> Simülatör 'ı hedef olarak ayarlayın

UWP uygulamanızı benzeticide çalıştırmak için hata ayıklayıcı **Standart** araç çubuğunda **hata ayıklamayı Başlat** düğmesinin yanındaki aşağı açılan listeden **simülatör** ' ı seçin. Bu seçenek, yalnızca uygulamanızın **hedef platform min. sürümü** geliştirme makinenizdeki işletim sistemine eşit veya ondan küçükse kullanılabilir.

![Simülatör 'da çalıştırma](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> Etkileşim modu seçin

Aşağıdaki etkileşim modlarını seçebilirsiniz:

- ![Fare modu düğmesi](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Fare modu: etkileşim modunu fare hareketleri olarak ayarlar. Tıklama, Çift tıklama ve sürüklendiğinde fare hareketleri vardır.

- ![Touch öykünme düğmesine başla](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Dokunma öykünmesini Başlat: etkileşim modunu, tek bir parmakla dokunma hareketlerine ayarlar. Tek parmakla olaylar arasında dokunma, sürükleme ve çekme dahildir.

   ![Simülatör bir parmak hedefi](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   Tek hedef simgesi simülatör içindeki olayların konumunu gösterir. İşaretçiyi konumlandırmak için fareyi kullanın.

   ![Bir Finger Touch hedefi](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Dokunma modunu etkinleştirmek için sol fare düğmesine basın. Örneğin, bir dokunun benzetimini yapmak için düğmeye tıklayın veya sürüklerken ya da çekerek düğmeye basın ve basılı tutun.

## <a name="pinch-and-zoom"></a>Pinç ve zoom

Etkileşim modunu iki parmağınızla bir Pinç ve yakınlaştırma hareketlerine ayarlar.

![Simülatör iki parmak hedefi](../debugger/media/simulator_twofinger.png)

Çift hedef simgesi, Cihaz ekranındaki iki parmağınızla konumunu gösterir.

- Simgeleri Cihaz ekranındaki nesnenin üzerine konumlandırmak için fareyi taşıyın.

- Bir veya daha fazla yakınlaştırma yapmadan önce iki parmağınızla oluşan sanal mesafeyi değiştirmek için fare tekerleğini geri veya ileri döndürün.

![Pinç, yakınlaştırma ve döndürme hedefleri](../debugger/media/simulator_twofingerengaged.png)

- Sol düğmesine basın ve tekerleği yakınlaştırmak için geri döndürün (Pinç).

- Sol düğmesine basın ve fare tekerleğini (yakınlaştırmadan uzağa) uzaklaştırmak için (yakınlaştırma) döndürün.

## <a name="object-rotation"></a>Nesne döndürme

**Dokunma öykünmesi döndürme** düğmesi, etkileşim modunu iki parmağınızı kullanarak döndürme hareketlerine ayarlar.

- Simgeleri Cihaz ekranındaki nesnenin üzerine konumlandırmak için fareyi taşıyın. Nesneyi döndürmeden önce iki parmağınızla oluşan sanal yönlendirmeyi değiştirmek için fare tekerleğini geri veya ileri döndürün.

- Nesne sayacını saat yönünde döndürmek için sol düğmesine basın ve tekerleği geriye doğru döndürün (sizin için). Fare tekerleğini döndürürken, iki hedef simgenin biri diğerinin etrafında dönerek dönüşün göreli boyutunu gösterir.

- Sol düğmeye basın ve fare tekerleğini ileri döndürün (uygulamadan uzağa), nesneyi saat yönünde döndürün.

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Always on üstteki modu etkinleştir veya devre dışı bırak
 Simülatör penceresini her zaman diğer pencerelerin üstünde olacak şekilde ayarlayabilirsiniz. **En üstteki pencereyi aç** düğmesi simülatör penceresinin **Always on üstteki** modunu sunar veya devre dışı bırakır.

## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> Cihaz yönünü değiştirme
 Simülatör 90 derece bir yöne döndürerek dikey ve yatay arasındaki cihaz yönünü değiştirebilirsiniz.

> [!NOTE]
> Simülatör bir projenin [DisplayProperties. oto Rotationpreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) özelliğini dikkate almaz. Örneğin, projeniz yönü olarak ayarlarsa `Landscape` ve simülatörü dikey yönlendirmeye döndürdüğünüzde simülatör görüntü görüntüsü de döndürülür ve yeniden boyutlandırılır. Bu ayarları gerçek bir cihazda test edin.

> [!NOTE]
> Simülatör 'in bir kenarının, üzerinde görüntülenen ekrandan daha büyük olması için simülatörü döndürdüğünüzde, simülatör ekran içine sığacak şekilde otomatik olarak yeniden boyutlandırılır. Yeniden döndürürseniz simülatör özgün boyutuna yeniden boyutlandırılmaz.

## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Sanal ekran boyutunu ve çözünürlüğünü değiştirme
 Sanal ekran boyutunu ve çözünürlüğünü değiştirmek için paletteki **çözümü Değiştir** düğmesini seçin ve listeden yeni bir boyut ve çözünürlük seçin.

 Ekran boyutu ve çözümlemesi *, ekran genişliği inç, piksel genişliği X piksel yüksekliği*olarak listelenir. Hem ekran boyutunun hem de çözümlemenin benzetildiğini unutmayın. Simülatörde birlikte bulunan konum, seçilen cihaz boyutuna ve çözümüne çevrilir.

> [!NOTE]
> Uygulamanıza bit eşlem görüntülerinin ölçeklendirilen sürümlerini kaydedebilir ve Windows geçerli ölçek için doğru görüntüyü yükler. Daha fazla bilgi için bkz. [Tasarım ve UI girişi](/windows/uwp/layout/design-and-ui-intro). Ancak, Windows 'un çözünürlüğe uyacak şekilde farklı bir görüntü görebilmesi için simülatör çözünürlüğünü değiştirirseniz, yeni görüntüyü görüntülemek için hata ayıklama oturumunuzu durdurup yeniden başlatmanız gerekir.

## <a name="capture-a-screenshot-of-your-app-for-submission-to-microsoft-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Microsoft Store göndermek için uygulamanızın ekran görüntüsünü yakalayın
 Microsoft Store bir uygulama gönderdiğinizde, uygulamanın ekran görüntülerini dahil etmeniz gerekir.

> [!NOTE]
> Ekran görüntüsü, simülatör 'ın geçerli çözümüne kaydedilir. Çözünürlüğü değiştirmek için, **çözümü Değiştir** düğmesini seçin.

- Simülatörden uygulamanızın ekran görüntülerini oluşturmak için **ekran görüntüsünü panoya yakala** düğmesini seçin.

- Ekran görüntülerinin bulunduğu konumu ayarlamak için **ekran görüntüsü ayarları** düğmesini seçin ve kısayol menüsünden konumu seçin.

   ![Ekran görüntüsü ayarları bağlam menüsü](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> Ağ bağlantısı özelliklerinin benzetimini yap

Ağ bağlantısı maliyetinin veya veri planı durum değişikliklerinin farkında tutarak ve uygulamanızın bu bilgileri kullanarak dolaşım veya belirtilen bir veri aktarım limitini aşmaktan kaçınmak için bu bilgileri kullanmasını sağlayarak uygulamanızın kullanıcılarına tarifeli ağ bağlantısı maliyetini yönetmesine yardımcı olabilirsiniz. [Windows. Networking. Connectivity](/uwp/api/windows.networking.connectivity) API 'leri, oturum açmak Için [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) ve [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) olaylarına yanıt vermenizi sağlar. Bkz. [hızlı başlangıç: tarifeli ağ maliyeti kısıtlamalarını yönetme](/previous-versions/windows/apps/hh750310(v=win.10)).

Ağ maliyetinizi algılayan kodunuzun hatalarını ayıklamak veya test etmek için simülatör, [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation)tarafından döndürülen [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) nesnesi aracılığıyla kullanıma sunulan bir ağın özelliklerini taklit edebilir.

Ağ özelliklerinin benzetimini yapmak için:

1. Simülatör araç çubuğunda **ağ özelliklerini değiştir** düğmesini seçin.

2. **Ağ özelliklerini ayarla** iletişim kutusunda, **sanal ağ özelliklerini kullan**' ı seçin.

    Benzetimi kaldırmak ve şu anda bağlı olan arabirimin Ağ özelliklerine dönmek için onay kutusunu temizleyin.

3. Sanal ağ için bir **profil adı** girin. [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) nesnesinin [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) özelliğinde benzetimi tanımlamak için kullanabileceğiniz benzersiz bir ad kullanmanızı öneririz.

4. **Ağ maliyet türü** listesinden profil Için [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) değerini seçin.

5. **Veri sınırı durum bayrağı** listesinden, [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) özelliğini veya [oververiııt](/uwp/api/windows.networking.connectivity.connectioncost) özelliğini true olarak ayarlayabilir ya da her iki değeri de false olarak ayarlamak için **veri sınırı altında** seçeneğini belirleyebilirsiniz.

6. **Dolaşım durumu** listesinden [dolaşım](/uwp/api/windows.networking.connectivity.connectioncost) özelliğini ayarlayın.

7. Ön plan [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) olayını tetikleyerek ve **NetworkStateChange**türünde bir arka plan [sistem tetikleyicisi](/uwp/api/windows.applicationmodel.background.systemtrigger) Ile ağ özelliklerinin benzetimini yapmak için **Özellikleri ayarla** ' yı seçin.

Ağ bağlantılarını yönetme hakkında daha fazla bilgi için bkz.:

[Hızlı başlangıç: tarifeli ağ maliyeti kısıtlamalarını yönetme](/previous-versions/windows/apps/hh750310(v=win.10))

[Ağ bilgileri örneği](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Enerji kullanımını çözümleme](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows. Networking. Connectivity](/uwp/api/windows.networking.connectivity)

[Arka plan görevleriyle sistem olaylarına yanıt verme](/previous-versions/windows/apps/hh977058(v=win.10))

[UWP uygulamalarında askıya alma, sürdürme ve arka plan olayları tetikleme](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Klavyeye Benzetici ile gezinme

Simülatör penceresi simülatör araç çubuğuna odaklanmak için **Ctrl + Alt + Yukarı ok** tuşlarına basarak simülatör araç çubuğuna gidebilirsiniz. Araç çubuğu düğmeleri arasında gezinmek için **yukarı oku** ve **aşağı oku** kullanın.

**Ctrl + Alt + F4**tuşlarına basarak simülatörü kapatabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’dan uygulamaları çalıştırma](debugging-windows-store-and-windows-universal-apps.md)