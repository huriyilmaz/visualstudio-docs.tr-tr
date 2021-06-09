---
title: CPU kullanım verilerini analiz etme (C++)
description: CPU Kullanımı tanılama aracını kullanarak C++ ile uygulama performansını ölçme
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
ms.workload:
- cplusplus
ms.openlocfilehash: 8c68cc67d768dbe2b1c42671a02360e5cef2b56b
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760945"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Hızlı Başlangıç: Visual Studio'de CPU kullanım verilerini analiz etme (C++)

Bu Visual Studio, uygulamanıza ilişkin performans sorunlarını analiz etmenize yardımcı olacak birçok güçlü özellik sağlar. Bu konu, temel özelliklerden bazıları hakkında bilgi edinmek için hızlı bir yol sağlar. Burada, yüksek CPU kullanımından dolayı performans sorunlarını belirlemek için aracına göz atabilirsiniz. Tanılama Araçları, Visual Studio ve yerel/C++ geliştirmesi ASP.NET .NET geliştirmesi için de desteklemektedir.

Tanılama hub'ı, tanılama oturumlarınızı çalıştırmak ve yönetmek için size birçok farklı seçenek sunar. Burada **açıklanan CPU Kullanımı** aracı size ihtiyacınız olan verileri vermezse, diğer [profil](../profiling/profiling-feature-tour.md) oluşturma araçları size yardımcı olacak farklı türlerde bilgiler sağlar. Çoğu durumda, cpu' dışında bellek, işleme kullanıcı arabirimi veya ağ isteği süresi gibi bir şey, uygulama performans sorununa neden olabilir. Bu Performans Profili Oluşturucu, bu tür verileri kaydetmek ve analiz etmek için size birçok farklı seçenek sunar. Başka bir hata ayıklayıcı ile tümleşik profil oluşturma aracı [olan PerfTips,](../profiling/perftips.md)kodda adım adım ilerler ve belirli işlevlerin veya kod bloklarının tamamlanmasının ne kadar zaman alır olduğunu tanımlamanıza da olanak sağlar.

