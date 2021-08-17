---
title: CPU kullanım verilerini çözümleme (C#, Visual Basic)
description: CPU kullanımı tanılama aracını kullanarak C# ve Visual Basic uygulama performansını ölçme
ms.custom: mvc
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
- dotnet
ms.openlocfilehash: d3902d8119b8de8eba49cf28a7730cc41d505438
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107075"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>hızlı başlangıç: Visual Studio CPU kullanım verilerini çözümleme (C#, Visual Basic)

Visual Studio, uygulamanızdaki performans sorunlarını çözümlemenize yardımcı olacak birçok güçlü özellik sunar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımı nedeniyle performans sorunlarını belirlemek için araca bakacağız. tanılama araçları, ASP.NET dahil olmak üzere Visual Studio .net geliştirme ve yerel/C++ geliştirmesi için desteklenir.

Tanılama hub 'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size çok sayıda seçenek sunar. Burada açıklanan **CPU kullanım** aracı size ihtiyacınız olan verileri sağlamıyorsa, [diğer profil oluşturma araçları](../profiling/profiling-feature-tour.md) sizin için yararlı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorununa bellek, işleme Kullanıcı arabirimi veya ağ isteği süresi gibi CPU 'nuzun bir neden olabilir. Performans Profiler, bu tür verileri kaydetmek ve analiz etmek için size çok sayıda seçenek sunar. Diğer bir hata ayıklayıcı ile tümleşik profil oluşturma aracı olan [PerfTips](../profiling/perftips.md), kod içinde ileretmenize ve belirli işlevlerin ya da kod bloklarının ne kadar sürdüğünü tanımlamanızı sağlar.

hata ayıklayıcı (**Tanılama Araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir. Windows 7 ve üzeri sürümlerde, [performans profil oluşturucuyu](../profiling/profiling-feature-tour.md)son mordıtem aracı ' nı kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

   sol bölmedeki **yeni Project** iletişim kutusunda, **C#** veya **Visual Basic**' i genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından projeyi *Myprofilerapp* olarak adlandırın.

   **konsol uygulaması (.net Core)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** veya **Visual Basic** seçin ve ardından Platform listesinden **Windows** öğesini seçin.

   Dil ve platform filtrelerini uyguladıktan sonra .NET Core **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. sonra, Visual Studio Yükleyicisi **.net Core platformlar arası geliştirme** iş yükünü seçin.

   **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *myprofilerapp* yazın veya girin. Ardından **İleri**' yi seçin.

   Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açar.

2. *Program. cs* ' i açın ve tüm kodu aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
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
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic, başlangıç nesnesinin `Sub Main` (**özellikler**  >  **uygulaması**  >  **başlangıç nesnesi**) olarak ayarlandığından emin olun.

## <a name="step-1-collect-profiling-data"></a>1. Adım: profil oluşturma verilerini toplama

1. İlk olarak, işlevdeki Bu kod satırında uygulamanızda bir kesme noktası ayarlayın `Main` :

    `for (int i = 0; i < 200; i++)`

    ya da Visual Basic için:

    `For i As Integer = 0 To 199`

    Kod satırının solundaki cilt paya tıklayarak bir kesme noktası ayarlayın.

2. Sonra, işlevin sonundaki kapanış küme ayracı üzerinde ikinci bir kesme noktası ayarlayın `Main` :

     ![Profil oluşturma için kesme noktaları ayarla](../profiling/media/quickstart-cpu-usage-breakpoints.png "Profil oluşturma için kesme noktaları ayarla")

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

3. **Tanılama araçları** pencere, siz kapatmadığınız müddetçe zaten görünür. pencereyi yeniden getirmek için **hata ayıkla**  >  **Windows**  >  **Tanılama Araçları göster**' e tıklayın.

4. Hata   >  **ayıklamayı Başlat** ' a tıklayın (veya araç çubuğundan veya **F5**' i **başlatın** ).

     Uygulamanın yüklenmesi bittiğinde, tanılama araçlarının **Özet** görünümü görüntülenir.

5. Hata ayıklayıcı duraklatıldığında, CPU kullanım verilerinin toplanmasını sağlamak için **CPU profilini kaydet**' i seçip **CPU kullanımı** sekmesini açın.

     ![Tanılama araçları CPU profilini oluşturmayı etkinleştirir](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama araçları CPU profilini oluşturmayı etkinleştirir")

     Veri toplama etkinleştirildiğinde, kayıt düğmesi kırmızı bir daire görüntüler.

     **CPU profilini kaydet**' i seçtiğinizde Visual Studio işlevlerinizi ve ne kadar süre yürütülmeye başlayabileceğini ve ayrıca örnekleme oturumunun belirli kesimlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Bu toplanan verileri yalnızca, uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

6. Uygulamanızı ikinci kesme noktasına çalıştırmak için **F5** tuşuna basın.

     Artık, özellikle iki kesme noktası arasında çalışan kod bölgesi için uygulamanız için performans verileri vardır.

     Profil Oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekleyin.

     CPU kullanımı aracı, raporu **CPU kullanımı** sekmesinde görüntüler.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini çözümleme

CPU kullanımı altındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından bakarak verilerinizi analiz etmeye başlamanızı öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

     ![Tanılama araçları CPU kullanımı sekmesi](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en çok iş yapmaktan (çağrı sırasıyla değil) başlayarak sırayla listelenir. Bu, en uzun çalışan işlevleri hızlıca belirlemenize yardımcı olur.

2. İşlev listesinde, işlevine çift tıklayın `ServerClass::GetNumber` .

    İşleve çift tıkladığınızda, **çağıran/çağrılan** görünümü sol bölmede açılır.

    ![Tanılama araçları çağıran çağrılan görünümü](../profiling/media/quickstart-cpu-usage-caller-callee.png "Diagtoolscallerçağrılan")

    Bu görünümde, seçilen işlev başlıkta ve **geçerli işlev** kutusunda ( `GetNumber` Bu örnekte) görüntülenir. Geçerli işlevi çağıran işlev sol tarafta **çağıran işlevin** altında gösterilir ve geçerli işlev tarafından çağrılan işlevler sağ taraftaki **çağrılan işlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutuyu da seçebilirsiniz.)

    Bu görünümde, işlevin tamamlanışında toplam süre (MS) ve Toplam uygulama çalışma zamanının yüzdesi gösterilir.

    **Işlev gövdesi** Ayrıca, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. (Bu çizimde, işlev gövdesinde 2856 MS 'tan 2863 tanesi harcanmış ve kalan süre (<20 ms) Bu işlev tarafından çağrılan harici kodda harcanmıştı). Gerçek değerler ortamınıza bağlı olarak farklı olacaktır.

    > [!TIP]
    > **Işlev gövdesindeki** yüksek değerler işlevin içinde bir performans sorununa işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans sorunlarını belirlemek için [bellek kullanımını çözümleyin](../profiling/memory-usage.md).
- CPU kullanımı aracı hakkında daha ayrıntılı bilgi için [CPU kullanımını çözümleyin](../profiling/cpu-usage.md) .
- Bir hata ayıklayıcı ekli veya çalışan bir uygulamayı hedefleyerek CPU kullanımını analiz etme-daha fazla bilgi için bkz. hata [ayıklayıcı ile veya olmayan profil oluşturma araçlarında](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [hata ayıklama olmadan profil oluşturma verileri toplama](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) .

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
