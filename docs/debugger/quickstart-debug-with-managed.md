---
title: Yönetilen kod hata ayıklama | Microsoft Docs
description: Visual Studio hata ayıklayıcısını kullanarak C# Visual Basic hata ayıklama
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 9387d4a7ef763357d79b9d185e79de9229735afb
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635977"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Hızlı Başlangıç: Visual Studio hata ayıklayıcısını kullanarak C# veya Visual Basic hata ayıklama

Hata Visual Studio hata ayıklayıcısı, uygulamalarınızı hata ayıklamanıza yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmenin hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

1. Yeni Visual Studio ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

    Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin.

    Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından **Oluştur'a seçin.**

    .NET Core için  Konsol Uygulaması proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin ve bu işlem  >  Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında **.NET Core'ı** seçin ve orta bölmede Konsol Uygulaması **(.NET Core) öğesini seçin.** Ardından **MyDbgApp** gibi bir ad yazın ve Tamam'a **tıklayın.**

    Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
    ::: moniker-end

    Visual Studio projeyi oluşturur.

1. *Program.cs veya* *Module1.vb içinde* aşağıdaki kodu değiştirin

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

    yerine şu kodu yazın:

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
    > Bu Visual Basic, başlangıç nesnesinin ( Uygulama Ve Başlangıç Nesnesi) `Sub Main` > özellikler > emin **olun.**

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Kesme *noktası,* değişkenlerin değerlerine Visual Studio veya bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz. Hata ayıklamanın en temel özelliğidir.

1. Kesme noktası ayarlamak için işlev çağrısının sol tarafından sol tarafta yer alan oluklara tıklayın (veya kod satırına tıklayın ve `doWork` **F9 tuşuna basın).**

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Kesme noktası ayarlama")

2. Şimdi **F5 tuşuna basın** (veya Hata **Ayıkla'> Hata Ayıklamayı Başlat'ı seçin).**

    ![Kesme noktası isabeti](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Kesme noktası isabeti")

    Hata ayıklayıcısı kesme noktası ayarlayıcıyı duraklatıyor. Hata ayıklayıcısı ve uygulama yürütmenin duraklatılmış olduğu deyim sarı okla işaret ediyor. İşlev `doWork` çağrısına sahip satır henüz yürütülmedi.

    > [!TIP]
    > Döngüde veya yeniden çalışmada kesme noktanız varsa veya sık sık adım attığınız çok sayıda [](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) kesme noktanız varsa, kodunuzun YALNIZCA belirli koşullar karşılandı olduğunda askıya alındıktan emin olmak için koşullu kesme noktası kullanın. Koşullu kesme noktası zamandan tasarruf sağlar ve yeniden üretile zor olan sorunlarda hata ayıklamayı da kolaylaştırır.

## <a name="navigate-code"></a>Kodda gezinme

Hata ayıklayıcıya devam etme talimatı için farklı komutlar vardır. 2017'den itibaren kullanılabilen yararlı bir kod gezinti Visual Studio gösteriyoruz.

Kesme noktası duraklatılırken, yeşil renkli Çalıştır düğmesine tıklar gibi görünene kadar deyimin üzerine gelin ve ardından `c1.AddLast(20)` **Çalıştır'a tıklayarak düğmesine** basın.  ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

![Tıklamak için çalıştır](../debugger/media/dbg-qs-run-to-click-csharp.png "Tıklamak için çalıştır")

Uygulama, çağrısıyla `doWork` yürütmeye devam eder ve düğmesine tıklamış kod satırı üzerinde duraklatılır.

Kodda adım adım gezinmek için kullanılan yaygın klavye komutları **F10** ve **F11'tir.** Daha ayrıntılı yönergeler için bkz. [Hata ayıklayıcıya ilk bakış.](../debugger/debugger-feature-tour.md)

## <a name="inspect-variables-in-a-data-tip"></a>Veri ipucunda değişkenleri inceleme

1. Geçerli kod satırı (sarı yürütme işaretçisi ile işaretlenmiş) farenizin olduğu nesnenin üzerine gelerek `c1` bir veri ipucu gösterir.

    ![Veri ipucu görüntüleme](../debugger/media/dbg-qs-data-tip-csharp.png "Veri ipucu görüntüleme")

    Veri ipucu, değişkenin geçerli değerini `c1` gösterir ve özelliklerini incelemeye olanak sağlar. Hata ayıklama sırasında, beklemeyebilirsiniz bir değer görüyorsanız, büyük olasılıkla önceki veya çağıran kod satırlarında bir hata vardır.

2. Nesnenin geçerli özellik değerlerine bakmak için veri ipucu'nda `c1` genişletin.

3. Kodu yürütürken değerini görmeye devam etmek için veri ipucuna sabitlemek için küçük pin `c1` simgesine tıklayın. (Sabitlenmiş veri ipucunı uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasındayken kodunda test etmek istediğiniz bir değişikliği tespit ediyorsanız, bunu da kullanabilirsiniz.

1. İkinci örneğine tıklayın `c2.First.Value` ve olarak `c2.First.Value` `c2.Last.Value` değişir.

2. Hata ayıklayıcıyı ilerlemek ve **düzenlenen kodu yürütmek >** **F10** 'a (veya Hata Ayıkla veya Adımla) birkaç kez basın.

    ![Düzenle ve devam](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Düzenle ve devam")

    **F10,** hata ayıklayıcıyı tek tek bir deyime ilerletmektedir, ancak işlevlere adımlarını atlar (atlayıp atlayılan kod yine de yürütülür).

Düzenleme ve devam ile özellik sınırlamaları hakkında daha fazla bilgi için, bkz. [Düzenle ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklayıcıyı başlatmayı, kodu adım adım incelemeyi ve değişkenleri incelemeyi öğrendiniz. Daha fazla bilgi için bağlantılarla birlikte hata ayıklayıcı özelliklerine üst düzey bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
