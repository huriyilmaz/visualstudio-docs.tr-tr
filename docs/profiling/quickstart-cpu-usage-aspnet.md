---
title: CPU kullanım verilerini analiz etme (ASP.NET Core)
description: CPU Kullanımı tanılama aracını ASP.NET Core uygulamalar için uygulama performansını ölçme
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 05841860e096186706966e96b55357883fbf606b
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970470"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Hızlı Başlangıç: Cpu kullanım verilerini Visual Studio (ASP.NET Core)

Visual Studio uygulamanıza performans sorunlarını analiz etmenize yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmenin hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımından dolayı performans sorunlarını belirlemek için bir araça göz atabilirsiniz. Tanılama Araçları, ASP.NET ve yerel/C++ geliştirme dahil olmak üzere Visual Studio.NET geliştirmesi için de desteklemektedir.

Tanılama hub'ı, tanılama oturumlarınızı çalıştırmak ve yönetmek için size birçok farklı seçenek sunar. Burada **açıklanan CPU Kullanımı** aracı size ihtiyacınız olan verileri vermezse, diğer [profil](../profiling/profiling-feature-tour.md) oluşturma araçları size yardımcı olacak farklı türlerde bilgiler sağlar. Çoğu durumda, cpu' dışında bellek, işleme kullanıcı arabirimi veya ağ isteği süresi gibi bir şey, uygulama performans sorununa neden olabilir. Başka bir hata ayıklayıcı ile tümleşik profil oluşturma aracı [olan PerfTips,](../profiling/perftips.md)kodda adım adım ilerler ve belirli işlevlerin veya kod bloklarının tamamlanmasının ne kadar zaman alır olduğunu tanımlamanıza da olanak sağlar.

