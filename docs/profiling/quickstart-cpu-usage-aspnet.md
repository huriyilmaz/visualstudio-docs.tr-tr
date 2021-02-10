---
title: CPU kullanım verilerini çözümleme (ASP.NET Core)
description: CPU kullanımı Tanılama aracını kullanarak ASP.NET Core uygulamalarda uygulama performansını ölçme
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 7170983732ff1350061629e1e8aa4ec88fad3fa1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952843"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Hızlı başlangıç: Visual Studio 'da CPU kullanım verilerini çözümleme (ASP.NET Core)

Visual Studio, uygulamanızdaki performans sorunlarını çözümlemenize yardımcı olacak birçok güçlü özellik sunar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımı nedeniyle performans sorunlarını belirlemek için bir araca bakacağız. Tanılama araçları, ASP.NET dahil olmak üzere Visual Studio 'da .NET geliştirme ve yerel/C++ geliştirmesi için desteklenir.

Tanılama hub 'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size çok sayıda seçenek sunar. Burada açıklanan **CPU kullanım** aracı size ihtiyacınız olan verileri sağlamıyorsa, [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) sizin için yararlı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorununa bellek, işleme Kullanıcı arabirimi veya ağ isteği süresi gibi CPU 'nuzun bir neden olabilir. Diğer bir hata ayıklayıcı ile tümleşik profil oluşturma aracı olan [PerfTips](../profiling/perftips.md), kod içinde ileretmenize ve belirli işlevlerin ya da kod bloklarının ne kadar sürdüğünü tanımlamanızı sağlar.

Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir. Windows 7 ve üzeri sürümlerde, [performans profil oluşturucuyu](../profiling/profiling-feature-tour.md)son mordıtem Aracı ' nı kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio 'Yu açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

   Sol bölmedeki **Yeni proje** iletişim kutusunda, **Visual C#**' ı genişletin ve ardından **Web**' i seçin. Orta bölmede **ASP.NET Web uygulaması (.NET Core)** öğesini seçin. Sonra *MyProfilingApp_MVC* projeyi adlandırın.

   > [!NOTE]
   > **ASP.NET Web uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **ASP.net ve Web geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   Görüntülenen iletişim kutusunda Ortadaki bölmede **MVC** ' yi seçin ve ardından **Tamam**' a tıklayın.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *ASP.net* girin veya yazın. Ardından, dil listesinden **C#** öğesini seçin ve ardından platform listesinden **Windows** ' u seçin.

   Dil ve platform filtrelerini uyguladıktan sonra, **ASP.NET Web uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > **ASP.NET Web uygulaması (.NET Core)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Ardından Visual Studio Yükleyicisi, **ASP.net ve Web geliştirme** iş yükünü seçin.

   **Yeni projeyi yapılandırın** penceresinde, **proje adı** kutusuna *MyProfilingApp_MVC* yazın veya girin. Ardından **Oluştur**' u seçin.

   Görüntülenen pencerede, **Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **Oluştur**' u seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açar.

1. Çözüm Gezgini, modeller klasörüne sağ tıklayın ve sınıf **Ekle**' yi seçin  >  .

1. Yeni sınıfı adlandırın `Data.cs` ve **Ekle**' yi seçin.

1. Çözüm Gezgini ' de açın `Models/Data.cs` ve aşağıdaki `using` ifadeyi dosyanın en üstüne ekleyin:

    ```csharp
    using System.Threading;
    ```

1. Data.cs ' de, aşağıdaki kodu değiştirin:

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

1. Çözüm Gezgini, *Controller/HomeControllers. cs*' yi açın ve aşağıdaki kodu değiştirin:

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
    ::: moniker range="vs-2019"

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


## <a name="step-1-collect-profiling-data"></a>1. Adım: profil oluşturma verilerini toplama

1. İlk olarak, kurucudaki Bu kod satırında uygulamanızda bir kesme noktası ayarlayın `Simple` :

    `for (int i = 0; i < 200; i++)`

    Kod satırının solundaki cilt paya tıklayarak bir kesme noktası ayarlayın.

