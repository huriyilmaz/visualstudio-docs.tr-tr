---
title: 'İzlenecek yol: köşe gölgelemesi nedeniyle eksik nesneler | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc3bd288044c9fea1da648b64cabc87148b8463a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825525"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler
Bu izlenecek yol, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] köşe gölgelendirici aşamasında oluşan bir hata nedeniyle eksik olan bir nesneyi araştırmak için grafik tanılama araçlarının nasıl kullanılacağını gösterir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Sorunun olası kaynaklarını bulmak için **grafik olay listesini** kullanma.

- Direct3D API çağrılarının etkisini denetlemek için **grafik ardışık düzen aşamaları** penceresini kullanma `DrawIndexed` .

- Köşe gölgelendiriciyi incelemek için **HLSL hata ayıklayıcısını** kullanma.

- Yanlış bir HLSL sabitinin kaynağını bulmaya yardımcı olması için **grafik olay çağrı yığınını** kullanma.

## <a name="scenario"></a>Senaryo
 3-b uygulamadaki eksik bir nesnenin yaygın nedenlerinin biri, köşe gölgelendiricisi nesnenin köşelerini yanlış veya beklenmedik bir şekilde dönüştürdüğünden oluşur — Örneğin, nesne çok küçük bir boyuta ölçeklenmekte veya kendisi yerine kameranın arkasında görünecek şekilde dönüştürülebilmesine olanak sağlar.

 Bu senaryoda, uygulama test etmek üzere çalıştırıldığında, arka plan beklenen şekilde işlenir, ancak nesnelerden biri görünmez. Grafik Tanılama kullanarak, uygulamanın hatalarını ayıklayabilmeniz için sorunu bir grafik günlüğüne yakalarsınız. Sorun uygulamada şöyle görünür:

 ![Nesne görülemedi.](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>Araştırma
 Grafik Tanılama araçlarını kullanarak, test sırasında yakalanan çerçeveleri incelemek için grafik günlük dosyasını yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğündeki bir çerçeveyi incelemek için

1. İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , eksik nesneyi gösteren bir çerçeve içeren bir grafik günlüğü yükleyin. İçinde yeni bir grafik günlüğü sekmesi görüntülenir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu sekmenin en üst kısmında, seçili karenin işleme hedefi çıkışı bulunur. Alt kısımda, yakalanan her çerçeveyi bir küçük resim olarak görüntüleyen **çerçeve listesidir**.

2. **Çerçeve listesinde**, nesnenin görüntülenmediğini gösteren bir çerçeve seçin. Oluşturma hedefi seçili çerçeveyi yansıtacak şekilde güncelleştirilir. Bu senaryoda grafik günlüğü sekmesi şöyle görünür:

    ![Visual Studio 'da grafik günlüğü belgesi](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   Sorunu gösteren bir çerçeve seçtikten sonra **grafik olay listesini**kullanarak tanımayı deneyebilirsiniz. **Grafik olay listesi** , etkin çerçeveyi işlemek için yapılan her Direct3D API çağrısını içerir, örneğin, cihaz durumunu ayarlamak için API çağrıları, arabellekleri oluşturma ve güncelleştirme, ve çerçevede görünen nesneleri çizme. Birçok çağrı türü, uygulama beklendiği gibi çalıştığında (her zaman değil) işleme hedefinde karşılık gelen bir değişikliğin (örneğin, çizim, dağıtım, kopyalama veya temizleme) olduğu için ilginç hale gelir. Çizim çağrıları özellikle ilginç olduğundan, her biri uygulamanın işlenmiş olduğu geometriyi temsil ettiğinden (dağıtım çağrıları geometriyi de işleyebilir).

   Eksik nesnenin render Target 'a çizilmediğini (Bu durumda) bildiğiniz, ancak sahnenin geri kalanının beklenen şekilde çizildiğini bildiğiniz için grafik **olay listesini** **grafik ardışık düzen aşamaları** aracıyla birlikte kullanarak, hangi çizim çağrısının eksik nesnenin geometrisine karşılık geldiğini belirleyebilirsiniz. **Grafik ardışık düzen aşamaları** penceresi, işleme hedefi üzerindeki etkisiyle bağımsız olarak her bir çizim çağrısına gönderilen geometriyi gösterir. Çizim çağrılarında geçiş yaparken, işlem hattı aşamaları bu çağrıyla ilişkili geometriyi gösterecek şekilde güncelleştirilir ve işleme hedefi çıkışı, çağrı tamamlandıktan sonra oluşturma hedefinin durumunu gösterecek şekilde güncelleştirilir.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Eksik geometri için çizim çağrısını bulmak için

1. **Grafik olay listesi** penceresini açın. **Grafik tanılama** araç çubuğunda **olay listesi**' ni seçin.

2. **Grafik ardışık düzen aşamaları** penceresini açın. **Grafik tanılama** araç çubuğunda, Işlem **hattı aşamaları**' nı seçin.

3. **Grafik olay listesi** penceresinde her çizim çağrısıyla geçiş yaparken, eksik nesnenin **grafik ardışık düzen aşamaları** penceresini izleyin. Bunun daha kolay olması için **grafik olay listesi** penceresinin sağ üst köşesindeki **arama** kutusuna "Çiz" yazın. Bu, listeyi yalnızca kendi başlıklarında "Çiz" olan olayları içerecek şekilde filtreler.

    **Grafik ardışık düzen aşamaları** penceresinde, **giriş assembler** aşaması nesnenin geometrisini dönüştürüldükten önce gösterir ve **köşe gölgelendirici** aşaması dönüştürüldükten sonra aynı nesneyi gösterir. Bu senaryoda, eksik nesneyi **Input assembler** aşamasında görüntülenirken buldığınızı ve **köşe gölgelendirici** aşamasında hiçbir şey gösterilmediğini bilirsiniz.

   > [!NOTE]
   > Diğer geometri aşamaları — Örneğin, Hull gölgelendirici, etki alanı gölgelendirici veya geometri gölgelendirici aşamaları — nesneyi işlerse, bu, sorunun nedeni olabilir. Genellikle, sorun, sonucun görüntülenmeyen veya beklenmedik bir şekilde görüntülendiği en erken aşama ile ilgilidir.

4. Eksik nesneye karşılık gelen çizim çağrısına ulaştığınızda durdur. Bu senaryoda, **grafik ardışık düzen aşamaları** penceresi, GEOMETRININ GPU 'ya verildiğini (giriş derleyicisi küçük resminin gösterdiği) belirtir, ancak köşe gölgelendirici aşamasında (köşe gölgelendirici küçük resminin gösterdiği) bir sorun oluştuğundan işleme hedefinde görünmez:

    ![Bir DrawIndexed olayı ve bu işlem hattı üzerindeki etkisi](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   Uygulamanın eksik nesnenin geometrisi için bir çizim çağrısı yaptığını ve bu sorunun köşe gölgelendirici aşamasında olduğunu bulduktan sonra, köşe gölgelendiriciyi incelemek ve nesnenin geometrisine ne olduğunu bulmak için HLSL hata ayıklayıcısını kullanabilirsiniz. HLSL hata ayıklayıcısını kullanarak yürütme sırasında HLSL değişkenlerinin durumunu inceleyebilir, HLSL kodunda adım adım ilerleyin ve sorunu tanılamanıza yardımcı olması için kesme noktaları ayarlayabilirsiniz.

#### <a name="to-examine-the-vertex-shader"></a>Köşe gölgelendiriciyi incelemek için

1. Köşe gölgelendirici aşamasında hata ayıklamayı başlatın. **Grafik ardışık düzen aşamaları** penceresinde, **köşe gölgelendirici** aşamasının altında, **hata ayıklamayı Başlat** düğmesini seçin.

2. **Giriş** derleyicisi aşaması, köşe gölgelendiricisine iyi veri sunacak şekilde göründüğünden ve **köşe gölgelendirici** aşaması hiçbir çıkış üretmediğinde göründüğünden, köşe gölgelendirici çıkış yapısını incelemek istersiniz `output` . HLSL kodunda iler, değiştirildiğinde, daha yakından bir görünüme sahip olursunuz `output` .

3. İlk kez `output` değiştirildiğinde, üye `worldPos` öğesine yazılır.

    !["Output. worldPos" değeri makul görünüyor](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    Değeri makul bir şekilde göründüğünden, değiştiren bir sonraki satıra kadar koddan çalışmaya devam edersiniz `output` .

4. Sonraki sefer `output` değiştirildiğinde, üye `pos` öğesine yazılır.

    !["Output. POS" değeri sıfırlandı](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    Bu kez, `pos` üyenin değeri — tüm sıfır — şüpheli görünür. Sonra, nasıl `output.pos` sıfırlardan oluşan bir değere sahip olduğunu öğrenmek istersiniz.

5. Öğesinin `output.pos` değerini adlı bir değişkenden aldığını fark edersiniz `temp` . Önceki satırda, değerinin, `temp` önceki değerini adlı bir sabit değerle çarpması sonucu olduğunu görürsünüz `projection` . `temp`Bu çarpma 'nın sonucu şüpheli bir değer olduğunu şüphelenir. İşaretçiyi üzerine getirdiğinizde `projection` , değerinin de tümünün sıfırlardan olduğunu fark edersiniz.

    ![Projeksiyon matrisi hatalı bir dönüşüm içeriyor](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    Bu senaryoda, İnceleme `temp` şüpheli değeri büyük olasılıkla çarpmasının neden olduğu anlamına gelir `projection` ve `projection` bir yansıtma matrisi içermesi amaçlanan bir sabit olduğundan, tümünün sıfırlardan oluşmalıdır.

   `projection`Uygulamanızın gölgelendiricisine geçirdiğini belirten HLSL sabitinin, sorunun olası kaynağı olduğunu belirledikten sonra, bir sonraki adım, sabit arabelleğin doldurulduğu uygulamanızın kaynak kodunda konumunu bulmakta olur. Bu konumu bulmak için **grafik olay çağrı yığınını** kullanabilirsiniz.

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Uygulamanın, uygulamanızın kaynak kodunda ayarlandığı yeri bulmak için

1. **Grafik olay çağrı yığını** penceresini açın. **Grafik tanılama** araç çubuğunda **grafik olay çağrı yığını**' nı seçin.

2. Çağrı yığınını uygulamanızın kaynak koduna gidin. **Grafik olay çağrı yığını** penceresinde, sabit arabelleğin orada doldurulup doldurulamayacağını görmek için en üstteki çağrıyı seçin. Aksi takdirde, nerede doldurulacağını bulana kadar çağrı yığınını devam edin. Bu senaryoda, sabit arabelleğin doldurulduğunu ( `UpdateSubresource` DIRECT3D API 'sini kullanarak), adlandırılmış bir işlevde çağrı yığınını daha `MarbleMaze::Render` sonra ve değeri adlı bir sabit arabellek nesnesinden geldiğini fark edersiniz `m_marbleConstantBufferData` :

    ![Nesnenin sabit arabelleğini ayarlayan kod](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   > Uygulamanızda aynı anda hata ayıklaması yapıyorsanız, bu konumda bir kesme noktası ayarlayabilirsiniz ve bir sonraki çerçeve işlendiğinde bu, bu noktada bu olacaktır. Ardından üyelerini inceleyerek, `m_marbleConstantBufferData` `projection` sabit arabellek doldurulduktan sonra üyenin değerinin tümünün sıfıra ayarlandığını doğrulayabilirsiniz.

   Sabit arabelleğin doldurulduğu konumu bulduktan ve değerlerinin değişkenden geldiği keşfederden sonra `m_marbleConstantBufferData` , bir sonraki adım `m_marbleConstantBufferData.projection` üyenin tüm sıfırları olarak ayarlandığını bulmayacaktır. Değerini değiştiren kodu hızla taramak için **tüm başvuruları bul** ' a yararlanabilirsiniz `m_marbleConstantBufferData.projection` .

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Yansıtma üyesinin uygulamanızın kaynak kodunda ayarlandığı yeri bulmak için

1. Başvuruları bulun `m_marbleConstantBufferData.projection` . Değişken için kısayol menüsünü açın `m_marbleConstantBufferData` ve ardından **tüm başvuruları bul**' u seçin.

2. Uygulamanın, üyenin değiştirildiği kaynak kodundaki satırın konumuna gitmek için `projection` , **sembol sonuçları bul** penceresinde bu satırı seçin. Projeksiyon üyesini değiştiren ilk sonuç sorunun nedeni olmayabilir, uygulamanızın kaynak kodunun birkaç alanını incelemeniz gerekebilir.

   Öğesinin ayarlandığı konumu bulduktan sonra `m_marbleConstantBufferData.projection` , hatalı değerin kaynağını belirleyebilmek için çevreleyen kaynak kodunu inceleyebilirsiniz. Bu senaryoda, değerinin bir `m_marbleConstantBufferData.projection` `projection` sonraki satırdaki kod tarafından verilen bir değere başlatılmadan önce adlı yerel bir değişkene ayarlandığını fark edersiniz `m_camera->GetProjection(&projection);` .

   ![Mermer projeksiyonu başlatmadan önce ayarlandı](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   Sorunu gidermek için, `m_marbleConstantBufferData.projection` yerel değişkenin değerini Başlatan satırdan sonra değerini ayarlayan kod satırını taşırsınız `projection` .

   ![Düzeltilen C&#43;&#43; kaynak kodu](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   Kodu düzelttikten sonra, oluşturma sorununun çözümlenme sorununu saptamak için yeniden oluşturabilir ve uygulamayı tekrar çalıştırabilirsiniz:

   ![Nesne artık görüntülendi.](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")