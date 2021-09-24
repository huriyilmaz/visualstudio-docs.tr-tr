---
title: 'Öğretici: C# kodunda hata ayıklama'
description: Hata ayıklayıcısının Visual Studio hata ayıklayıcısını başlatmayı, kodda adım adım ilerler ve bir C# uygulamasındaki verileri incelemeyi öğrenin.
ms.custom: debug-experiment, vs-acquisition, get-started
ms.date: 09/14/2020
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
ms.openlocfilehash: 22224b405f8e6cce41b99e36936bb2449f7827ea
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128374785"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C# kodunda hata ayıklamayı Visual Studio

Bu makalede, Visual Studio hata ayıklayıcısının özellikleri adım adım izlenecek yol açıklanmıştır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü almak için [bkz. İlk olarak hata ayıklayıcıya bakın.](../../debugger/debugger-feature-tour.md) Uygulamanıza *hata ayıklarken,* genellikle hata ayıklayıcı eklenmiş olarak çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişip değişmeyişini görmek için değişkenler üzerinde izlemeler ayarlayın, kodunuzun yürütme yolunu inceleyebilirsiniz, bir kod dalını çalıştırıp çalıştırmama gibi. İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi okumadan önce yeni başlayanlar için [hata](../../debugger/debugging-absolute-beginners.md) ayıklama makalesine bakabilirsiniz.

Tanıtım uygulaması C# olsa da özelliklerin çoğu C++, Visual Basic, F#, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F# Düzenle ve devamını desteklemez). F# ve JavaScript, Otomatikler **penceresini desteklemez).** Ekran görüntüleri C# içindedir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlat ve kesme noktalarına isabet.
> * Hata ayıklayıcıda kodda adım adım ilerlerken gereken komutları öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı pencerelerde değişkenleri inceleme
> * Çağrı yığınını inceleme

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2022"

2022 Preview Visual Studio ve .NET masaüstü geliştirme iş **yükünüz yüklü** olması gerekir.

::: moniker-end

::: moniker range="vs-2019"

2019 Visual Studio **ve .NET Core** platformlar arası geliştirme iş yükünüz olması gerekir.

::: moniker-end

::: moniker range="vs-2017"

2017 Visual Studio **ve .NET Core** platformlar arası geliştirme iş yükünüz olması gerekir.

::: moniker-end

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="<=vs-2019"

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2022"

Zaten bir Visual Studio ancak **.NET masaüstü** geliştirme iş yükü yüklü değilse Araçlar Araçları ve Özellikleri  >  **Al...** bağlantısına gidin ve Visual Studio Yükleyicisi. Uygulamanın Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir .NET Core konsol uygulaması projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

1. Sol **bölmede yeni Project** iletişim kutusunda **C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *get-started-debugging adını girin.*

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,  Yeni Visual Studio Yükleyicisi iletişim kutusunun sol bölmesindeki  Açık Project seçin.

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması için C# şablonunun ekran görüntüsü.](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** *GetStartedDebugging yazın* **veya Project** girin. Ardından, **Sonraki'yi seçin.**

1. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uyguladikten sonra Konsol Uygulaması **şablonunu ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/get-started-create-console-project.png" alt-text="2022'de 'Yeni proje oluştur' penceresindeki 'Konsol Uygulaması' şablonunun ekran Visual Studio.":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** *GetStartedDebugging yazın* **veya Project** girin. Ardından, **Sonraki'yi seçin.**

1. Ek bilgiler penceresinde **Çerçeve** açılan menüsünde  **.NET 6.0 (Önizleme)** öğesinin seçili olduğundan emin olun ve oluştur'a **tıklayın.**

    Visual Studio projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

*Program.cs içinde,* varsayılan kodun hepsini aşağıdaki kodla değiştirin:

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

::: moniker range="<=vs-2019"

