---
title: Grafik Bilgilerini Yakalama | Microsoft Docs
description: İşleme sorunlarını ve performans sorunlarını tanılamak için Visual Studio Grafik Çözümleyicisi'yi kullanmak için Direct3D uygulamanıza ait grafik bilgilerini yakalama.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d5334a7b4cfde556b269f21669fe1a22f9322292
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105255"
---
# <a name="capturing-graphics-information"></a>Grafik Bilgilerini Yakalama
İşleme sorunlarını ve performans sorunlarını tanılamak için Visual Studio Grafik Çözümleyicisi'yi kullanmak için Direct3D uygulamanıza ait grafik bilgilerini yakalama.

## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
 Graf bilgilerini yakalama iki adımlı bir işlemdir. Önce uygulamanızı Grafik Tanılama altında çalıştırın ve sonra ayrıntılı bilgilerini yakalamak üzere bir veya daha fazla kare belirtin.

### <a name="to-run-your-app-under-graphics-diagnostics"></a>Uygulamanızı Grafik Tanılama altında çalıştırmak için

- Menü çubuğunda Hata Ayıkla, **Grafikler,** Grafik **Hata Ayıklamayı** **Başlat'ı seçin.** (Klavye: Alt+F5 tuşlarına basın)

- Grafik araç **çubuğunda** Grafik Hata **Ayıklamayı Başlat düğmesini** seçin.

  Bir uygulama Grafik Tanılama altında çalışırken, belirli grafik bilgisi türleri sürekli olarak yakalanır; bunlar cihaz kurulumu, takas zincirinin oluşturulması, grafik nesnelerinin ve kaynakların oluşturulması ve birden fazla kareyi etkileyen diğer önemli olayları içerir. Aynı zamanda, belirli kareler hakkında ayrıntılı bilgiler yakalayabilirsiniz; Direct3D nesneleri ve bunları destekleyen kaynaklar ile birlikte çizim çağrıları ve hesaplayıcı-gölgelendirici sevkleri buna dahildir.

### <a name="to-capture-a-frame"></a>Bir kareyi yakalamak için

