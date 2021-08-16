---
title: Grafik tanılamayı kullanarak işlem gölgelendiricisinde hata ayıklama
description: İşlem gölgelendiricisi sorunlarını giderme örneğini izleyin. Grafik Olay Listesi, Grafik Olay Çağrı Yığını ve Grafik İşlem Hattı Aşamaları'nın kullanımını görüyorsunuz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4383a2214c3f8afb52e67981ef0599377f40b041ec27cc2e968d3d022fa78b87
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454225"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>İzlenecek yol: Hesaplayıcı Gölgelendiricisinde Hata Ayıklamak için Grafik Tanılamayı Kullanma
Bu kılavuzda, hatalı sonuçlar oluşturan bir Visual Studio Grafik Tanılama gölgelendiriciyi araştırmak için Visual Studio Grafik Tanılama araçlarının nasıl kullanıldığı açıklanır.

 Bu izlenecek yol şu görevleri gösterir:

- Sorunun **olası kaynaklarını bulmak** için Grafik Olay Listesi'nin kullanımı.

- DirectCompute **olayı tarafından yürütülen** işlem gölgelendiricisini belirlemek için Grafik Olay Çağrı Yığını'nın `Dispatch` kullanımı.

- Sorunun **kaynağı olan işlem** gölgelendiriciyi incelemek için Grafik İşlem Hattı Aşamaları penceresini ve HLSL hata ayıklayıcısını kullanma.

