---
title: Yanlış yapılandırılmış işlem hattı nedeniyle eksik nesneler
description: Yanlış yapılandırılmış işlem hattı bulan bir araştırmayı izleyin. Grafik Olay Listesi, Grafik İşlem Hattı Aşamaları ve Grafik Olay Çağrı Yığınının kullanımını gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1e45a0e45e0806fb5614be3aecbd9011c2bfa57a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058527"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>İzlenecek yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler
Bu kılavuzda, kümeden Grafik Tanılama gölgelendiricisi nedeniyle eksik olan bir nesneyi araştırmak için Grafik Tanılama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] araçlarının nasıl kullanıldığı anlatılmaktadır.

 Bu izlenecek yol şu görevleri gösterir:

- Sorunun **olası kaynaklarını bulmak** için Grafik Olay Listesi'nin kullanımı.

- Direct3D API **çağrısının** etkisini incelemek için Grafik İşlem `DrawIndexed` Hattı Aşamaları penceresini kullanma.

- Gölgelendirici aşamasının ayar olmadığını onaylamak için cihaz bağlamını inceleme.

- Grafik İşlem **Hattı Aşamaları** penceresini  Grafik Olay Çağrı Yığını ile birlikte kullanarak, kümesiz piksel gölgelendiricinin kaynağını bulun.

## <a name="scenario"></a>Senaryo
 3-D uygulamasında bir nesne eksik olduğunda, bunun nedeni bazen nesne işlenecek şekilde gölgelendirici aşamalarından birinin ayarlanmaz. Basit işleme ihtiyaçları olan uygulamalarda, bu hatanın kaynağı genellikle nesnenin draw çağrısının çağrı yığınında bir yerde bulunur. Ancak, bir iyileştirme olarak bazı uygulamalar, durum değişikliği ek yükünü en aza indirmek için gölgelendirici programları, dokuları veya diğer verilerin ortak olduğu nesneleri toplu hale getirir. Bu uygulamalarda hatanın kaynağı, çekme çağrısının çağrı yığınında değil toplu iş sisteminde gömülü olabilir. Bu kılavuzda yer alan senaryo, basit işleme ihtiyaçları olan bir uygulamayı gösterir ve bu nedenle hatanın kaynağı çağrı yığınında bulunabilir.

 Bu senaryoda, uygulama test etmek için çalıştır olduğunda arka plan beklendiği gibi işlenir, ancak nesnelerden biri görünmez. Bu Grafik Tanılama kullanarak, uygulamanın hata ayıklaması için sorunu bir grafik günlüğüne yakalarsanız. Sorun uygulamada şöyle görünüyor:

 ![Nesne görüle](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Araştırma
 Aşağıdaki Grafik Tanılama kullanarak, test sırasında yakalanan kareleri incelemek için grafik günlüğü belgesini yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için

1. içinde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eksik nesneyi sergileyen bir çerçeve içeren bir grafik günlüğü belgesi yükleme. içinde yeni bir grafik günlüğü sekmesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] görüntülenir. Bu sekmenin üst kısmında, seçilen çerçevenin işleme hedefi çıkışı yer atır. Alt kısım, yakalanan her **kareyi küçük** resim görüntüsü olarak görüntüleyen Çerçeve Listesi'dir.