- Bu Visual Studio Grafik araç **çubuğunda Çerçeve** yakala düğmesine **Grafikler** yakalama düğmesi simgesi ![tıklayın.](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

- Klavyede Yazdırma Ekranı tuşuna basın.

  > [!NOTE]
  > Bir uygulama, Grafik Tanılama **altında** çalışırken, Yazdırma Ekranı anahtarı yalnızca bir grafik bilgisi çerçevesi yakalamak için kullanılabilir; normal işlevini gerçekleştirmez. Başka bir uygulama odakta olsa bile, grafik bilgilerini yakalamayı durduruncaya kadar (genellikle hata ayıklamayı durdurarak veya uygulamadan normal yolla çıkarak) bu durum devam eder.

- Visual Studio yakalama arabiriminde Tanılama oturumu zaman çizelgesinin altında  bulunan Çerçeve yakala düğmesini  seçin veya Ikinci  kulvar başına çerçeveler'in altında ve daha önce yakalanan çerçevelerin sağ tarafından bulunan büyük Yakalama Çerçevesi düğmesini seçin.  Her iki düğme de aşağıdaki görüntüde vurgulanmıştır.

   ![GPU Kullanımı aracını kullanarak kareleri yakalama.](media/pix_gpu_usage_tool_capture_frame.png)

   Yakaladığınız kareleri incelemeye hazır olduğunda, görüntü küçük resimlerinin üzerindeki Çerçeve **...** bağlantısını takip edin veya küçük resime çift tıklayarak **Visual Studio Graphics Analyzer'ı** çalıştırın.

  Yalnızca tam kareler yakalanır, bu nedenle bir yakalamayı başlattığında bu, kaydedilen sonraki karedeki grafik bilgileridir. Kayıt, yakalama işlemini başlattığınız kare sunulduktan hemen sonra başlar ve yakalanan kare sunulduğunda sona erer. Uygulama Grafik Tanılama altında çalışırken istediğiniz sayıda kare yakalayabilirsiniz. Hiçbir kare yakalamazsanız, grafik günlüğü atılır.

  Çerçeveleri yakalayan Visual Studio tanılama oturumu (.diagsession) penceresini görüntüler. Bu pencereyi kapatırsanız, hata ayıklamayı durdurursanız veya uygulamayı kapatırsanız, o günlüğe daha fazla kare yakalayabilirsiniz. Daha fazla grafik bilgisi yakalamak için uygulamayı yeni bir tanılama oturumu Grafik Tanılama altında yeniden çalıştırmalısınız.

### <a name="graphics-diagnostics-capture-options"></a>Grafik Tanılama Yakalama Seçenekleri
 Yakalamayı tüm grafik olayları veya sınırlı bir alt küme için çağrı yığınlarını toplamak, yakalama HUD'sini devre dışı bırakmak ve yakalama uyumluluk modunu etkinleştirmek veya devre dışı bırakmak için yapılandırabilirsiniz.

#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Yakalama seçeneklerini Grafik Tanılama için

1. Menü çubuğunda Araçlar, Seçenekler'i seçin. Seçenekler iletişim kutusu görüntülenir.

2. Sol tarafta yer alan seçenekler kategorisi listesinde, Grafik Tanılama'ı seçin ve Grafik Tanılama seçenekleri yapılandırabilirsiniz.

     **Yakalama sırasında çağrı yığınlarını toplama (yakalamayı daha yavaş yapar)** Çağrı yığınlarını toplamak için bu kutuyu işaretleyin. Varsayılan olarak, çağrı yığınları toplanmaz. Çağrı yığınlarını yakalamak için Yakalama sırasında çağrı yığınlarını topla **(yakalamayı** daha yavaş yapar) onay kutusunun koleksiyonu etkinleştirmek için ayarlanmış olduğundan emin olun ve ardından yalnızca en önemli çağrı  yığınlarını toplamak için **draw, dispatch, present ve perf markers** seçeneğini (varsayılan) veya tüm çağrı yığınlarını toplamak için her şey seçeneğini ayarlayın. Daha sonra çağrı yığınlarını toplamayı durdurmak için Yakalama sırasında çağrı yığınlarını topla (yakalamayı daha yavaş **yapar) onay** kutusunu temizleyin.

     **Yakalama sırasında oyun içinde HUD'yi devre dışı bırakma** Grafik tanılama altında çalışan bir uygulamanın genellikle görüntüde yer alan HUD katmanlarını devre dışı bırakmak için bu kutuyu işaretleyin. HUD katmanını görüntülemek için işaretini kaldırın.

     **Uyumluluk modunda yakalama** Grafik bilgilerini uyumluluk modunda yakalamak için bu kutuyu işaretleyin. Uyumluluk modunda yakalama varsayılandır. Uyumluluk modu altında Direct3D, GPU'nun temel özellik düzeyinde tanımlananların ötesinde ek özellikleri desteklediğini bildirmez. Bu, uygulamanın yakalanan GPU'nun donanıma özgü uzantılarını kullanmasını önler ve grafik günlüğünün aynı veya daha yüksek özellik düzeyini destekleyen herhangi bir GPU kullanılarak yeniden çalınmalarını sağlar. Uyumluluk modunu devre dışı bırakmak için bu kutunun işaretini kaldırın; Uyumluluk modu devre dışıyken yakalanan günlükler, yakalama sırasında uygulama tarafından kullanılan ek özellikleri desteklemeen herhangi bir GPU'da yeniden oynatılamaz.

     **SDK katmanı hataları bulunursa yakalamayı durdurma** Hatalarla karşılaşırsanız yakalamayı hemen durdurmak için bu kutuyu işaretleyin.

## <a name="capturing-graphics-information-remotely"></a>Graf bilgilerini uzaktan yakalama
 Grafik bilgileri, yerel makinede ya da uzak bir makine veya cihazda çalışan bir uygulamadan yakalanabilir. Uzaktan yakalama, makineler ve [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] cihazlar için [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)] de kullanılabilir. Uzakta çalışan bir uygulamadan grafik bilgilerini yakalamak için, projenizi uzaktan hata ayıklama için yapılandırın ve sonra uygulamanızı, daha önce açıklandığı gibi, Grafik Tanılama altında çalıştırın. Uygulama uzak makinede çalışır ve yakalanan grafik bilgileri geliştirme makinenizde kaydedilir.

 Projenizi uzaktan hata ayıklama için yapılandırma şekliniz, geliştirmekte olduğunuz uygulamanın türüne ve kullandığınız programlama diline göre değişir. UWP uygulaması için uzaktan hata ayıklamayı yapılandırma hakkında bilgi için bkz. [Uzak makinede UWP uygulamalarını çalıştırma.](../run-windows-store-apps-on-a-remote-machine.md) Bir masaüstü uygulaması için uzaktan hata ayıklamayı yapılandırma hakkında Windows için bkz. [Uzaktan Hata Ayıklama.](../remote-debugging.md)

 Daha sonra, bilgilerin yakalandığı yerden bağımsız olarak, grafik bilgilerini kayıttan yürütmek için bir uzak makine veya cihaz kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Change the Grafik Tanılama Playback Machine](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="capturing-graphics-information-from-the-command-line"></a>Komut satırına ilişkin grafik bilgilerini yakalama
 Grafik bilgileri, bir komut satırı aracı kullanılarak bir uygulamadan yakalanabilirsiniz. Bu araç DXCap.exe veya programlı yakalama olmadan grafik bilgilerini hızla Visual Studio ve oynatabilirsiniz. Özellikle, otomasyon için DXCap.exe veya bir test ortamında bu bilgileri kullanabilirsiniz. Daha fazla bilgi DXCap.exe için [bkz. Komut Satırı Yakalama Aracı](command-line-capture-tool.md)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)