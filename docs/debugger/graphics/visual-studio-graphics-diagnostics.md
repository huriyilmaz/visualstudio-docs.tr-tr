---
title: Grafik tanılama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e69d88bb5764836d82232cec26606009eaf694d7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187741"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama
Visual Studio*Grafik tanılama* , Direct3D uygulamalarında işleme ve performans sorunlarını kaydetmek ve analiz etmek için bir araç kümesidir. Grafik Tanılama, Windows bilgisayarınızda, Windows cihaz öykünücüsünde veya uzak bir bılgısayarda veya cihazda yerel olarak çalışan uygulamalarda kullanılabilir.

 Grafik Tanılama iş akışı, uygulamanızın daha sonra hemen, paylaşılan veya daha sonra çözümlenebilmesini sağlayacak şekilde Direct3D 'yi nasıl kullandığı gibi (canlı) bir kayıt yakalayarak başlar. Yakalama oturumları, Visual Studio 'dan veya komut satırı yakalama aracı **DXCap. exe**' den el ile başlatılabilir ve denetlenebilir. Yakalama oturumları Ayrıca, Grafik Tanılama yakalama API 'Leri kullanılarak programlı bir şekilde başlatılabilir ve denetlenebilir.

 Bir yakalama oturumu kaydedildikten sonra, içeriği Visual Studio *grafik Çözümleyicisi* tarafından herhangi bir zamanda çalınabilir ve uygulamanın kullandığı tam aynı kaynakları ve işleme komutlarını kullanarak yakalanan çerçeveleri yeniden oluşturabilirsiniz. Daha sonra, grafik Çözümleyicisi penceresinde sunulan araçları kullanarak, yakalanan çerçevelerden herhangi biri ayrıntılı olarak analiz edilebilir. Bu araçlar, herhangi bir Direct3D API çağrısını, kaynağını, ardışık düzen durumu nesnesini, ardışık düzen aşamasını veya Yakalanan çerçevede herhangi bir pikselin tüm boyutlarını incelemek için kullanılabilir. Concert içindeki bu araçları kullanarak, bir işleme sorunu, Yakalanan çerçevede nasıl göründüğünü ve uygulamanın kaynak kodunda, gölgelendiricilerinin veya grafik varlıklarındaki kök nedenine nasıl gidebilirler.

 Performans sorunlarını tanılamak için, yakalanan bir çerçeve, *Çerçeve Analizi* Aracı kullanılarak analiz edilebilir. Bu araç, uygulamanın Direct3D kullanma şeklini otomatik olarak değiştirerek ve sizin için tüm çeşitliliğe işaret ederek olası performans iyileştirmelerini araştırır. Geçmişte, ne fark yaptığını öğrenmek için bu tür değişiklikleri el ile işaretlemiş olabilirsiniz. Çerçeve Analizi ile yalnızca bildiğiniz değişikliklerin ödemesini yapmanız gerekir.

 Grafik Tanılama, grafik açıdan zengin Direct3D uygulamanızın en iyi şekilde bakmanıza ve çalışmasına yardımcı olur.

 Visual Studio Grafik Tanılama sunduğu hakkında daha fazla bilgi edinmek için [genel bakışa](overview-of-visual-studio-graphics-diagnostics.md) devam edin.

