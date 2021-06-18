---
title: 'Öğretici: C# kodunda hata ayıklama'
description: Visual Studio hata ayıklayıcısının özelliklerini ve hata ayıklayıcıyı başlatmayı, kodda adım adım incelemeyi ve bir C# uygulamasındaki verileri incelemeyi öğrenin.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 04/23/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cbc35eaabec2dae8bd8b97ba22f55a50fc436c3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308460"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C# kodunda hata ayıklamayı Visual Studio

Bu makalede, Visual Studio hata ayıklayıcısının özellikleri adım adım izlenecek yol açıklanmıştır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü almak için [bkz. İlk olarak hata ayıklayıcıya bakın.](../../debugger/debugger-feature-tour.md) Uygulamanıza *hata ayıklarken* genellikle hata ayıklayıcı eklenmiş olarak çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişip değişmeyişini görmek için değişkenler üzerinde izlemeler ayarlayın, kodunuzun yürütme yolunu inceleyebilirsiniz, bir kod dalını çalıştırıp çalıştırmama gibi. İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi okumadan önce yeni başlayanlar için [hata](../../debugger/debugging-absolute-beginners.md) ayıklama makalesine bakabilirsiniz.

Tanıtım uygulaması C# olsa da özelliklerin çoğu C++, Visual Basic, F#, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F# Düzenle ve devamını desteklemez). F# ve JavaScript, Otomatikler **penceresini desteklemez).** Ekran görüntüleri C# içindedir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlat ve kesme noktalarına isabet.
> * Hata ayıklayıcıda kodda adım adım ilerlerken gereken komutları öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı pencerelerde değişkenleri inceleme
> * Çağrı yığınını inceleme

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

2019 Visual Studio **ve .NET Core** platformlar arası geliştirme iş yükünüz olması gerekir.

::: moniker-end
::: moniker range="vs-2017"

2017'Visual Studio ve .NET Core platformlar arası geliştirme **iş yükünüz yüklü** olması gerekir.

::: moniker-end

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir .NET Core konsol uygulaması projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

3. Sol **bölmede Yeni** Proje iletişim kutusunda **C#** öğesini genişletin ve **ardından .NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *get-started-debugging adını girin.*

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız Yeni Proje iletişim kutusunun sol bölmesinde **Visual Studio Yükleyicisi** Aç **bağlantısını** seçin.

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'u** seçin. 

   Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması için C# şablonunu seçin](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** Proje adı kutusuna *GetStartedDebugging* **yazın veya** girin. Ardından, **Sonraki'yi seçin.**

1. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

