---
title: Yanlış yapılandırılmış işlem hattı nedeniyle nesneler eksik
description: Yanlış yapılandırılmış bir işlem hattı bulan araştırmayı izleyin. Grafik olay listesini kullan, grafik ardışık düzen aşamaları ve grafik olay çağrı yığınını gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b2ce885969ec8b9e382f453eddf388a850e8ac7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906501"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>İzlenecek yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler
Bu izlenecek yol, bir geçersiz bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] piksel gölgelendiricisi nedeniyle eksik olan bir nesneyi araştırmak için grafik tanılama araçlarının nasıl kullanılacağını gösterir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Sorunun olası kaynaklarını bulmak için **grafik olay listesini** kullanma.

- Direct3D API çağrısının etkisini incelemek için **grafik ardışık düzen aşamaları** penceresini kullanma `DrawIndexed` .

- Gölgelendirici aşamasının ayarlanmadığından emin olmak için cihaz bağlamı inceleniyor.

- **Grafik ardışık düzen aşamaları** penceresini, bir **grafik olay çağrısı yığını** ile birlikte kullanarak, bu ayarı yapılan piksel gölgelendiricisi kaynağını bulmaya yardımcı olur.

## <a name="scenario"></a>Senaryo
 3-b uygulamada bir nesne eksik olduğunda, bazı durumlarda gölgelendirici aşamalarının biri nesne işlenmeden önce ayarlanmadığından. Basit işleme ihtiyaçlarına sahip uygulamalarda, bu hatanın kaynağı genellikle nesnenin çizim çağrısının çağrı yığınında bir yerde bulunur. Ancak, bir iyileştirme olarak, bazı uygulamalar, durum değişikliği yükünü en aza indirmek için, gölgelendirici programları, dokular veya ortak olarak diğer veriler içeren nesneleri toplu olarak oluşturur. Bu uygulamalarda hatanın kaynağı, çizim çağrısının çağrı yığınında değil, toplu işleme sisteminde bulunabilir. Bu izlenecek yolda, basit işleme ihtiyaçlarına sahip bir uygulama gösterilmektedir ve bu nedenle hatanın kaynağı çağrı yığınında bulunabilir.

 Bu senaryoda, uygulama test etmek üzere çalıştırıldığında, arka plan beklenen şekilde işlenir, ancak nesnelerden biri görünmez. Grafik Tanılama kullanarak, uygulamanın hatalarını ayıklayabilmeniz için sorunu bir grafik günlüğüne yakalarsınız. Sorun uygulamada şöyle görünür:

 ![Nesne görülemedi](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Araştırma
 Grafik Tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlüğü belgesini yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğündeki bir çerçeveyi incelemek için

1. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , eksik nesneyi gösteren bir çerçeve içeren bir grafik günlüğü belgesi yükleyin. İçinde yeni bir grafik günlüğü sekmesi görüntülenir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu sekmenin en üst kısmında, seçili karenin işleme hedefi çıkışı bulunur. Alt kısımda, yakalanan her çerçeveyi bir küçük resim olarak görüntüleyen **çerçeve listesidir**.

2. **Çerçeve listesinde**, nesnenin görüntülenmediğini gösteren bir çerçeve seçin. Oluşturma hedefi seçili çerçeveyi yansıtacak şekilde güncelleştirilir. Bu senaryoda grafik günlüğü sekmesi şöyle görünür:

    ![Visual Studio 'da grafik günlüğü belgesi](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Sorunu gösteren bir çerçeve seçtikten sonra **grafik olay listesini** kullanarak tanımayı başlatabilirsiniz. **Grafik olay listesi** , etkin çerçeveyi işlemek için yapılan her Direct3D API çağrısını içerir — örneğin, cihaz durumunu ayarlamak, arabellekleri oluşturmak ve güncelleştirmek ve çerçevede görünen nesneleri çizmek için. Birçok çağrı türü — örneğin, çizim, dağıtma, kopyalama veya temizleme çağrıları — uygulama beklendiği gibi çalıştığında işleme hedefinde genellikle karşılık gelen bir değişikliğe (her zaman değil) göre ilginç olur. Her biri uygulamanın işlendiği geometriyi temsil ettiğinden, çizim çağrıları özellikle ilginç hale alınır.

   Render hedefinin eksik nesne içermediğini, ancak başka hatalar gibi görünmediğini bildiğiniz için, hangi çizim çağrısının eksik nesnenin geometrisine karşılık geldiğini öğrenmek için grafik **olay listesi** ' ni **grafik ardışık düzen aşamaları** aracıyla birlikte kullanabilirsiniz. **Grafik ardışık düzen aşamaları** penceresi, işleme hedefi üzerindeki etkisiyle bağımsız olarak her bir çizim çağrısına gönderilen geometriyi gösterir. Çizim çağrılarında ilerledikten sonra, işlem hattı aşamaları her bir çağrı ile ilişkili geometriyi göstermek üzere güncelleştirilir ve bu işlem hedef çıkışı, çağrı tamamlandıktan sonra oluşturma hedefinin durumunu gösterecek şekilde güncelleştirilir.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Eksik geometri için çizim çağrısını bulmak için

1. **Grafik olay listesi** penceresini açın. **Grafik tanılama** araç çubuğunda **olay listesi**' ni seçin.

2. **Grafik ardışık düzen aşamaları** penceresini açın. **Grafik tanılama** araç çubuğunda, Işlem **hattı aşamaları**' nı seçin.

3. **Grafik olay listesi** penceresinde her çizim çağrısıyla geçiş yaparken, eksik nesnenin **grafik ardışık düzen aşamaları** penceresini izleyin. Bunun daha kolay olması için **grafik olay listesi** penceresinin sağ üst köşesindeki **arama** kutusuna "Çiz" yazın. Bu, listeyi yalnızca kendi başlıklarında "Çiz" olan olayları içerecek şekilde filtreler.

    **Grafik ardışık düzen aşamaları** penceresinde, **giriş assembler** aşaması, nesnenin geometrisini dönüştürülmeden önce gösterir ve **köşe gölgelendirici** aşaması dönüştürüldükten sonra aynı nesneyi gösterir. Bu senaryoda, **grafik ardışık düzen aşamaları** penceresinin **giriş assembler** ve  **köşe gölgelendirici** aşamalarını gösterdiğini, ancak çizim çağrılarından biri için **piksel gölgelendirici** aşamasını göstermediğine dikkat edin.

   > [!NOTE]
   > Diğer işlem hattı aşamaları — Örneğin, kabuk gölgelendirici, etki alanı gölgelendirici veya geometri gölgelendirici aşamaları — nesneyi iş, bu, sorunun nedeni olabilir. Genellikle, sorun, sonucun görüntülenmeyen veya beklenmedik bir şekilde görüntülendiği en erken aşama ile ilgilidir.

4. Eksik nesneye karşılık gelen çizim çağrısına ulaştığınızda durdur. Bu senaryoda, **grafik ardışık düzen aşamaları** penceresi, GEOMETRININ GPU 'ya verildiğini ( **giriş derleyici** aşamasının varlığı tarafından belirtilir) ve dönüştürüldüğünü ( **köşe gölgelendirici** aşamasına göre gösterilir), ancak etkin bir piksel gölgelendirici ( **piksel gölgelendirici** aşamasının yokluğu ile belirtilir) olmadığı için işleme hedefinde görünmeyeceğini gösterir. Bu senaryoda, **Çıkış Merger** aşamasında eksik nesnenin silueti de görebilirsiniz:

    ![Bir DrawIndexed olayı ve bu işlem hattı üzerindeki etkisi](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Uygulamanın eksik nesnenin geometrisi için bir çizim çağrısı verildiğini ve piksel gölgelendirici aşamasının etkin olmadığını keşfettiğiniz doğruladıktan sonra, bulgularınızı onaylamak için cihaz durumunu inceleyebilirsiniz. Cihaz bağlamını ve diğer Direct3D nesne verilerini incelemek için **Graphics nesne tablosunu** kullanabilirsiniz.

#### <a name="to-examine-device-context"></a>Cihaz bağlamını incelemek için

1. **D3d11 cihaz bağlamını** açın. **Grafik ardışık düzen aşamaları** penceresinde, pencerenin üst kısmında görüntülenen çağrının parçası olan **ID3D11DeviceContext** bağlantısını seçin `DrawIndexed` .

2. Çizim çağrısı sırasında hiçbir piksel gölgelendiricisi etkin olmadığını doğrulamak için **d3d11 cihaz bağlamı** sekmesinde görüntülenen cihaz durumunu inceleyin. Bu senaryoda, **piksel gölgelendirici durumu** altında görüntülenen **gölgelendirici genel bilgileri**, gölgelendiricinin **null** olduğunu belirtir:

    ![D3D 11 cihaz bağlamı piksel gölgelendirici durumunu gösterir](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Piksel gölgelendiricisinin uygulamanız tarafından null olarak ayarlandığını doğruladıktan sonra, bir sonraki adım, uygulamanızın gölgelendirici ayarlanan kaynak kodundaki konumu bulmiydi. Bu konumu bulmak için grafik olay **listesini** **grafik olay çağrısı yığını** ile birlikte kullanabilirsiniz.

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Piksel gölgelendiricisinin uygulamanızın kaynak kodunda ayarlandığı yeri bulmak için

1. `PSSetShader`Eksik nesneye karşılık gelen çağrıyı bulun. **Grafik olay listesi** penceresinde "Çiz" yazın. PSSetShader " **grafik olay listesi** penceresinin sağ üst köşesindeki **arama** kutusunda. Bu, listeyi yalnızca "PSSetShader" olaylarını ve kendi başlıklarında "Çiz" olan olayları içerecek şekilde filtreler. `PSSetShader`Eksik nesnenin çizim çağrısından önce görüntülenen ilk çağrıyı seçin.

   > [!NOTE]
   > `PSSetShader` Bu çerçeve sırasında ayarlanmamışsa **grafik olay listesi** penceresinde görüntülenmez. Genellikle bu yalnızca bir piksel gölgelendiricisi tüm nesneler için kullanıldığında veya `PSSetShader` çağrının bu çerçeve sırasında istenmeden atlanması durumunda oluşur. Her iki durumda da, çağrılar için uygulamanın kaynak kodunda arama yapmanızı `PSSetShader` ve bu çağrıların davranışını incelemek için geleneksel hata ayıklama tekniklerini kullanmanızı öneririz.

2. **Grafik olay çağrı yığını** penceresini açın. **Grafik tanılama** araç çubuğunda **grafik olay çağrı yığını**' nı seçin.

3. Uygulamanın kaynak kodunda çağrıyı bulmak için çağrı yığınını kullanın `PSSetShader` . **Grafik olay çağrı yığını** penceresinde, en üstteki çağrıyı seçin ve piksel gölgelendiricisinin ayarlandığı değeri inceleyin. Piksel gölgelendiricisi doğrudan null olarak ayarlanabilir veya işleve ya da başka bir duruma geçirilmiş bir bağımsız değişken nedeniyle null değer oluşabilir. Doğrudan ayarlanmamışsa, çağrı yığınında bir yerde null değer kaynağını bulabilirsiniz. Bu senaryoda, piksel gölgelendiricisinin adında en üstteki işlevde doğrudan ayarlandığını fark edersiniz `nullptr` `CubeRenderer::Render` :

    ![Piksel gölgelendiriciyi başlatmeyen kod](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   > Yalnızca çağrı yığınını inceleyerek null değerin kaynağını bulamıyorsanız, çağrı üzerinde bir koşullu kesme noktası ayarlamanızı öneririz `PSSetShader` . bu nedenle, piksel gölgelendiricisi null olarak ayarlandığında programın yürütülmesi kesintiye neden olur. Ardından, uygulamayı hata ayıklama modunda yeniden başlatın ve null değerin kaynağını bulmak için geleneksel hata ayıklama tekniklerini kullanın.

   Sorunu gidermek için, API çağrısının ilk parametresini kullanarak doğru piksel gölgelendiriciyi atayın `ID3D11DeviceContext::PSSetShader` .

   ![Düzeltilen C&#43;&#43; kaynak kodu](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Kodu düzelttikten sonra, oluşturma sorununun çözümlendiğini doğrulamak için yeniden oluşturabilir ve uygulamayı tekrar çalıştırabilirsiniz:

   ![Nesne artık gösteriliyor](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")