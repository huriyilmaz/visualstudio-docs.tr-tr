---
title: CPU kullanım verilerini analiz etme (C#, Visual Basic)
description: CPU Kullanımı tanılama aracını kullanarak C# Visual Basic uygulama performansını ölçme
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
- dotnet
ms.openlocfilehash: 056996782d2b38adb96ee53250cc3ea0c0f75596
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761166"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Hızlı Başlangıç: Cpu kullanım verilerini Visual Studio (C#, Visual Basic)

Visual Studio uygulamanıza performans sorunlarını analiz etmenize yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmenin hızlı bir yolunu sağlar. Burada, yüksek CPU kullanımından dolayı performans sorunlarını belirlemek için aracına göz atabilirsiniz. Tanılama Araçları, Visual Studio ve yerel/C++ geliştirmesi ASP.NET .NET geliştirmesi için de desteklemektedir.

Tanılama hub'ı, tanılama oturumlarınızı çalıştırmak ve yönetmek için size birçok farklı seçenek sunar. Burada **açıklanan CPU Kullanımı** aracı size ihtiyacınız olan verileri vermezse, diğer [profil](../profiling/profiling-feature-tour.md) oluşturma araçları size yardımcı olacak farklı türlerde bilgiler sağlar. Çoğu durumda, cpu' dışında bellek, işleme kullanıcı arabirimi veya ağ isteği süresi gibi bir şey, uygulama performans sorununa neden olabilir. Bu Performans Profili Oluşturucu, bu tür verileri kaydetmek ve analiz etmek için size birçok farklı seçenek sunar. Başka bir hata ayıklayıcı ile tümleşik profil oluşturma aracı [olan PerfTips,](../profiling/perftips.md)kodda adım adım ilerler ve belirli işlevlerin veya kod bloklarının tamamlanmasının ne kadar zaman alır olduğunu tanımlamanıza da olanak sağlar.

Windows 8 aracılarını hata ayıklayıcısıyla **(profil** oluşturma penceresiyle) çalıştırmak için Tanılama Araçları gerekir. Windows 7 ve sonraki bir sürümü için post-mortem aracını [Performans Profili Oluşturucu.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Proje oluşturma

1. Visual Studio açın ve projeyi oluşturun.

   ::: moniker range="vs-2017"
   Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

   Sol **bölmede Yeni** Proje iletişim kutusunda **C#** veya Visual Basic **genişletin** ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *MyProfilerApp adını girin.*

   Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız Yeni Proje iletişim kutusunun **sol** bölmesinde Visual Studio Yükleyicisi Aç **bağlantısını** seçin. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

   Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** **Visual Basic** seçin ve ardından Platform **listesinden Windows'u** seçin.

   Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.

   Yeni **projenizi yapılandır penceresinde** Proje adı kutusuna *MyProfilerApp* **yazın veya** girin. Ardından, **Sonraki'yi seçin.**

   Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   ::: moniker-end

   Visual Studio projenizi açar.

2. *Program.cs'yi* açın ve tüm kodu aşağıdaki kodla değiştirin:

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
    > Bu Visual Basic başlangıç nesnesinin ( Uygulama Başlangıç Nesnesini `Sub Main` **Özellikler)**  >  **olarak ayarlanmış olduğundan** emin  >  **olun.**

## <a name="step-1-collect-profiling-data"></a>1. Adım: Profil oluşturma verilerini toplama

1. İlk olarak, işlevinde bu kod satırı üzerinde uygulamanıza bir kesme noktası `Main` ayarlayın:

    `for (int i = 0; i < 200; i++)`

    veya, Visual Basic:

    `For i As Integer = 0 To 199`

    Kod satırın sol tarafından sol tarafta yer alan oluklulara tıklayarak bir kesme noktası ayarlayın.

2. Ardından, işlevin sonundaki kapanış ayracı üzerinde ikinci bir kesme noktası `Main` ayarlayın:

     ![Profil oluşturma için kesme noktaları ayarlama](../profiling/media/quickstart-cpu-usage-breakpoints.png "Profil oluşturma için kesme noktaları ayarlama")

    İki kesme noktası ayarerek veri toplamayı analiz etmek istediğiniz kod bölümleriyle sınırabilirsiniz.

3. Kapalı **Tanılama Araçları** pencere zaten görünür durumdadır. Pencereyi yeniden getirmek için Windows Show'da Hata  >  **Ayıkla'ya**  >  **Tanılama Araçları.**

4. Hata **AyıklamaYı**  >  **Başlat 'a (veya** araç çubuğunda **Başlat'a** veya **F5'e) tıklayın.**

     Uygulamanın yüklenmesi tamam olduğunda Tanılama **Araçları'nın** Özet görünümü görüntülenir.

5. Hata ayıklayıcı duraklatılmışken, CPU Profilini Kayded'i seçerek CPU Kullanımı verileri koleksiyonunu **etkinleştirin** ve **ardından CPU** Kullanımı sekmesini açın.

     ![Tanılama Araçları CPU Profili Oluşturmayı Etkinleştirme](../profiling/media/quickstart-cpu-usage-summary.png "Tanılama Araçları CPU Profili Oluşturmayı Etkinleştirme")

     Veri toplama etkinleştirildiğinde kayıt düğmesi kırmızı bir daire görüntüler.

     CPU Profilini **Kayded'i** Visual Studio, işlevlerinizi kaydetmeye ve ne kadar süreyle yürütüleceklerini kaydetmeye başlar ve ayrıca örnekleme oturumunun belirli segmentlerine odaklanmak için kullanabileceğiniz bir zaman çizelgesi grafiği sağlar. Toplanan bu verileri yalnızca uygulama bir kesme noktası durdurulduğu zaman görüntüebilirsiniz.

6. Uygulamayı ikinci kesme noktanıza çalıştırmak için **F5** tuşuna basın.

     Şimdi, özel olarak iki kesme noktası arasında çalışan kod bölgesi için uygulamanıza yönelik performans verilerine sahipsiniz.

     Profilleyici iş parçacığı verilerini hazırlamaya başlar. Bitimini bekleyin.

     CPU Kullanımı aracı raporu CPU Kullanımı **sekmesinde** görüntüler.

     Bu noktada, verileri analiz etmek için başlayabilirsiniz.

## <a name="step-2-analyze-cpu-usage-data"></a>2. Adım: CPU kullanım verilerini analiz etme

CPU Kullanımı altındaki işlev listesini inceler, en çok işi yapan işlevleri belirleyip her birini daha yakından inceler ve verilerinizi analiz ederek verilerinizi analize başlamanızı öneririz.

1. İşlev listesinde, en çok işi yapan işlevleri inceler.

     ![Tanılama Araçları CPU Kullanımı Sekmesi](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > İşlevler, en çok işi yapanlarla (çağrı sırasına göre değil) sırayla listelenir. Bu, en uzun süre çalışan işlevleri hızlıca tanımlamanıza yardımcı olur.

2. İşlev listesinde işleve çift `ServerClass::GetNumber` tıklayın.

    İşleve çift tıklarken, **sol bölmede Arayan/Çağrılı** görünümü açılır.

    ![Tanılama Araçları Çağıran Çağrılı Görünümü](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    Bu görünümde, seçilen işlev başlığında ve Geçerli İşlev **kutusunda** ( `GetNumber` , bu örnekte) görünür. Geçerli işlevi çağıran işlev sol tarafta İşlev Çağırma'nın altında, geçerli işlev tarafından çağrılan tüm işlevler ise sağ tarafta **çağrılır** İşlevler kutusunda gösterilir. (Geçerli işlevi değiştirmek için iki kutudan birini de seçin.)

    Bu görünümde, işlevin tamamlanması için gereken toplam süre (ms) ve genel uygulama çalışma süresi yüzdesi yer a gösterir.

    **İşlev Gövdesi** ayrıca, çağrılan ve çağrılan işlevlerde harcanan süre hariç olmak üzere işlev gövdesinde harcanan toplam süre miktarını (ve zaman yüzdesini) gösterir. (Bu çizimde, 2863 ms'den 2863 ms'nin 2856'sı işlev gövdesinde harcandı ve kalan süre (<20 ms) bu işlev tarafından çağrılan dış kodda harcandı). Gerçek değerler ortamınıza bağlı olarak farklı olur.

    > [!TIP]
    > İşlev **Gövdesi'nde yüksek** değerler, işlevin içinde bir performans sorunu olduğunu gösteriyor olabilir.

## <a name="next-steps"></a>Sonraki adımlar

- [Performans sorunlarını belirlemek](../profiling/memory-usage.md)için bellek kullanımını analiz edin.
- [CPU kullanım aracı](../profiling/cpu-usage.md) hakkında daha ayrıntılı bilgi için CPU kullanımını analiz edin.
- Hata ayıklayıcı ekli olmadan veya çalışan bir uygulamayı hedefleerek CPU kullanımını analiz edin. Daha fazla bilgi için hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma'da profil oluşturma verilerini [toplama'ya bakın.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) [](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
