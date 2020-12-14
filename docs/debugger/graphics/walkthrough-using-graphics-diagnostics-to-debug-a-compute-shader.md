---
title: Grafik tanılamayı kullanarak işlem Gölgelendiricisinde hata ayıklama
description: İşlem Gölgelendiricisinde sorun gidermeye yönelik bir örnek izleyin. Grafik olay listesi, grafik olay çağrı yığını ve grafik ardışık düzen aşamaları kullanımını görürsünüz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 939b1906a32c48aa1ad32f2fb03372a74afc43ec
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398720"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>İzlenecek yol: Hesaplayıcı Gölgelendiricisinde Hata Ayıklamak için Grafik Tanılamayı Kullanma
Bu izlenecek yol, yanlış sonuçlar üreten bir işlem gölgelendiricisi araştırmak için Visual Studio Grafik Tanılama araçlarının nasıl kullanılacağını göstermektedir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Sorunun olası kaynaklarını bulmak için **grafik olay listesini** kullanma.

- Bir DirectCompute olayı tarafından hangi bilgi işlem gölgelendiricisinin yürütüleceğini belirleyen **grafik olay çağrı yığınını** kullanma `Dispatch` .

- Sorun kaynağı olan işlem gölgelendiriciyi incelemek için **grafik ardışık düzen aşamaları** penceresini ve HLSL hata ayıklayıcısını kullanma.