Windows 8 aracılarını hata ayıklayıcısıyla **(profil** oluşturma penceresiyle) çalıştırmak için Tanılama Araçları gerekir. Windows 7 ve sonraki bir sürümü için post-mortem aracını [Performans Profili Oluşturucu.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

   Sol **bölmede Yeni** Proje iletişim kutusunda, Visual C++'ı **genişletin** ve **ardından Windows Masaüstü'nü seçin.** Orta bölmede Windows Konsol **Uygulaması'ı seçin.** Ardından projeyi olarak *Diagnostics_Get_Started_Native.*

   **Windows** Konsolu Uygulaması proje şablonunu görmüyorsanız Yeni Proje iletişim kutusunun **Visual Studio Yükleyicisi** Aç **bağlantısını** seçin. Uygulama Visual Studio Yükleyicisi başlatıyor. **C++ ile masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

   Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C++** 'ı ve ardından Platform **listesinden Windows'u** seçin.

   Dil ve platform filtrelerini uyguladikten sonra Konsol Uygulaması **şablonunu ve** ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **C++ ile masaüstü geliştirme iş yükünü** seçin.

   Yeni **projenizi yapılandır penceresinde** Proje adı kutusuna *Diagnostics_Get_Started_Native* yazın **veya** girin. Ardından **Oluştur'a seçin.**

   ::: moniker-end

   Visual Studio projenizi açar.

1. Içinde *Diagnostics_Get_Started_Native,* aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    bu kodla (kaldırmayın): `#include "stdafx.h"`

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

## <a name="step-1-collect-profiling-data"></a>1. Adım: Profil oluşturma verilerini toplama

1. İlk olarak, işlevinde bu kod satırı üzerinde uygulamanıza bir kesme noktası `main` ayarlayın:

    `for (int i = 0; i < 10; ++i) {`

    Kod satırın sol tarafından sol tarafta yer alan oluk içinde tıklayarak bir kesme noktası ayarlayın.

2. Ardından, işlevin sonundaki kapanış ayracı üzerinde ikinci bir kesme noktası `main` ayarlayın:

     ![Profil oluşturma için kesme noktaları ayarlama](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Profil oluşturma için kesme noktaları ayarlama")

    İki kesme noktası ayarerek veri toplamayı analiz etmek istediğiniz kod bölümleriyle sınırabilirsiniz.

3. Kapalı **Tanılama Araçları** pencere zaten görünür durumdadır. Pencereyi yeniden getirmek için Windows Show'da **Hata**  >  **Ayıkla'ya**  >  **Tanılama Araçları.**

4. Hata **AyıklamaYı**  >  **Başlat 'a** tıklayın (veya araç **çubuğunda** Başlat'a veya **F5'e tıklayın.**

     Uygulamanın yüklenmesi tamam olduğunda Tanılama **Araçları'nın** Özet görünümü görüntülenir.

5. Hata ayıklayıcı duraklatılmışken, **CPU** Profilini Kayded'i seçerek CPU Kullanımı verilerini toplamayı etkinleştirin ve **ardından CPU Kullanımı sekmesini** açın.

     ![Tanılama Araçları CPU Profili Oluşturmayı Etkinleştirme](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama Araçları CPU Profili Oluşturmayı Etkinleştirme")

     Veri toplama etkinleştirildiğinde kayıt düğmesi kırmızı bir daire görüntüler.

     CPU Profilini **Kayded'i** Visual Studio, işlevlerinizi kaydetmeye ve yürütme süresine başlar ve ayrıca örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Toplanan bu verileri yalnızca uygulama bir kesme noktası durdurulduğu zaman görüntüebilirsiniz.

6. Uygulamayı ikinci kesme noktanıza çalıştırmak için F5'e tıklayın.

     Şimdi, özel olarak iki kesme noktası arasında çalışan kod bölgesi için uygulamanıza yönelik performans verilerine sahipsiniz.

     Profilleyici iş parçacığı verilerini hazırlamaya başlar. Bitimini bekleyin.

     CPU Kullanımı aracı, raporu **CPU** Kullanımı sekmesinde görüntüler.

     Bu noktada, verileri analiz etmek için başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini analiz etme

CPU Kullanımı altındaki işlev listesini inceler, en çok işi yapan işlevleri belirleyip her birini daha yakından inceler ve verilerinizi analiz ederek verilerinizi analize başlamanızı öneririz.

1. İşlev listesinde, en çok işi yapan işlevleri inceler.

     ![Tanılama Araçları CPU Kullanımı Sekmesi](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en çok işi yapanlarla (çağrı sırasına göre değil) sırayla listelenir. Bu, en uzun süre çalışan işlevleri hızlıca tanımlamanıza yardımcı olur.

2. İşlev listesinde işleve çift `getNumber` tıklayın.

    İşleve çift tıklarken, **sol bölmede Arayan/Çağrılı** görünümü açılır.

    ![Tanılama Araçları Çağıran Çağrılı Görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    Bu görünümde, seçilen işlev başlığında ve Geçerli İşlev **kutusunda** ( `getNumber` , bu örnekte) görünür. Geçerli işlevi çağıran işlev sol tarafta İşlev Çağırma'nın altında, geçerli işlev tarafından çağrılan tüm işlevler ise sağ tarafta **çağrılır** İşlevler kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutudan birini de seçin.)

    Bu görünümde, işlevin tamamlanması için gereken toplam süre (ms) ve genel uygulama çalışma süresi yüzdesi yer a gösterir.

    **İşlev Gövdesi** ayrıca, çağrılan ve çağrılan işlevlerde harcanan süre hariç olmak üzere işlev gövdesinde harcanan toplam süre miktarını (ve zaman yüzdesini) gösterir. (Bu çizimde, 43602 ms'den 119'u işlev gövdesinde harcandı ve kalan süre bu işlev tarafından çağrılan diğer kodda harcandı). Gerçek değerler ortamınıza bağlı olarak çok farklı olur.

    > [!TIP]
    > İşlev **Gövdesi'nde yüksek** değerler, işlevin içinde bir performans sorunu olduğunu gösteriyor olabilir.

## <a name="next-steps"></a>Sonraki adımlar

- [Performans sorunlarını belirlemek](../profiling/memory-usage.md)için bellek kullanımını analiz edin.
- [CPU kullanım aracı](../profiling/cpu-usage.md) hakkında daha ayrıntılı bilgi için CPU kullanımını analiz edin.
- Hata ayıklayıcı ekli olmadan veya çalışan bir uygulamayı hedefleerek CPU kullanımını analiz edin. Daha fazla bilgi için hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma'da profil oluşturma verilerini [toplama'ya bakın.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
