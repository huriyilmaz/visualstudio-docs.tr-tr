---
title: Çok iş parçacıklı uygulamalarda hata ayıklamayı öğrenin
description: Visual Studio içindeki paralel yığınları ve paralel Gözcü pencerelerini kullanarak hata ayıklayın
ms.custom: ''
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3bc0af209930e385d315bfb95ae6b960439f6a05
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635405"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Çoklu iş parçacıklı uygulamalarda hata ayıklamaya başlama (C#, Visual Basic, C++)

Visual Studio, çok iş parçacıklı uygulamalarda hata ayıklamanıza yardımcı olacak çeşitli araçlar ve kullanıcı arabirimi öğeleri sağlar. Bu öğreticide, iş parçacığı işaretçilerinin, **Paralel Yığınlar** penceresinin, **paralel izleme** penceresinin, koşullu kesme noktalarının ve filtre kesme noktalarının nasıl kullanılacağı gösterilmektedir. bu öğreticiyi tamamlamak, çok iş parçacıklı uygulamalarda hata ayıklamaya yönelik Visual Studio özellikler hakkında bilgi sağlayacaktır.

Bu iki konu, diğer çok iş parçacıklı hata ayıklama araçlarını kullanmayla ilgili ek bilgiler sağlar:

- **Hata ayıklama konumu** araç çubuğunu ve **iş parçacıkları** penceresini kullanmak Için bkz. [izlenecek yol: çok iş parçacıklı uygulamada hata ayıklama](../debugger/how-to-use-the-threads-window.md).

- <xref:System.Threading.Tasks.Task>(Yönetilen kod) ve eşzamanlılık çalışma zamanı (C++) kullanan bir örnek için bkz. [izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md). Çok iş parçacıklı uygulama türleri için uygulanan genel hata ayıklama ipuçları için, bu konu başlığını ve bunu okuyun.

Öncelikle çok iş parçacıklı bir uygulama projesine ihtiyacınız vardır. Aşağıda bir örnek verilmiştir.

## <a name="create-a-multithreaded-app-project"></a>Çok iş parçacıklı uygulama projesi oluşturma

1. Visual Studio açın ve yeni bir proje oluşturun.

   ::: moniker range=">=vs-2019"

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

   Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#**, **C++** veya **Visual Basic** seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra .NET Core veya C++ **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   > [!NOTE]
   > doğru şablonu görmüyorsanız **araçlar**  >  **ve özellikler al..**. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **.NET Core platformlar arası geliştirme** veya C++ iş yükü **ile masaüstü geliştirme** seçeneklerini belirleyin ve ardından **Değiştir**' i seçin.

   **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *MyThreadWalkthroughApp* yazın veya girin. Sonra, **İleri** veya **Oluştur**' u seçin, hangisi kullanılabilir seçeneği vardır.

   Bir .NET Core projesi için, önerilen hedef Framework veya .NET 6 ' ı seçin ve ardından **Oluştur**' u seçin.

   ::: moniker-end
   ::: moniker range="vs-2017"
   üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **Yeni proje** iletişim kutusunun sol bölmesinde aşağıdakileri seçin:

   - c# uygulaması için, **Visual C#** altında, **masaüstü Windows**' yi seçin ve ardından ortadaki bölmede **konsol uygulaması ' nı (.NET Framework)** seçin.
   - Visual Basic bir uygulama için, **Visual Basic** altında **masaüstü Windows**' yı seçin ve ardından orta bölmedeki **konsol uygulaması (.NET Framework)** seçeneğini belirleyin.
   - C++ uygulaması için, **Visual C++** altında masaüstü ' ne **Windows** ve ardından **Windows konsol uygulaması**' nı seçin.

   için **konsol uygulaması (.NET Framework)** görmüyorsanız, C++, **konsol uygulama** projesi şablonu için, Visual Studio Yükleyicisi açan **araçlar**  >  **ve özellikler al...**' a gidin. C++ iş yüküyle **.net masaüstü geliştirme** veya **masaüstü geliştirme** seçeneklerini belirleyin ve ardından **Değiştir**' i seçin.

   Ardından, *MyThreadWalkthroughApp* gibi bir ad yazın ve **Tamam**' a tıklayın.

   **Tamam**’ı seçin.
   ::: moniker-end

   Yeni bir konsol projesi görüntülenir. Proje oluşturulduktan sonra bir kaynak dosya görüntülenir. Seçtiğiniz dile bağlı olarak, kaynak dosya *program. cs*, *MyThreadWalkthroughApp. cpp* veya *Module1. vb* olarak adlandırılır.

