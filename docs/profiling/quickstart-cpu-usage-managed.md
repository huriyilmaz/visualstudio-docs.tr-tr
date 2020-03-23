---
title: CPU kullanım verilerini analiz edin (C#, Visual Basic)
description: CPU Kullanımı tanılama aracını kullanarak C# ve Visual Basic'teki uygulama performansını ölçün
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
- dotnet
ms.openlocfilehash: b4d36d9b758e0171452a909d85c799503389a1a9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550069"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Quickstart: Visual Studio'da CPU kullanım verilerini analiz edin (C#, Visual Basic)

Visual Studio, uygulamanızdaki performans sorunlarını analiz etmenize yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmek için hızlı bir yol sağlar. Burada, yüksek CPU kullanımı nedeniyle performans darboğazları belirlemek için araca bakıyoruz. Tanılama Araçları, Visual Studio'da ASP.NET ve yerel/C++ geliştirme dahil .NET geliştirme için desteklenir.

Tanılama hub'ı, tanılama oturumunuzu çalıştırmak ve yönetmek için size birçok seçenek sunar. Burada açıklanan **CPU Kullanımı** aracı size ihtiyacınız olan verileri vermiyorsa, diğer profil [oluşturma araçları](../profiling/profiling-feature-tour.md) size yardımcı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans darboğazı, bellek, kullanıcı arabirimi oluşturma veya ağ isteği süresi gibi CPU'nuz dışında başka bir şeyden kaynaklanabilir. Tanılama hub'ı, bu tür verileri kaydetmek ve çözümlemek için size birçok seçenek sunar.

Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir. Windows 7 ve sonraki sürümlerinde, post-mortem aracı, [Performans Profilleyicik](../profiling/profiling-feature-tour.md)kullanabilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio'yu açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

   Sol bölmedeki **Yeni Proje** iletişim kutusunda **C#** veya **Visual Basic'i**genişletin ve ardından **.NET Core'u**seçin. Orta bölmede Konsol **Uygulaması'nı (.NET Core)** seçin. Sonra proje *MyProfilerApp*adı .

   **Konsol Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Bulunan Görsel **Stüdyo Yükleyicisi** Açık bağlantısını seçin. Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Başlangıç penceresi açık değilse, **Dosya** > **Başlangıç Penceresi'ni**seçin.

   Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **C#** veya **Visual Basic'i** seçin ve ardından Platform listesinden **Windows'u** seçin.

   Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **sonra İleri'yi**seçin.

   > [!NOTE]
   > **Konsol Uygulaması (.NET Core)** şablonunu görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin. Ardından, Visual Studio Installer'da **.NET Core çapraz platform geliştirme** iş yükünü seçin.

   Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *MyProfilerApp* yazın veya girin. Ardından **Oluştur'u**seçin.

   ::: moniker-end

   Visual Studio yeni projenizi açıyor.

2. *Program.cs* açın ve tüm kodu aşağıdaki kodla değiştirin:

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
    > Visual Basic'te, başlangıç nesnesinin `Sub Main` **(Properties** > **Application** > **Startup Object)** ayarlandıklarına emin olun.

## <a name="step-1-collect-profiling-data"></a>Adım 1: Profil oluşturma verilerini toplama

1. İlk olarak, `Main` işlevinde bu kod satırında uygulamanızda bir kesme noktası ayarlayın:

    `for (int i = 0; i < 200; i++)`

    veya Visual Basic için:

    `For i As Integer = 0 To 199`

    Kod satırının solundaki oluk ta tıklayarak bir kesme noktası ayarlayın.

2. Ardından, `Main` işlevin sonundaki kapanış ayracına ikinci bir kesme noktası ayarlayın:

     ![Profil oluşturma için kesme noktalarını ayarlama](../profiling/media/quickstart-cpu-usage-breakpoints.png "Profil oluşturma için kesme noktalarını ayarlama")

    İki kesme noktası ayarlayarak, veri toplamayı çözümlemek istediğiniz kod bölümleriyle sınırlayabilirsiniz.

    >[!TIP]
    > Bir kesme noktasında veya kod adımatma işleminde duraklatıldığında, [PerfTips](../profiling/perftips.md)kullanarak performansı da analiz edebilirsiniz.

3. **Tanılama Araçları** penceresi, siz kapatmadığınız sürece zaten görünür. Pencereyi yeniden açmak için **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**tıklatın.

4. **Hata Ayıklama** > **Başlat Hata Ayıklama'yı** (veya araç çubuğunda **başlat'ı** veya **F5'i)** tıklatın.

     Uygulama yüklemeyi bitirdiğinde, Tanılama Araçlarının **Özet** görünümü görüntülenir.

5. Hata ayıklama duraklatılmış olsa da, **Cpu Profili Kaydet'i**seçerek CPU Kullanım verilerinin toplanmasını etkinleştirin ve ardından **CPU Kullanım** sekmesini açın.

     ![Tanılama Araçları CPU Profiloluşturmayı Etkinleştirin](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama Araçları CPU Profiloluşturmayı Etkinleştirin")

     Veri toplama etkinleştirildiğinde, kayıt düğmesi kırmızı bir daire görüntüler.

     **Cpu Profilini Kaydet'i**seçtiğinizde, Visual Studio işlevlerinizi kaydetmeye başlar ve bunların yürütülmesi için ne kadar zaman alır ve örnekleme oturumunun belirli bölümlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Toplanan bu verileri yalnızca uygulamanız bir kesme noktasında durdurulduğunda görüntüleyebilirsiniz.

6. Uygulamayı ikinci kesme noktanıza çalıştırmak için **F5** tuşuna basın.

     Şimdi, uygulamanız için özellikle iki kesme noktası arasında çalışan kod bölgesi için performans verilerine sahipsiniz.

     Profil oluşturucu iş parçacığı verilerini hazırlamaya başlar. Bitmesini bekle.

     CPU Kullanımı aracı raporu **CPU Kullanımı** sekmesinde görüntüler.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>Adım 2: CPU kullanım verilerini analiz edin

CPU Kullanımı kapsamındaki işlevlerin listesini inceleyerek, en çok iş yapan işlevleri tanımlayarak ve sonra her birine daha yakından göz atarak verilerinizi çözüme güncellemenizi öneririz.

1. İşlev listesinde, en çok iş yapan işlevleri inceleyin.

     ![Tanılama Araçları CPU Kullanım Sekmesi](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en çok işi yapanlarla başlayarak sırayla listelenir (çağrı sırasına göre değillerdir). Bu, en uzun çalışan işlevleri hızla belirlemenize yardımcı olur.

2. İşlev listesinde, `ServerClass::GetNumber` işlevi çift tıklatın.

    İşlevi çift tıklattığınızda, **Arayan/Callee** görünümü sol bölmede açılır.

    ![Tanılama Araçları Arayan Callee Görünümü](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    Bu görünümde, seçili işlev başlıkta ve **Geçerli İşlev** kutusunda (,`GetNumber`bu örnekte) görünür. Geçerli işlev olarak adlandırılan **işlev, Arama Işlevi**altında solda gösterilir ve geçerli işlev tarafından çağrılan işlevler sağdaki **Çağrı İşlevler** kutusunda gösterilir. (Geçerli işlevi değiştirmek için her iki kutuyu seçebilirsiniz.)

    Bu görünüm, toplam uygulamanın tamamlanma süresinin (ms) ve genel uygulamanın çalışma süresinin yüzdesini gösterir.

    **Fonksiyon Gövdesi** ayrıca, arama ve çağrılan işlevler dışında işlev gövdesinde harcanan toplam süreyi (ve zaman yüzdesini) gösterir. (Bu resimde, 2863 ms'den 2856'sı işlev gövdesinde, kalan süre ise (20 ms <) bu işlev tarafından çağrılan dış kodda harcandı). Gerçek değerler ortamınıza bağlı olarak farklı olacaktır.

    > [!TIP]
    > **İşlev Gövdesindeki** yüksek değerler, işlevin kendi içinde bir performans darboğazına işaret edebilir.

## <a name="next-steps"></a>Sonraki adımlar

- Performans darboğazlarını belirlemek için [bellek kullanımını analiz edin.](../profiling/memory-usage.md)
- [CPU kullanım](../profiling/cpu-usage.md) aracı hakkında daha ayrıntılı bilgi için CPU kullanımını analiz edin.
- CPU kullanımını ekli bir hata ayıklayıcı olmadan veya çalışan bir uygulamayı hedefleyerek analiz edin - [Run profiling tools with or without the debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
