---
title: CPU kullanım verilerini analiz et (ASP.NET Core)
description: CPU Kullanımı tanılama aracını kullanarak ASP.NET Core uygulamalarında uygulama performansını ölçün
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bb1d5fc769254f112e3a4cb757b173e0dbded3bb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550099"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Quickstart: Visual Studio'da CPU kullanım verilerini analiz edin (ASP.NET Core)

Visual Studio, uygulamanızdaki performans sorunlarını analiz etmenize yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmek için hızlı bir yol sağlar. Burada, yüksek CPU kullanımı nedeniyle performans darboğazları belirlemek için bir araç bakmak. Tanılama Araçları, Visual Studio'da ASP.NET ve yerel/C++ geliştirme dahil .NET geliştirme için desteklenir.

Tanılama hub'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size birçok seçenek sunar. Burada açıklanan **CPU Kullanımı** aracı size ihtiyacınız olan verileri vermiyorsa, diğer profil [oluşturma araçları](../profiling/profiling-feature-tour.md) size yardımcı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans darboğazı, bellek, kullanıcı arabirimi oluşturma veya ağ isteği süresi gibi CPU'nuz dışında başka bir şeyden kaynaklanabilir.

Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir. Windows 7 ve sonraki sürümlerinde, post-mortem aracı, [Performans Profilleyicik](../profiling/profiling-feature-tour.md)kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'yu açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

   Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual C#** seçeneğini genişletin ve ardından **Web'i**seçin. Orta bölmede, **Web Uygulaması (.NET Core) ASP.NET**seçin. Sonra proje *MyProfilingApp_MVC.*

   > [!NOTE]
   > **web uygulaması (.NET Core)** proje şablonunun ASP.NET görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Open Visual **Studio Installer** bağlantısını seçin. Visual Studio Installer başlattı. ASP.NET **ve web geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

   Görünen iletişim kutusunda, orta bölmedeki **MVC'yi** seçin ve ardından **Tamam'ı**tıklatın.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Başlangıç penceresi açık değilse, **Dosya** > **Başlangıç Penceresi'ni**seçin.

   Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   Yeni **proje oluştur** penceresinde, arama kutusuna *asp.net* girin veya yazın. Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Windows'u** seçin.

   Dil ve platform filtrelerini uyguladıktan **sonra, ASP.NET Web Uygulaması (.NET Core)** şablonuna ve ardından **İleri'yi**seçin.

   > [!NOTE]
   > **web uygulaması (.NET Core) şablonu ASP.NET** görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin. Ardından, Visual Studio Installer'da **ASP.NET ve web geliştirme** iş yükünü seçin.

   Yeni **proje pencerenizi Yapılandır'** da Proje **adı** kutusuna *MyProfilingApp_MVC* yazın veya girin. Ardından **Oluştur'u**seçin.

   Görüntülenen pencerede **Web Uygulaması'nı (Model-View-Controller)** seçin ve ardından **Oluştur'u**seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açıyor.

1. Çözüm Gezgini'nde Modeller klasörüne sağ tıklayın ve**Sınıf** **Ekle'yi** > seçin.

1. Yeni sınıfı `Data.cs` adlandırın ve **Ekle'yi**seçin.

1. Çözüm Gezgini'nde, dosyanın üst kısmında aşağıdaki `Models/Data.cs` `using` ifadeyi açın ve ekleyin:

    ```csharp
    using System.Threading;
    ```

1. Data.cs olarak, aşağıdaki kodu değiştirin:

    ```csharp
    public class Data
    {
    }
    ```

    bu kod ile:

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

1. Solution Explorer'da *Controller/HomeControllers.cs'yi*açın ve aşağıdaki kodu değiştirin:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    bu kod ile:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range="vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    bu kod ile:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Adım 1: Profil oluşturma verilerini toplama

1. İlk olarak, `Simple` oluşturucudaki bu kod satırında uygulamanızda bir kesme noktası ayarlayın:

    `for (int i = 0; i < 200; i++)`

    Kod satırının solundaki oluk ta tıklayarak bir kesme noktası ayarlayın.

