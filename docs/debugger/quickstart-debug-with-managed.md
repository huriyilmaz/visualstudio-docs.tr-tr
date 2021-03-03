---
title: Yönetilen kodda hata ayıklama | Microsoft Docs
description: Visual Studio hata ayıklayıcısını kullanarak C# veya Visual Basic hatalarını ayıklama
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f790d30dc97d5549737c3c1cd003086477ce984f
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683010"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Hızlı başlangıç: Visual Studio hata ayıklayıcısını kullanarak C# veya Visual Basic hatalarını ayıklama

Visual Studio hata ayıklayıcı, uygulamalarınızda hata ayıklamanıza yardımcı olmak için birçok güçlü özellik sunar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

    **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil listesinden **C#** öğesini seçin ve ardından platform listesinden **Windows** ' u seçin.

    Dil ve platform filtrelerini uyguladıktan sonra .NET Core **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

    .NET Core için **konsol uygulaması** proje şablonunu görmüyorsanız, **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açan araçlar ' a gidin. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında **.NET Core**' u seçin ve ardından Ortadaki bölmede **konsol uygulaması (.NET Core)** seçeneğini belirleyin. Ardından, **Mydbgapp** gibi bir ad yazın ve **Tamam**' a tıklayın.

    **Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açan araçlar ' a gidin. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.
    ::: moniker-end

    Visual Studio projeyi oluşturur.

1. *Program.cs* veya *Module1. vb* dosyasında aşağıdaki kodu değiştirin

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
    > Visual Basic, başlangıç nesnesinin `Sub Main` (**Özellikler > uygulama > başlangıç nesnesi**) olarak ayarlandığından emin olun.

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

*Kesme noktası* , Visual Studio 'nun çalışan kodunuzu askıya alması gerektiğini belirten bir işaretleyicidir, böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz. Hata ayıklamada en temel özelliktir.

1. Kesme noktasını ayarlamak için, işlev çağrısının solundaki cilt payın içine tıklayın `doWork` (veya kod satırını seçip **F9** tuşuna basın).

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Kesme noktası ayarlama")

2. Şimdi **F5** tuşuna basın (veya hata **ayıklamayı başlatmak > hata ayıkla** seçeneğini belirleyin).

    ![Kesme noktasına isabet edin](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Kesme noktasına isabet edin")

    Hata ayıklayıcı, kesme noktasını ayarladığınız yerde duraklatılır. Hata ayıklayıcının ve uygulama yürütmenin duraklatıldığı ifade sarı oklu belirtilir. İşlev çağrısının bulunduğu satır `doWork` henüz yürütülmedi.

    > [!TIP]
    > Bir döngüde veya özyinelemedeki bir kesme noktası varsa veya sık sık adımtığınız çok sayıda kesme noktasına sahipseniz, kodunuzun yalnızca belirli koşullar karşılandığında askıya alındığından emin olmak için [koşullu bir kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) kullanın. Koşullu kesme noktası zamandan tasarruf edebilir ve yeniden oluşturulması zor olan sorunların hatalarını ayıklamanızı da kolaylaştırabilir.

## <a name="navigate-code"></a>Koda git

Hata ayıklayıcının devam etmesini bildirmek için farklı komutlar vardır. Visual Studio 2017 ' den başlayarak kullanılabilecek yararlı bir kod Gezinti komutu gösteririz.

Kesme noktasında duraklalarken, tıklama `c1.AddLast(20)` düğmesine tıklayarak ve ardından tıklama düğmesine tıklayarak  deyimin üzerine gelin ve ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick") sonra da **Çalıştır** düğmesine basın.

![Tıklama için Çalıştır](../debugger/media/dbg-qs-run-to-click-csharp.png "Tıklama için Çalıştır")

Uygulama, `doWork` düğmeye tıklamış olduğunuz kod satırında yürütme, çağırma ve duraklamaya devam eder.

Kod içinde ilerlemek için kullanılan yaygın klavye komutları **F10** ve **F11**. Daha ayrıntılı yönergeler için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-data-tip"></a>Bir veri ipucunda değişkenleri İnceleme

1. Geçerli kod satırında (Sarı yürütme işaretçisi tarafından işaretlenir), `c1` bir veri ipucu göstermek için farenizle nesnenin üzerine gelin.

    ![Veri ipucunu görüntüleme](../debugger/media/dbg-qs-data-tip-csharp.png "Veri ipucunu görüntüleme")

    Veri ipucu, değişkenin geçerli değerini gösterir `c1` ve özelliklerini incelemenizi sağlar. Hata ayıklarken, beklemediğinizi bir değer görürseniz, büyük olasılıkla kodun önceki veya çağırma satırlarında bir hata oluşur.

2. Nesnenin geçerli özellik değerlerini görmek için veri ipucunu genişletin `c1` .

3. Kodu yürüttüğünüzde değerini görmeye devam edebilmeniz için veri ipucunu sabitlemek istiyorsanız `c1` , küçük sabitle simgesine tıklayın. (Sabitlenmiş veri ipucunu uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasında kodunuzda test etmek istediğiniz bir değişikliği belirlerseniz, bunu da yapabilirsiniz.

1. İkinci örneğine tıklayın ve öğesini `c2.First.Value` olarak değiştirin `c2.First.Value` `c2.Last.Value` .

2. Hata ayıklayıcıyı ilerletmek ve düzenlenmiş kodu yürütmek için **F10** 'e (veya **hata ayıklama > adımla**) birkaç kez basın.

    ![Düzenle ve devam et](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Düzenle ve devam et")

    **F10** , hata ayıklayıcı bir ifadeyi tek seferde ilerletir, ancak bunlar içine adımlamak yerine işlevler üzerinde adımlar (yine de atladığınız kod).

Düzenle ve devam et ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm sağlamak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
