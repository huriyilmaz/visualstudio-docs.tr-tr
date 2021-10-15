---
title: Simülatörde UWP uygulamalarını | Microsoft Docs
description: UWP uygulamasının benzetimini Windows masaüstü uygulaması olan Visual Studio simülatörde Universal Windows Platform (UWP) uygulamalarını çalıştırmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 29de5f0ff7d0ae040923bd24f1db712f39e15cf6
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130010749"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Simülatörde UWP uygulamaları çalıştırma

UWP Visual Studio simülatör, UWP uygulamasının benzetimini yapılan bir masaüstü uygulamasıdır. Genellikle, yerel makinede, bağlı bir cihazda veya uzak makinede hata ayıklamak istersiniz. Ancak bazı senaryolarda, farklı bir fiziksel ekran boyutuna ve Visual Studio benzetim yapmak için Visual Studio simülatörünü kullanmak istiyor olabilirsiniz. Ayrıca ortak dokunma ve döndürme olaylarını simüle etmek ve ağ bağlantısı özelliklerinin benzetimini yapmak için de kullanılabilirsiniz.

Simülatör, UWP uygulamalarını tasarlama, geliştirme, hata ayıklama ve test etmek için bir ortam sağlar. Ancak, uygulamayı Microsoft Store yayımlamadan önce gerçek bir cihazda test edin.

UWP Visual Studio simülatör, yerel makineniz üzerinde yalıtılmış bir ortamda çalışmaz. Bu nedenle, kurtarılamaz sistem genelindeki bir hata gibi simülatörde oluşan hatalar da makinenin tamamını etkileyebilir.

> [!IMPORTANT]
> Visual Studio 2015 simülatörü coğrafi konum düğmesini içermez. Bunun nedeni, Windows 10 benzetimi içermemedir.

## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> Simülatörü hedef olarak ayarlama

UWP uygulamanızı simülatörde  çalıştırmak için, hata ayıklayıcı  Standart araç çubuğundaki Hata Ayıklamayı Başlat düğmesinin yanındaki açılan listeden Simülatör'ü seçin.  Bu seçenek yalnızca, uygulamanın Hedef **Platform En Düşük** Sürümü geliştirme makinenizin işletim sisteminden küçük veya ona eşitse kullanılabilir.

