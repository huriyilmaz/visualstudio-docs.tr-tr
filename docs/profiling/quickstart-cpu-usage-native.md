---
title: CPU kullanım verilerini analiz etme (C++)
description: CPU kullanımı Tanılama aracını kullanarak C++ ' da uygulama performansını ölçme
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 31a7336bca97dde1d01be15a54c86d7b690a69928e4e1131064124c91871f59d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442111"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>hızlı başlangıç: Visual Studio CPU kullanım verilerini analiz etme (C++)

Visual Studio, uygulamanızdaki performans sorunlarını çözümlemenize yardımcı olacak çok sayıda güçlü özellik sağlar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımı nedeniyle performans sorunlarını belirlemek için araca bakacağız. tanılama araçları, ASP.NET dahil olmak üzere Visual Studio .net geliştirme ve yerel/C++ geliştirmesi için desteklenir.

Tanılama hub 'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size çok sayıda seçenek sunar. Burada açıklanan **CPU kullanım** aracı size ihtiyacınız olan verileri sağlamıyorsa, [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) sizin için yararlı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorununa bellek, işleme Kullanıcı arabirimi veya ağ isteği süresi gibi CPU 'nuzun bir neden olabilir. Performans Profiler, bu tür verileri kaydetmek ve analiz etmek için size çok sayıda seçenek sunar. Diğer bir hata ayıklayıcı ile tümleşik profil oluşturma aracı olan [PerfTips](../profiling/perftips.md), kod içinde ileretmenize ve belirli işlevlerin ya da kod bloklarının ne kadar sürdüğünü tanımlamanızı sağlar.

hata ayıklayıcı (**Tanılama Araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir. Windows 7 ve üzeri sürümlerde, [performans profil oluşturucuyu](../profiling/profiling-feature-tour.md)son mordıtem aracı ' nı kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

   sol bölmedeki **yeni Project** iletişim kutusunda, **Visual C++**' i genişletin ve ardından **Windows masaüstü**' ne tıklayın. orta bölmede **Windows konsol uygulaması**' nı seçin. Sonra *Diagnostics_Get_Started_Native* projeyi adlandırın.

   **Windows konsol uygulaması** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. C++ iş yükü **Ile masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C++** ' ı seçin ve ardından Platform listesinden **Windows** ' yi seçin.

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. ardından Visual Studio Yükleyicisi, C++ iş yüküyle **masaüstü geliştirmeyi** seçin.

   **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *Diagnostics_Get_Started_Native* yazın veya girin. Ardından **Oluştur**' u seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açar.

1. *Diagnostics_Get_Started_Native*, aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    Bu kodla (kaldırmayın `#include "stdafx.h"` ):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>

    //.cpp file code:

    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;

    int getNumber()
    {

        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();

        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here
        // to increase CPU usage
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }

    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;

        auto x = getNumber();
    }

    int main()
    {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

## <a name="step-1-collect-profiling-data"></a>1. Adım: profil oluşturma verilerini toplama

1. İlk olarak, işlevdeki Bu kod satırında uygulamanızda bir kesme noktası ayarlayın `main` :

    `for (int i = 0; i < 10; ++i) {`

    Kod satırının solundaki cilt paya tıklayarak bir kesme noktası ayarlayın.

2. Sonra, işlevin sonundaki kapanış küme ayracı üzerinde ikinci bir kesme noktası ayarlayın `main` :

     ![Profil oluşturma için kesme noktaları ayarla](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Profil oluşturma için kesme noktaları ayarla")

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

3. **Tanılama araçları** pencere, siz kapatmadığınız müddetçe zaten görünür. pencereyi yeniden getirmek için **hata ayıkla**  >  **Windows**  >  **Tanılama Araçları göster**' e tıklayın.

4. Hata   >  **ayıklamayı Başlat** ' a tıklayın (veya araç çubuğundan veya **F5**' i **başlatın** ).

     Uygulamanın yüklenmesi bittiğinde, tanılama araçlarının **Özet** görünümü görüntülenir.

5. Hata ayıklayıcı duraklatıldığında, CPU kullanım verilerinin toplanmasını sağlamak için **CPU profilini kaydet**' i seçip **CPU kullanımı** sekmesini açın.

     ![Tanılama araçları CPU profilini oluşturmayı etkinleştirir](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama araçları CPU profilini oluşturmayı etkinleştirir")

     Veri toplama etkinleştirildiğinde, kayıt düğmesi kırmızı bir daire görüntüler.

     **CPU profilini kaydet**' i seçtiğinizde Visual Studio işlevlerinizi ve ne kadar süre yürütülmeye başlayabileceğini ve ayrıca örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Bu toplanan verileri yalnızca, uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

6. Uygulamanızı ikinci kesme noktasına çalıştırmak için F5 'e basın.

     Artık, özellikle iki kesme noktası arasında çalışan kod bölgesi için uygulamanız için performans verileri vardır.

     Profil Oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekleyin.

     CPU kullanımı aracı, raporu **CPU kullanımı** sekmesinde görüntüler.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini çözümleme

CPU kullanımı altındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından bakarak verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

     ![Tanılama araçları CPU kullanımı sekmesi](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en çok iş yapmaktan (çağrı sırasıyla değil) başlayarak sırayla listelenir. Bu, en uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde, işlevine çift tıklayın `getNumber` .

    İşleve çift tıkladığınızda, **çağıran/çağrılan** görünümü sol bölmede açılır.

    ![Tanılama araçları çağıran çağrılan görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "Diagtoolscallerçağrılan")

    Bu görünümde, seçilen işlev başlıkta ve **geçerli işlev** kutusunda ( `getNumber` Bu örnekte) görüntülenir. Geçerli işlevi çağıran işlev sol tarafta **çağıran işlevin** altında gösterilir ve geçerli işlev tarafından çağrılan işlevler sağ taraftaki **çağrılan işlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutuyu da seçebilirsiniz.)

    Bu görünümde, işlevin tamamlanışında toplam süre (MS) ve Toplam uygulama çalışma zamanının yüzdesi gösterilir.

    **Işlev gövdesi** Ayrıca, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. (Bu çizimde, işlev gövdesinde 119 MS 'den 43602 tanesi harcanmış ve kalan süre bu işlev tarafından çağrılan diğer kodda harcanmıştı). Gerçek değerler ortamınıza bağlı olarak çok farklı olacaktır.

    > [!TIP]
    > **Işlev gövdesindeki** yüksek değerler işlevin içinde bir performans sorununa işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans sorunlarını belirlemek için [bellek kullanımını çözümleyin](../profiling/memory-usage.md).
- CPU kullanımı aracı hakkında daha ayrıntılı bilgi için [CPU kullanımını çözümleyin](../profiling/cpu-usage.md) .
- Bir hata ayıklayıcı ekli veya çalışan bir uygulamayı hedefleyerek CPU kullanımını analiz etme-daha fazla bilgi için bkz. hata [ayıklayıcı ile veya olmayan profil oluşturma araçlarında](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [hata ayıklama olmadan profil oluşturma verileri toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) .

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