1. Sonra, oluşturucunun sonundaki kapanış küme ayracı üzerinde ikinci bir kesme noktası ayarlayın `Simple` :

     ![Profil oluşturma için kesme noktaları ayarla](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

1. **Tanılama araçları** pencere, siz kapatmadığınız müddetçe zaten görünür. Pencereyi yeniden getirmek için, **Hata Ayıkla**  >  **Windows**  >  **Tanılama araçları göster**' e tıklayın.

1. Hata   >  **ayıklamayı Başlat** ' a tıklayın (veya araç çubuğundan veya **F5**' i **başlatın** ).

1. Uygulamanın yüklenmesi bittiğinde, yeni kodu çalıştırmaya başlamak için Web sayfasının en üstündeki uygun bağlantıya tıklayın.

   ::: moniker range="vs-2017"
   Visual Studio 2017 ' de, kodu çalıştırmak için **hakkında** bağlantısına tıklayın.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Visual Studio 2019 ' de, kodu çalıştırmak için **Gizlilik** bağlantısına tıklayın.
   ::: moniker-end

1. Tanılama araçlarının **Özet** görünümüne bakın.

1. Hata ayıklayıcı duraklatıldığında, CPU kullanım verilerinin toplanmasını sağlamak için **CPU profilini kaydet**' i seçip **CPU kullanımı** sekmesini açın.

     ![Tanılama araçları CPU profilini oluşturmayı etkinleştirir](../profiling/media/quickstart-cpu-usage-summary.png)

     Veri toplama etkinleştirildiğinde, kayıt düğmesi kırmızı bir daire görüntüler.

     **CPU profilini kaydet**' i seçtiğinizde, Visual Studio işlevlerinizi kaydetmeye başlar ve ne kadar sürer ve ayrıca örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Bu toplanan verileri yalnızca, uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

6. Uygulamanızı ikinci kesme noktasına çalıştırmak için F5 'e basın.

     Artık, özellikle iki kesme noktası arasında çalışan kod bölgesi için uygulamanız için performans verileri vardır.

     Profil Oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekleyin.

     CPU kullanımı aracı, raporu **CPU kullanımı** sekmesinde görüntüler.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini çözümleme

CPU kullanımı altındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından bakarak verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

     ![Tanılama araçları CPU kullanımı sekmesi](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > İşlevler, en çok iş yapmaktan (çağrı sırasıyla değil) başlayarak sırayla listelenir. Bu, en uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde, işlevine çift tıklayın `MyProfilingApp_MVC.Models.ServerClass::GetNumber` .

    İşleve çift tıkladığınızda, **çağıran/çağrılan** görünümü sol bölmede açılır.

    ![Tanılama araçları arayan/çağrılan görünümü](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    Bu görünümde, seçilen işlev başlıkta ve **geçerli işlev** kutusunda ( `ServerClass::GetNumber` Bu örnekte) görüntülenir. Geçerli işlevi çağıran işlev sol tarafta **çağıran işlevin** altında gösterilir ve geçerli işlev tarafından çağrılan işlevler sağ taraftaki **çağrılan işlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutuyu da seçebilirsiniz.)

    Bu görünümde, işlevin tamamlanışında toplam süre (MS) ve Toplam uygulama çalışma zamanının yüzdesi gösterilir.

    **Işlev gövdesi** Ayrıca, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. (Bu çizimde, işlev gövdesinde 2220 MS 'tan 2235 tanesi harcanmış ve kalan süre (<20 ms) Bu işlev tarafından çağrılan harici kodda harcanmıştı). Gerçek değerler ortamınıza bağlı olarak farklı olacaktır.

    > [!TIP]
    > **Işlev gövdesindeki** yüksek değerler işlevin içinde bir performans sorununa işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans sorunlarını belirlemek için [bellek kullanımını çözümleyin](../profiling/memory-usage.md).
- CPU kullanımı aracı hakkında daha ayrıntılı bilgi için [CPU kullanımını çözümleyin](../profiling/cpu-usage.md) .
- Bir hata ayıklayıcı ekli veya çalışan bir uygulamayı hedefleyerek CPU kullanımını analiz etme-daha fazla bilgi için bkz. hata [ayıklayıcı ile veya olmayan profil oluşturma araçlarında](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [hata ayıklama olmadan profil oluşturma verileri toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) .

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
