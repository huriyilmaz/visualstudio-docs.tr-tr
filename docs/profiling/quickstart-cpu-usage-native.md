---
title: CPU kullanım verilerini analiz et (C++)
description: CPU Kullanımı tanılama aracını kullanarak C++'da uygulama performansını ölçme
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
ms.openlocfilehash: 602a185b598410de47dc9d3c98ca2b0ae3c45633
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80412005"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Quickstart: Visual Studio'da CPU kullanım verilerini analiz edin (C++)

Visual Studio, uygulamanızdaki performans sorunlarını analiz etmenize yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmek için hızlı bir yol sağlar. Burada, yüksek CPU kullanımı nedeniyle performans darboğazları belirlemek için araca bakıyoruz. Tanılama Araçları, Visual Studio'da ASP.NET ve yerel/C++ geliştirme dahil .NET geliştirme için desteklenir.

Tanılama hub'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size birçok seçenek sunar. Burada açıklanan **CPU Kullanımı** aracı size ihtiyacınız olan verileri vermiyorsa, diğer profil [oluşturma araçları](../profiling/profiling-feature-tour.md) size yardımcı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans darboğazı, bellek, kullanıcı arabirimi oluşturma veya ağ isteği süresi gibi CPU'nuz dışında başka bir şeyden kaynaklanabilir. Tanılama hub'ı, bu tür verileri kaydetmek ve çözümlemek için size birçok seçenek sunar. [PerfTips](../profiling/perftips.md), başka bir hata ayıklama entegre profil oluşturma aracı, aynı zamanda kod üzerinden adım ve tamamlamak için belirli işlevleri veya kod blokları ne kadar sürdüğünü belirlemenize olanak sağlar.

Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir. Windows 7 ve sonraki sürümlerinde, post-mortem aracı, [Performans Profilleyicik](../profiling/profiling-feature-tour.md)kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'yu açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

   Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual C++'ı**genişletin ve ardından **Windows Desktop'ı**seçin. Orta bölmede Windows **Console Uygulaması'nı**seçin. O zaman projeyi *Diagnostics_Get_Started_Native.*

   **Windows Console Application** proje şablonu görmüyorsanız, Yeni **Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** Aç bağlantısını seçin. Visual Studio Installer başlattı. C++ iş **yüküyle Masaüstü geliştirmeyi** seçin ve sonra **Değiştir'i**seçin.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Başlangıç penceresi açık değilse, **Dosya** > **Başlangıç Penceresi'ni**seçin.

   Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **C++'yi** seçin ve ardından Platform listesinden **Windows'u** seçin.

   Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması** şablonu'nu seçin ve **sonra İleri'yi**seçin.

   > [!NOTE]
   > **Konsol Uygulaması** şablonu görmüyorsanız, yeni bir **proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin. Ardından, Visual Studio Installer'da C++ iş **yüküne sahip Masaüstü geliştirmesini** seçin.

   Yeni **proje pencerenizi Yapılandır'** da Proje **adı** kutusuna *Diagnostics_Get_Started_Native* yazın veya girin. Ardından **Oluştur'u**seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açıyor.

1. *Diagnostics_Get_Started_Native,* aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    bu kod ile (kaldırmayın): `#include "stdafx.h"`

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

## <a name="step-1-collect-profiling-data"></a>Adım 1: Profil oluşturma verilerini toplama

1. İlk olarak, `main` işlevinde bu kod satırında uygulamanızda bir kesme noktası ayarlayın:

    `for (int i = 0; i < 10; ++i) {`

    Kod satırının solundaki oluk ta tıklayarak bir kesme noktası ayarlayın.

2. Ardından, `main` işlevin sonundaki kapanış ayracına ikinci bir kesme noktası ayarlayın:

     ![Profil oluşturma için kesme noktalarını ayarlama](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Profil oluşturma için kesme noktalarını ayarlama")

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

3. **Tanılama Araçları** penceresi, siz kapatmadığınız sürece zaten görünür. Pencereyi yeniden açmak için **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**tıklatın.

4. **Hata Ayıklama** > **Başlat Hata Ayıklama'yı** (veya araç çubuğunda **başlat'ı** veya **F5'i)** tıklatın.

     Uygulama yüklemeyi bitirdiğinde, Tanılama Araçlarının **Özet** görünümü görüntülenir.

5. Hata ayıklama duraklatılmış olsa da, **Cpu Profili Kaydet'i**seçerek CPU Kullanım verilerinin toplanmasını etkinleştirin ve ardından **CPU Kullanım** sekmesini açın.

     ![Tanılama Araçları CPU Profiloluşturmayı Etkinleştirin](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama Araçları CPU Profiloluşturmayı Etkinleştirin")

     Veri toplama etkinleştirildiğinde, kayıt düğmesi kırmızı bir daire görüntüler.

     **Cpu Profilini Kaydet'i**seçtiğinizde, Visual Studio işlevlerinizi kaydetmeye başlar ve bunların yürütülmesi için ne kadar zaman alır ve örnekleme oturumunun belirli bölümlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Toplanan bu verileri yalnızca uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

6. Uygulamayı ikinci kesme noktanıza çalıştırmak için F5 tuşuna basın.

     Şimdi, uygulamanız için özellikle iki kesme noktası arasında çalışan kod bölgesi için performans verilerine sahipsiniz.

     Profil oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekle.

     CPU Kullanımı aracı raporu **CPU Kullanımı** sekmesinde görüntüler.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>Adım 2: CPU kullanım verilerini analiz edin

CPU Kullanımı kapsamındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından göz atarak verilerinizi çözüme güncellemenizi öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

     ![Tanılama Araçları CPU Kullanım Sekmesi](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en çok işi yapanlarla başlayarak sırayla listelenir (çağrı sırasına göre değillerdir). Bu, en uzun çalışan işlevleri hızla belirlemenize yardımcı olur.

2. İşlev listesinde, `getNumber` işlevi çift tıklatın.

    İşlevi çift tıklattığınızda, **Arayan/Callee** görünümü sol bölmede açılır.

    ![Tanılama Araçları Arayan Callee Görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    Bu görünümde, seçili işlev başlıkta ve **Geçerli İşlev** kutusunda (,`getNumber`bu örnekte) görünür. Geçerli işlev olarak adlandırılan **işlev, Arama Işlevi**altında solda gösterilir ve geçerli işlev tarafından çağrılan işlevler sağdaki **Çağrı İşlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için her iki kutuyu seçebilirsiniz.)

    Bu görünüm, toplam uygulamanın tamamlanma süresinin (ms) ve genel uygulamanın çalışma süresinin yüzdesini gösterir.

    **Fonksiyon Gövdesi** ayrıca, arama ve çağrılan işlevler dışında işlev gövdesinde harcanan toplam süreyi (ve zaman yüzdesini) gösterir. (Bu resimde, 43602 ms'den 119'u işlev gövdesinde harcandı ve kalan süre bu işlev tarafından çağrılan diğer kodda harcandı). Gerçek değerler ortamınıza bağlı olarak çok farklı olacaktır.

    > [!TIP]
    > **İşlev Gövdesindeki** yüksek değerler, işlevin kendi içinde bir performans darboğazına işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans darboğazlarını belirlemek için [bellek kullanımını analiz edin.](../profiling/memory-usage.md)
- [CPU kullanım](../profiling/cpu-usage.md) aracı hakkında daha ayrıntılı bilgi için CPU kullanımını analiz edin.
- CPU kullanımını ekli bir hata ayıklayıcı olmadan veya çalışan bir uygulamayı hedefleyerek analiz edin - [Run profiling tools with or without the debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
