---
title: HLSL Gölgelendirici Hata Ayıklayıcısı | Microsoft Docs
description: HLSL kodunuzun uygulamanıza nasıl aksı olduğunu kavramak için Grafik Çözümleyicisi'nin HLSL hata ayıklayıcısını kullanın. Hata ayıklayıcısı, sizi ilgilendiren tam HLSL iş parçacığının benzetimini yapmak için kullanabilir.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b9cc3cb9a0792121f03d16be1f52ba3c1cf9fe39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133932"
---
# <a name="hlsl-shader-debugger"></a>HLSL Gölgelendirici Hata Ayıklayıcısı
Visual Studio Graphics Analyzer'daki HLSL hata ayıklayıcısı, HLSL gölgelendirici kodunuzun, uygulamanın gerçek koşulları altında nasıl çalışmalı olduğunu anlamanıza yardımcı olur.

 HLSL hata ayıklayıcısı şudur:

 ![İzleme ve çağrı yığını pencerelerini kullanarak HLSL'de hata ayıklama.](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")

## <a name="understanding-the-hlsl-debugger"></a>HLSL hata ayıklayıcısını anlama
 HLSL hata ayıklayıcısı, gölgelendirici kodunuzda ortaya çıkan sorunları anlamanıza yardımcı olur. içinde HLSL kodunda hata ayıklamak, C++, C# veya diğer dillerde yazılmış olan hata ayıklama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] koduna Visual Basic. Aynı diğer dillere hata ayıklaması yaparken olduğu gibi, değişkenlerin içeriğini inceleyebilir, kesim noktaları ayarlayabilir, kodda adım adım ilerleyebilir ve çağrı yığınına yaklaşabilirsiniz.

 Ancak GPU'lar aynı anda yüzlerce iş parçacığında gölgelendirici kodu çalıştırarak yüksek performans elde edince, HLSL hata ayıklayıcısı diğer Grafik Çözümleyicisi araçlarıyla birlikte çalışarak tüm bu bilgileri anlamlı bir şekilde sunmak üzere tasarlanmıştır. Grafik Çözümleyicisi, yakalanan kareleri bir grafik günlüğüne kaydedilen bilgileri kullanarak yeniden oluşturulur; HLSL hata ayıklayıcısı, gölgelendirici kodu çalıştırarak GPU yürütmeyi gerçek zamanlı olarak izlemez. Grafik günlüğü çıkışın herhangi bir bölümünü yeniden oluşturmak için yeterli bilgi içerdiği için ve Grafik Analizi bir hatanın oluştuğu pikseli ve olayı tam olarak tespit etmeye yardımcı olacak araçlar sağladığı için HLSL hata ayıklayıcısının yalnızca ilgilendiğimiz gölgelendirici iş parçacığının benzetimini yapmak zorunda. Başka bir deyişle, gölgelendiricinin çalışması, iç çalışmalarının tam görünümde olduğu CPU üzerinde benzetilebilir. Bu da, HLSL hata ayıklayıcısına CPU benzeri bir hata ayıklama deneyimi kazandırır.

 Ancak, HLSL hata ayıklayıcısı şu an için aşağıdaki bakımlardan sınırlıdır:

- HLSL hata ayıklayıcısı düzenleme ve devam etme desteğine sahip değildir, ancak gölgelendiricilerde değişiklik yapabilirsiniz ve ardından sonuçları görmek için çerçeveyi yeniden üretebilirsiniz.

- Bir uygulamanın ve gölgelendirici kodunun hatalarını aynı anda ayıklamak mümkün değildir. Ancak, bunlar arasında geçiş yapabilirsiniz.

- İzle penceresine değişkenler ve kayıtlar ekleyebilirsiniz, ancak ifadeler desteklenmez.

  Yine de, HLSL hata ayıklayıcısı başka bir yöntemle sağlanabilecek olandan daha iyi ve daha CPU benzeri bir hata ayıklama deneyimi sağlar.

## <a name="hlsl-shader-edit--apply"></a>HLSL Gölgelendiricisi Düzenle & Uygula
 GPU yürütme modeli gölgelendirici durumunun geri alınarak izin vermey olduğundan HLSL gölgelendirici hata ayıklayıcısı, CPU hata ayıklayıcısıyla aynı şekilde & Devam Düzenle'yi desteklemez. Bunun yerine, HLSL hata ayıklayıcısı, HLSL kaynak dosyalarını düzenlemenize ve sonra  değişikliklerinizin etkisini görmek için çerçeveyi yeniden oluşturması için Uygula'ya seçmenize olanak sağlayan Düzenle & Apply'ı destekler. Değiştirilen gölgelendirici kodunuz, projenizin özgün HLSL kaynak dosyasının bütünlüğünü korumak için ayrı bir dosyada depolanır, ancak değişikliklerinizi memnunsanız, değişiklikleri projenize kopyalamak için **Kopyala...** 'yi seçebilirsiniz. Bu özelliği kullanarak, hataları içeren gölgelendirici kodunu hızla tekrarlar ve HLSL hata ayıklama iş akışından maliyetli yeniden oluşturma ve yakalama adımlarını ortadan kaldırabilirsiniz.

## <a name="hlsl-disassembly"></a>HLSL Ayrım
 HLSL gölgelendirici hata ayıklayıcısı, HLSL kaynak kodu listesinin sağ tarafından HLSL gölgelendirici derlemesi listesini sağlar.

## <a name="debugging-hlsl-code"></a>HLSL kodunda hata ayıklama
 HLSL hata ayıklayıcısına İşlem Hattı Aşamaları veya Piksel Geçmişi pencerelerinden erişin.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>HLSL hata ayıklayıcısını Grafik Ardışık Düzen Aşamaları penceresinden başlatmak için

1. Grafik **İşlem Hattı Aşamaları** penceresinde, hata ayıklamak istediğiniz gölgelendiriciyle ilişkili işlem hattı aşamasını bulun.

2. İşlem hattı aşamasının başlığının altında, küçük bir **yeşil** ok olarak görünen Hata Ayıklamayı Başlat'ı seçin.

    > [!NOTE]
    > HLSL hata ayıklayıcısına bu giriş noktası, karşılık gelen aşamanın yalnızca ilk gölgelendirici iş parçacığında (yani işlenen ilk köşe veya piksel) hata ayıklar. Piksel Geçmişi'ne bu gölgelendirici aşamalarının diğer iş parçacıklarına erişmek için kullanabilirsiniz.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>HLSL hata ayıklayıcısını Grafik Piksel Geçmişi'nden başlatmak için

1. Grafik **Piksel Geçmişi penceresinde,** hata ayıklamak istediğiniz gölgelendiriciyle ilişkili çizim çağrısını genişletin. Her bir çizim çağrısı birden fazla temel öğeye karşılık gelebilir.

2. Çizim çağrısı ayrıntılarında, elde edilen renk katkısı gölgelendirici kodunda bir hata olduğunu gösteren bir temel öğeyi genişletin. Hata olduğunu ortaya koyan birden fazla temel öğe varsa, soruna tanı koymayı zorlaştırabilecek hata birikiminden kaçınmak için bu duruma işaret eden ilk temel öğeyi seçin.

3. Temel ayrıntılarda, Köşe Gölgelendiricisi'nin mi yoksa **Piksel Gölgelendiricisi'nin** mi hata **ayıklaması yapmak olduğunu seçin.** Piksel gölgelendiricisinin doğru olduğu, ancak köşe gölgelendiricisinin kendisine yanlış sabitler aktarması nedeniyle yanlış renk katkısı ürettiğinden şüphelendiğiniz durumlarda, köşe gölgelendiricisi için hata ayıklama uygulayın. Aksi durumlarda piksel gölgelendiricisi için hata ayıklama uygulayın.

    Seçilen gölgelendiricinin sağ tarafından, küçük bir yeşil **ok olarak görünen** Hata Ayıklamayı Başlat'ı seçin.

   > [!NOTE]
   > HLSL hata ayıklayıcısına bu giriş noktası, ya seçilen çizim çağrısına, temel öğeye ve seçtiğiniz piksele karşılık gelen piksel gölgelendiricisi iş parçacığına ya da sonuçları çizim çağrısı, temel öğe ve seçmiş olduğunuz piksel tarafından ilişkilendirilen köşe gölgelendiricisi iş parçacıklarına hata ayıklama uygular. Köşe gölgelendiricileri durumunda, köşe gölgelendiricisi ayrıntılarını genişleterek giriş noktasını belirli bir köşeye kadar iyice daraltabilirsiniz.

   Gölgelendirici hatalarında hata ayıklamak için HLSL Hata Ayıklayıcısı'nın nasıl kullanıla ilgili örnekler için, Ayrıca Bkz. bölümünde Örnekler veya bağlantılı kılavuzlar bölümüne bakın. [](graphics-diagnostics-examples.md)

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)
- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)
- [İzlenecek yol: Hesaplayıcı Gölgelendiricisinde Hata Ayıklamak için Grafik Tanılamayı Kullanma](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)