1. **F5** (**Hata Ayıklama > Başlat**) veya Hata Ayıklamayı Başlat düğmesi  !['Hata Ayıklamayı Başlat' düğmesinin görüntüsü.](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") Hata Ayıklama Araç Çubuğunda.

     **F5,** uygulamayı uygulama sürecine eklenmiş hata ayıklayıcısıyla başlatır, ancak şu anda kodu incelemek için özel bir işlem yapmadık. Bu nedenle uygulama yüklenir ve bu konsol çıktısını görüntülenir.

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

     Bu öğreticide hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından bakacak ve hata ayıklayıcı özelliklerine göz atalım.

1. 'Hata Ayıklamayı Durdur' düğmesinin kırmızı ![durdurma Görüntüsüne basarak hata ayıklayıcıyı durdurun.](../../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") button (**Shift**  +  **F5**).

1. Konsol penceresinde, konsol penceresini kapatmak için bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2022"

Hata ayıklayıcı komutlarını yürütmenin hızlı bir yolu olduğundan, burada çoğunlukla klavye kısayollarını kullanırız. Araç çubuğu veya menü komutları gibi eşdeğer komutlar da not edilmektedir.

1. Hata ayıklayıcıyı başlatmak için **F5'i** seçin veya Standart araç çubuğunda  Hata Ayıklama Hedefi düğmesini seçin ya  da Hata Ayıklama araç çubuğunda Hata Ayıklamayı Başlat düğmesini seçin veya menü çubuğundan Hata AyıklamaYı Başlat'ı  >  seçin.

    :::image type="content" source="media/vs-2022/dbg-tour-start-debugging.png" alt-text="Visual Studio 2022'nin Standart araç çubuğundaki 'Hedefte Hata Ayıkla' düğmesinin ekran görüntüsü.":::

    **F5,** uygulama işleminin hata ayıklayıcısını ekli olarak başlatır. Kodu incelemek için özel bir şey yapılmadan uygulama tamamlandıktan sonra konsol çıktısını görüyorsunuz.

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

1. Hata ayıklayıcıyı durdurmak için **Shift+F5'i** seçin veya Hata Ayıklama araç  çubuğunda Hata Ayıklamayı Durdur düğmesini seçin veya menü çubuğundan Hata AyıklamaYı  >  Durdur'u seçin.

    :::image type="content" source="media/vs-2022/dbg-tour-stop-debugging.png" alt-text="Visual Studio 2022'nin Hata Ayıklama araç çubuğundaki 'Hata ayıklamayı durdur' düğmesinin ekran görüntüsü.":::

1. Konsol penceresinde herhangi bir tuş seçerek konsol penceresini kapatın.

::: moniker-end

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

::: moniker range="<=vs-2019"

1. işlevinin `for` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kırmızı daire ![Kesme noktası resmi.](../../debugger/media/dbg-breakpoint.png "Kesme noktası") kesme noktası ayar merkezi görüntülenir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerindendir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

1. **F5** tuşuna  basın veya Hata Ayıklamayı Başlat düğmesi 'Hata Ayıklamayı Başlat' düğmesinin ekran ![görüntüsü.](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat"), uygulama başlatılır ve hata ayıklayıcı kesme noktası ayarlayıcısı kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../csharp/media/get-started-set-breakpoint.gif)

    Sarı ok, aynı noktada uygulama yürütmeyi de askıya alan (bu deyim henüz yürütülmedi) hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur. Aksi **takdirde, F5** uygulamayı bir sonraki kesme noktasıyla çalıştırmaya devam eder.

    Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Ayar yalnızca koşullu kesme noktaları gibi farklı kesme noktası türleri hakkında bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

::: moniker-end

::: moniker range=">=vs-2022"

1. işlevinin `for` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktası ayarda kırmızı bir daire görünür.

    :::image type="content" source="media/vs-2022/dbg-tour-breakpoint.png" alt-text="Visual Studio 2022'de kesme noktası ekran görüntüsü."::: 

    Kesme noktaları, güvenilir hata ayıklamanın temel bir özelliğidir. Değişkenlerin değerlerine veya bellek davranışına bakarak veya bir kod dalını çalıştırıp çalıştırmama konusunda bilgi almak için, çalışan kodunuzu duraklatmak için Visual Studio istediğiniz kesme noktaları ayarlayın.

1. Hata ayıklamayı başlatmak için **F5'i** seçin veya Standart araç çubuğunda  Hata Ayıklama Hedefi düğmesini seçin ya da Hata Ayıklama araç çubuğunda Hata Ayıklamayı Başlat düğmesini seçin veya menü çubuğundan Hata AyıklamaYı Başlat'ı   >   seçin. Uygulama başlatılır ve hata ayıklayıcı, kesme noktası ayarlayıcının ayar bulunduğu kod satırına çalışır.

    :::image type="content" source="media/vs-2022/get-started-set-breakpoint.png" alt-text="Visual Studio 2022'nin kod düzenleyicisinde kesme noktası gösteren ve kesme noktası sırasında kod yürütmenin duraklatılmış olduğu ekran görüntüsü.":::

    Sarı ok, hata ayıklayıcının duraklatılmış olduğu deyimini belirtir. Uygulama yürütme aynı noktada duraklatılır ve deyimi henüz yürütülmedi.

    Uygulama çalışmadığı zaman **F5** hata ayıklayıcıyı başlatacak ve ilk kesme noktası ulaşana kadar uygulamayı çalıştıracak. Uygulama bir kesme noktası üzerinden duraklatılırsa **F5,** bir sonraki kesme noktası ulaşana kadar uygulamayı çalıştırmaya devam eder.

    Kesme noktaları, ayrıntılı olarak incelemek istediğiniz kod satırı veya bölümünü biliyorken yararlı bir özelliktir. Koşullu kesme noktaları gibi ayar yalnızca farklı kesme noktası türleri hakkında daha fazla bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

::: moniker-end

## <a name="navigate-code-and-inspect-data-by-using-data-tips"></a>Veri ipuçlarını kullanarak kodda gezinme ve verileri inceleme

::: moniker range="<=vs-2019"

Genellikle burada klavye kısayollarını kullanırız çünkü bu, uygulamanızı hata ayıklayıcısında yürütmenin hızlı bir yolu olduğundan (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. deyiminde duraklatılmışken değişkeninin üzerine gelin ve bunun varsayılan değeri olan dizideki `name += letters[i]` `letters` ilk öğenin değerini `char[10]` görüyorsunuz.

     Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerindendir ve bunu yapmak için farklı yollar vardır. Genellikle bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

     !['name+= letters[I]' deyiminde duraklatılmış olan hata ayıklayıcının ekran görüntüsü.](../csharp/media/get-started-view-data-tip.png)

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Yöntem **çağrısına ilerlemek için F10** **tuşuna basın (veya >** Adım At) hata ayıkla'ya basın ve ardından `SendMessage` **F10'a** bir kez daha basın.

     F10, uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı bir sonraki deyime ilerletmektedir (kod yürütülmektedir). Yöntem çağrısında F10'a basarak, uygulama kodunu atlamıştık (şu anda `SendMessage` `SendMessage` ilgilenmediğimiz bir şey olabilir).

1. Döngüde birkaç kez  tekrarlama, kesme noktası üzerinde tekrar duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F10'a** (veya Hata Ayıklama Adımında Hata Ayıkla) birkaç kez >  `for` `name` basın.

     ![Hata Ayıklayıcısı'Visual Studio F10'a "AdımLa" tuşuna basmanın ve hata ayıklama sırasında döngüde tekrarlamanın etkisini gösteren animasyonlu ekran görüntüsü.](../csharp/media/get-started-data-tip.gif)

     Değişkenin değeri döngüde her yineleme ile birlikte değişir ve ardından `for` , ve gibi değerleri `f` `fr` `fre` gösterir. Bu senaryoda hata ayıklayıcıyı döngüde daha hızlı ilerlemek için  **F5** tuşuna basabilirsiniz (veya Devam Et'i seçerek) bir sonraki deyim yerine kesme noktası  >  üzerinden ilerleyin.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin hızlı bir yolunu, depolamasını beklediğiniz değerleri depolayarak depolamalarını isteyip istemediklerini ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek istersiniz.

1. yönteminde döngüde duraklatılmışken, yöntem çağrısında duraklatana kadar F11 tuşuna basın (veya Hata ayıkla'> `for` `Main` **Adımla)**  `SendMessage` seçin.

     Şu kod satırına bakabilirsiniz:

     `SendMessage(name, a[i]);`

1. yöntemine **adımını atarak F11'e** bir kez daha `SendMessage` basın.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     !['SendMessage' yönteminde yürütme işaretçisinin ekran görüntüsü.](../csharp/media/get-started-f11.png "F10 Içine Adımla")

     F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../../debugger/just-my-code.md)

     Yöntemini incelemeyi tamamlayanın ve yöntemin dışında kalmak ancak hata `SendMessage` ayıklayıcısında kalmak istediğinizi diyelim. Bunu Yapmak için Dışarı **Adımla komutunu kullanın.**

1. Shift  + **F11 tuşuna** basın (veya **> AdımLa) tuşlarına basın.**

     Bu komut, geçerli yöntem veya işlev döndürene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

     yöntem çağrısında `for` duraklatılmış `Main` yönteminde döngüsüne geri `SendMessage` dönmeniz gerekir. Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

::: moniker range=">=vs-2022"

1. deyiminde duraklatılırken, dizi boyutunu ve öğe türünü gösteren bir veri ipucu görmek için `name += letters[i]` `letters` değişkeninin üzerine `char[10]` gelin.

    > [!NOTE]
    > Hata ayıklayıcının en kullanışlı özelliklerinden biri, değişkeni incelemesidir. Genellikle bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda beklediğiniz değerlere sahip olup olmadığını bulmaya çalışıyor oluruz. Veri ipuçlarını görüntüleme, bunu denetlemenin iyi bir yolu olabilir.

1. Tüm dizi `letters` öğelerini ve değerlerini görüntülemek için değişkenini genişletin.

    :::image type="content" source="media/vs-2022/get-started-view-data-tip.png" alt-text="'Letters' dizi değişkeninin öğe değerlerini gösteren Visual Studio 2022'de hata ayıklayıcısı veri ipucu ekran görüntüsü.":::

1. Boş bir `name` dize olan geçerli değerini görmek için değişkenin üzerine gelin.

1. Hata ayıklayıcıyı bir sonraki deyime ilerlemek için  **F10'u** seçin veya Hata Ayıklama araç çubuğundaKi Adım Adım düğmesini seçin veya menü çubuğundan Hata Ayıklama Adımını  >   Ayıkla'ya tıklayın. Yöntem **çağrısının geri adımını** taşımak için F10'ı iki `SendMessage` kez daha seçin. 

    **F10,** kodu hala yürütülse de işlev veya yöntemlere adımlamadan hata ayıklayıcıyı ilerleter. Bu şekilde yönteminde kodun hata ayıklamasını atlamış oluruz ve şu anda `SendMessage` ilgilenmeziz.

1. Döngüde birkaç kez yinelenirken tekrar tekrar `for` **F10'ı** seçin. Her döngü yinelemesi sırasında kesme noktası sırasında duraklatın ve ardından veri ipucunda `name` değerini kontrol etmek için değişkenin üzerine gelin.

    :::image type="content" source="media/vs-2022/get-started-data-tip.png" alt-text="'name' değişkeninin dize değerini gösteren Visual Studio 2022'de hata ayıklayıcısı veri ipucu ekran görüntüsü.":::

    Değişkenin değeri döngüde her yineleme ile birlikte değişir ve ardından `for` , ve gibi değerleri `f` `fr` `fre` gösterir. Hata ayıklayıcıyı döngüde daha hızlı ilerlemek için **F5'i** seçin. Bu seçim sonraki deyim yerine kesme noktanıza ilerler.

1. Yöntemin döngüsünde duraklatılmışken `for` `Main`   **F11'i** seçin veya Hata Ayıklama araç çubuğundan Adımla düğmesini seçin veya yöntem çağrısına ulaşana kadar menü çubuğundan Hata Ayıkla Adımını Ayıkla'ya >  `SendMessage` tıklayın.

     Hata ayıklayıcısı şu kod satırına duraklatılmış olması gerekir:

     `SendMessage(name, a[i]);`

1. yöntemine adımını `SendMessage` eklemek için **F11'i yeniden** seçin.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     :::image type="content" source="media/vs-2022/get-started-f11.png" alt-text="'SendMessage' yönteminde hata ayıklayıcının yürütme işaretçisini gösteren ekran görüntüsü.":::

     **F11,** kodunuzun yürütme akışını daha ayrıntılı incelemenize yardımcı olur. Yöntem çağrısından bir yönteme adım eklemek için **F11'i seçin.** Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan yöntemlere adımlamayı atlar. Kullanıcı olmayan kodda hata ayıklama hakkında bilgi edinmek için [bkz. Yalnızca kendi kodum.](../../debugger/just-my-code.md)

     Yöntemin hata ayıklamasını `SendMessage` tamamladikten sonra yöntemin döngüsüne `for` geri dönmek için hazır `main` oluruz.

1. Yöntemi bırakmak `SendMessage` için **Shift+F11'i** seçin  veya Hata Ayıklama araç çubuğundaki  Adım At düğmesini seçin veya menü çubuğundan Hata Ayıklama Adımını >  Ayıkla'ya tıklayın.

     **Dışarı Adımla,** uygulama yürütmeyi sürdürür ve geçerli yöntem veya işlev geri dönene kadar hata ayıklayıcıyı ilerleter.

     Yöntemin döngüsünde sarı `for` işaretçiyi, yöntem `Main` çağrısında duraklatılmış `SendMessage` olarak yeniden görüyorsunuz. Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Tıklarken Çalıştır'ı kullanarak kodda gezinme

::: moniker range="<=vs-2019"

1. Kesme noktası tekrar ilerlemek için **F5'i** seçin.

1. Kod düzenleyicisinde aşağı kaydırın ve yeşil renkli Tıklanacak Şekilde Çalıştır düğmesi 'Tıklanacak Şekilde Çalıştır' düğmesinin görüntüsüne kadar `Console.WriteLine` `SendMessage` ![yönteminde yönteminin üzerine gelin.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")  sol tarafta görünür. Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

     !['Tıklamak için Çalıştır' düğmesinin ekran görüntüsü.](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > Tıklayarak **Çalıştır düğmesi** içinde [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] yenidir. (Yeşil ok düğmesini görmüyorsanız hata ayıklayıcıyı doğru yere ilerlemek için bu örnekte **F11** kullanın.)

1. **Tıklarken Çalıştır düğmesine** Tıklayın !['Tıklanacak Şekilde Çalıştır' düğmesinin görüntüsü.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Hata ayıklayıcısı yöntemine `Console.WriteLine` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklarken Çalıştır,** uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

::: moniker-end

::: moniker range=">=vs-2022"

1. Kesme noktası tekrar ilerlemek için **F5'i** seçin.

1. Kod düzenleyicisinde, sol tarafta `Console.WriteLine` Tıklanacak Şekilde Çalıştır düğmesi görünene kadar `SendMessage` **yönteminde yöntem** çağrısının üzerine gelin. Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

    :::image type="content" source="media/vs-2022/get-started-run-to-click.png" alt-text="2022'de 'Tıkla' düğmesini Visual Studio ekran görüntüsü.":::

1. **Tıklarken Çalıştır düğmesini** seçin. Alternatif olarak imlecinizi deyiminde `Console.WriteLine` **Ctrl+F10 tuşlarına basın.** Ya da yöntem çağrısına `Console.WriteLine` sağ tıklayın ve bağlam **menüsünden İmleçte** Çalıştır'ı seçin.

    Hata ayıklayıcısı yöntem `Console.WriteLine` çağrısına ilerler.

    Tıklayarak **Çalıştır düğmesinin** kullanımı geçici bir kesme noktası ayarlamaya benzer ve uygulama kodunuzun görünür bir bölgesi içinde açık bir dosyada hızlıca dolaşabilir.

::: moniker-end

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

::: moniker range="<=vs-2019"

'Uygulamayı **Yeniden** ![Başlat' düğmesinin Yeniden Başlat Görüntüsüne tıklayın.](../../debugger/media/dbg-tour-restart.png "RestartApp") Hata Ayıklama Araç Çubuğundaki düğmesi (**Ctrl**  +  **Shift**  +  **F5**).

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı, daha önce döngü içinde ayaranı kesme noktası sırasında yeniden `for` durur.

::: moniker-end

::: moniker range=">=vs-2022"

Hata ayıklayıcısında en baştan uygulamayı yeniden çalıştırmak için **Ctrl+Shift+F5** tuşlarını veya Hata Ayıkla  araç çubuğunda Yeniden Başlat düğmesini seçin veya menü çubuğundan Yeniden Başlatmada Hata Ayıkla'ya  >  tıklayın.

:::image type="content" source="media/vs-2022/dbg-tour-restart-debugging.png" alt-text="Visual Studio 2022'nin Hata Ayıklama araç çubuğundaki 'Yeniden Başlat' düğmesinin ekran görüntüsü.":::

**Yeniden** başlatma, hata ayıklayıcıyı durdurur ve ardından tek adımda yeniden başlatın. Hata ayıklayıcı yeniden başlatıldığında, döngü içinde daha önce ayar istediğiniz kesme noktası olan ilk kesme noktasıyla `for` çalışır ve ardından duraklatılır.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

::: moniker range="<=vs-2019"

1. Kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

    Kapalı ise Hata Ayıkla'ya ve Otomatik'e  göre hata ayıkla'Windows >  > **ayıklayıcıda duraklatılmış olarak açın.**

    Otomatikler **penceresinde** değişkenleri ve bunların geçerli değerini görebilirsiniz. Otomatikler **penceresinde** geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (Dile özgü davranış için belgeleri kontrol edin).

1. Ardından, Otomatikler **penceresinin** yanındaki sekmede Yereller **penceresine** bakın.

1. Içerdiği `letters` öğeleri göstermek için değişkeni genişletin.

     ![Visual Studio'da Yereller Penceresinin ekran görüntüsü.](../csharp/media/get-started-locals-window.png "YerelLer Penceresi")

    **YerelLer** penceresi, geçerli kapsamda olan, yani [geçerli](https://www.wikipedia.org/wiki/Scope_(computer_science))yürütme bağlamındaki değişkenleri gösterir.

::: moniker-end

::: moniker range=">=vs-2022"

Otomatikler **ve** **Yereller** pencereleri, hata ayıklama sırasında değişken değerlerini gösterir. Pencereler yalnızca bir hata ayıklama oturumu sırasında kullanılabilir. **Otomatikler** penceresinde, hata ayıklayıcının olduğu geçerli satırda ve önceki satırda kullanılan değişkenler gösterilir. **Yereller penceresinde** yerel kapsamda tanımlanan değişkenler gösterilir ve bu genellikle geçerli işlev veya yöntemdir.

1. Hata ayıklayıcı duraklatılmışken, kod **düzenleyicisinin** en altındaki Otomatikler penceresini açın.

    Otomatikler **penceresi kapalı** **ise, menü çubuğundan Ctrl+D, A** veya Hata  > **ayıkla'Windows** > **Otomatikler'i** seçin.

1. Hata ayıklayıcı duraklatılmış şekilde, **Otomatikler** penceresinin yanındaki sekmede Yereller **penceresini** görüntüleyin.

    Yereller **penceresi kapalı** ise **Ctrl+D, L** veya  YerelLer'de Hata > **Ayıkla'Windows** > **seçin.**

1. Yereller **penceresinde,** dizi öğelerini `letters` ve değerlerini görmek için değişkeni genişletin.

     :::image type="content" source="media/vs-2022/get-started-locals-window.png" alt-text="2022'de 'letters' dizi değişkeni genişletilmiş şekilde Visual Studio yereller penceresinin ekran görüntüsü.":::

Otomatikler ve **Yereller pencereleri** hakkında **daha fazla bilgi için** [Bkz. Otomatikler ve Yereller pencerelerinde değişkenleri inceleme.](/visualstudio/debugger/autos-and-locals-windows?view=vs-2022&preserve-view=true)

::: moniker-end

## <a name="set-a-watch"></a>Saat ayarlama

::: moniker range="<=vs-2019"

1. Ana kod düzenleyicisi penceresinde değişkenine sağ tıklayın ve İzleme `name` **Ekle'yi seçin.**

    Kod  düzenleyicisinin alt kısmında İzleme penceresi açılır. İzleme penceresi **kullanarak** göz tutmak istediğiniz bir değişken (veya ifade) belirtebilirsiniz.

    Artık değişkende bir izleme kümemiz var ve hata ayıklayıcıda ilerlerken `name` değerinin değişti olduğunu görüyorsunuz. Diğer değişken pencerelerinin aksine, **İzleme** penceresi her zaman izlediğiniz değişkenleri gösterir (kapsam dışındayken bunlar gri renkte olur).

::: moniker-end

::: moniker range=">=vs-2022"

İzleme penceresine ekleyerek kodda adım adım ilerlerken izlemek istediğiniz bir değişken veya ifade &mdash; **belirtebilirsiniz.**

1. Hata ayıklayıcı duraklatılmışken değişkenine sağ tıklayın ve İzleme `name` **Ekle'yi seçin.**

    Kod **düzenleyicisinin** alt kısmında varsayılan olarak İzleme penceresi açılır.

1. Değişkende bir saat ayar her döngü yinelemesinde değişkenin değerini görmek için kodunuz üzerinde `name` bir izleme ayar her zaman için bir saat `name` `for` ayarlayabilirsiniz. 

    Diğer değişken pencerelerinin  aksine, İzleme penceresi her zaman izlediğiniz değişkenleri gösterir, ancak kapsam dışında olduğunda bunlar gri renkte görünür.

İzleme penceresi hakkında daha **fazla bilgi** için [bkz. İzleme pencereleri ile değişkenleri izleme.](/visualstudio/debugger/watch-and-quickwatch-windows?view=vs-2022&preserve-view=true)

::: moniker-end

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleme

::: moniker range="<=vs-2019"

1. Döngüde duraklatılmışken, varsayılan olarak sağ alt bölmede açık `for` olan Çağrı Yığını penceresine tıklayın. 

    Kapalı ise, Çağrı Yığınında Hata Ayıkla'yı seçerek hata **ayıklayıcıda** > **duraklatılmış Windows** > **açın.**

1. Yönteminde hata ayıklayıcı duraklamasını görene kadar **F11'e** birkaç kez `SendMessage` tıklayın. Çağrı Yığını **penceresine** bakın.

    ![Visual Studio'daki Çağrı Yığını penceresinin ekran görüntüsü.](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Üst satır geçerli işlevi (bu `SendMessage` uygulamanın yöntemi) gösterir. İkinci satır, `SendMessage` yönteminin çağrıl `Main` olduğunu gösterir ve bu şekilde devam etti.

   > [!NOTE]
   > Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yol sağlar.

    Bir kod satırına çift tıklar ve bu kaynak kodu inceler ve hata ayıklayıcı tarafından denetlenen geçerli kapsamı da değiştirir. Bu eylem hata ayıklayıcıyı ilerleten bir eylem değildir.

    Başka şeyler yapmak için Çağrı Yığını penceresinden sağ **tıklama** menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları eklemek, İmleçte Çalıştır'ı kullanarak hata ayıklayıcıyı **ilerletin** ve kaynak kodu incelemeye gidebilirsiniz. Daha fazla bilgi için, [bkz. How to: Examine the Call Stack](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

::: moniker range=">=vs-2022"

Çağrı **Yığını,** yöntemlerin ve işlevlerin çağrıldığı sırayı göstererek, uygulamanın yürütme akışını anlamanıza yardımcı olabilir.

1. Hata ayıklayıcı döngüde duraklatılmışken, kod düzenleyicisinin sağ alt bölmesinde varsayılan olarak açılan Çağrı Yığını `for` penceresini görüntüleyin. 

    Çağrı Yığını **penceresi kapalı** **ise, Ctrl+D, C'yi** seçin veya menü  > **çubuğundan Windows** > **Yığınında** Hata Ayıkla'yı seçin.

    Çağrı **Yığını penceresinde** geçerli yöntemde sarı işaretçiyi `Main` görebilirsiniz.

1. Yönteminde hata ayıklayıcının duraklatılmış olduğunu görene kadar **F11'i** birkaç kez `SendMessage` seçin.

    Çağrı Yığını **penceresinin üst** satırı, yöntemi olan geçerli işlevi `SendMessage` gösterir. İkinci satır, yönteminin `SendMessage` yönteminden çağrıldı olduğunu `Main` gösterir.

    :::image type="content" source="media/vs-2022/get-started-call-stack.png" alt-text="Visual Studio 2022'de Çağrı Yığını penceresinin ekran görüntüsü.":::

   > [!NOTE]
   > Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

    Çağrı **Yığını penceresinde** bir kod satırına çift tıklar ve hata ayıklayıcı tarafından denetlenen geçerli kapsamı değiştirir. Bu eylem hata ayıklayıcıyı ilerleten bir eylem değildir.

    Başka şeyler yapmak için Çağrı Yığını penceresinden sağ **tıklama** menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları eklemek, İmleçte Çalıştır'ı kullanarak hata ayıklayıcıyı **ilerletin** veya kaynak koda gidebilirsiniz. 

Çağrı Yığını hakkında daha **fazla bilgi için** [bkz. Nasıl: Çağrı Yığınını Inceleme.](../../debugger/how-to-use-the-call-stack-window.md)

::: moniker-end

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

::: moniker range="<=vs-2019"

1. yöntemini **çalıştırmak için F11'e** iki kez `Console.WriteLine` basın.

1. Hata ayıklayıcı yöntem çağrısında duraklatılmış şekilde, fareyle sol tarafta sarı oku (yürütme işaretçisi) alıp sarı oku bir satır yukarı, geri `SendMessage` doğru hareket `Console.WriteLine` ettirin.

1. **F11 tuşuna basın.**

    Hata ayıklayıcısı yöntemini yeniden `Console.WriteLine` çalıştırıyor (konsol penceresi çıkışında bunu görüyorsunuz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etmek veya hata ayıklayıcıyı yeniden başlatmadan kodu yeniden çalıştırma gibi şeyler yapabiliriz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmalısınız ve araç ipucunda bir uyarı görüyorsunuz. Başka uyarılar da görebilir. İşaretçiyi hareket ettiren uygulama önceki bir uygulama durumuna geri döndürülebilir.

1. Uygulamayı **çalıştırmaya devam** etmek için F5 tuşuna basın.

    Tebrikler, bu öğreticiyi tamamladıktan sonra!

::: moniker-end

::: moniker range=">=vs-2022"

Hata ayıklama sırasında uygulamanın akışını değiştirmek için yürütme işaretçisini hareket ettirebilirsiniz.

1. Hata ayıklayıcı döngüde yöntem çağrısında duraklatılmış şekilde, yöntemine adımını atarak ve yürüttkten sonra yöntemin gerisinde taşımak için `SendMessage` `for` **F11'i** `SendMessage` üç kez `Console.WriteLine` seçin.

    Hata ayıklayıcısı artık yöntemin son kapanış ayracında `SendMessage` duraklatıldı.

1. Fareyle sarı oku veya yürütme işaretçisini (sol kenar boşluğunda) tutun ve işaretçiyi bir satır yukarı sürükleyin.

    Hata ayıklayıcısı artık deyimine `Console.WriteLine` geri döner.

1. **F11'i seçin.**

    Hata ayıklayıcısı yöntemini `Console.WriteLine` yeniden çalıştırıyor ve konsol penceresi çıkışında yinelenen bir satır görüyorsunuz.

1. Uygulamayı çalıştırmaya devam etmek için **F5'i** seçin.

Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etmek veya hata ayıklayıcıyı yeniden başlatmadan kodu yeniden çalıştırma gibi şeyler yapabiliriz.

> [!WARNING]
> Bu özelliği çok özenli kullanın. Yürütme işaretçisinin araç ipucunda, intenededi sonuçların olasılığı hakkında bir uyarı görünür. Başka uyarılar da görebilir. Yürütme işaretçisini taşıma işlemi, uygulamanızı önceki bir durumuna döndürebilir.

Yürütme akışını değiştirme hakkında daha fazla bilgi için [bkz. Yürütme akışını değiştirmek için işaretçiyi taşıma.](/visualstudio/debugger/navigating-through-code-with-the-debugger?view=vs-2022#BKMK_Set_the_next_statement_to_execute&preserve-view=true)

Tebrikler, bu öğreticiyi tamamladıktan sonra!

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklayıcıyı başlatmayı, kodu adım adım incelemeyi ve değişkenleri incelemeyi öğrendiniz. Daha fazla bilgi için bağlantılarla birlikte hata ayıklayıcı özelliklerine üst düzey bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
