---
title: 'İzlenecek yol: gölgeleme nedeniyle Işleme hatalarını ayıklama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44e542bcbb801ee4035ba501b50bad81b53e8bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62849373"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama
Bu izlenecek yol [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , gölgelendirici hatası nedeniyle yanlış renkli bir nesneyi araştırmak için grafik tanılama nasıl kullanacağınızı gösterir.

 Bu izlenecek yol, nasıl yapılacağını göstermektedir:

- Sorunu gösteren pikselleri belirlemek için grafik günlüğü belgesini inceleyin.

- Piksel durumunu daha yakından incelemek için **Grafik piksel geçmişi** penceresini kullanın.

- Piksel ve Köşe Gölgelendiricileri incelemek için **HLSL hata ayıklayıcısını** kullanın.

## <a name="scenario"></a>Senaryo
 Bir köşe gölgelendiricisi, bir piksel gölgelendiricisi yanlış veya eksik bilgileri geçtiğinde nesneler üzerinde yanlış renklendirme oluşur.

 Bu senaryoda, son zamanlarda uygulamanıza bir nesne eklediniz. Ayrıca, nesneyi dönüştürmek ve benzersiz bir görünüm vermek için yeni bir köşe ve Piksel gölgelendiricileri eklemiş olursunuz. Uygulamayı bir test sırasında çalıştırdığınızda, nesne düz siyah olarak işlenir. Grafik Tanılama kullanarak, uygulamanın hatalarını ayıklayabilmeniz için sorunu bir grafik günlüğüne yakalarsınız. Sorun, uygulamada bu görüntüde olduğu gibi görünür:

 ![Nesne yanlış renklerle işlenir.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Araştırma
 Grafik Tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlüğü belgesini yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğündeki bir çerçeveyi incelemek için

1. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , eksik modeli gösteren bir çerçeveye sahip bir grafik günlüğü yükleyin. İçinde yeni bir grafik günlüğü belgesi penceresi görüntülenir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu pencerenin üst kısmında, seçili karenin işleme hedefi çıkışı bulunur. Alt kısımda, yakalanan her çerçeveyi bir küçük resim olarak görüntüleyen **çerçeve listesidir**.

2. **Çerçeve listesinde**nesnenin doğru görünümü olmayan bir çerçeve seçin. Oluşturma hedefi seçili çerçeveyi yansıtacak şekilde güncelleştirilir. Bu senaryoda, grafik günlük belgesi penceresi şu resme benzer şekilde görünür:

    ![Visual Studio 'da grafik günlüğü belgesi.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Sorunu gösteren bir çerçeve seçtikten sonra, bunu tanılamak için **Grafik piksel geçmişi** penceresini kullanabilirsiniz. **Grafik piksel geçmişi** penceresi, belirli bir piksel, gölgelendiriciler ve işleme hedefi üzerindeki etkileri, kronolojik sırada olan temel öğeleri gösterir.

#### <a name="to-examine-a-pixel"></a>Bir pikseli incelemek için

1. **Grafik piksel geçmişi** penceresini açın. **Grafik tanılama** araç çubuğunda **piksel geçmişi**' ni seçin.

2. İncelenecek bir piksel seçin. Grafik günlüğü Belgesi penceresinde, nesne üzerindeki yanlış renkli olan piksellerden birini seçin:

    ![Bir pikselin seçilmesi geçmişiyle ilgili bilgileri görüntüler.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    **Grafik piksel geçmişi** penceresi seçili pikseli yansıtacak şekilde güncelleştirilir. Bu senaryoda **Grafik piksel geçmişi** penceresi şöyle görünür:

    ![Piksel geçmişi bir DrawIndexed olayını gösterir.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Piksel gölgelendiricisinin sonucunun tamamen donuk (0, 0, 0, 1) olduğuna ve **çıktının birleştiğinde** , bu piksel gölgelendiricinin pikselin bir **önceki** rengiyle, **sonucun** aynı zamanda tamamen opak bir şekilde birleştirildiğine dikkat edin.

   Yanlış renkli bir piksel inceledikten ve piksel gölgelendirici çıkışının beklenen rengi bulduktan sonra, HLSL hata ayıklayıcısını kullanarak piksel gölgelendiriciyi inceleyebilir ve nesnenin rengine ne olduğunu bulabilirsiniz. HLSL hata ayıklayıcısını kullanarak yürütme sırasında HLSL değişkenlerinin durumunu inceleyebilir, HLSL kodunda adım adım ilerleyin ve sorunu tanılamanıza yardımcı olması için kesme noktaları ayarlayabilirsiniz.

#### <a name="to-examine-the-pixel-shader"></a>Piksel gölgelendiriciyi incelemek için

1. Piksel Gölgelendiricisinde hata ayıklamayı başlatın. **Grafik piksel geçmişi** penceresinde, nesnenin ilkel öğesi, **piksel gölgelendiricisi**' nin yanında, **hata ayıklamayı Başlat** düğmesini seçin.

2. Bu senaryoda, piksel gölgelendiricisi yalnızca köşeyi köşe gölgelendiriciden geçirdiğinden, piksel gölgelendiricisinin sorunun kaynağı olmadığı gözlemleyebilirsiniz.

3. İşaretçiyi üzerinde bekletin `input.color` . Değerin tamamen opak siyah (0, 0, 0, 1) olduğuna dikkat edin.

    !["İnput" öğesinin "Color" üyesi siyah.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    Bu senaryoda İnceleme, yanlış rengin büyük olasılıkla, piksel gölgelendiricisinin üzerinde çalışacağı doğru renk bilgilerini sağlamayan bir Köşe gölgelendiricisinin sonucu olduğunu gösterir.

   Köşe gölgelendiricisinin piksel gölgelendiricisine doğru bilgileri sağlamadığınızı belirledikten sonra, bir sonraki adım köşe gölgelendiriciyi incelemektir.

#### <a name="to-examine-the-vertex-shader"></a>Köşe gölgelendiriciyi incelemek için

1. Köşe Gölgelendiricisinde hata ayıklamayı başlatın. **Grafik piksel geçmişi** penceresinde, nesnenin ilkel öğesi altında, **köşe gölgelendirici**' nin yanında, **hata ayıklamayı Başlat** düğmesini seçin.

2. Köşe gölgelendiricisinin çıkış yapısını bulun — bu, piksel gölgelendiricisine giriştir. Bu senaryoda, bu yapının adı `output` . Köşe gölgelendirici kodunu inceleyin ve `color` `output` birisinin hata ayıklama çabalarının bir sonucu olarak, yapının üyesinin açıkça tamamen opak siyah olarak ayarlandığını unutmayın.

3. Renk üyesinin giriş yapısından hiçbir şekilde kopyalanmadığını doğrulayın. Değeri, `output.color` Yapı döndürülmeden hemen önce tamamen opak siyah olarak ayarlandığından `output` , değerinin `output` önceki bir satırda doğru bir şekilde başlatılmamış olduğundan emin olmak iyi bir fikir olabilir. Değerini izlerken siyah olarak ayarlayan çizgiye ulaşana kadar köşe gölgelendirici kodunda ilerleyin `output.color` `output.color` . Değerinin, `output.color` siyah olarak ayarlanana kadar başlatıldığına dikkat edin. Bu `output.color` , siyah olarak ayarlayan kod satırının silinmeden değil, değiştirilmesi gerektiğini doğrular.

    !["Output. Color" değeri siyah.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   İşleme sorununun nedeninin Köşe gölgelendiricisinin piksel gölgelendiriciye doğru renk değeri sağlamamasını belirledikten sonra, bu bilgileri sorunu gidermek için kullanabilirsiniz. Bu senaryoda, köşe gölgelendiricide aşağıdaki kodu değiştirerek çözümü çözebilirsiniz

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 şöyle değiştirin:

```hlsl
output.color = input.color;
```

 Bu kod yalnızca nesnenin köşelerine göre Köşe rengini geçirir; daha karmaşık Köşe Gölgelendiricileri, üzerinden geçirmeden önce rengi değiştirebilir. Düzeltilen köşe gölgelendirici kodu şuna benzemelidir:

 ![Düzeltilen köşe gölgelendirici kodu.](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Kodu düzelttikten sonra, oluşturma sorununun çözümlenme sorununu saptamak için yeniden derleyin ve uygulamayı yeniden çalıştırın.

 ![Nesnesi doğru renklerle işlenir.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