2. Çerçeve **Listesi'ne** nesnenin görüntülenmez olduğunu gösteren bir çerçeve seçin. İşleme hedefi, seçilen çerçeveyi yansıtacak şekilde güncelleştirilir. Bu senaryoda grafik günlüğü sekmesi şu şekilde görünür:

    ![Visual Studio'daki grafik günlüğü Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Sorunu gösteren bir çerçeveyi seçmenizin ardından Grafik Olay Listesi'ne bakarak **tanılamaya başlayabilirsiniz.** Grafik **Olay Listesi,** etkin çerçeveyi işlemek için yapılan her Direct3D API çağrısını içerir; örneğin, cihaz durumunu ayarlamak, arabellekleri oluşturmak ve güncelleştirmek ve çerçevede görünen nesneleri çizmek için. Draw, Dispatch, Copy veya Clear çağrıları gibi birçok çağrı türü ilgi çekicidir çünkü uygulama beklendiği gibi çalışırken işleme hedeflerinde genellikle buna karşılık gelen bir değişiklik vardır (ancak her zaman değildir). Çizim çağrıları özellikle ilgi çekicidir çünkü her biri uygulamanın işlenen geometrisini temsil eder.

   İşleme hedefinin eksik nesneyi içermediği, ancak başka hatalar olduğu da görünmediği için, eksik  nesnenin geometrisi  için hangi çizim çağrısının karşılık gelen çizim çağrısını belirlemek için Grafik Olay Listesi'nin grafik işlem hattı aşamaları aracıyla birlikte kullanabileceğiniz. Grafik **İşlem Hattı Aşamaları** penceresi, işleme hedefi üzerindeki etkisine bakılmaksızın her çizim çağrısına gönderilen geometriyi gösterir. Çizim çağrıları arasında ilerlediğinde, işlem hattı aşamaları her etkin aşamadan akan her çağrıyla ilişkili geometriyi gösterecek şekilde güncelleştirilir ve işleme hedefi çıkışı, çağrı tamamlandıktan sonra işleme hedefinin durumunu gösterecek şekilde güncelleştirilir.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Eksik geometri için çizim çağrısını bulmak için

1. Grafik **Olay Listesi penceresini** açın. Araç çubuğunda **Grafik Tanılama** Listesi'ne **tıklayın.**

2. Grafik İşlem **Hattı Aşamaları penceresini** açın. İşlem hattı **Grafik Tanılama** İşlem Hattı **Aşamaları'nu seçin.**

3. Grafik Olay Listesi penceresindeki her çizim **çağrısında** ilerlerken, eksik nesnenin **Grafik İşlem** Hattı Aşamaları penceresini izleyin. Bunu kolaylaştırmak için Grafik Olay Listesi  penceresinin sağ üst köşesindeki Arama kutusuna **"Çiz"** yazın. Bu, listeyi yalnızca başlıklarında "Draw" olan olayları içeren şekilde filtreler.

    Grafik **İşlem Hattı** Aşamaları penceresinde, **Giriş Assembler** aşaması nesnenin geometrisini dönüştürülmeden önce, **Köşe Gölgelendiricisi** aşaması da dönüştürüldikten sonra aynı nesneyi gösterir. Bu senaryoda Grafik İşlem  Hattı Aşamaları penceresinde Giriş **Assembler** ve **Köşe Gölgelendiricisi** aşamalarını gösterir, ancak çizim çağrılarından biri için **Piksel** Gölgelendiricisi aşamalarını değil.

   > [!NOTE]
   > Diğer işlem hattı aşamaları (örneğin gölge gölgelendiricisi, etki alanı gölgelendiricisi veya geometri gölgelendiricisi aşamaları) nesneyi işlese, sorunun nedeni bunlardan herhangi biri olabilir. Genellikle sorun, sonucun görüntülenmediği veya beklenmeyen bir şekilde görüntülendiğinden en erken aşamayla ilgili olur.

4. Eksik nesneye karşılık gelen draw çağrısına ulaşarak durdurun. Bu senaryoda Grafik  İşlem Hattı Aşamaları penceresi, geometrinin GPU'ya (Giriş **Assembler** aşamasının varlığıyla gösterilir) ve dönüştürülerek (Köşe Gölgelendiricisi aşamasıyla gösterilir) düzende olduğunu, ancak etkin piksel gölgelendiricisi **(Piksel** Gölgelendiricisi aşamasının olmamasıyla gösterilir) olmadığı için işleme hedefine görünmemesi olduğunu gösterir.  Bu senaryoda, Output Merger aşamasında eksik nesnenin ne kadar küçük olduğunu **bile** görüyorsunuz:

    ![DrawIndexed olayı ve bunun işlem hattı üzerindeki etkisi](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Uygulamanın eksik nesnenin geometrisi için bir çizim çağrısı verdikten ve piksel gölgelendiricisi aşamasının etkin değil olduğunu keşfettikten sonra, bulgularınızı onaylamak için cihaz durumunu inceebilirsiniz. Cihaz bağlamını ve **diğer** Direct3D nesne verilerini incelemek için Grafik Nesne Tablosu kullanabilirsiniz.

#### <a name="to-examine-device-context"></a>Cihaz bağlamını incelemek için

1. **d3d11 cihaz bağlamını açın.** Grafik **İşlem Hattı Aşamaları** penceresinde, pencerenin en üstünde görüntülenen çağrının parçası olan **ID3D11DeviceContext** `DrawIndexed` bağlantısını seçin.

2. Çizim çağrısı sırasında hiçbir piksel gölgelendiricinin etkin olmadığını onaylamak için **d3d11** cihaz bağlamı sekmesinde görüntülenen cihaz durumunu inceleyebilirsiniz. Bu senaryoda, **gölgelendirici genel bilgileri**(piksel gölgelendiricisi durumu altında **görüntülenir)** gölgelendiricinin NULL olduğunu **gösterir:**

    ![D3D 11 Cihaz Bağlamı piksel gölgelendirici durumunu gösteriyor](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Piksel gölgelendiricinin uygulamanız tarafından null olarak ayar olduğunu onaylarsanız, sonraki adım, gölgelendiricinin ayar bulunduğu uygulamanın kaynak kodunda konumu bulmaktır. Bu konumu bulmak **için Grafik Olay Listesi'nin** **yanında Grafik Olay Çağrı Yığını'yı** da kullanabilirsiniz.

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Piksel gölgelendiricinin, uygulamanın kaynak kodunda ayar bulunduğu yeri bulmak için

1. Eksik `PSSetShader` nesneye karşılık gelen çağrıyı bulun. Grafik Olay **Listesi penceresine** "Draw; PsSetShader" yazın.   Bu, listeyi yalnızca "PSSetShader" olaylarını ve başlıklarında "Draw" olan olayları içeren şekilde filtreler. Eksik nesnenin `PSSetShader` çizim çağrısının öncesinde görüntülenen ilk çağrıyı seçin.

   > [!NOTE]
   > `PSSetShader` bu çerçeve sırasında **ayarlanmazsa** Grafik Olay Listesi penceresinde görünmez. Bu durum genellikle yalnızca tüm nesneler için yalnızca bir piksel gölgelendiricisi kullanılırsa veya çağrı bu çerçeve sırasında istensiz bir şekilde `PSSetShader` atlandı ise gerçekleşir. Her iki durumda da, uygulamanın kaynak kodunda çağrıları aramanızı ve bu çağrıların davranışını incelemek için geleneksel hata ayıklama `PSSetShader` tekniklerini kullanmanızı öneririz.

2. Grafik Olay **Çağrı Yığını penceresini** açın. Grafik araç **Grafik Tanılama** Grafik Olay **Çağrı Yığını'yı seçin.**

3. Çağrı yığınını kullanarak `PSSetShader` uygulamanın kaynak kodundaki çağrıyı bulun. Grafik **Olay Çağrı Yığını penceresinde** en çok çağrıyı seçin ve piksel gölgelendiricinin ayarda olduğu değeri inceler. Piksel gölgelendiricisi doğrudan null olarak ayarlanmış olabilir veya işleve veya başka bir duruma geçirilen bir bağımsız değişken nedeniyle null değer oluşabilir. Doğrudan ayarlanmazsa, çağrı yığınının yukarısı üzerinde bir yerde null değerin kaynağını bulabilirsiniz. Bu senaryoda, piksel gölgelendiricinin adı olan en üst düzey işlevde doğrudan `nullptr` değerine ayar olduğunu keşfedersiniz: `CubeRenderer::Render`

    ![Piksel gölgelendiriciyi başlatan kod](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   > Yalnızca çağrı yığınını incelerken null değerin kaynağını bulamazsanız, çağrıda piksel gölgelendiricisi null olarak ayarlanacaksa programın yürütülmesinin sonlanacak şekilde bir koşullu kesme noktası ayarlamanız `PSSetShader` önerilir. Ardından uygulamayı hata ayıklama modunda yeniden başlatın ve null değerin kaynağını bulmak için geleneksel hata ayıklama tekniklerini kullanın.

   Sorunu çözmek için API çağrısının ilk parametresini kullanarak doğru piksel `ID3D11DeviceContext::PSSetShader` gölgelendiricisini attayın.

   ![Düzeltilmiş C&#43;&#43; kodu](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Kodu düzeltdikten sonra yeniden yapılandırabilir ve işleme sorununun çözüldüğünü doğrulamak için uygulamayı yeniden çalıştırabilirsiniz:

   ![Nesne artık görüntüleniyor](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")