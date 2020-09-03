---
title: Grafik bilgilerini yakalama | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38dd994eca30bfee071f00431f3b111c2ea444a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736200"
---
# <a name="capturing-graphics-information"></a>Grafik Bilgilerini Yakalama
Oluşturma sorunlarını ve performans sorunlarını tanılamak için Visual Studio Grafik Çözümleyicisi kullanabilmeniz için Direct3D uygulamanızdan grafik bilgilerini yakalayın.

## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
 Graf bilgilerini yakalama iki adımlı bir işlemdir. Önce uygulamanızı Grafik Tanılama altında çalıştırın ve sonra ayrıntılı bilgilerini yakalamak üzere bir veya daha fazla kare belirtin.

### <a name="to-run-your-app-under-graphics-diagnostics"></a>Uygulamanızı Grafik Tanılama altında çalıştırmak için

- Menü çubuğunda **Hata Ayıkla**, **grafikler**, **grafik hata ayıklamayı Başlat**' ı seçin. (Klavye: Alt+F5 tuşlarına basın)

- **Grafik** araç çubuğunda **grafik hata ayıklamayı Başlat** düğmesini seçin.

  Bir uygulama Grafik Tanılama altında çalışırken, belirli grafik bilgisi türleri sürekli olarak yakalanır; bunlar cihaz kurulumu, takas zincirinin oluşturulması, grafik nesnelerinin ve kaynakların oluşturulması ve birden fazla kareyi etkileyen diğer önemli olayları içerir. Aynı zamanda, belirli kareler hakkında ayrıntılı bilgiler yakalayabilirsiniz; Direct3D nesneleri ve bunları destekleyen kaynaklar ile birlikte çizim çağrıları ve hesaplayıcı-gölgelendirici sevkleri buna dahildir.

### <a name="to-capture-a-frame"></a>Bir kareyi yakalamak için

- Visual Studio 'da, **grafik** araç çubuğunda, **çerçeve** yakala düğmesi ![grafik yakala düğme simgesine](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")tıklayın.

- Klavyede PRINT Screen tuşuna basın.

  > [!NOTE]
  > Bir uygulama **Grafik tanılama**altında çalışırken, yazdırma ekranı anahtarı yalnızca bir grafik bilgileri çerçevesini yakalamak için kullanılabilir; normal işlevini gerçekleştirmez. Başka bir uygulama odakta olsa bile, grafik bilgilerini yakalamayı durduruncaya kadar (genellikle hata ayıklamayı durdurarak veya uygulamadan normal yolla çıkarak) bu durum devam eder.

- Visual Studio yakalama arabiriminde, **Tanılama oturumu** zaman çizelgesinin altında bulunan **yakalama çerçevesi** düğmesini seçin ya da **saniye başına alınan karelerin** ve daha önce yakalanan çerçevelerin sağındaki büyük **yakalama çerçevesi** düğmesini seçin. Aşağıdaki görüntüde her iki düğme de vurgulanır.

   ![GPU kullanımı aracını kullanarak çerçeveleri yakalayın.](media/pix_gpu_usage_tool_capture_frame.png)

   Yakaladığınız çerçeveleri incelemek için hazırsanız, görüntü küçük resimlerinin üzerindeki **çerçeve...** bağlantısını izleyerek veya küçük resme çift tıklayarak **Visual Studio grafik Çözümleyicisi** başlatın.

  Yalnızca tüm çerçeveler yakalanabilir, bu nedenle bir yakalama başlattığınızda, kaydedilen bir sonraki çerçevede grafik bilgileri aslında yer alabilir. Kayıt, yakalama işlemini başlattığınız kare sunulduktan hemen sonra başlar ve yakalanan kare sunulduğunda sona erer. Uygulama Grafik Tanılama altında çalışırken istediğiniz sayıda kare yakalayabilirsiniz. Hiçbir kare yakalamazsanız, grafik günlüğü atılır.

  Çerçeveleri yakalarken, Visual Studio Tanılama oturumu (. diagsession) penceresini görüntüler. Bu pencereyi kapatır, hata ayıklamayı durdurur veya uygulamayı kapatırsanız, bu günlüğe daha fazla kare yakalayamazsınız. Daha fazla grafik bilgisi yakalamak için, yeni bir Tanılama oturumu başlatmak üzere uygulamayı yeniden Grafik Tanılama altında çalıştırmanız gerekir.

### <a name="graphics-diagnostics-capture-options"></a>Grafik Tanılama yakalama seçenekleri
 Yakalama 'yı tüm grafik olayları veya sınırlı bir alt küme için çağrı yığınları toplayacak, yakalama HUD 'yi devre dışı bırakarak ve yakalama uyumluluk modunu etkinleştirebilir veya devre dışı bırakacak şekilde yapılandırabilirsiniz.