## <a name="scenario"></a>Senaryo
 Bu senaryoda, simülasyon güncelleştirmesinin en yoğun hesaplama kullanan parçalarını gerçekleştirmek için DirectCompute kullanan bir sıvı-Dynamics simülasyonu yazmış olursunuz. Uygulama çalıştırıldığında, veri kümesinin ve Kullanıcı arabiriminin işlenmesi doğru görünür, ancak benzetim beklendiği gibi davranır. Grafik Tanılama kullanarak, uygulamanın hatalarını ayıklayabilmeniz için sorunu bir grafik günlüğüne yakalayabilirsiniz. Sorun uygulamada şöyle görünür:

 ![Sanal akıcı yanlış davranır.](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")

 Grafik sorunlarının grafik günlüğünde nasıl yakalanacağı hakkında daha fazla bilgi için bkz. [grafik bilgilerini yakalama](capturing-graphics-information.md).

## <a name="investigation"></a>Araştırma
 Yakalanan çerçeveleri incelemenize olanak sağlamak için Grafik Tanılama araçlarını kullanarak grafik günlük dosyasını yükleyebilirsiniz.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Grafik günlüğündeki bir çerçeveyi incelemek için

1. Visual Studio 'da, yanlış simülasyon sonuçlarını gösteren bir çerçeve içeren bir grafik günlüğü yükleyin. Visual Studio 'da yeni bir Grafik Tanılama sekmesi görüntülenir. Bu sekmenin en üst kısmında, seçili karenin işleme hedefi çıkışı bulunur. Alt kısımda, yakalanan her çerçevenin küçük resmini görüntüleyen **çerçeve listesidir**.

2. **Çerçeve listesinde**, yanlış simülasyon davranışını gösteren bir çerçeve seçin. Hata, işleme kodu değil simülasyon kodunda yer alsa da, DirectCompute olayları, Direct3D olayları ile birlikte çerçeve temelinde yakalandığından, hala bir çerçeve seçmeniz gerekir. Bu senaryoda grafik günlüğü sekmesi şöyle görünür:

    ![Visual Studio 'da grafik günlüğü belgesi.](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")

   Sorunu gösteren bir çerçeve seçtikten sonra, grafikleri tanımak için **grafik olay listesi** ' ni kullanabilirsiniz. **Grafik olay listesi** , etkin çerçeve sırasında yapılan her DirectCompute çağrısı ve Direct3D API çağrısı için bir olay içerir — ÖRNEĞIN, GPU üzerinde bir hesaplama ÇALıŞTıRMAK için API çağrıları veya veri kümesini veya Kullanıcı arabirimini işlemek. Bu durumda, `Dispatch` GPU üzerinde çalışan benzetimin parçalarını temsil eden olaylarla ilgileniyoruz.

#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Simülasyon güncelleştirmesine ait dağıtım olayını bulmak için

1. **Grafik tanılama** araç çubuğunda **olay listesi** ' ni seçerek **grafik olay listesi** penceresini açın.

2. Veri kümesini işleyen çizim olayı için **grafik olay listesini** inceleyin. Bunun daha kolay olması için `Draw` **grafik olay listesi** penceresinin sağ üst köşesindeki **arama** kutusuna girin. Bu, listeyi yalnızca kendi başlıklarında "Çiz" olan olayları içerecek şekilde filtreler. Bu senaryoda, bu çizim olaylarının oluştuğunu fark edersiniz:

    ![Olay listesi &#40;EL&#41; çizim olaylarını gösterir.](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")

3. Grafik günlüğü belgesi sekmesinde işleme hedefini izlerken her çizim olayında ilerleyin.

4. Render hedefinin işlenen veri kümesini ilk kez görüntülediğini durdur. Bu senaryoda, veri kümesi ilk çizim olayında işlenir. Simülasyonu içindeki hata gösterilir:

    ![Bu çizim olayı simülasyon veri kümesini işler.](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")

5. Şimdi benzetimi güncelleştiren olay için **grafik olay listesini** inceleyin `Dispatch` . Simülasyonu işlenmeden önce güncelleştirildiğinden, önce `Dispatch` sonuçları işleyen çizim olayından önce oluşan olaylara odaklanabilirsiniz. Bunun daha kolay olması için **arama** kutusunu okumak üzere değiştirin `Draw;Dispatch;CSSetShader(` . Bu, listenin Ayrıca, `Dispatch` `CSSetShader` Çizim olaylarının yanı sıra olayları da içermesi için listeye filtre uygular. Bu senaryoda, `Dispatch` Çizim olayından önce birkaç olay oluştuğunu fark edersiniz:

    ![EL ile çizim, dağıtım ve CSSetShader olayları gösterilmektedir](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")

   Potansiyel olarak çok sayıda olayın kaç kez `Dispatch` soruna karşılık geldiğini bildiğinize göre, bunları daha ayrıntılı bir şekilde inceleyebilirsiniz.

#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Bir dağıtım çağrısının hangi işlem gölgelendiricisinin yürüttüğünü belirleme

1. **Grafik tanılama** araç çubuğunda, **olay çağrısı yığını** ' nı seçerek **grafik olay çağrı yığını** penceresini açın.

2. Simülasyon sonuçlarını işleyen çizim olayından başlayarak, bir önceki olaya geri doğru ilerleyin `CSSetShader` . Ardından, **grafik olay çağrı yığını** penceresinde, çağrı sitesine gitmek için en üstteki işlevi seçin. Çağıran sitede, bir sonraki olay tarafından hangi işlem gölgelendiricisinin yürütüleceğini öğrenmek için [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) işlev çağrısının ilk parametresini kullanabilirsiniz `Dispatch` .

   Bu senaryoda, `CSSetShader` her çerçevede üç çift ve olay vardır `Dispatch` . Geriye doğru çalışarak, üçüncü çift tümleştirme adımını temsil eder (akıcı parçacıkların gerçekten taşındığı), ikinci çift, zorunlu hesaplama adımını (her parçacığı etkileyen güçler hesaplanır) ve ilk çift, yoğunluk hesaplama adımını temsil eder.

#### <a name="to-debug-the-compute-shader"></a>İşlem Gölgelendiricisinde hata ayıklamak için

1. **Grafik tanılama** araç çubuğunda, Işlem **hattı aşamaları** ' nı seçerek **grafik ardışık düzen aşamaları** penceresini açın.

2. Üçüncü olayı seçin `Dispatch` (çizim olayından hemen önce gelen bir olay) ve ardından **grafik ardışık düzen aşamaları** penceresinde, **işlem gölgelendirici** aşaması altında, **hata ayıklamayı Başlat**' ı seçin.

    ![EL ile üçüncü dağıtım olayını seçme.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")

    HLSL hata ayıklayıcısı, tümleştirme adımını gerçekleştiren gölgelendiricide başlatılır.

3. Hatanın kaynağını aramak üzere tümleştirme adımının işlem gölgelendirici kaynak kodunu inceleyin. HLSL COMPUTE-Shader kodunda hata ayıklamak için Grafik Tanılama kullandığınızda, kod içinde iler, izleme pencereleri gibi diğer tanıdık hata ayıklama araçlarını kullanabilirsiniz. Bu senaryoda, tümleştirme adımını gerçekleştiren işlem gölgelendiricide bir hata gibi görünmediğini belirlersiniz.

    ![Integratecs işlem Gölgelendiricisinde hata ayıklama.](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")

4. İşlem gölgelendiricide hata ayıklamayı durdurmak için, **hata** ayıklama araç çubuğunda **hata ayıklamayı Durdur** (klavye: Shift + F5) öğesini seçin.

5. Ardından, ikinci olayı seçin `Dispatch` ve daha önceki adımda yaptığınız gibi işlem Gölgelendiricisinde hata ayıklamayı başlatın.

    ![EL ile ikinci dağıtım olayını seçme.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")

    HLSL hata ayıklayıcısı, her bir sıvı parçacığı üzerinde işlem yapan güçleri hesaplayan gölgelendiricide başlatılır.

6. Zorla Hesaplama adımı için işlem gölgelendirici kaynak kodunu inceleyin. Bu senaryoda, hatanın kaynağının burada olduğunu belirlersiniz.

    ![ForceCS&#95;basit işlem Gölgelendiricisinde hata ayıklama.](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")

   Hatanın konumunu belirledikten sonra, hata ayıklamayı durdurabilir ve işlem gölgelendirici kaynak kodunu değiştirerek, etkileşim kuran parçacıkların arasındaki mesafeyi doğru şekilde hesaplayabilirsiniz. Bu senaryoda, yalnızca satırı şu `float2 diff = N_position + P_position;` şekilde değiştirirsiniz `float2 diff = N_position - P_position;` :

   ![Düzeltilen işlem gölgelendirici kodu&#45;.](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")

   Bu senaryoda, işlem gölgelendiriciler çalışma zamanında derlendiğinden, değişiklikleri yaptıktan sonra, benzetimi nasıl etkilediğini gözlemlemek için uygulamayı yeniden başlatmanız yeterlidir. Uygulamayı yeniden derlemek zorunda değilsiniz. Uygulamayı çalıştırdığınızda, simülasyonu 'nin artık doğru şekilde davranacağını fark edersiniz.

   ![Sanal akıcı doğru şekilde davranır.](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")