![Simülatörde Çalıştırma](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> Etkileşim modu seçme

Aşağıdaki etkileşim modlarını seçebilirsiniz:

- ![Fare modu düğmesi](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Fare modu: Etkileşim modunu fare hareketleri olarak ayarlar. Fare hareketleri tıklamaları, çift tıklamaları ve sürüklemeleri içerir.

- ![Dokunma öykünmesi başlat düğmesi](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Dokunma öykünmesi başlatma: Etkileşim modunu tek bir parmakla dokunma hareketleri olarak ayarlar. Tek parmaklı olaylar dokunmayı, sürüklemeyi ve çekmeyi içerir.

   ![Simülatör tek parmak hedefi](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   Tek hedef simgesi simülatörde olayların konumunu gösterir. İşaretçiyi konumlandırmak için fareyi kullanın.

   ![Tek parmakla dokunma hedefi](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Dokunma modunu etkinleştirmek için farenin sol düğmesine basın. Örneğin dokunma simülasyonu yapmak için düğmeye tıklayın veya sürükle veya çekerek düğmeyi basılı tutun.

## <a name="pinch-and-zoom"></a>Sıkıştırma ve Yakınlaştırma

etkileşim modunu iki parmakla sıkıştırıp yakınlaştırmak için ayarlar.

![Simülatör iki parmak hedefi](../debugger/media/simulator_twofinger.png)

Çift hedef simgesi, cihaz ekranındaki iki parmak konumunu gösterir.

- Simgeleri cihaz ekranında nesnenin üzerine konumlandırmak için fareyi hareket ettirin.

- Sıkıştırma veya yakınlaştırmadan önce iki parmak arasındaki simülasyon mesafesini değiştirmek için fare tekerleğini geri veya ileri döndürün.

![Hedefleri sıkıştırma, yakınlaştırma ve döndürme](../debugger/media/simulator_twofingerengaged.png)

- Sol düğmeye basın ve yakınlaştırmak (sıkıştırma) için tekerleği geriye (size doğru) döndürün.

- Sol düğmeye basın ve uzaklaştırmak (yakınlaştırma) için fare tekerleğini ileri (uzak) döndürün.

## <a name="object-rotation"></a>Nesne döndürme

Dokunma **öykünmesi döndürme** düğmesi, iki parmak kullanarak etkileşim modunu döndürme hareketlerine ayarlar.

- Simgeleri cihaz ekranında nesnenin üzerine konumlandırmak için fareyi hareket ettirin. Nesneyi döndürmeden önce iki parmakla ilgili simülasyon yönünü değiştirmek için fare tekerleğini geri veya ileri döndürün.

- Nesneyi saat yönünün tersine döndürmek için sol düğmeye basın ve tekerleği geriye (size doğru) döndürün. Fare tekerleğini döndürünce, iki hedef simgeden biri, döndürmenin göreli boyutunu belirtmek için diğerini döndürmektedir.

- Nesneyi saat yönünde döndürmek için sol düğmeye basın ve fare tekerleğini ileri (uzak) döndürün.

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Always on top modunu etkinleştirme veya devre dışı bırakma
 Simülatör penceresini her zaman diğer pencerelerin üstünde olacak şekilde ayarlayın. En **ÜstTeki Pencereyi Aç/Aç** düğmesi, simülatör penceresinin Her zaman **en üstteki** modunu açar veya devre dışı bıraktırır.

## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> Cihaz yönünü değiştirme
 Simülatörü herhangi bir yönde 90 derece döndürerek dikey ve yatay arasında cihaz yönünü değiştirebilirsiniz.

> [!NOTE]
> Simülatör, bir [projenin DisplayProperties.AutoRotationPreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) özelliğine uygun değildir. Örneğin, projeniz yönlendirmeyi olarak ayarlarsa ve ardından simülatörü dikey yönlendirmeye döndürecek olursanız simülatör görüntü görüntüsü de döndürülür `Landscape` ve yeniden boyutlandırılır. Bu ayarları gerçek bir cihazda test edin.

> [!NOTE]
> Simülatörün bir kenarının görüntülenen ekrandan daha büyük olması için simülatörü döndürün. Simülatör, ekranın içine sığacak şekilde otomatik olarak yeniden boyutlandırılır. Simülatörü yeniden döndürerek özgün boyutuna yeniden boyutlandırılmaz.

## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Simülasyon ekranı boyutunu ve çözünürlüğünü değiştirme
 Simüle ekran boyutunu ve çözünürlüğü  değiştirmek için paletde Çözünürlüğü Değiştir düğmesini seçin ve listeden yeni bir boyut ve çözünürlük seçin.

 Ekran boyutu ve çözünürlüğü Ekran genişliği inç, piksel *genişliği X piksel yükseklik olarak listelenir.* Hem ekran boyutunun hem de çözünürlüğün simülasyonu olduğunu unutmayın. Simülatörde konum koordinatları seçilen cihaz boyutuna ve çözünürlüğüne çevrilir.

> [!NOTE]
> Bit eşlem görüntülerinin ölçeklendirilmiş sürümlerini uygulamanıza kaydedebilirsiniz Windows geçerli ölçek için doğru görüntüyü yükleyebilirsiniz. Ancak, simülatör çözünürlüğünü, çözüme uyacak Windows farklı bir görüntü seçecek şekilde değiştirirsanız, yeni görüntüyü görüntülemek için hata ayıklama oturumlarınızı durdurmanız ve yeniden başlatmanız gerekir.

## <a name="capture-a-screenshot-of-your-app-for-submission-to-microsoft-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Microsoft Store'a gönderim için uygulamanın ekran Microsoft Store
 Bir uygulamayı Microsoft Store, uygulamanın ekran görüntülerini dahil edin.

> [!NOTE]
> Ekran görüntüsü, simülatörün geçerli çözünürlüğünde kaydedilir. Çözünürlüğü değiştirmek için Çözümlemeyi Değiştir **düğmesini** seçin.

- Simülatörden uygulama ekran görüntüleri oluşturmak için Panoya ekran **görüntüsü yakala düğmesini** seçin.

- Ekran görüntülerinin bulunduğu konumu ayarlamak için Ekran görüntüsü ayarları **düğmesini** ve kısayol menüsünden konumu seçin.

   ![Ayarlar bağlam menüsünün ekran görüntüsü](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> Ağ bağlantısı özelliklerinin benzetimini

Ağ bağlantısı maliyeti veya veri planı durumu değişikliklerinin farkındalığını koruyarak ve dolaşım için ek maliyetler ödemesini veya belirtilen veri aktarımı sınırını aşmayı önlemek için bu bilgileri kullanmalarını sağlayarak, uygulama kullanıcılarının tarifeli ağ bağlantılarının maliyetini yönetmesinde yardımcı olabilirsiniz. Aşağıdaki [Windows. Networking.Connectivity](/uwp/api/windows.networking.connectivity) API'leri, [imzalayan NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) ve [TriggerType olaylarına](/uwp/api/windows.applicationmodel.background.systemtrigger) yanıt vermenizi sağlar. Bkz. [Hızlı Başlangıç: Tarifeli ağ maliyeti kısıtlamalarını yönetme.](/previous-versions/windows/apps/hh750310(v=win.10))

Simülatör, ağ maliyetine uygun kodda hata ayıklamak veya test etmek için [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation)tarafından döndürülen [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) nesnesi aracılığıyla açığa çıkarilen bir ağın özelliklerini taklit eder.

Ağ özelliklerinin benzetimini yapmak için:

1. Simülatör araç çubuğunda Ağ özelliklerini **değiştir düğmesini** seçin.

2. Ağ Özelliklerini **Ayarla iletişim kutusunda** Sanal ağ özelliklerini **kullan'ı seçin.**

    Simülasyonu kaldırmak ve o anda bağlı olan arabirimin ağ özelliklerine dönmek için onay kutusunun işaretini kaldırın.

3. Sanal **ağ için** bir Profil Adı girin. [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) nesnesinin [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) özelliğinde simülasyonu tanımlamak için kullanabileceğiniz benzersiz bir ad kullanılması önerilir.

4. Ağ Maliyet Türü listesinden profil için [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) **değerini** seçin.

5. Veri Sınırı Durum **Bayrağı** [listesinden ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) özelliğini veya [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) özelliğini true olarak  ayarlayın veya Veri Sınırının Altında'ı seçip her iki değeri de false olarak ayarlayın.

6. Dolaşım **Durumu listesinden** Roaming [özelliğini](/uwp/api/windows.networking.connectivity.connectioncost) ayarlayın.

7. Bir **ön plan** [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) olayı ve NetworkStateChange türünde bir arka plan [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) tetikleerek ağ özelliklerinin benzetimini yapmak için **Özellikleri Ayarla'yı seçin.**

Ağ bağlantılarını yönetme hakkında daha fazla bilgi için bkz:

[Hızlı Başlangıç: Tarifeli ağ maliyeti kısıtlamalarını yönetme](/previous-versions/windows/apps/hh750310(v=win.10))

[Ağ bilgileri örneği](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Enerji kullanımını çözümleme](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows. Networking.Connectivity](/uwp/api/windows.networking.connectivity)

[Arka plan görevleriyle sistem olaylarına yanıt verme](/previous-versions/windows/apps/hh977058(v=win.10))

[UWP uygulamalarında askıya alma, sürdürme ve arka plan olayları tetikleme](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Klavye ile simülatörde gezinme

Simülatör penceresinden simülatör araç çubuğuna odağı **değiştirmek için CTRL + ALT + Yukarı** Ok tuşlarına basarak simülatör araç çubuğunda gezinebilirsiniz. Araç çubuğu **düğmeleri arasında** hareket etmek için **Yukarı Ok** ve Aşağı Ok tuşlarını kullanın.

**CTRL + ALT + F4 tuşlarına basarak simülatörü kapatarak kapatarak.**

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’dan uygulamaları çalıştırma](debugging-windows-store-and-windows-universal-apps.md)
