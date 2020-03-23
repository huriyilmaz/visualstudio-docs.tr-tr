---
title: Hata ayıklama yönetilen kod | Microsoft Dokümanlar
description: Visual Studio hata ayıklayıcısını kullanarak Hata Ayıklama C# veya Visual Basic
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e5495bb1f531db00d43e04cce9f5f771c88cc1a7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679200"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Quickstart: Visual Studio hata ayıklayıcısını kullanarak C# veya Visual Basic ile hata ayıklama

Visual Studio hata ayıklama, uygulamalarınızı hata ayıklamanıza yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmek için hızlı bir yol sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

1. Visual Studio'u açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **konsol**yazın, **Şablonlar'ı**seçin, ardından **yeni Konsol Uygulaması Oluştur (.NET Core) projesini**seçin. Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında **,.NET Core'u**seçin ve sonra orta bölmede **Konsol Uygulaması'nı (.NET Core)** seçin. Ardından, **MyDbgApp** gibi bir ad yazın ve **Tamam'ı**tıklatın.
    ::: moniker-end

     **Konsol Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, Visual Studio Installer'ı açan **Araçlar** > **Araçları ve Özellikleri Al...**(Visual Studio Installer'ı açar) gidin. **.NET masaüstü geliştirme** ve **.NET Core** iş yükünü seçin, ardından **Değiştir'i**seçin.

    Visual Studio projeyi oluşturur.

1. *Program.cs* veya *Module1.vb*olarak, aşağıdaki kodu değiştirin

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    bu kod ile:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic'te, başlangıç nesnesinin `Sub Main` **(Özellikler > Uygulama > Başlangıç Nesnesi)** olarak ayarlandıklarına emin olun.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

*Kesme noktası,* Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösteren bir işaretçidir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz. Hata ayıklamanın en temel özelliğidir.

1. Kesme noktasını ayarlamak `doWork` için, işlev çağrısının solundaki olukta tıklayın (veya kod çizgisini seçin ve **F9**tuşuna basın).

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Kesme noktası ayarlama")

2. Şimdi **F5** tuşuna basın (veya **Hata Ayıklama > Hata Ayıklama'yı başlat'ı**seçin).

    ![Bir kesme noktasına çarptım](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Bir kesme noktasına çarptım")

    Hata ayıklama, kesme noktasını ayarladığınız yerde duraklar. Hata ayıklama ve uygulama yürütmenin duraklattığı deyim sarı okla gösterilir. İşlev çağrısının `doWork` olduğu satır henüz yürütülmedi.

    > [!TIP]
    > Bir döngü veya özyinelemede bir kesme noktanız varsa veya sık sık adım attığınız çok sayıda kesme noktanız varsa, yalnızca belirli koşullar karşılandığında kodunuzun askıya aldığından emin olmak için [koşullu](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) bir kesme noktası kullanın. Koşullu bir kesme noktası zamandan tasarruf sağlayabilir ve yeniden oluşturulması zor olan sorunları ayıklamayı da kolaylaştırabilir.

## <a name="navigate-code"></a>Kodda gezinme

Hata ayıkıcıya devam etmesini emretmek için farklı komutlar vardır. Visual Studio 2017'den itibaren kullanılabilen kullanışlı bir kod navigasyon komutu gösteriyoruz.

Kesme noktasında duraklatılırken, yeşil `c1.AddLast(20)` **Çalıştır'dan Tıklatdüğmesine tıklayın** düğmesine kadar deyimin üzerine basın ve ardından ![Run to Click](../debugger/media/dbg-tour-run-to-click.png "RunToClick") **Tıklatmak için Çalıştır düğmesine basın.**

![Tıklatmak için çalıştırın](../debugger/media/dbg-qs-run-to-click-csharp.png "Tıklatmak için çalıştırın")

Uygulama yürütmeye devam `doWork`eder, arama ve düğmeyi tıklattığınızda kod satırında duraklar.

Koda basmak için kullanılan yaygın klavye komutları **F10** ve **F11'i**içerir. Daha ayrıntılı talimatlar için [hata ayıklama bölümüne ilk bakışta](../debugger/debugger-feature-tour.md)bakın.

## <a name="inspect-variables-in-a-datatip"></a>Veri ucundaki değişkenleri inceleyin

1. Geçerli kod satırında (sarı yürütme işaretçisi ile `c1` işaretlenmiş), bir veri ipucu göstermek için fareniz ile nesnenin üzerine gelin.

    ![Veri ipucunu görüntüleme](../debugger/media/dbg-qs-data-tip-csharp.png "Veri ipucunu görüntüleme")

    Veri ipucu, `c1` değişkenin geçerli değerini gösterir ve değişkenin özelliklerini incelemenize olanak tanır. Hata ayıklama yaparken, beklemediğiniz bir değer görürseniz, büyük olasılıkla önceki veya kod satırlarını çağıran bir hatanız vardır.

2. Nesnenin geçerli özellik değerlerine bakmak için `c1` veri ucunu genişletin.

3. Kod `c1` yürütürken değerini görmeye devam etmek için veri ucunu sabitlemek istiyorsanız, küçük pin simgesini tıklatın. (Sabitlenmiş veri ucunu uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasındayken kodunuzda sınamak istediğiniz bir değişikliği tanımlarsanız, bunu da yapabilirsiniz.

1. İkinci örneğini `c2.First.Value` tıklatın `c2.First.Value` ve `c2.Last.Value`'' olarak değiştirin

2. Hata ayıklayıcıyı ilerletmek ve düzenlenen kodu yürütmek için **F10** (veya **Hata Ayıklama > Adım At)** tuşuna birkaç kez basın.

    ![Edin ve devam edin](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edin ve devam edin")

    **F10** hata ayıklayıcıyı bir defada bir ifadeyi ilerletir, ancak bunlara adım atmak yerine işlevlerin üzerine adım atar (atladığınız kod hala yürütülür).

Edit-and-continue ve özellik sınırlamaları hakkında daha fazla bilgi için [bkz.](../debugger/edit-and-continue.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatmayı, koda nasıl basabileceğinizi ve değişkenleri nasıl inceleyincenizi öğrendiniz. Hata ayıklama özelliklerine daha fazla bilgi bağlantılarıyla birlikte üst düzey bir görünüm elde etmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