1. Kaynak dosyada görüntülenen kodu silin ve aşağıdaki uygun örnek kod listesi ile değiştirin.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended. " + data);
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended. " + data)
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. **Dosya** menüsünde **Tümünü Kaydet**’i seçin.

1. (yalnızca Visual Basic) Çözüm Gezgini (sağ bölme) menüsünde, proje düğümüne sağ tıklayın, **Özellikler**' i seçin. **Uygulama** sekmesinde, **Başlangıç nesnesini** **basit** olarak değiştirin.

## <a name="debug-the-multithreaded-app"></a>Çok iş parçacıklı uygulamada hata ayıklama

1. Kaynak kodu düzenleyicisinde, aşağıdaki kod parçacıklarında birini arayın:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. `Thread.Sleep` `std::this_thread::sleep_for` Yeni bir kesme noktası eklemek için veya ifadesinin sol cilt payını sola tıklayın.

    Cilt payı içinde kırmızı bir daire, bu konumda bir kesme noktasının ayarlandığını gösterir.

2. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** (**F5**) öğesini seçin.

    Visual Studio çözümü oluşturduğunda, uygulama hata ayıklayıcı eklenmiş olarak çalışmaya başlar ve sonra da uygulama kesme noktasında durmaktadır.

3. Kaynak kodu düzenleyicisinde, kesme noktasını içeren çizgiyi bulun.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>İş parçacığı işaretçisini bulma  

1. Hata ayıklama araç çubuğunda, ![kaynak bölümünde iş](../debugger/media/dbg-multithreaded-show-threads.png "Threadişaretleyici")parçacıklarını **göster** düğmesini seçin.

2. Hata ayıklayıcı bir kod satırına ilerlemek için **F11** tuşuna basın.

3. Pencerenin sol tarafındaki cilt paya bakın. Bu satırda iki bükümlü iş parçacığına benzeyen bir *iş parçacığı işaretleyici* simgesi  ![iş parçacığı işaretçisi](../debugger/media/dbg-thread-marker.png "Threadişaretleyici") görürsünüz. İş parçacığı işaretçisi, bu konumda bir iş parçacığının durdurulduğunu gösterir.

    Bir iş parçacığı işaretleyicisi, bir kesme noktası tarafından kısmen eklenebilir.

4. İşaretçiyi iş parçacığı işaretçisinin üzerine getirin. Her durdurulan iş parçacığı için ad ve iş parçacığı KIMLIĞI numarasını bildiren bir veri Ipucu görünür. Bu durumda, ad muhtemelen `<noname>` .

5. Kısayol menüsünde kullanılabilir seçenekleri görmek için iş parçacığı işaretçisini seçin.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>İş parçacığı konumlarını görüntüleme

**Paralel Yığınlar** penceresinde, bir iş parçacığı görünümü ile (görev tabanlı programlama Için) görevler görünümü arasında geçiş yapabilir ve her iş parçacığı için çağrı yığını bilgilerini görüntüleyebilirsiniz. Bu uygulamada, Iş parçacıkları görünümünü kullanabiliriz.

