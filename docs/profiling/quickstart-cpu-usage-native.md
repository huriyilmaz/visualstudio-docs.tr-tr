---
title: CPU kullanım verilerini çözümleme (C++)
description: CPU kullanımı Tanılama aracını C++ kullanarak uygulama performansını ölçme
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 5912e433f4d2bc05dc4e460456c8858af82183f6
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279228"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Hızlı başlangıç: Visual Studio 'da CPU kullanım verilerini çözümlemeC++()

Visual Studio, uygulamanızdaki performans sorunlarını çözümlemenize yardımcı olacak birçok güçlü özellik sunar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımı nedeniyle performans sorunlarını belirlemek için araca bakacağız. Tanılama araçları, yerel/C++ geliştirme ve ASP.NET dahil olmak üzere Visual Studio .NET geliştirme için desteklenir.

Tanılama hub'ı, çok sayıda çalıştırın ve tanılama oturumunuzu yönetmek için diğer bir seçenek sunar. Burada açıklanan **CPU kullanım** aracı size ihtiyacınız olan verileri sağlamıyorsa, [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) sizin için yararlı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorunu, CPU, bellek, işleme kullanıcı Arabirimi veya ağ isteği süresi gibi dışında bir şey tarafından kaynaklanabilir. Tanılama hub'ı, çok sayıda kaydedin ve bu tür verilerin analiz etmek için diğer bir seçenek sunar.

Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir. Windows 7 ve üzeri sürümlerde, [performans profil oluşturucuyu](../profiling/profiling-feature-tour.md)son mordıtem Aracı ' nı kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 'Yu açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin.

   Sol bölmedeki **Yeni proje** iletişim kutusunda, **görsel C++** ' i genişletin ve ardından **Windows Masaüstü**' ne tıklayın. Orta bölmede **Windows konsol uygulaması**' nı seçin. Sonra *Diagnostics_Get_Started_Native*projeyi adlandırın.

   **Windows konsol uygulaması** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi'ni başlatır. İş yüküyle **Masaüstü geliştirmeyi C++**  seçin ve ardından **Değiştir**' i seçin.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Başlangıç penceresi açık değilse **dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil **C++** listesinden seçin ve ardından platform listesinden **Windows** ' u seçin.

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Ardından Visual Studio yükleyicisi, iş yüküyle **Masaüstü geliştirmeyi C++**  seçin.

   **Yeni projeyi yapılandırın** penceresinde, **proje adı** kutusuna *Diagnostics_Get_Started_Native* yazın veya girin. Ardından **Oluştur**' u seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açar.

1. *Diagnostics_Get_Started_Native*, aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    Bu kodla (`#include "stdafx.h"`kaldırmayın):

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

## <a name="step-1-collect-profiling-data"></a>1\. adım: profil oluşturma verilerini topla

1. İlk olarak, `main` işlevindeki bu kod satırında uygulamanızda bir kesme noktası ayarlayın:

    `for (int i = 0; i < 10; ++i) {`

    Kod satırının solundaki cilt paya tıklayarak bir kesme noktası ayarlayın.

2. Sonra, `main` işlevinin sonundaki kapanış küme ayracı üzerinde ikinci bir kesme noktası ayarlayın:

     ![Profil oluşturma için kesme noktaları ayarla](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Profil oluşturma için kesme noktaları ayarla")

    > [!TIP]
    > İki kesme noktaları ayarlayarak veri toplamayı çözümlemek istediğiniz kod parçalarını sınırlayabilirsiniz.

3. **Tanılama araçları** pencere, siz kapatmadığınız müddetçe zaten görünür. Pencereyi yeniden getirmek için **hata ayıkla** > **Windows** > **Tanılama araçları göster**' e tıklayın.

4. Hata **ayıklamayı başlatmak** > **Hata Ayıkla** ' ya tıklayın (ya da araç çubuğundan veya **F5**' i **başlatın** ).

     Uygulamanın yüklenmesi bittiğinde, tanılama araçlarının **Özet** görünümü görüntülenir.

5. Hata ayıklayıcı duraklatıldığında, CPU kullanım verilerinin toplanmasını sağlamak için **CPU profilini kaydet**' i seçip **CPU kullanımı** sekmesini açın.

     ![Tanılama araçları CPU profilini oluşturmayı etkinleştirir](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama araçları CPU profilini oluşturmayı etkinleştirir")

     Veri toplama etkinleştirildiğinde, kayıt düğmesi kırmızı bir daire görüntüler.

     **CPU profilini kaydet**' i seçtiğinizde, Visual Studio işlevlerinizi kaydetmeye başlar ve ne kadar sürer ve ayrıca örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Bu toplanan verileri yalnızca, uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

6. Uygulamayı, ikinci bir kesme noktasına kadar çalıştırmak için F5'e basın.

     Şimdi, artık performans verileri bölge için özellikle uygulamanız iki kesme noktaları arasında çalışan kod için var.

     Profil Oluşturucu, iş parçacığı veri hazırlama başlar. Bitmesini bekleyin.

     CPU kullanımı aracı, raporu **CPU kullanımı** sekmesinde görüntüler.

     Bu noktada, verileri çözümlemek başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2\. adım: CPU kullanım verilerini çözümleme

CPU kullanımı altında işlevler listesini inceleyerek, en fazla çalışmayı yapan işlevleri tanımlama ve ardından her birine daha yakından bakalım alma verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en fazla çalışmayı yapan işlevler inceleyin.

     ![Tanılama araçları CPU kullanımı sekmesi](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en fazla çalışmayı yapan olanlar başlayarak sırayla listelenir (çağrı sırayla olmadıklarını). Bu, uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde `getNumber` işlevine çift tıklayın.

    İşleve çift tıkladığınızda, **çağıran/çağrılan** görünümü sol bölmede açılır.

    ![Tanılama araçları çağıran çağrılan görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "Diagtoolscallerçağrılan")

    Bu görünümde, seçilen işlev başlıkta ve **geçerli işlev** kutusunda (`getNumber`, bu örnekte) görüntülenir. Geçerli işlevi çağıran işlev sol tarafta **çağıran işlevin**altında gösterilir ve geçerli işlev tarafından çağrılan işlevler sağ taraftaki **çağrılan işlevler** kutusunda gösterilir. (Geçerli işlevin değiştirmek için ya da kutusunu seçebilirsiniz.)

    Bu görünüm, toplam süre (ms) ve genel uygulamayı işlevi tamamlamak için gerçekleştirdiği zaman yüzdesini gösterir.

    **Işlev gövdesi** Ayrıca, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. (Bu çizimde, işlev gövdesinde 119 MS 'den 43602 tanesi harcanmış ve kalan süre bu işlev tarafından çağrılan diğer kodda harcanmıştı). Gerçek değerler ortamınıza bağlı olarak çok farklı olacaktır.

    > [!TIP]
    > **Işlev gövdesindeki** yüksek değerler işlevin içinde bir performans sorununa işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans sorunlarını belirlemek için [bellek kullanımını çözümleyin](../profiling/memory-usage.md).
- CPU kullanımı aracı hakkında daha ayrıntılı bilgi için [CPU kullanımını çözümleyin](../profiling/cpu-usage.md) .
- Bir hata ayıklayıcı ekli veya çalışan bir uygulamayı hedefleyerek CPU kullanımını analiz etme-daha fazla bilgi için bkz. hata [ayıklayıcı ile veya olmayan profil oluşturma araçlarında](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [hata ayıklama olmadan profil oluşturma verileri toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) .

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