## <a name="scenario"></a>Senaryo
 Bu senaryoda, benzetim güncelleştirmesinde en yoğun hesaplamayı gerçekleştirmek için DirectCompute kullanan bir akışkanlar dinamiği simülasyonu yazdınız. Uygulama çalıştır olduğunda, veri kümesi ve kullanıcı arabiriminin işlemesi doğru görünüyor, ancak simülasyon beklendiği gibi davranmaz. Bu Grafik Tanılama kullanarak, uygulamanın hata ayıklaması için sorunu bir grafik günlüğüne yakalayabilirsiniz. Sorun uygulamada şöyle görünüyor:

 ![Simülasyon sıvısı yanlış şekilde davranır.](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")

 Grafik günlüğünde grafik sorunlarını yakalama hakkında bilgi için bkz. [Grafik Bilgilerini Yakalama.](capturing-graphics-information.md)

## <a name="investigation"></a>Araştırma
 Yakalanan kareleri ince Grafik Tanılama grafik günlük dosyasını yüklemek için Grafik Tanılama araçlarını kullanabilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğünde bir çerçeveyi incelemek için

1. Bu Visual Studio hatalı benzetim sonuçlarını sergileyen bir çerçeve içeren bir grafik günlüğü yükleyebilirsiniz. Yeni bir Grafik Tanılama sekmesi, Visual Studio. Bu sekmenin üst kısmında, seçilen çerçevenin işleme hedefi çıkışı yer atır. Alt kısım, yakalanan her **çerçevenin küçük** resmini görüntüleyen Çerçeve Listesi'dir.

2. Çerçeve **Listesi'ne** yanlış benzetim davranışını gösteren bir çerçeve seçin. Hata işleme kodunda değil simülasyon kodunda gibi görünüyor olsa da, DirectCompute olayları Direct3D olaylarıyla birlikte kare temelinde yakalanır. Bu senaryoda grafik günlüğü sekmesi şu şekilde görünür:

    ![Grafik günlüğü belgesi Visual Studio.](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")

   Sorunu gösteren bir çerçeveyi seçmenizin ardından, tanılamak için **Grafik Olay Listesi'ne** bakabilirsiniz. Grafik **Olay Listesi,** etkin çerçeve sırasında yapılan her DirectCompute çağrısı ve Direct3D API çağrısı için bir olay içerir; örneğin, GPU üzerinde hesaplama çalıştırmak veya veri kümesi ya da kullanıcı arabirimini işlemek için API çağrıları. Bu durumda, `Dispatch` simülasyonun GPU üzerinde çalıştıran parçalarını temsil eden olaylarla ilgileniyoruz.

#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Benzetim güncelleştirmesi için Dispatch olayı bulmak için

1. Grafik **Grafik Tanılama** Olay Listesi **penceresini açmak için** Olay **Listesi'ne** tıklayın.

2. Veri **kümelerini işleyen** çizim olayı için Grafik Olay Listesi'ne tıklayın. Bunu kolaylaştırmak için Grafik `Draw` Olay Listesi **penceresinin** sağ üst köşesindeki Arama **kutusuna yazın.** Bu, listeyi yalnızca başlıklarında "Draw" olan olayları içeren şekilde filtreler. Bu senaryoda, bu çizim olaylarını ortaya çıktınız:

    ![EL &#40;Olay&#41; çizim olayları gösterir.](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")

3. Grafik günlüğü belge sekmesinde işleme hedefini izlerken her çizim olayında hareket etme.

4. İşleme hedefi işlenmiş veri kümesi ilk kez görüntüleye kadar durdur. Bu senaryoda veri kümesi ilk çizim olayında işlenir. Simülasyonda hata gösterilir:

    ![Bu çizim olayı simülasyon veri kümesi işler.](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")

5. Şimdi **simülasyonu güncelleştirme olayı** için `Dispatch` Grafik Olay Listesi'ne bakabilirsiniz. Benzetim işlenmeden önce güncelleştirilme olasılığı yüksek olduğundan, ilk olarak sonuçları işlenen çizim olayından `Dispatch` önce oluşan olaylara odaklanabilir. Bunu kolaylaştırmak için Arama kutusunu **olarak değiştirerek** 'i `Draw;Dispatch;CSSetShader(` okuyun. Bu, çizim olaylarını ve olaylarını da `Dispatch` `CSSetShader` içeren listeyi filtreler. Bu senaryoda, çizim olayı öncesinde `Dispatch` çeşitli olayların meydana geldiği keşfedersiniz:

    ![EL draw, Dispatch ve CSSetShader olaylarını gösterir](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")

   Soruna karşılık olabilecek birçok `Dispatch` olaydan hangilerinin olduğunu artık biliyorsunuz. Bunları daha ayrıntılı bir şekilde inceleyebileceksiniz.

#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Bir Dispatch çağrısının hangi işlem gölgelendiricisi yürütülür olduğunu belirlemek için

1. Grafik **Grafik Tanılama** Grafik Olay **Çağrı Yığını penceresini açmak** için Olay Çağrı **Yığını'yı** seçin.

2. Simülasyon sonuçlarını işleyici çizim olayından başlayarak önceki her olayda geriye `CSSetShader` doğru hareket etme. Ardından Grafik Olay **Çağrı Yığını** penceresinde, çağrı sitesine gitmek için en üst düzey işlevi seçin. Çağrı sitesinde [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) işlev çağrısının ilk parametresini kullanarak bir sonraki olay tarafından hangi işlem gölgelendiricinin yürütülecek olduğunu tespit `Dispatch` edebilirsiniz.

   Bu senaryoda, her karede üç `CSSetShader` ve `Dispatch` olay çifti vardır. Geriye doğru çalışırken, üçüncü çift tümleştirme adımını (akıcı parçacıkların gerçekten taşındığı), ikinci çift zorlama hesaplama adımını (her parçacığı etkileyen zorlamaların hesaplanması) temsil eder ve ilk çift yoğunluk hesaplama adımını temsil eder.

#### <a name="to-debug-the-compute-shader"></a>İşlem gölgelendiricisinde hata ayıklamak için

1. Grafik **Grafik Tanılama** İşlem Hattı Aşamaları **penceresini açmak** için İşlem Hattı **Aşamaları'nu** seçin.

2. Üçüncü olayı (çizim olayından hemen önce gelen olay) seçin ve ardından Grafik İşlem Hattı Aşamaları penceresindeki İşlem Gölgelendiricisi aşamasında Hata Ayıklamayı `Dispatch` **Başlat'ı seçin.**  

    ![EL'de üçüncü Dispatch olayı seçerek.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")

    HLSL Hata Ayıklayıcısı tümleştirme adımını gerçekleştiren gölgelendiricide başlatıldı.

3. Hatanın kaynağını aramak üzere tümleştirme adımı için işlem gölgelendiricisi kaynak kodunu inceleme. HLSL Grafik Tanılama gölgelendiricisi kodunda hata ayıklamak için Grafik Tanılama'yi kullanarak kod adımlarını atabilir ve izleme pencereleri gibi diğer tanıdık hata ayıklama araçlarını kullanabilirsiniz. Bu senaryoda, tümleştirme adımını gerçekleştiren işlem gölgelendiricisinde hata olmadığını belirlersiniz.

    ![IntegrateCS işlem gölgelendiricisinde hata ayıklama.](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")

4. İşlem gölgelendiricisinde hata ayıklamayı  durdurmak için Hata Ayıklama araç çubuğunda Hata Ayıklamayı Durdur **(Klavye:** Shift+F5) seçin.

5. Ardından, ikinci olayı seçin `Dispatch` ve önceki adımda olduğu gibi işlem gölgelendiricisinde hata ayıklamaya başlayabilirsiniz.

    ![EL'de ikinci Dispatch olayı seçerek.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")

    HLSL Hata Ayıklayıcısı, her bir akıcı parçacık üzerinde işlem yapmayan güçler hesaplandırıcıda başlatıldı.

6. Zorlamalı hesaplama adımı için işlem gölgelendiricisi kaynak kodunu inceleme. Bu senaryoda, hatanın kaynağının burada olduğunu belirlersiniz.

    ![ForceCS'de Hata Ayıklama&#95;Basit işlem gölgelendiricisi.](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")

   Hatanın konumunu belirledikten sonra hata ayıklamayı durdurabilir ve işlem gölgelendiricisi kaynak kodunu değiştirerek etkileşime olan parçacıklar arasındaki mesafeyi doğru şekilde hesapabilirsiniz. Bu senaryoda, yalnızca satırı olarak `float2 diff = N_position + P_position;` `float2 diff = N_position - P_position;` değiştirirsiniz:

   ![Düzeltilmiş işlem&#45;gölgelendirici kodudur.](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")

   Bu senaryoda, işlem gölgelendiricileri çalışma zamanında derlenmiş olduğundan, simülasyonu nasıl etkilediğini gözlemlemek için değişiklikleri yaptıktan sonra uygulamayı yeniden başlatabilirsiniz. Uygulamayı yeniden oluşturmanıza gerek yok. Uygulamayı çalıştırarak simülasyonun artık doğru şekilde davrandığını fark edin.

   ![Simülasyon sıvısı doğru şekilde davranır.](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")