1. **hata ayıkla**   >  **Windows**  >  **paralel yığınlar**' i seçerek paralel yığınlar penceresini açın. Aşağıdakine benzer bir şey görmeniz gerekir. Tam bilgiler, her iş parçacığının, donanımınızın ve programlama dilinizin geçerli konumuna göre farklılık gösterir.

    ![Paralel Yığınlar penceresi](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    Bu örnekte, soldan sağa, bu bilgileri yönetilen kod için görürsünüz:

    - Ana iş parçacığı (sol taraf) `Thread.Start` , durdurma noktasının iş parçacığı işaretleyici simgesi ![Iş parçacığı işaretçisi](../debugger/media/dbg-thread-marker.png "Threadişaretleyici")tarafından belirtildiği üzerinde durdurulur.
    - İki iş parçacığı, `ServerClass.InstanceMethod` biri geçerli iş parçacığı (sarı ok) olan, diğeri de durdurulduğunda bir tane girdi `Thread.Sleep` .
    - Yeni bir iş parçacığı de başlatılıyor, ancak tarihinde durdurulur `ThreadHelper.ThreadStart` .

2. Kısayol menüsünde kullanılabilir seçenekleri görmek için **Paralel Yığınlar** penceresinde girişler ' e sağ tıklayın.

    Bu sağ tıklama menülerinden çeşitli eylemler gerçekleştirebilirsiniz, ancak bu öğreticide **paralel izleme** penceresinde (sonraki bölümlerde) bu ayrıntıların daha fazla görünmesini göstereceğiz.

    > [!NOTE]
    > Her iş parçacığı hakkında bilgi içeren bir liste görünümünü görmek için, bunun yerine **Iş parçacıkları** penceresini kullanın. Bkz. [Izlenecek yol: çok Iş parçacıklı uygulamada hata ayıklama](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Bir değişkende izleme ayarlama

1. **hata ayıkla** Windows paralel izleme paralel izleme 1 ' i seçerek **paralel izleme** penceresini açın  >    >    >  .

2. `<Add Watch>`Metni (veya 4 sütununda boş üst bilgi hücresini) gördüğünüz hücreyi seçin ve girin `data` .

    Her bir iş parçacığının veri değişkeni için değerler pencerede görüntülenir.

3. `<Add Watch>`Metni (veya 5. sütundaki boş başlık hücresini) gördüğünüz hücreyi seçin ve girin `count` .

    `count`Her bir iş parçacığının değişkeninin değerleri pencerede görüntülenir. Bu çok bilgiyi henüz görmüyorsanız, hata ayıklayıcıdaki iş parçacıklarının yürütülmesini ilerletmek için **F11** tuşuna birkaç kez basmayı deneyin.

    ![Paralel Izleme penceresi](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Mevcut seçenekleri görmek için penceredeki satırlardan birine sağ tıklayın.

### <a name="flag-and-unflag-threads"></a>İş parçacıklarını bayrakla işaretleme ve işareti geri alma
İş parçacıklarını, önemli iş parçacıklarını izlemek ve diğer iş parçacıklarını yoksaymak için işaretleyebilirsiniz.

1. **Paralel izleme** penceresinde, **SHIFT** tuşunu basılı tutarak birden çok satır seçin.

2. Sağ tıklayıp **bayrak**' i seçin.

    Seçilen tüm iş parçacıkları işaretlenir. Şimdi yalnızca bayraklı iş parçacıklarını göstermek için filtre uygulayabilirsiniz.

3. **Paralel izleme** penceresinde **yalnızca bayraklı iş parçacıklarını göster** düğmesini ![işaretli iş parçacıklarını göster](../debugger/media/dbg-threads-show-flagged.png "Threadişaretleyici")düğmesini seçin.

    Listede yalnızca bayraklı iş parçacıkları görüntülenir.

    > [!TIP]
    > Bazı iş parçacıklarını işaretledikten sonra, kod düzenleyicisinde bir kod satırına sağ tıklayıp **bayraklı Iş parçacıklarını Imlece Çalıştır**' ı seçebilirsiniz. İşaretlenen tüm iş parçacıklarının ulaşabileceği kodu seçtiğinizden emin olun. Visual Studio, seçili kod satırında iş parçacıklarını duraklatarak [iş parçacıklarını dondurarak ve thanerek](#bkmk_freeze)yürütme sırasını denetlemeyi kolaylaştırır.

4. **Tüm Iş parçacıkları modunu göstermek** için geri dönmek üzere **yalnızca bayraklı iş parçacıklarını göster** düğmesini yeniden seçin.

5. İş parçacıklarını işaretlemek için, **paralel izleme** penceresinde bir veya daha fazla bayraklı iş parçacığına sağ tıklayın ve **bayrağı kaldır**' ı seçin.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> İş parçacığı yürütmeyi dondurma ve çözme

> [!TIP]
> İş parçacıklarının iş gerçekleştirdiği sırayı denetlemek için iş parçacıklarını dondurabilir ve çözme (askıya al ve devam ettir). Bu, Kilitlenmeler ve yarış koşulları gibi eşzamanlılık sorunlarını çözmenize yardımcı olabilir.

1. **Paralel izleme** penceresinde, tüm satırlar seçiliyken, sağ tıklayıp **Dondur**' ı seçin.

    İkinci sütunda, her satır için bir duraklatma simgesi görüntülenir. Duraklat simgesi iş parçacığının dondurulmuş olduğunu gösterir.

2. Yalnızca bir satır seçerek diğer tüm satırların seçimini kaldırın.

3. Bir satıra sağ tıklayın ve **çözme**' yi seçin.

    Bu satırda, iş parçacığının artık dondurulmuş olmadığını belirten duraklatma simgesi kaybolur.

4. Kod düzenleyicisine geçin ve **F11** tuşuna basın. Yalnızca dondurulmamış iş parçacığı çalışır.

    Uygulama, bazı yeni iş parçacıkları da oluşturabilir. Herhangi bir yeni iş parçacığı işaretlenir ve dondurulmuş değildir.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> Koşullu kesme noktalarıyla tek bir iş parçacığını takip edin

Hata ayıklayıcıda tek bir iş parçacığının yürütülmesini izlemek faydalı olabilir. Bunu yapmanın bir yolu, ilgilendiğiniz iş parçacıklarını donduruyor. Bazı senaryolarda, belirli bir hatayı yeniden oluşturmak için diğer iş parçacıklarını dondurmadan tek bir iş parçacığını izlemeniz gerekebilir. Diğer iş parçacıklarını dondurmadan bir iş parçacığını izlemek için, ilgilendiğiniz iş parçacığı hariç koda aşmaktan kaçınmanız gerekir. Bunu, [koşullu bir kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)ayarlayarak yapabilirsiniz.

İş parçacığı adı veya iş parçacığı KIMLIĞI gibi farklı koşullarda kesme noktaları ayarlayabilirsiniz. Her iş parçacığı için benzersiz olduğunu bildiğiniz veriler üzerindeki koşulu ayarlamak yararlı olabilir. Bu, belirli bir iş parçacığından daha fazla belirli bir veri değeriyle daha fazla ilgilendiğiniz ortak bir hata ayıklama senaryosudur.

1. Daha önce oluşturduğunuz kesme noktasına sağ tıklayın ve **koşullar**' ı seçin.

2. **kesme noktası Ayarlar** penceresinde, `data == 5` koşullu ifade için girin.

    ![Koşullu kesme noktası](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Belirli bir iş parçacığında daha fazla ilgileniyorsanız, koşul için bir iş parçacığı adı veya iş parçacığı KIMLIĞI kullanın. bunu **kesme noktası Ayarlar** penceresinde yapmak için **koşullu ifade** yerine **filtre** ' yi seçin ve filtre ipuçlarını izleyin. Hata ayıklayıcıyı yeniden başlattığınızda iş parçacıkları kimlikleri değiştikçe iş parçacıklarınızı uygulama kodunuzda adlandırmak isteyebilirsiniz.

3. **kesme noktası Ayarlar** penceresini kapatın.

4. Hata ayıklama oturumunuzu yeniden başlatmak için yeniden ![Başlat uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") yeniden Başlat düğmesini seçin.

    Veri değişkeninin değeri 5 olan iş parçacığında kod ile karşılaşırsınız. **Paralel izleme** penceresinde, geçerli hata ayıklayıcı bağlamını gösteren Sarı oka bakın.

5. Şimdi kod (**F10**) üzerinde ilerleyebilmeniz ve kod Içine (**F11**) ve tek bir iş parçacığının yürütülmesini izleyebilirsiniz.

    Kesme noktası koşulu iş parçacığına benzersiz olduğu sürece ve hata ayıklayıcı diğer iş parçacıklarında başka bir kesme noktasına isabet etmiyor (bunları devre dışı bırakmanız gerekebilir), diğer iş parçacıklarıyla geçiş yapmadan kod üzerinde ilerlebilmenizi ve kodun içine adımlamayı sağlayabilirsiniz.

    > [!NOTE]
    > Hata ayıklayıcıyı ilerletin, tüm iş parçacıkları çalışır. Ancak, diğer iş parçacıklarından biri bir kesme noktasına isabet etmediği takdirde hata ayıklayıcı diğer iş parçacıklarında koda bölünmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl yapılır: Hata ayıklarken başka bir iş parçacığına geçme](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Nasıl yapılır: paralel yığın penceresini kullanma](../debugger/using-the-parallel-stacks-window.md)
- [Nasıl yapılır: Paralel İzleme penceresini kullanma](../debugger/how-to-use-the-parallel-watch-window.md)