Windows 8 aracılarını hata ayıklayıcısıyla **(profil** oluşturma penceresiyle) çalıştırmak için Tanılama Araçları gerekir. 7 Windows ve sonraki bir sonraki bir gün için, post-mortem aracını [Performans Profili Oluşturucu.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

   Sol **bölmede yeni Project** iletişim kutusunda Visual **C#** öğesini genişletin ve ardından **Web'i seçin.** Orta bölmede Web Uygulaması **ASP.NET (.NET Core) 'yi seçin.** Ardından projeyi olarak *MyProfilingApp_MVC.*

   > [!NOTE]
   > **ASP.NET Web Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, Yeni  Project iletişim kutusunun sol bölmesindeki Visual Studio Yükleyicisi Aç **bağlantısını** seçin. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**

   Görüntülenen iletişim kutusunda orta bölmede **MVC'yi** seçin ve ardından Tamam'a **tıklayın.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **ve** ardından Yeni proje **oluştur'a tıklayın.**

   Arama **kutusuna web uygulaması** yazın, dil olarak **C#** seçin, ASP.NET Core Web Uygulaması **(Model-Görünüm-Denetleyici)** seçin ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeyi olarak MyProfilingApp_MVC *ve* ardından Sonraki'yi **seçin.**

   Önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından **Oluştur'a seçin.**

   > [!NOTE]
   > ASP.NET Web Uygulaması **(.NET Core)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **iş yükünü** seçin.
   ::: moniker-end

   Visual Studio projenizi oluşturur ve açar.

1. Bu Çözüm Gezgini Models klasörüne sağ tıklayın ve Sınıf **Ekle'yi**  >  **seçin.**

1. Yeni sınıfı olarak ad girin `Data.cs` ve **Ekle'yi seçin.**

1. Aşağıdaki Çözüm Gezgini dosyasını `Models/Data.cs` açın ve `using` dosyanın en üstüne aşağıdaki deyimini ekleyin:

    ```csharp
    using System.Threading;
    ```

1. Data.cs içinde aşağıdaki kodu değiştirin:

    ```csharp
    public class Data
    {
    }
    ```

    yerine şu kodu yazın:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. Bu Çözüm Gezgini *Controller/HomeControllers.cs'yi* açın ve aşağıdaki kodu değiştirin:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    yerine şu kodu yazın:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range=">=vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    yerine şu kodu yazın:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>1. Adım: Profil oluşturma verilerini toplama

1. İlk olarak, oluşturucuda bu kod satırı üzerinde uygulamanıza bir kesme noktası `Simple` ayarlayın:

    `for (int i = 0; i < 200; i++)`

    Kod satırın sol tarafından sol tarafta yer alan oluk içinde tıklayarak bir kesme noktası ayarlayın.

1. Ardından, oluşturucuslarının sonundaki kapanış ayracı üzerinde ikinci bir kesme noktası `Simple` ayarlayın:

     ![Profil oluşturma için kesme noktaları ayarlama](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    İki kesme noktası ayarerek veri toplamayı analiz etmek istediğiniz kod bölümleriyle sınırabilirsiniz.

1. Kapalı **Tanılama Araçları** pencere zaten görünür durumdadır. Pencereyi yeniden getirmek için Hata Ayıkla'ya **tıklayın**  >  **Windows**  >  **Show Tanılama Araçları**.

1. Hata **AyıklamaYı**  >  **Başlat 'a** tıklayın (veya araç **çubuğunda** Başlat'a veya **F5'e tıklayın.**

1. Uygulamanın yüklenmesi tamam olduğunda, yeni kodu çalıştırmaya başlamak için web sayfasının üst kısmında uygun bağlantıya tıklayın.

   ::: moniker range="vs-2017"
   2017 Visual Studio de, kodu çalıştırmak **için Hakkında** bağlantısına tıklayın.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Bu Visual Studio 2019'da, **kodu çalıştırmak** için Gizlilik bağlantısına tıklayın.
   ::: moniker-end

1. Tanılama **Araçları'nın** Özet görünümüne bakın.

1. Hata ayıklayıcı duraklatılmışken, CPU Profilini Kayded'i seçerek CPU Kullanımı verileri koleksiyonunu **etkinleştirin** ve **ardından CPU** Kullanımı sekmesini açın.

     ![Tanılama Araçları CPU Profili Oluşturmayı Etkinleştirme](../profiling/media/quickstart-cpu-usage-summary.png)

     Veri toplama etkinleştirildiğinde kayıt düğmesi kırmızı bir daire görüntüler.

     CPU Profilini **Kayded'i** Visual Studio, işlevlerinizi kaydetmeye ve yürütme süresine başlar ve ayrıca örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Toplanan bu verileri yalnızca uygulama bir kesme noktası durdurulduğu zaman görüntüebilirsiniz.

6. Uygulamayı ikinci kesme noktanıza çalıştırmak için F5'e tıklayın.

     Şimdi, iki kesme noktası arasında çalışan kodun bölgesi için özel olarak uygulamanıza yönelik performans verilerine sahipsiniz.

     Profilleyici iş parçacığı verilerini hazırlamaya başlar. Bitimini bekleyin.

     CPU Kullanımı aracı raporu CPU Kullanımı **sekmesinde** görüntüler.

     Bu noktada, verileri analiz etmek için başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini analiz etme

CPU Kullanımı altındaki işlev listesini inceler, en çok işi yapan işlevleri belirleyip her birini daha yakından inceler ve verilerinizi analiz ederek verilerinizi analize başlamanızı öneririz.

1. İşlev listesinde, en çok işi yapan işlevleri inceler.

     ![Tanılama araçları CPU Kullanımı sekmesi](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > İşlevler, en çok işi yapanlarla (çağrı sırasına göre değil) sırayla listelenir. Bu, en uzun süre çalışan işlevleri hızlıca tanımlamanıza yardımcı olur.

2. İşlev listesinde işleve çift `MyProfilingApp_MVC.Models.ServerClass::GetNumber` tıklayın.

    İşleve çift tıklarken, **sol bölmede Arayan/Çağrılı** görünümü açılır.

    ![Tanılama araçları Arayan/Çağrılı Görünüm](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    Bu görünümde, seçilen işlev başlığında ve Geçerli İşlev **kutusunda** ( `ServerClass::GetNumber` , bu örnekte) görünür. Geçerli işlevi çağıran işlev sol tarafta İşlev Çağırma'nın altında, geçerli işlev tarafından çağrılan tüm işlevler ise sağ tarafta **çağrılır** İşlevler kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutudan birini de seçin.)

    Bu görünümde, işlevin tamamlanması için gereken toplam süre (ms) ve genel uygulama çalışma süresi yüzdesi yer a gösterir.

    **İşlev Gövdesi** ayrıca, çağrılan ve çağrılan işlevlerde harcanan süre hariç olmak üzere işlev gövdesinde harcanan toplam süre miktarını (ve zaman yüzdesini) gösterir. (Bu çizimde, 2235 ms'den 2220 ms'i işlev gövdesinde harcandı ve kalan süre (<20 ms) bu işlev tarafından çağrılan dış kodda harcandı). Gerçek değerler ortamınıza bağlı olarak farklı olur.

    > [!TIP]
    > İşlev **Gövdesi'nde yüksek** değerler, işlevin içinde bir performans sorunu olduğunu gösteriyor olabilir.

## <a name="next-steps"></a>Sonraki adımlar

- [Performans sorunlarını belirlemek](../profiling/memory-usage.md)için bellek kullanımını analiz edin.
- [CPU kullanım aracı](../profiling/cpu-usage.md) hakkında daha ayrıntılı bilgi için CPU kullanımını analiz edin.
- Hata ayıklayıcı ekli olmadan veya çalışan bir uygulamayı hedefleerek CPU kullanımını analiz edin. Daha fazla bilgi için hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma'da profil oluşturma verilerini [toplama'ya bakın.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de profil Visual Studio](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