1. Ardından, `Simple` oluşturucunun sonundaki kapanış ayracına ikinci bir kesme noktası ayarlayın:

     ![Profil oluşturma için kesme noktalarını ayarlama](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

    >[!TIP]
    > Bir kesme noktasında veya kod adımatma işleminde duraklatıldığında, [PerfTips](../profiling/perftips.md)kullanarak performansı da analiz edebilirsiniz.

1. **Tanılama Araçları** penceresi, siz kapatmadığınız sürece zaten görünür. Pencereyi yeniden açmak için **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**tıklatın.

1. **Hata Ayıklama** > **Başlat Hata Ayıklama'yı** (veya araç çubuğunda **başlat'ı** veya **F5'i)** tıklatın.

1. Uygulama yüklemeyi bitirdiğinde, yeni kodu çalıştırmaya başlamak için web sayfasının üst kısmındaki uygun bağlantıyı tıklatın.

   ::: moniker range="vs-2017"
   Visual Studio 2017'de kodu çalıştırmak için **Hakkında** bağlantısını tıklayın.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Visual Studio 2019'da kodu çalıştırmak için **Gizlilik** bağlantısını tıklatın.
   ::: moniker-end

1. Tanılama Araçlarının **Özet** görünümüne bakın.

1. Hata ayıklama duraklatılmış olsa da, **Cpu Profili Kaydet'i**seçerek CPU Kullanım verilerinin toplanmasını etkinleştirin ve ardından **CPU Kullanım** sekmesini açın.

     ![Tanılama Araçları CPU Profiloluşturmayı Etkinleştirin](../profiling/media/quickstart-cpu-usage-summary.png)

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

     ![Tanılama araçları CPU Kullanım sekmesi](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > İşlevler, en çok işi yapanlarla başlayarak sırayla listelenir (çağrı sırasına göre değillerdir). Bu, en uzun çalışan işlevleri hızla belirlemenize yardımcı olur.

2. İşlev listesinde, `MyProfilingApp_MVC.Models.ServerClass::GetNumber` işlevi çift tıklatın.

    İşlevi çift tıklattığınızda, **Arayan/Callee** görünümü sol bölmede açılır.

    ![Tanılama araçları Arayan/Callee Görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    Bu görünümde, seçili işlev başlıkta ve **Geçerli İşlev** kutusunda (,`ServerClass::GetNumber`bu örnekte) görünür. Geçerli işlev olarak adlandırılan **işlev, Arama Işlevi**altında solda gösterilir ve geçerli işlev tarafından çağrılan işlevler sağdaki **Çağrı İşlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için her iki kutuyu seçebilirsiniz.)

    Bu görünüm, toplam uygulamanın tamamlanma süresinin (ms) ve genel uygulamanın çalışma süresinin yüzdesini gösterir.

    **Fonksiyon Gövdesi** ayrıca, arama ve çağrılan işlevler dışında işlev gövdesinde harcanan toplam süreyi (ve zaman yüzdesini) gösterir. (Bu resimde, 2235 ms'den 2220'si işlev gövdesinde, kalan süre ise 20 ms'<bu işlevtarafından çağrılan dış kodda harcandı). Gerçek değerler ortamınıza bağlı olarak farklı olacaktır.

    > [!TIP]
    > **İşlev Gövdesindeki** yüksek değerler, işlevin kendi içinde bir performans darboğazına işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans darboğazlarını belirlemek için [bellek kullanımını analiz edin.](../profiling/memory-usage.md)
- [CPU kullanım](../profiling/cpu-usage.md) aracı hakkında daha ayrıntılı bilgi için CPU kullanımını analiz edin.
- CPU kullanımını ekli bir hata ayıklayıcı olmadan veya çalışan bir uygulamayı hedefleyerek analiz edin - [Run profiling tools with or without the debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
