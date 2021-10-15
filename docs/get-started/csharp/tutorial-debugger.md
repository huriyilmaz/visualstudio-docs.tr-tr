---
title: 'Öğretici: C# kodunda hata ayıklama'
description: Visual Studio hata ayıklayıcının özelliklerini ve hata ayıklayıcıyı nasıl başlatacağınızı, kodda adım adım ilerleyeceğinizi ve bir C# uygulamasındaki verileri incelemeyi öğrenin.
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
ms.openlocfilehash: 1ccbcddfaff619a56299279583fe14a0326519dc
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130011516"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C# kodunun hatalarını ayıklamayı öğrenin

bu makalede, adım adım izlenecek yol Visual Studio hata ayıklayıcının özellikleri tanıtılmaktadır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md). Uygulamanızda *hata ayıklarken*, genellikle uygulamanızı hata ayıklayıcı eklenmiş şekilde çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı kodun çalışırken ne yaptığını görmek için birçok yol sunar. Kodunuzda saklanan değerlere bakabilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerlerin ne zaman değişenleri görebileceğiniz, kodunuzun yürütme yolunu inceleyebileceğiniz, kodun bir dalında çalışıp çalışmadığını ve bu şekilde devam edebilirsiniz. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce [mutlak yeni başlayanlar Için hata ayıklamayı](../../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

tanıtım uygulaması C# olsa da, özelliklerin çoğu C++, Visual Basic, F #, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F # düzenle ve devam et ' i desteklemez. F # ve JavaScript, **oto** penceresini desteklemez). Ekran görüntüleri C# ' de bulunur.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktalarını isabet edin.
> * Hata Ayıklayıcıdaki kodu adım adım ilerme komutlarını öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı Windows 'da değişkenleri İnceleme
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2022"

Visual Studio 2022 RC yüklü ve **.net masaüstü geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 yüklü ve **.net Core platformlar arası geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 yüklü ve **.net Core platformlar arası geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="<=vs-2019"

iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range=">=vs-2022"

zaten Visual Studio sahipseniz ancak **.net masaüstü geliştirme** iş yükü yüklü değilse, **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi başlatan araçlar ' a gidin. Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir .NET Core konsol uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda **C#**' ı genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından Proje *Get-Started-hata ayıklama* adını adlandırın.

     **konsol uygulaması (.net Core)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin.

     Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra .NET Core **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması için C# şablonunun ekran görüntüsü.](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. sonra, Visual Studio Yükleyicisi **.net Core platformlar arası geliştirme** iş yükünü seçin.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *getstarteddebugging* yazın veya girin. Ardından **İleri**' yi seçin.

1. Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

   Visual Studio yeni projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2022/get-started-create-console-project.png" alt-text="Visual Studio 2022 ' nin ' yeni proje oluşturma ' penceresindeki ' konsol uygulaması ' şablonunun ekran görüntüsü.":::

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *getstarteddebugging* yazın veya girin. Ardından **İleri**' yi seçin.

1. **Ek bilgi** penceresinde, **Framework** açılan menüsünde **.net 6,0 (Önizleme)** ' nin seçili olduğundan emin olun ve ardından **Oluştur**' u seçin.

    Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

*Program. cs*' de, varsayılan tüm kodu aşağıdaki kodla değiştirin:

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

## <a name="start-the-debugger"></a>Hata ayıklayıcıyı başlatın!

::: moniker range="<=vs-2019"

1. **F5** tuşuna basın (hata ayıklama **> başlatın**) veya ![' hata ayıklamayı Başlat ' düğmesinin görüntü](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **hata ayıklamayı Başlat** düğmesi. Hata Ayıkla araç çubuğunda.

     **F5** uygulama işlemine eklenen hata ayıklayıcı ile uygulamayı başlatır, ancak şimdi kodu incelemek için özel bir şey yapmadık. Bu nedenle uygulama yalnızca yüklenir ve bu konsol çıktısını görürsünüz.

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

     Bu öğreticide, hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından bakacağız ve hata ayıklayıcı özelliklerine göz atalım.

1. ![' Hata ayıklamayı Durdur ' düğmesinin](../../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") kırmızı durma görüntüsüne basarak hata ayıklayıcıyı durdurun. düğme (**SHIFT**  +  **F5**).

1. Konsol penceresinde bir tuşa basarak konsol penceresini kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

Genellikle, burada klavye kısayollarını kullanıyoruz. Bu, hata ayıklayıcı komutlarının yürütülmesi için hızlı bir yoldur. Araç çubuğu veya menü komutları gibi eşdeğer komutlar da belirtilmiştir.

1. Hata ayıklayıcıyı başlatmak için **F5**' i seçin veya Standart araç çubuğunda **hedefi Ayıkla hedefi** düğmesini seçin veya hata ayıklama araç çubuğunda Hata **ayıklamayı Başlat** düğmesini seçin veya  > menü çubuğunda Hata **ayıklamayı Başlat** ' ı seçin.

    :::image type="content" source="media/vs-2022/dbg-tour-start-debugging.png" alt-text="Visual Studio 2022 standart araç çubuğunda ' hata ayıkla hedefi ' düğmesinin ekran görüntüsü.":::

    **F5** uygulamayı uygulama işlemine iliştirilmiş hata ayıklayıcı ile başlatır. Kodu incelemek için özel bir şey yapmadığımızdan, uygulama tamamlandığında çalışır ve konsol çıkışını görürsünüz.

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

1. Hata ayıklayıcıyı durdurmak için **SHIFT + F5**' i seçin veya hata ayıklama araç çubuğunda Hata **ayıklamayı Durdur** düğmesini seçin ya da menü çubuğunda hata ayıklamayı Durdur ' **u seçin** >  .

    :::image type="content" source="media/vs-2022/dbg-tour-stop-debugging.png" alt-text="Visual Studio 2022 hata ayıklama araç çubuğundaki ' hata ayıklamayı durdur ' düğmesinin ekran görüntüsü.":::

1. Konsol penceresinde, konsol penceresini kapatmak için herhangi bir anahtar seçin.

::: moniker-end

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

::: moniker range="<=vs-2019"

1. `for` `Main` İşlevin döngüsünde, aşağıdaki kod satırının sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    ![Kesme noktasının kırmızı daire resmi.](../../debugger/media/dbg-breakpoint.png "Kesme noktası") kesme noktasını ayarladığınız yerde görüntülenir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede askıya alınacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

1. **F5** tuşuna basın veya ![' hata ayıklamayı Başlat ' düğmesinin ekran görüntüsünü](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **başlatın** ., uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../csharp/media/get-started-set-breakpoint.gif)

    Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

     Uygulama henüz çalışmıyorsa, **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır. Aksi halde, **F5** uygulamayı bir sonraki kesme noktasına çalıştırmaya devam eder.

    Kod satırını veya kodun ayrıntılı olarak incelemek istediğiniz bölümünü bildiğiniz kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../../debugger/using-breakpoints.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. işlevinin `for` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktası ayarda kırmızı bir daire görünür.

    :::image type="content" source="media/vs-2022/dbg-tour-breakpoint.png" alt-text="Visual Studio 2022'de kesme noktası ekran görüntüsü."::: 

    Kesme noktaları, güvenilir hata ayıklamanın temel bir özelliğidir. Değişkenlerin değerlerine veya bellek davranışına bakarak Visual Studio ya da bir kod dalını çalıştırıp çalıştırmama konusunda bilgi almak için, çalışan kodunuzu duraklatmak istediğiniz kesme noktaları ayarlayın.

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

1. Yöntem **çağrısına ilerlemek için F10** **tuşuna basın**(veya > Adım At) hata ayıkla'ya basın ve `SendMessage` ardından **F10'a** bir kez daha basın.

     F10, uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı bir sonraki deyime ilerletmektedir (kod yürütülmektedir). Yöntem çağrısında F10'a basarak, uygulama kodunu atlamıştık (şu anda `SendMessage` `SendMessage` ilgilenmediğimiz bir şey olabilir).

1. Döngüde birkaç kez  tekrarlama, kesme noktası üzerinde tekrar duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F10'a** (veya Hata Ayıklama Adımında Hata Ayıkla) birkaç kez >  `for` `name` basın.

     ![Hata Ayıklayıcısı'Visual Studio F10'a "Adım At" tuşuna basmanın ve hata ayıklama sırasında döngüde tekrarlamanın etkisini gösteren animasyonlu ekran görüntüsü.](../csharp/media/get-started-data-tip.gif)

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

1. Shift  + **F11 tuşuna** basın (veya **> AdımLa) hata ayıkla'ya basın.**

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

     **F11,** kodunuzun yürütme akışını daha ayrıntılı incelemenize yardımcı olur. Yöntem çağrısından bir yönteme adım eklemek için **F11'i seçin.** Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan yöntemlere adımlamayı atlar. Kullanıcı olmayan kodda hata ayıklama hakkında bilgi edinmek için bkz. [Yalnızca kendi kodum.](../../debugger/just-my-code.md).

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

:::image type="content" source="media/vs-2022/dbg-tour-restart-debugging.png" alt-text="Visual Studio 2022'de hata ayıkla araç çubuğundaki 'Yeniden Başlat' düğmesinin ekran görüntüsü.":::

**Yeniden** başlatma, hata ayıklayıcıyı durdurur ve ardından tek adımda yeniden başlatın. Hata ayıklayıcı yeniden başlatıldığında, döngü içinde daha önce ayar istediğiniz kesme noktası olan ilk kesme noktasıyla `for` çalışır ve ardından duraklatılır.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

::: moniker range="<=vs-2019"

1. Kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

    Kapalı ise Hata Ayıkla'ya veya Otomatikler'e göre hata ayıkla'Windows  >  > **ayıklayıcıda duraklatılmış olarak açın.**

    Otomatikler **penceresinde** değişkenleri ve bunların geçerli değerini görebilirsiniz. Otomatikler **penceresinde** geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (Dile özgü davranış için belgeleri kontrol edin).

1. Ardından, Otomatikler **penceresinin** yanındaki sekmede Yereller **penceresine** bakın.

1. Içerdiği `letters` öğeleri göstermek için değişkeni genişletin.

     ![Visual Studio'da Yereller Penceresinin ekran görüntüsü.](../csharp/media/get-started-locals-window.png "YerelLer Penceresi")

    **YerelLer** penceresi, geçerli kapsamda olan, yani [geçerli](https://www.wikipedia.org/wiki/Scope_(computer_science))yürütme bağlamındaki değişkenleri gösterir.

::: moniker-end

::: moniker range=">=vs-2022"

Otomatikler **ve** **Yereller** pencereleri, hata ayıklama sırasında değişken değerlerini gösterir. Pencereler yalnızca bir hata ayıklama oturumu sırasında kullanılabilir. **Otomatikler** penceresinde, hata ayıklayıcının olduğu geçerli satırda ve önceki satırda kullanılan değişkenler gösterilir. **Yereller penceresinde** yerel kapsamda tanımlanan değişkenler gösterilir ve bu genellikle geçerli işlev veya yöntemdir.

1. Hata ayıklayıcı duraklatılmışken, kod **düzenleyicisinin** en altındaki Otomatikler penceresini açın.

    Otomatikler **penceresi kapalı** ise **Ctrl+D, A** veya  menü çubuğundan Hata > **ayıkla'Windows** > **Otomatikler'i** seçin.

1. Hata ayıklayıcı duraklatılmış şekilde, **Otomatikler** penceresinin yanındaki sekmede Yereller **penceresini** görüntüleyin.

    Yereller **penceresi kapalı** ise **Ctrl+D, L** veya  YerelLer'de Hata > **Ayıkla'Windows** > **seçin.**

1. Yereller **penceresinde,** dizi öğelerini `letters` ve değerlerini görmek için değişkeni genişletin.

     :::image type="content" source="media/vs-2022/get-started-locals-window.png" alt-text="2022'de yereller penceresinin ekran Visual Studio ve 'letters' dizisi değişkeni genişletilmiş.":::

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