#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Grafik Tanılama yakalama seçeneklerini yapılandırmak için

1. Menü çubuğunda Araçlar, Seçenekler ' i seçin. Seçenekler iletişim kutusu görüntülenir.

2. Soldaki Seçenekler Kategori listesinde Grafik Tanılama ' yi seçin ve sonra istediğiniz Grafik Tanılama seçeneklerini yapılandırın.

     **Yakalama sırasında çağrı yığınlarını topla (yakalamayı yavaşlatır)** Çağrı yığınlarını toplamak için bu kutuyu işaretleyin. Varsayılan olarak, çağrı yığınları toplanmaz. Çağrı yığınlarını yakalamak için **yakalama sırasında çağrı yığınlarının birikmesini sağlama (daha yavaş yakala** onay kutusu ' nu toplamayı etkinleştirmek için ayarlanmış olduğundan) ve ardından yalnızca en önemli çağrı yığınlarını toplamak için **Çizim, dağıtım, sunma ve performans işaretçileri** **seçeneğini (** varsayılan) veya tüm çağrı yığınlarını toplamak için ayarlayın. Daha sonra çağrı yığınlarını toplamayı durdurmak için **yakalama sırasında çağrı yığınlarını topla (daha yavaş yakala** onay kutusunu temizleyin.

     **Yakalama sırasında oyun ıçı HUD 'Yi devre dışı bırakma** Grafik tanılama altında çalışan bir uygulamanın genellikle görüntülediği HUD kaplamasını devre dışı bırakmak için bu kutuyu işaretleyin. HUD kaplamasını göstermek için işaretini kaldırın.

     **Uyumluluk modunda yakala** Grafik bilgilerini uyumluluk modunda yakalamak için bu kutuyu işaretleyin. Uyumluluk modunda yakalama varsayılandır. Uyumluluk modu ' nun altında Direct3D, GPU 'nun temel özellik düzeyinde tanımlananların ötesinde ek özellikleri desteklediğini raporlamaz. Bu, yakalanan uygulamanın, üzerinde yakalanan GPU 'nun donanıma özgü uzantılarını kullanmasını önler ve grafik günlüğünün aynı veya daha yüksek özellik düzeyini destekleyen herhangi bir GPU kullanılarak yürütülebilmesini sağlar. Uyumluluk modunu devre dışı bırakmak için bu kutunun işaretini kaldırın; Uyumluluk modu devre dışı ile yakalanan Günlükler, yakalama sırasında uygulama tarafından kullanılan ek özellikleri desteklemeyen hiçbir GPU üzerinde oynatılamaz.

     **Herhangi BIR SDK katmanı hatası bulunursa yakalamayı durdur** Hatalarla karşılaşıldığında hemen yakalamayı durdurmak için bu kutuyu işaretleyin.

## <a name="capturing-graphics-information-remotely"></a>Graf bilgilerini uzaktan yakalama
 Grafik bilgileri, yerel makinede ya da uzak bir makine veya cihazda çalışan bir uygulamadan yakalanabilir. Uzaktan yakalama, [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] makineler ve cihazlar için desteklenir [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)] . Uzakta çalışan bir uygulamadan grafik bilgilerini yakalamak için, projenizi uzaktan hata ayıklama için yapılandırın ve sonra uygulamanızı, daha önce açıklandığı gibi, Grafik Tanılama altında çalıştırın. Uygulama uzak makinede çalışır ve yakalanan grafik bilgileri geliştirme makinenizde kaydedilir.

 Projenizi uzaktan hata ayıklama için yapılandırma şekliniz, geliştirmekte olduğunuz uygulamanın türüne ve kullandığınız programlama diline göre değişir. UWP uygulaması için uzaktan hata ayıklamayı yapılandırma hakkında daha fazla bilgi için bkz. [uzak MAKINEDE UWP uygulamaları çalıştırma](../run-windows-store-apps-on-a-remote-machine.md). Bir Windows masaüstü uygulaması için uzaktan hata ayıklamayı yapılandırma hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../remote-debugging.md).

 Daha sonra, bilgilerin yakalandığı yerden bağımsız olarak, grafik bilgilerini kayıttan yürütmek için bir uzak makine veya cihaz kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="capturing-graphics-information-from-the-command-line"></a>Komut satırından grafik bilgilerini yakalama
 Grafik bilgileri, bir komut satırı aracı kullanılarak bir uygulamadan yakalanabilir. Bu araç DXCap.exe, Visual Studio veya programlı yakalama kullanmadan grafik bilgilerini hızlıca yakalayabilir ve kayıttan yürütebilir. Özellikle, Otomasyon veya test ortamında DXCap.exe kullanabilirsiniz. DXCap.exe hakkında daha fazla bilgi için bkz. [komut satırı yakalama aracı](command-line-capture-tool.md)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)