1. *Program.cs içinde,* varsayılan kodun hepsini aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    class ArrayExample
    {
        static void Main()
        {
            char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
            string name = "";
            int[] a = new int[10];
            for (int i = 0; i < letters.Length; i++)
            {
                name += letters[i];
                a[i] = i + 1;
                SendMessage(name, a[i]);
            }
            Console.ReadKey();
        }
        static void SendMessage(string name, int msg)
        {
            Console.WriteLine("Hello, " + name + "! Count to " + msg);
        }
    }
    ```

## <a name="start-the-debugger"></a>Hata ayıklayıcıyı başlatma!

1. **F5** (**Hata Ayıklama > Başlat**) veya Hata Ayıklama ![](../../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") Araç Çubuğunda Hata Ayıklamayı Başlat düğmesine basın. 

     **F5,** uygulamayı uygulama sürecine eklenmiş hata ayıklayıcısıyla başlatır, ancak şu anda kodu incelemek için özel bir işlem yapmadık. Bu nedenle uygulama yüklenir ve konsol çıktısını görüntülenir.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     Bu öğreticide, hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından bakacak ve hata ayıklayıcı özelliklerine göz atalım.

2. Hata ayıklamayı kırmızı durdur Hata Ayıklamayı Durdur düğmesine basarak hata ![ayıklayıcıyı durdurun](../../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") (**Shift**  +  **F5**).

3. Konsol penceresinde, konsol penceresini kapatmak için bir tuşa basın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

1. işlevinin `for` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktası ![ayarda kırmızı](../../debugger/media/dbg-breakpoint.png "Ilı") bir daire Kesme Noktası görüntülenir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerindendir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

2. **F5 tuşuna** **basın** veya Hata Ayıklamayı Başlat düğmesine ![basın;](../../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat")uygulama başlatılır ve hata ayıklayıcı kesme noktası ayarlayıcının ayar bulunduğu kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../csharp/media/get-started-set-breakpoint.gif)

    Sarı ok, aynı noktada uygulama yürütmeyi de askıya alan (bu deyim henüz yürütülmedi) hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur. Aksi **takdirde, F5** uygulamayı bir sonraki kesme noktasıyla çalıştırmaya devam eder.

    Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Ayar yalnızca koşullu kesme noktaları gibi farklı kesme noktası türleri hakkında bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Veri ipuçlarını kullanarak kodda gezinme ve verileri inceleme

Genellikle burada klavye kısayollarını kullanırız çünkü bu, uygulamanızı hata ayıklayıcısında yürütmeyi hızlı bir şekilde yürütmenin iyi bir yolu olduğundan (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. deyiminde duraklatılmışken değişkeninin üzerine gelin ve bunun varsayılan değeri olan dizideki ilk `name += letters[i]` `letters` öğenin değerini `char[10]` görüyorsunuz.

     Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerindendir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

     ![Visual Studio 'name+= letters[I]' deyiminin vurgulanmış olduğu ve letters dizisinde yer alan öğeleri gösteren bir açılan liste ile Birlikte Hata Ayıklayıcısı'nın ekran görüntüsü.](../csharp/media/get-started-view-data-tip.png)

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Yöntem **çağrısına ilerlemek için F10** **tuşuna basın**(veya > AdımLa) hata ayıkla'ya basın ve `SendMessage` ardından **F10'a** bir kez daha basın.

     F10, uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı bir sonraki deyime ilerletmektedir (kod yürütülmektedir). Yöntem çağrısında F10'a basarak, uygulama kodunu atlamıştık (şu anda `SendMessage` `SendMessage` ilgilenmediğimiz bir şey olabilir).

1. Döngüde birkaç kez tekrarlama, kesme noktası üzerinde yeniden duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F10'a** (veya Adım Adım Hata Ayıklama) birkaç kez  >   `for` `name` basın.

     ![Hata Ayıklayıcısı'Visual Studio F10'a "AdımLa" tuşuna basmanın ve hata ayıklama sırasında döngüde tekrarlamanın etkisini gösteren animasyonlu ekran görüntüsü.](../csharp/media/get-started-data-tip.gif)

     Değişkenin değeri döngüde her yineleme ile birlikte değişir ve ardından `for` , ardından , ve gibi değerleri `f` `fr` `fre` gösterir. Bu senaryoda hata ayıklayıcısını döngüde daha hızlı ilerlemek için  **F5** tuşuna basabilirsiniz (veya Devam Et'i seçerek) bir sonraki deyim yerine kesme noktası  >  üzerinden ilerleyin.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin, depolamasını beklediğiniz değerleri depolayarak depolamalarının gerekip gerek olmadığını ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek için hızlı bir yol gerekir.

1. yönteminde döngüde duraklatılmışken, yöntem çağrısında duraklatana kadar F11 tuşuna basın (veya Hata ayıkla `for` `Main` > **Adımla)**  `SendMessage` seçin.

     Şu kod satırına bakabilirsiniz:

     `SendMessage(name, a[i]);`

1. yöntemine **adımını atarak F11'e** bir kez daha `SendMessage` basın.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     ![Koda Adımını At için F11 kullanma](../csharp/media/get-started-f11.png "F10 adımla")

     F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../../debugger/just-my-code.md)

     Yöntemini incelemeyi tamamlayanın ve yöntemin dışında kalmak ancak hata `SendMessage` ayıklayıcısında kalmak istediğinizi diyelim. Bunu Yapmak için Dışarı **Adımla komutunu kullanın.**

1. Shift   +  **F11 tuşuna** basın (veya **> AdımLa) tuşlarına basın.**

     Bu komut, geçerli yöntem veya işlev döndürene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

     Yöntem `for` çağrısında duraklamış olması için, yöntemde döngüde geri dönüş yapmanız gerekir `Main` `SendMessage` . Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Çalıştırmak için Çalıştır 'ı kullanarak kodu gezin

1. Kesme noktasına tekrar ilerlemek için **F5** tuşuna basın.

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak metodun üzerine gelin ve `Console.WriteLine` `SendMessage` **tıklama düğmesine tıklayarak** düğmenin sol tarafta görünmesini bekleyin. ![](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![Tıklama için Çalıştır özelliğini kullanın](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > **Tıklama Için Çalıştır düğmesi '** de yenidir [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Yeşil ok düğmesini görmüyorsanız, hata ayıklayıcıyı doğru yere ilerletmek için bu örnekte **F11** kullanın.)

2. **Tıklama düğmesine tıklayarak** ![' ye tıklayın.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcı `Console.WriteLine` yöntemine ilerler.

    Bu düğme kullanıldığında geçici bir kesme noktası ayarlamaya benzer. **' I tıklatarak** , uygulama kodunun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır (herhangi bir açık dosyaya tıklayabilirsiniz).

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlıca yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL**  +  **SHIFT**  +  **F5**) düğmesine tıklayın.

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

Hata ayıklayıcı daha önce döngü içinde ayarladığınız kesme noktasında yeniden durmaktadır `for` .

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

1. Kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

    Kapatılmışsa, hata ayıklayıcıda **hata ayıklama**  >  **Windows**  >  **oto öğeleri**' ni seçerek açın.

    **Oto** penceresinde, değişkenleri ve bunların geçerli değerlerini görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

1. Ardından, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresine bakın.

1. Değişkenini, `letters` içerdiği öğeleri göstermek için genişletin.

     ![Locals penceresinde değişkenleri İnceleme](../csharp/media/get-started-locals-window.png "Yereller penceresi")

    **Yereller** penceresi, geçerli yürütme bağlamı olan geçerli [kapsamda](https://www.wikipedia.org/wiki/Scope_(computer_science))olan değişkenleri gösterir.

## <a name="set-a-watch"></a>İzleme ayarlama

1. Ana kod Düzenleyicisi penceresinde değişkene sağ tıklayın `name` ve **Gözcü Ekle**' yi seçin.

    **İzleme** penceresi, kod düzenleyicisinin en altında açılır. Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz.

    Artık değişkende bir izleme kümesi vardır `name` ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Gözcü** penceresi her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte gösterilir).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

1. Döngüde durakladığında `for` , varsayılan olarak sağ alt bölmede açık olan **çağrı yığını** penceresine tıklayın.

    Kapatılmışsa, hata ayıklayıcıda hata **Ayıkla**  >  **Windows**  >  **çağrı yığını**' nı seçerek dosyayı açın.

2. Yöntemde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın `SendMessage` . **Çağrı yığını** penceresine bakın.

    ![Çağrı yığınını inceleyin](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `SendMessage` Bu uygulamadaki yöntemi) gösterilir. İkinci satır, `SendMessage` `Main` yönteminden çağrılan ve bu şekilde devam eden gösterir.

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

    Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu eylem, hata ayıklayıcıyı ilerlemez.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilir, çalışma hata ayıklayıcıyı kullanarak Imleç ' i **Imlece** ilerletebilirsiniz ve kaynak kodu İnceleme ' ye gidebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

1. Yöntemi çalıştırmak için **F11** tuşuna iki kez basın `Console.WriteLine` .

1. Yöntem çağrısında hata ayıklayıcı duraklatıldığında `SendMessage` , sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve sarı oku bir satır yukarı doğru aşağı taşıyın `Console.WriteLine` .

1. **F11** tuşuna basın.

    Hata ayıklayıcı yöntemini yeniden çalıştırır `Console.WriteLine` (bunu konsol penceresi çıktısında görürsünüz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etme veya hata ayıklayıcıyı yeniden başlatmanıza gerek kalmadan kodu yeniden çalıştırma gibi işlemleri yapabilirsiniz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmanız ve araç ipucunda bir uyarı görmeniz gerekir. Diğer uyarıları da görebilirsiniz. İşaretçinin taşınması uygulamanızı önceki bir uygulama durumuna döndüremezsiniz.

1. Uygulamayı çalıştırmaya devam etmek için **F5** tuşuna basın.

    Tebrikler, bu öğreticiyi tamamlama!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm sağlamak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