## <a name="in-this-section"></a>Bu Bölümde
 [Genel bakış](overview-of-visual-studio-graphics-diagnostics.md) Grafik Tanılama iş akışını ve araçları tanıtır.

 [Başlarken](getting-started-with-visual-studio-graphics-diagnostics.md) Bu bölümde, Visual Studio Grafik Tanılama yüklemeyi ve Direct3D uygulamanız ile Grafik Tanılama kullanmaya nasıl başlayacağınızı öğreneceksiniz.

 [Grafik bilgilerini yakalama](capturing-graphics-information.md) Uygulamanızda bir işleme sorununu incelemek üzere Grafik Tanılama kullanmak için, önce uygulamanın DirectX kullanma hakkında bilgi kaydedersiniz. Kayıt oturumu sırasında, uygulamanız normal şekilde çalıştığı sırada ilgilendiğiniz çerçeveleri *yakalar* (yani, seçersiniz). Yakalamalar, çerçevelerin nasıl işlendiği hakkında ayrıntılı bilgiler içerir. Yakalanan bilgileri, daha sonra incelemek veya takımınızın diğer üyeleriyle paylaşmak için bir grafik günlüğü belgesi olarak kaydedebilirsiniz.

 [GPU kullanımı](../../profiling/gpu-usage.md) Uygulamanızı profile Grafik Tanılama kullanmak için GPU kullanımı aracını kullanın. GPU kullanımı, uygulamanızın performans sorunlarına katkıda bulunma gerektirebilecek CPU ve GPU etkinliklerini ilişkilendirmek için CPU kullanımı gibi diğer profil oluşturma araçlarıyla birlikte kullanılabilir.

 [Grafik günlük belgesi](graphics-log-document.md) Kayıtlı bir grafik günlüğünün incelemesini başlatmak için, yakalanan bir çerçeveyi (veya belirli bir pikseli) seçmek üzere grafik günlüğü belgesi penceresini kullanın. böylece, bunu etkileyen *olayları* (yanı DirectX API çağrısı) ayrıntılı olarak inceleyebilirsiniz.

 [Çerçeve Analizi](graphics-frame-analysis.md) Bir çerçeve seçtikten sonra, işleme performansınızı incelemek ve ayarlamak için Grafik Çerçeve Çözümlemesi kullanırsınız.

 [Olay listesi](graphics-event-list.md) Bir çerçeve seçtikten sonra, oluşturma sorunuyla ilişkili olup olmadıklarını belirlemek üzere olaylarını incelemek için **grafik olay listesini** kullanırsınız.

 [Durum](graphics-state.md) Durum penceresi, geçerli olay sırasında etkin olan grafik durumunu anlamanıza yardımcı olur.

 [Ardışık düzen aşamaları](graphics-pipeline-stages.md) **Grafik ardışık düzen aşamaları** penceresinde, işlem sorununun ilk olarak nerede göründüğünü belirleyebilmeniz için grafik ardışık düzeninin her aşamasında şu anda seçili olan olayın nasıl işlendiğini araştırabilirsiniz. İşlem hattı aşamalarını incelemek, özellikle yanlış bir dönüşüm nedeniyle bir nesne görünmediği veya aşamaların biri sonraki aşamanın beklediği şekilde eşleşmeyen bir çıktı ürettiğinden yararlıdır.

 [Olay çağrısı yığını](graphics-event-call-stack.md) Şu anda seçili olan olayın çağrı yığınını incelemek için **grafik olay çağrı yığınını** kullanın. böylece, işleme sorunuyla ilgili uygulama koduna gidebilirsiniz.

 [Piksel geçmişi](graphics-pixel-history.md) Şu anda seçili olan pikselin onu etkileyen olaylardan nasıl etkilendiğini analiz etmek için **Grafik piksel geçmişi** penceresini kullanarak belirli işleme sorunlarına neden olan olayların olayını veya birleşimini belirleyebilirsiniz. Piksel geçmişi özellikle bir nesne yanlış işlendiğinde, piksel gölgelendirici çıkışı yanlış veya çerçeve arabelleği ile yanlış şekilde birleştirildiğinden ya da pikselleri atıldığından bile bir nesne görünmediğinde yararlı olur çerçeve arabelleğine ulaşmadan önce.

 [Nesne tablosu](graphics-object-table.md) Seçili olan olay için geçerli olan belirli Direct3D nesnelerinin ve kaynakların özelliklerini ve içeriğini incelemek için **grafik nesne tablosunu** kullanın. Nesne tablosu, bir olay sırasında etkin olan grafik cihazı bağlamını belirlemenize ve sabit arabellekler, köşe arabellekleri ve dokular gibi grafik kaynaklarının içeriğini incelemenize yardımcı olabilir.

 [HLSL hata ayıklayıcısı](hlsl-shader-debugger.md) Şu anda seçili olan olay ve grafik ardışık düzen aşamasının gölgelendirici kodunun nasıl davranacağını incelemek için, **HLSL hata ayıklayıcısını** kullanarak kodu, değişkenlerin içeriğini inceleyin ve diğer tipik hata ayıklama görevlerini gerçekleştirebilirsiniz. Ayrıca, sonuçların grafik ardışık düzeni tarafından daha fazla işlenip işlenmediğine veya uygulamanız tarafından yalnızca geri okunduğuna bakılmaksızın, işlem gölgelendirici kodunu incelemek için HLSL hata ayıklayıcısını de kullanabilirsiniz.

 [Komut satırı yakalama aracı](command-line-capture-tool.md) Visual Studio veya programlı yakalama kullanmadan grafik bilgilerini hızlıca yakalamak ve oynatmak için komut satırı Yakalama aracını kullanın. Özellikle, otomasyon için komut satırı Yakalama aracını veya bir test ortamında kullanabilirsiniz.

 [Örnekler](graphics-diagnostics-examples.md) Birçok örnek, farklı işleme sorunlarını tanılamak için Grafik Tanılama araçlarının birlikte nasıl kullanılacağını göstermektedir.

## <a name="related-sections"></a>İlgili Bölümler

| Başlık | Açıklama |
| - | - |
| [Hata ayıklayıcı Özellik turu](../debugger-feature-tour.md) | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hata ayıklama işlevini tanıtır. |
| [DirectX grafik ve oyun](/windows/win32/directx) | DirectX grafik teknolojilerini tartışan makaleler sağlar. |
