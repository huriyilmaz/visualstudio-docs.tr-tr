---
title: Visual Studio Grafik Tanılama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29ca6b2110038a427c76622d50f769321cda9ff9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296892"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*Grafik tanılama* , Direct3D uygulamalarında işleme ve performans sorunlarını kaydetmek ve analiz etmek için bir araç kümesidir. Grafik Tanılama, Windows PC, bir Windows cihaz öykünücüsü veya bir uzak bilgisayar veya cihaz üzerinde yerel olarak çalışan uygulamalarda kullanılabilir.  
  
 Grafik tanılama iş akışının nasıl Direct3D uygulamanızın kullandığı kaydını yakalayarak başlar — Canlı çalıştığı gibi — davranışını hemen çözümlenebilir böylece paylaşılan ya da daha sonra kullanmak üzere kaydedildi. Yakalama oturumları, Visual Studio 'dan veya komut satırı yakalama aracı **DXCap. exe**' den el ile başlatılabilir ve denetlenebilir. Yakalama oturumları Ayrıca, Grafik Tanılama yakalama API 'Leri kullanılarak programlı bir şekilde başlatılabilir ve denetlenebilir.  
  
 Bir yakalama oturumu kaydedildikten sonra, içeriği Visual Studio *grafik Çözümleyicisi* tarafından herhangi bir zamanda çalınabilir ve uygulamanın kullandığı tam aynı kaynakları ve işleme komutlarını kullanarak yakalanan çerçeveleri yeniden oluşturabilirsiniz. Daha sonra, grafik Çözümleyicisi penceresinde sunulan araçları kullanarak, yakalanan çerçevelerden herhangi biri ayrıntılı olarak analiz edilebilir. Bu araçlar, her Direct3D API çağrısı, kaynak, işlem hattı durum nesnesi, ardışık düzen aşamasını veya yakalanan çerçevede bir piksel bile tam geçmişini incelemek için kullanılabilir. Bu araçları birlikte kullanarak, bir işleme sorunuyla sezgisel, yakalanan çerçevede görüntülenme şeklini öğesinden başlayarak ve aşağı uygulamanın kaynak kodu, gölgelendiriciler veya grafik varlıklar, sorunun kök nedenini araştırıp bulma notebook'ta incelenebilir.  
  
 Performans sorunlarını tanılamak için, yakalanan bir çerçeve, *Çerçeve Analizi* Aracı kullanılarak analiz edilebilir. Bu araç, olası performans iyileştirmeleri otomatik olarak uygulama Direct3D nasıl kullanacağını değiştirip sizin için tüm çeşitlemeleri değerlendirmesi keşfediyor. Daha önce yapmış olabilirsiniz ve bu tür değişiklikler yalnızca el ile bulmak için benchmarked hangilerinin yapılan bir fark giden. Çerçeve Analizi ile yalnızca faydalı olur bildiğiniz değişiklikler yapmanız gerekir.  
  
 Grafik Tanılama'yı arayın ve en iyi şekilde çalıştırın, grafik açısından zengin Direct3D uygulaması yardımcı olur.  
  
 Visual Studio Grafik Tanılama sunduğu hakkında daha fazla bilgi edinmek için [genel bakışa](../debugger/overview-of-visual-studio-graphics-diagnostics.md) devam edin.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Genel bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Grafik tanılama iş akışı ve araçları sunar.  
  
 [Başlarken](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Bu bölümde, Visual Studio grafik Tanılama'yı yükleme ve grafik tanılama Direct3D uygulamanızla kullanmaya başlamak nasıl öğreneceksiniz.  
  
 [Grafik Bilgilerini Yakalama](../debugger/capturing-graphics-information.md)  
 Uygulamanızda bir işleme sorunuyla incelemek için grafik tanılama kullanmak için öncelikle uygulamayı DirectX nasıl kullandığı hakkında bilgi kaydedin. Kayıt oturumu sırasında, uygulamanız normal şekilde çalıştığı sırada ilgilendiğiniz çerçeveleri *yakalar* (yani, seçersiniz). Yakalamalar çerçeveleri nasıl işlendiğini hakkında ayrıntılı bilgi içerir. Yakalanan bilgiler grafik olarak kaydedebilirsiniz daha sonra incelemek veya takımınızın diğer üyeleriyle paylaşmak için günlük belgesi.  
  
 [GPU Kullanımı](../debugger/gpu-usage.md)  
 Uygulamanızın profilini çıkarmak için grafik tanılama kullanmak için GPU kullanımı aracı kullanın. GPU kullanımı, CPU kullanımı gibi diğer profil oluşturma araçları ile uyumlu bir şekilde uygulamanızdaki performans sorunlarını katkıda bulunabilir CPU ve GPU etkinliği ilişkilendirmek için kullanılabilir.  
  
 [Grafik Günlük Belgesi](../debugger/graphics-log-document.md)  
 Kayıtlı bir grafik günlüğünün incelemesini başlatmak için, yakalanan bir çerçeveyi (veya belirli bir pikseli) seçmek üzere grafik günlüğü belgesi penceresini kullanın. böylece, bunu etkileyen *olayları* (yanı DirectX API çağrısı) ayrıntılı olarak inceleyebilirsiniz.  
  
 [Çerçeve Analizi](../debugger/graphics-frame-analysis.md)  
 Bir çerçeveyi seçtikten sonra işleme performansını ayarlamak ve incelemek için grafik çerçeve çözümlemesi kullanın.  
  
 [Olay Listesi](../debugger/graphics-event-list.md)  
 Bir çerçeve seçtikten sonra, oluşturma sorunuyla ilişkili olup olmadıklarını belirlemek üzere olaylarını incelemek için **grafik olay listesini** kullanırsınız.  
  
 [Durum](../debugger/graphics-state.md)  
 Durum Penceresi'ni geçerli olay sırasında etkin olan grafik durumu anlamanıza yardımcı olur.  
  
 [Ardışık Düzen Aşamaları](../debugger/graphics-pipeline-stages.md)  
 **Grafik ardışık düzen aşamaları** penceresinde, işlem sorununun ilk olarak nerede göründüğünü belirleyebilmeniz için grafik ardışık düzeninin her aşamasında şu anda seçili olan olayın nasıl işlendiğini araştırabilirsiniz. Ardışık Düzen aşamaları İnceleme nesneyi nedeniyle yanlış bir dönüştürme görünmez yaklaştığında veya aşamalar birini ne sonraki aşamasına bekliyor eşleşmeyen bir çıktı üretir özellikle yararlı olur.  
  
 [Olay Çağırma Yığını](../debugger/graphics-event-call-stack.md)  
 Şu anda seçili olan olayın çağrı yığınını incelemek için **grafik olay çağrı yığınını** kullanın. böylece, işleme sorunuyla ilgili uygulama koduna gidebilirsiniz.  
  
 [Piksel Geçmişi](../debugger/graphics-pixel-history.md)  
 Şu anda seçili olan pikselin onu etkileyen olaylardan nasıl etkilendiğini analiz etmek için **Grafik piksel geçmişi** penceresini kullanarak belirli işleme sorunlarına neden olan olayların olayını veya birleşimini belirleyebilirsiniz. Piksel gölgelendirici çıkışı olduğundan nesne yanlış işlendiğinde piksel geçmişi özellikle yararlıdır hatalı veya yanlış çerçeve arabelleği veya piksellerinin atıldı çünkü nesne bile görünmediği zaman birleştirilmiştir çerçeve arabelleği ulaşmadan önce.  
  
 [Nesne Tablosu](../debugger/graphics-object-table.md)  
 Seçili olan olay için geçerli olan belirli Direct3D nesnelerinin ve kaynakların özelliklerini ve içeriğini incelemek için **grafik nesne tablosunu** kullanın. Nesne tablosu, bir olayı sırasında etkin olan grafik cihaz bağlamı belirlemek ve sabit arabellekler köşe arabellekleri ve dokular gibi grafik kaynakları içeriğini incelemek yardımcı olabilir.  
  
 [HLSL Hata Ayıklayıcısı](../debugger/hlsl-shader-debugger.md)  
 Şu anda seçili olan olay ve grafik ardışık düzen aşamasının gölgelendirici kodunun nasıl davranacağını incelemek için, **HLSL hata ayıklayıcısını** kullanarak kodu, değişkenlerin içeriğini inceleyin ve diğer tipik hata ayıklama görevlerini gerçekleştirebilirsiniz. HLSL hata ayıklayıcısı, compute gölgelendirici kodu sonuçlarını grafik ardışık düzen tarafından daha fazla işlenebilir veya yalnızca, uygulamanız tarafından okunur bağımsız olarak incelemek için de kullanabilirsiniz.  
  
 [Komut satırı Yakalama Aracı](../debugger/command-line-capture-tool.md)  
 Hızlı bir şekilde yakalayıp Visual Studio ya da programlı yakalama kullanmadan grafik bilgilerini kayıttan yürütmek için komut satırı yakalama Aracı'nı kullanın. Özellikle, bir test ortamında veya, otomasyon için komut satırı Yakalama aracı kullanabilirsiniz.  
  
 [Örnekler](../debugger/graphics-diagnostics-examples.md)  
 Birkaç örnek grafik tanılama araçları birlikte farklı türde işleme sorunlarını tanılamak için nasıl kullanılacağını gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Visual Studio’da hata ayıklama](../debugger/debugging-in-visual-studio.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]hata ayıklama işlevini tanıtır.|  
|[DirectX grafik ve oyun](https://go.microsoft.com/fwlink/?LinkId=256498)|DirectX grafik teknolojilerini açıklayan makaleleri sağlar.|
