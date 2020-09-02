---
title: 'İzlenecek yol: cihaz durumu nedeniyle nesneler eksik | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e85aa8fc5af3f32f117b112e8624962a49d90c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895456"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler
Bu izlenecek yol [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , hatalı yapılandırılmış cihaz durumu nedeniyle eksik olan bir nesneyi araştırmak için grafik tanılama nasıl kullanacağınızı gösterir.

 Bu izlenecek yol, nasıl yapılacağını göstermektedir:

- Sorunun olası kaynaklarını bulmak için **grafik olay listesi** ' ni kullanın.

- Direct3D API çağrılarının etkisini denetlemek için **grafik ardışık düzen aşamaları** penceresini kullanın `DrawIndexed` .

- Sorunu daha özel olarak bulmak için **Grafik piksel geçmişi** penceresini kullanın.

- Olası sorunlar veya yapılandırma hataları için cihaz durumunu inceleyin.

## <a name="scenario"></a>Senaryo
 Nesnelerin bir 3-b uygulamada beklendikleri yerde görünmemesinin nedenlerinden biri, grafik cihazının bir hatalı şekilde (örneğin, sargı sırası bir hata nedeniyle ortaya çıkarılmasına neden olur) veya derinlik testi işlevinin nesnedeki tüm piksellerin reddedilmesine neden olmasına neden olabilir.

 Bu kılavuzda açıklanan senaryoda, 3-b Uygulamanızı geliştirmede ilk kilometre taşına ulaştınız ve ilk kez test etmeye hazırsınız. Ancak, uygulamayı çalıştırdığınızda yalnızca kullanıcı arabirimi ekranda işlenir. Grafik Tanılama kullanarak, uygulamanın hatalarını ayıklayabilmeniz için sorunu bir grafik günlük dosyasına yakalarsınız. Sorun uygulamada şöyle görünür:

 ![Sorun düzeltilme öncesi uygulama](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")

 Grafik sorunlarının grafik günlüğünde nasıl yakalanacağı hakkında daha fazla bilgi için bkz. [grafik bilgilerini yakalama](capturing-graphics-information.md).

## <a name="investigation"></a>Araştırma
 Grafik Tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlük dosyasını yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğündeki bir çerçeveyi incelemek için

1. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , eksik modeli gösteren bir çerçeve içeren bir grafik günlüğü yükleyin. İçinde yeni bir Grafik Tanılama sekmesi görüntülenir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu sekmenin en üst kısmında, seçili karenin işleme hedefi çıkışı bulunur. Alt kısımda, yakalanan her çerçeveyi bir küçük resim olarak görüntüleyen **çerçeve listesidir**.

2. **Çerçeve listesinde**, modelin görüntülenmediğini gösteren bir çerçeve seçin. Oluşturma hedefi seçili çerçeveyi yansıtacak şekilde güncelleştirilir. Bu senaryoda grafik günlüğü sekmesi şöyle görünür:

    ![. Vsglog sekmesi framebuffer önizleme ve çerçeve listesi](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")

   Sorunu gösteren bir çerçeve seçtikten sonra, grafikleri tanımak için **grafik olay listesi** ' ni kullanabilirsiniz. **Grafik olay listesi** , etkin çerçeveyi işlemek için yapılan her Direct3D API çağrısını içerir, örneğin, cihaz durumunu ayarlamak için API çağrıları, arabellekleri oluşturma ve güncelleştirme, ve çerçevede görünen nesneleri çizme. Birçok çağrı türü, uygulama beklendiği gibi çalıştığında (her zaman değil) işleme hedefinde karşılık gelen bir değişikliğin (örneğin, çizim, dağıtım, kopyalama veya temizleme) olduğu için ilginç hale gelir. Çizim çağrıları özellikle ilginç olduğundan, her biri uygulamanın işlenmiş olduğu geometriyi temsil ettiğinden (dağıtım çağrıları geometriyi de işleyebilir).

#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Çizim çağrılarının yapıldığından emin olmak için

1. **Grafik olay listesi** penceresini açın. **Grafik tanılama** araç çubuğunda **olay listesi**' ni seçin.

2. Çizim çağrıları için **grafik olay listesini** inceleyin. Bunun daha kolay olması için **grafik olay listesi** penceresinin sağ üst köşesindeki **arama** kutusuna "Çiz" yazın. Bu, listeyi yalnızca kendi başlıklarında "Çiz" olan olayları içerecek şekilde filtreler. Bu senaryoda, birkaç çizim çağrısının yapıldığını fark edersiniz:

    ![Yakalanan olayları gösteren grafik olay listesi](media/vsg_walkthru1_.png "vsg_walkthru1_")

   Çizim çağrılarının yapıldığını doğruladıktan sonra, hangi hangisinin eksik geometriye karşılık geldiğini belirleyebilirsiniz. Eksik geometriyi oluşturma hedefine çizilmediğini bildiğiniz için (Bu durumda), hangi çizim çağrısının eksik geometriye karşılık geldiğini öğrenmek için **grafik ardışık düzen aşamaları** penceresini kullanabilirsiniz. **Grafik ardışık düzen aşamaları** penceresi, işleme hedefi üzerindeki etkisiyle bağımsız olarak her bir çizim çağrısına gönderilen geometriyi gösterir. Çizim çağrılarında geçiş yaparken, işlem hattı aşamaları bu çağrıyla ilişkili geometriyi gösterecek şekilde güncelleştirilir ve işleme hedefi çıkışı, çağrı tamamlandıktan sonra oluşturma hedefinin durumunu gösterecek şekilde güncelleştirilir.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Eksik geometri için çizim çağrısını bulmak için

1. **Grafik ardışık düzen aşamaları** penceresini açın. **Grafik tanılama** araç çubuğunda, Işlem **hattı aşamaları**' nı seçin.

2. Eksik model için **grafik ardışık düzen aşamaları** penceresini izlerken her çizim çağrısıyla geçiş yapın. **Giriş assembler** aşaması, ham model verilerini gösterir. **Köşe gölgelendirici** aşaması, dönüştürülmüş model verilerini gösterir. **Pixel gölgelendirici** aşaması, pixel gölgelendirici çıkışını gösterir. **Output-Merger** aşaması, bu çizim çağrısının birleştirilmiş işleme hedefini ve önceki tüm çizim çağrılarını gösterir.

3. Eksik modele karşılık gelen çizim çağrısına ulaşıldığında durur. Bu senaryoda, **grafik ardışık düzen aşamaları** penceresi, geometrinin oluşturulduğunu ancak render hedefinde görünmediğini belirtir:

    ![Eksik nesneyi gösteren ardışık düzen Görüntüleyicisi](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")

   Uygulamanın eksik geometriyi kullandığını ve ilgili çizim çağrısını bulacağını doğruladıktan sonra, oluşturma hedefi çıktısının eksik geometriyi göstermesi gereken bir kısmını seçebilirsiniz ve ardından piksellerin neden dışlandığına ilişkin bilgi edinmek için **Grafik piksel geçmişi** penceresini kullanın. Piksel geçmişi, belirli bir piksel üzerinde etkiye sahip olabilecek her çizim çağrısının bir listesini içerir. **Grafik piksel geçmişi** penceresindeki her çizim çağrısı, **grafik olay listesi** penceresinde de görüntülenen bir sayıyla tanımlanır. Bu, pikselin eksik geometriyi görüntülemesi gerektiğini ve pikselin neden dışlandığına ilişkin olduğunu doğrulamanıza yardımcı olur

#### <a name="to-determine-why-the-pixel-was-excluded"></a>Pikselin neden dışlanacağını belirleme

1. **Grafik piksel geçmişi** penceresini açın. **Grafik tanılama** araç çubuğunda **piksel geçmişi**' ni seçin.

2. **Piksel gölgelendirici** küçük resmine göre, eksik geometrinin bir kısmını içermesi gereken framebuffer çıkışında bir piksel seçin. Bu senaryoda, piksel gölgelendirici çıkışı, işleme hedefinin çoğunu kapsamalıdır; bir piksel seçildikten sonra **Grafik piksel geçmişi** penceresi şöyle görünür:

    ![İlgili çizim çağrılarını gösteren piksel geçmişi penceresi](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")

3. Seçilen işleme hedefi pikselinin, İnceleme yaptığınız çizim çağrısının sayısıyla ( **grafik olay listesi** penceresinden) **Grafik piksel geçmişi** penceresindeki çizim çağrılarından birine eşleştirerek geometri 'nin bir bölümünü içerdiğini doğrulayın. **Grafik piksel geçmişi** penceresindeki çağrılardan hiçbiri, araştırdığı çizim çağrısıyla eşleşmiyorsa, bir eşleşme bulana kadar bu adımları (1. adım) tekrarlayın. Bu senaryoda, eşleşen çizim çağrısı şöyle görünür:

    ![Parça bilgisini gösteren piksel geçmişi penceresi](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")

4. Bir eşleşme bulduğunuzda, **Grafik piksel geçmişi** penceresinde eşleşen çizim çağrısını genişletin ve pikselin dışlandığından emin olun. **Grafik piksel geçmişi** penceresindeki her çizim çağrısı, ilgili nesnenin geometrisinin bir sonucu olarak bu pikseli kesişen eden bir veya daha fazla geometrik temel noktalara (punto, çizgi veya üçgenler) karşılık gelir. Her bir kesişim, pikselin son rengine katkıda bulunabilir. Derinlik testinin, eğri olarak soldan sağa aşağı doğru bir ok üzerindeki Z harfini gösteren bir simge ile temsil edildiği, hariç tutulan bir temel.

5. Çıkarılan bir temel öğeyi, dışlanmasının neden olduğu durumu daha ayrıntılı incelemek için genişletin. **Çıktı Merger** grubunda, işaretçiyi **sonucun**üzerine taşıyın. Araç ipucu, temel masının Neden dışlandığını gösterir. Bu senaryoda, İnceleme, derinlik testinde başarısız olduğu ve bu nedenle pikselin son rengine katkıda bulunmadığı için ilkel öğesinin dışlanacağını ortaya koyar.

   Geometrinin derinlik testinde başarısız olduğu için geometri 'nin görünmediğini belirledikten sonra, bu sorunun hatalı yapılandırılmış cihaz durumuyla ilgili olduğunu şüpheli olabilirsiniz. Cihaz durumu ve diğer Direct3D nesne verileri **grafik nesne tablosu**kullanılarak incelenebilir.

#### <a name="to-examine-device-state"></a>Cihaz durumunu incelemek için

1. **Grafik nesne tablosu** penceresini açın. **Grafik tanılama** araç çubuğunda **nesne tablosu**' nu seçin.

2. **Grafik nesnesi tablosunda** **D3D10 cihaz** nesnesini bulun ve **D3D10 cihaz** nesnesini açın. Yeni bir **D3D10 cihazı** sekmesi içinde açılır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bunun daha kolay olması için **grafik nesne tablosunu** **türe**göre sıralayabilirsiniz:

    ![Grafik nesne tablosu ve ilgili cihaz durumu](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")

3. Olası sorunlar için **D3D10 cihaz** sekmesinde görüntülenen cihaz durumunu inceleyin. Geometri, temel elemanlar derinlik testinde başarısız olduğu için görünmediğinden, derinlik testini etkileyen derinlik kalıbı gibi cihaz durumuna odaklanırsınız. Bu senaryoda, **derinlik kalıbı açıklaması** ( **çıktı birleşme durumu**altında), **derinlik işlevi** üyesi için seyrek bir değer içerir `D3D10_COMPARISON_GREATER` :

    ![Derinlik kalıbı bilgilerini gösteren D3D10 cihaz penceresi](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")

   İşleme sorununun nedeninin yanlış yapılandırılmış bir derinlik işlevi olabileceğini belirledikten sonra, bu bilgileri, derinlik işlevinin doğru şekilde ayarlandığını bulmak için kodu bilginiz ile birlikte kullanabilir ve sonra sorunu çözebilirsiniz. Kodu tanımıyorsanız, hata ayıklarken topladığınız ipuçları kullanarak sorunu arayabilirsiniz — Örneğin, Bu senaryodaki **derinlik kalıbı açıklamasına** bağlı olarak, kodda "derinlik" veya "daha büyük" gibi sözcükleri arayabilirsiniz. Kodu düzelttikten sonra, oluşturma sorununun çözümlenme sorununu saptamak için yeniden derleyin ve uygulamayı yeniden çalıştırın:

   ![Sorun giderildikten sonra uygulama](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")