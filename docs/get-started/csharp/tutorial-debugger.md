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
ms.openlocfilehash: b872043a5e8b200f6f5678857aa1c4e67c53945b
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133257055"
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

Visual Studio 2022 yüklü ve **.net masaüstü geliştirme** iş yüküne sahip olmanız gerekir.

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

1. Önerilen hedef Framework 'ü (.NET Core 3,1 (uzun süreli destek)) veya .NET 5,0 (geçerli) seçin ve ardından **Oluştur**' u seçin.

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

1. **Ek bilgi** penceresinde, **Framework** açılan menüsünde **.net 6,0 (uzun vadeli destek)** seçildiğinden emin olun ve ardından **Oluştur**' u seçin.

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

1. **F5** tuşuna basın (hata ayıklama **> başlatın**) veya ![' hata ayıklamayı Başlat ' düğmesinin görüntü](../../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") **hata ayıklamayı Başlat** düğmesi. Hata Ayıkla araç çubuğunda.

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

1. ![' Hata ayıklamayı Durdur ' düğmesinin](../../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") kırmızı durma görüntüsüne basarak hata ayıklayıcıyı durdurun. düğme (**SHIFT**  +  **F5**).

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

    ![Kesme noktasının kırmızı daire resmi.](../../debugger/media/dbg-breakpoint.png "Ilı") kesme noktasını ayarladığınız yerde görüntülenir.

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

    Kesme noktası ayar yakın bir yerde kırmızı bir daire görünür.

    :::image type="content" source="media/vs-2022/dbg-tour-breakpoint.png" alt-text="Visual Studio 2022'de kesme noktası ekran görüntüsü."::: 

    Kesme noktaları, güvenilir hata ayıklamanın temel bir özelliğidir. Değişkenlerin değerlerine veya bellek davranışına bakarak veya bir kod dalını çalıştırıp çalıştırmama konusunda bilgi almak için Visual Studio'nin çalışan kodunuzu duraklatmanızı istediğiniz kesme noktaları ayarlayın.

1. Hata ayıklamayı başlatmak için **F5'i** seçin veya Standart araç çubuğundan  Hata Ayıklama Hedefi düğmesini seçin ya da Hata Ayıklama araç çubuğunda Hata Ayıklamayı Başlat düğmesini seçin veya menü çubuğundan Hata AyıklamaYı Başlat'ı   >   seçin. Uygulama başlatılır ve hata ayıklayıcı, kesme noktası ayarlayıcısının ayar bulunduğu kod satırına çalışır.

    :::image type="content" source="media/vs-2022/get-started-set-breakpoint.png" alt-text="Visual Studio 2022'nin kod düzenleyicisinde kesme noktası gösteren ve kesme noktası sırasında kod yürütmenin duraklatılmış olduğu ekran görüntüsü.":::

    Sarı ok, hata ayıklayıcının duraklatılmış olduğu deyimini belirtir. Uygulama yürütme aynı noktada duraklatılır ve deyimi henüz yürütülmedi.

    Uygulama çalışmadığı zaman **F5** hata ayıklayıcıyı başlatacak ve ilk kesme noktası ulaşana kadar uygulamayı çalıştıracak. Uygulama bir kesme noktası üzerinden duraklatılırsa **F5,** bir sonraki kesme noktası ulaşana kadar uygulamayı çalıştırmaya devam eder.

    Kesme noktaları, ayrıntılı olarak incelemek istediğiniz kod satırı veya bölümünü biliyorken yararlı bir özelliktir. Koşullu kesme noktaları gibi ayar yalnızca farklı kesme noktası türleri hakkında daha fazla bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

::: moniker-end

## <a name="navigate-code-and-inspect-data-by-using-data-tips"></a>Veri ipuçlarını kullanarak kodda gezinme ve verileri inceleme

::: moniker range="<=vs-2019"

Genellikle burada klavye kısayollarını kullanırız çünkü bu, uygulamanızı hata ayıklayıcısında yürütmeyi hızlı bir şekilde yürütmenin iyi bir yolu olduğundan (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. deyiminde duraklatılmışken değişkeninin üzerine gelin ve bunun varsayılan değeri olan dizideki ilk `name += letters[i]` `letters` öğenin değerini `char[10]` görüyorsunuz.

     Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerinden birisidir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

     !['name+= letters[I]' deyiminde duraklatılmış olan hata ayıklayıcının ekran görüntüsü.](../csharp/media/get-started-view-data-tip.png)

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Yöntem **çağrısına ilerlemek için F10** **tuşuna basın**(veya > AdımLa) hata ayıkla'ya basın ve `SendMessage` ardından **F10'a** bir kez daha basın.

     F10, uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı bir sonraki deyime ilerletmektedir (kod yürütülmektedir). Yöntem çağrısında F10 tuşuna basarak, uygulama kodunu atlamıştık (bu şu `SendMessage` `SendMessage` anda ilgilenmediğimiz bir şey olabilir).

1. Döngüde birkaç kez  tekrarlama, kesme noktası üzerinde yeniden duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F10'a** (veya Adım Adım Hata Ayıklama) birkaç kez >  `for` `name` basın.

     ![Hata Ayıklayıcısı'Visual Studio F10'a "Adım At" tuşuna basmanın ve hata ayıklama sırasında döngüde tekrarlamanın etkisini gösteren animasyonlu ekran görüntüsü.](../csharp/media/get-started-data-tip.gif)

     Değişkenin değeri, döngüde her yineleme ile birlikte değişir ve ardından `for` , ve gibi değerleri `f` `fr` `fre` gösterir. Bu senaryoda hata ayıklayıcıyı döngüde daha hızlı ilerlemek için  **F5** tuşuna basabilirsiniz (veya Devam Et'i seçerek) bir sonraki deyim yerine kesme noktası  >  üzerinden ilerleyin.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin, depolamasını beklediğiniz değerleri depolayarak depolamalarının gerekip gerek olmadığını ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek için hızlı bir yol gerekir.

1. yönteminde döngüde duraklatılmışken, yöntem çağrısında duraklatana kadar F11 tuşuna basın (veya Hata ayıkla > `for` `Main` **Adımla)**  `SendMessage` seçin.

     Şu kod satırına bakabilirsiniz:

     `SendMessage(name, a[i]);`

1. yöntemine **adımını atarak F11'e** bir kez daha `SendMessage` basın.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     !['SendMessage' yönteminde yürütme işaretçisinin ekran görüntüsü.](../csharp/media/get-started-f11.png "F10 Içine Adımla")

     F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../../debugger/just-my-code.md)

     Yöntemini incelemeyi tamamlaya kadar yöntemin dışında kalmak ancak hata `SendMessage` ayıklayıcıda kalmak istediğinizi diyelim. Bunu Yapmak için Dışarı **Adımla komutunu kullanın.**

1. Shift  + **F11 tuşuna** basın (veya **> Adım Atarak) hata ayıkla'ya basın.**

     Bu komut, geçerli yöntem veya işlev geri dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

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

1. Döngüde birkaç kez `for` yinelenirken **tekrar tekrar F10'ı** seçin. Her döngü yinelemesi sırasında kesme noktası sırasında duraklatın ve ardından veri ipucunda değerini `name` kontrol etmek için değişkenin üzerine gelin.

    :::image type="content" source="media/vs-2022/get-started-data-tip.png" alt-text="'name' değişkeninin dize değerini gösteren Visual Studio 2022'de hata ayıklayıcısı veri ipucu ekran görüntüsü.":::

    Değişkenin değeri, döngüde her yineleme ile birlikte değişir ve ardından `for` , ve gibi değerleri `f` `fr` `fre` gösterir. Hata ayıklayıcıyı döngüde daha hızlı ilerlemek için **F5'i** seçin. Bu seçim sonraki deyim yerine kesme noktanıza ilerler.

1. Yöntemin döngüsünde duraklatılmışken `for` `Main`   **F11'i** seçin veya Hata Ayıklama araç çubuğundan Adımla düğmesini seçin veya yöntem çağrısına ulaşana kadar menü çubuğundan Hata Ayıklama Adımını Ayıkla'ya >  `SendMessage` tıklayın.

     Hata ayıklayıcısı şu kod satırına duraklatılmış olması gerekir:

     `SendMessage(name, a[i]);`

1. yöntemine adımını `SendMessage` eklemek için **F11'i yeniden** seçin.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     :::image type="content" source="media/vs-2022/get-started-f11.png" alt-text="'SendMessage' yönteminde hata ayıklayıcının yürütme işaretçisini gösteren ekran görüntüsü.":::

     **F11,** kodunuzun yürütme akışını daha ayrıntılı incelemenize yardımcı olur. Yöntem çağrısından bir yönteme adım eklemek için **F11'i seçin.** Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan yöntemlere adımlamayı atlar. Kullanıcı olmayan kodda hata ayıklama hakkında bilgi edinmek için bkz. [Yalnızca kendi kodum.](../../debugger/just-my-code.md)

     Yöntemin hata ayıklamasını `SendMessage` tamamladikten sonra yöntemin döngüsüne `for` geri dönmek için hazır `main` oluruz.

1. Yöntemi bırakmak `SendMessage` için **Shift+F11'i** seçin  veya Hata Ayıklama araç çubuğundaki  Adım At düğmesini seçin veya menü çubuğundan Hata Ayıklama > **Adımını** Ayıkla'ya tıklayın.

     **Dışarı Adımla,** uygulama yürütmeyi sürdürür ve geçerli yöntem veya işlev geri dönene kadar hata ayıklayıcıyı ilerleter.

     Yöntemin döngüsünde sarı `for` işaretçiyi, yöntem `Main` çağrısında duraklatılmış `SendMessage` olarak tekrar görüyorsunuz. Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Tıklarken Çalıştır'ı kullanarak kodda gezinme

::: moniker range="<=vs-2019"

1. Kesme noktası tekrar ilerlemek için **F5'i** seçin.

1. Kod düzenleyicisinde aşağı kaydırın ve yeşil renkli Tıklanacak Şekilde Çalıştır düğmesinin Görüntüsü 'Tıklanacak Şekilde Çalıştır' düğmesinin görüntüsüne kadar `Console.WriteLine` `SendMessage` ![yönteminde yönteminin üzerine gelin.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")  sol tarafta görünür. Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

     !['Tıklamak için Çalıştır' düğmesinin ekran görüntüsü.](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > Tıklayarak **Çalıştır düğmesi** içinde [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] yenidir. (Yeşil ok düğmesini görmüyorsanız hata ayıklayıcıyı doğru yere ilerlemek için bu örnekte **F11** kullanın.)

1. **Tıklarken Çalıştır düğmesine** Tıklayın !['Tıklaya Çalıştır' düğmesinin görüntüsü.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Hata ayıklayıcısı yöntemine `Console.WriteLine` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklamak için** Çalıştır, uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

::: moniker-end

::: moniker range=">=vs-2022"

1. Kesme noktası tekrar ilerlemek için **F5'i** seçin.

1. Kod düzenleyicisinde, sol tarafta `Console.WriteLine` Tıklanacak Şekilde Çalıştır düğmesi görünene kadar `SendMessage` **yönteminde yöntem** çağrısının üzerine gelin. Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

    :::image type="content" source="media/vs-2022/get-started-run-to-click.png" alt-text="2022'de 'Tıkla' düğmesini Visual Studio ekran görüntüsü.":::

1. **Tıklarken Çalıştır düğmesini** seçin. Alternatif olarak imlecinizi deyiminde `Console.WriteLine` **Ctrl+F10 tuşlarına basarak da ctrl+F10 tuşlarına basın.** Ya da yöntem çağrısına `Console.WriteLine` sağ tıklayın ve bağlam **menüsünden İmleçte** Çalıştır'ı seçin.

    Hata ayıklayıcısı yöntem `Console.WriteLine` çağrısına ilerler.

    Tıklayarak **Çalıştır düğmesinin** kullanımı geçici bir kesme noktası ayarlamaya benzer ve uygulama kodunuzun görünür bir bölgesi içinde açık bir dosyada hızlıca dolaşabilir.

::: moniker-end

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

::: moniker range="<=vs-2019"

'Uygulamayı **Yeniden** ![Başlat' düğmesinin Yeniden Başlat Görüntüsüne tıklayın.](../../debugger/media/dbg-tour-restart.png "RestartApp") Hata Ayıklama Araç Çubuğundaki düğmesi (**Ctrl**  +  **Shift**  +  **F5**).

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı daha önce döngü içinde ayarladığınız kesme noktasında yeniden durmaktadır `for` .

::: moniker-end

::: moniker range=">=vs-2022"

Uygulamanızı hata ayıklayıcıda başlayarak yeniden çalıştırmak için **CTRL + SHIFT + F5**' i seçin veya hata ayıklama araç çubuğundaki **Yeniden Başlat** düğmesini seçin veya menü çubuğundan yeniden başlatma **hatalarını ayıkla** ' yı seçin >  .

:::image type="content" source="media/vs-2022/dbg-tour-restart-debugging.png" alt-text="Visual Studio 2022 ' nin hata ayıklama araç çubuğundaki ' yeniden başlat ' düğmesinin ekran görüntüsü.":::

**Yeniden başlatma** , hata ayıklayıcıyı durduruyor ve tek bir adımda yeniden başlatır. Hata ayıklayıcı yeniden başlatıldığında, döngü içinde daha önce ayarladığınız kesme noktası olan ilk kesme noktasına çalışır `for` ve ardından duraklatırsınız.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

::: moniker range="<=vs-2019"

1. Kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

    kapatılmışsa, **hata ayıklayıcıda hata ayıkla** > **Windows** > **oto**' yi seçerek açın.

    **Oto** penceresinde, değişkenleri ve bunların geçerli değerlerini görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

1. Ardından, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresine bakın.

1. Değişkenini, `letters` içerdiği öğeleri göstermek için genişletin.

     ![Visual Studio 'teki Yereller penceresinin ekran görüntüsü.](../csharp/media/get-started-locals-window.png "YerelLer Penceresi")

    **Yereller** penceresi, geçerli yürütme bağlamı olan geçerli [kapsamda](https://www.wikipedia.org/wiki/Scope_(computer_science))olan değişkenleri gösterir.

::: moniker-end

::: moniker range=">=vs-2022"

**Oto** ve **Locals** pencereleri, hata ayıklarken değişken değerlerini gösterir. Pencereler yalnızca bir hata ayıklama oturumu sırasında kullanılabilir. **Oto** penceresinde, hata ayıklayıcının ve önceki satırdaki geçerli satırda kullanılan değişkenler gösterilir. **Yereller** penceresi, genellikle geçerli işlev veya yöntem olan yerel kapsamda tanımlanan değişkenleri gösterir.

1. Hata ayıklayıcı duraklatıldığında, kod düzenleyicisinin alt kısmındaki **oto** penceresini görüntüleyin.

    **oto** pencere kapalıysa, **Ctrl + D, A**' yı seçin veya menü çubuğundan **hata ayıkla** > **Windows** > **oto** ' yi seçin.

1. Hata ayıklayıcı hala duraklatıldıktan sonra, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresini görüntüleyin.

    **yereller** penceresi kapalıysa, **Ctrl + D, L** veya  > **Windows** > **Locals**' ı seçin.

1. **Yereller** penceresinde, `letters` dizi öğelerini ve bunların değerlerini görmek için değişkeni genişletin.

     :::image type="content" source="media/vs-2022/get-started-locals-window.png" alt-text="Visual Studio 2022 ' deki Locals penceresinin ekran görüntüsü, ' harfler ' dizi değişkeni genişletilir.":::

**Oto** ve **Yereller** pencereleri hakkında daha fazla bilgi için bkz. [oto ve Yereller pencerelerinde değişkenleri İnceleme](/visualstudio/debugger/autos-and-locals-windows?view=vs-2022&preserve-view=true).

::: moniker-end

## <a name="set-a-watch"></a>İzleme ayarlama

::: moniker range="<=vs-2019"

1. Ana kod Düzenleyicisi penceresinde değişkene sağ tıklayın `name` ve **Gözcü Ekle**' yi seçin.

    **İzleme** penceresi, kod düzenleyicisinin en altında açılır. Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz.

    Artık değişkende bir izleme kümesi vardır `name` ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Gözcü** penceresi her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte gösterilir).

::: moniker-end

::: moniker range=">=vs-2022"

&mdash; **İzleme** penceresine ekleyerek kodda adım adım devam etmek istediğiniz bir değişken ya da bir ifade belirtebilirsiniz.

1. Hata ayıklayıcı duraklatıldığında, değişkene sağ tıklayıp `name` **Gözcü Ekle**' yi seçin.

    **İzleme** penceresi, kod düzenleyicisinin en altında varsayılan olarak açılır.

1. Artık değişken üzerinde bir izleme ayarlamış olduğunuza göre `name` , `name` her `for` döngü yinelemeyle değişken değişikliğinin değerini görmek için kodunuzda adım adım ilerleyin. 

    Diğer değişken pencerelerinin aksine, **Gözcü** penceresi her zaman izlemekte olduğunuz değişkenleri gösterir, ancak kapsam dışı olduklarında gri renkte olur.

**İzleme** penceresi hakkında daha fazla bilgi için bkz. gözcü [Windows ile değişkenleri izleme](/visualstudio/debugger/watch-and-quickwatch-windows?view=vs-2022&preserve-view=true).

::: moniker-end

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

::: moniker range="<=vs-2019"

1. Döngüde durakladığında `for` , varsayılan olarak sağ alt bölmede açık olan **çağrı yığını** penceresine tıklayın.

    kapalıysa, **hata** ayıklayıcı > **Windows** > **çağrı yığını**' nı seçerek hata ayıklayıcıda duraklalarken açın.

1. Yöntemde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın `SendMessage` . **Çağrı yığını** penceresine bakın.

    ![Visual Studio 'de çağrı yığını penceresinin ekran görüntüsü.](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `SendMessage` Bu uygulamadaki yöntemi) gösterilir. İkinci satır, `SendMessage` `Main` yönteminden çağrılan ve bu şekilde devam eden gösterir.

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

    Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu eylem, hata ayıklayıcıyı ilerlemez.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilir, çalışma hata ayıklayıcıyı kullanarak Imleç ' i **Imlece** ilerletebilirsiniz ve kaynak kodu İnceleme ' ye gidebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

::: moniker range=">=vs-2022"

**Çağrı yığını** , yöntemlerin ve işlevlerin çağrıldığı sırayı göstererek uygulamanızın yürütme akışını anlamanıza yardımcı olabilir.

1. Hata ayıklayıcı döngüde duraklatıldığında, `for` kod düzenleyicisinin sağ alt bölmesinde varsayılan olarak açılan **çağrı yığını** penceresini görüntüleyin.

    **çağrı yığını** penceresi kapalıysa, **Ctrl + D, C**' yi seçin veya  >  > menü çubuğundan **çağrı yığını** Windows ayıkla ' yı seçin.

    **Çağrı yığını** penceresinde, geçerli yöntemde sarı işaretçiyi görürsünüz `Main` .

1. Yöntemde hata ayıklayıcı duraklatıldığını görene kadar **F11** tuşunu birkaç kez seçin `SendMessage` .

    **Çağrı yığını** penceresinin üst satırı, yöntemi olan geçerli işlevi gösterir `SendMessage` . İkinci satır `SendMessage` yöntemin yönteminden çağrıldığını gösterir `Main` .

    :::image type="content" source="media/vs-2022/get-started-call-stack.png" alt-text="Visual Studio 2022 ' deki çağrı yığını penceresinin ekran görüntüsü.":::

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı Ides 'Teki hata ayıklama perspektifine benzer.

    **Çağrı yığını** penceresinde, bu kaynak koda gitmek için bir kod satırına çift tıklayabilirsiniz ve bu, hata ayıklayıcı tarafından incelenen geçerli kapsamı değiştirir. Bu eylem, hata ayıklayıcıyı ilerlemez.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilirsiniz, **Imlece Çalıştır**' ı kullanarak hata ayıklayıcıyı ilerletin veya kaynak koduna gidebilirsiniz. 

**Çağrı yığını** hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

::: moniker range="<=vs-2019"

1. Yöntemi çalıştırmak için **F11** tuşuna iki kez basın `Console.WriteLine` .

1. Yöntem çağrısında hata ayıklayıcı duraklatıldığında `SendMessage` , sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve sarı oku bir satır yukarı doğru aşağı taşıyın `Console.WriteLine` .

1. **F11** tuşuna basın.

    Hata ayıklayıcı yöntemini yeniden çalıştırır `Console.WriteLine` (bunu konsol penceresi çıktısında görürsünüz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etme veya hata ayıklayıcıyı yeniden başlatmanıza gerek kalmadan kodu yeniden çalıştırma gibi işlemleri yapabilirsiniz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmanız ve araç ipucunda bir uyarı görmeniz gerekir. Diğer uyarıları da görebilirsiniz. İşaretçinin taşınması uygulamanızı önceki bir uygulama durumuna döndüremezsiniz.

1. Uygulamayı çalıştırmaya devam etmek için **F5** tuşuna basın.

    Tebrikler, bu öğreticiyi tamamlama!

::: moniker-end

::: moniker range=">=vs-2022"

Hata ayıklama sırasında uygulamanızın akışını değiştirmek için yürütme işaretçisini taşıyabilirsiniz.

1. Hata ayıklayıcı, `SendMessage` döngüdeki Yöntem çağrısında duraklatıldığında `for` , yönteme gitmek  `SendMessage` ve `Console.WriteLine` yürüttükten sonra yöntemi taşımak için F11 üç kez seçeneğini belirleyin.

    Hata ayıklayıcı artık metodun son kapanış ayracından duraklatılır `SendMessage` .

1. Sarı ok veya yürütme işaretçisini (sol kenar boşluğunda) almak için fareyi kullanın ve sonra işaretçiyi bir satır yukarı sürükleyin.

    Hata ayıklayıcı artık ifadeye geri gönderilir `Console.WriteLine` .

1. **F11** seçeneğini belirleyin.

    Hata ayıklayıcı yöntemini yeniden çalıştırır `Console.WriteLine` ve konsol penceresi çıktısında yinelenen bir satır görürsünüz.

1. Uygulamayı çalıştırmaya devam etmek için **F5** ' i seçin.

Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etme veya hata ayıklayıcıyı yeniden başlatmanıza gerek kalmadan kodu yeniden çalıştırma gibi işlemleri yapabilirsiniz.

> [!WARNING]
> Bu özelliği dikkatli kullanın. Yürütme işaretçisinin araç ipucunda istem dışı sonuçlarla ilgili bir uyarı görürsünüz. Diğer uyarıları da görebilirsiniz. Yürütme işaretçisinin taşınması uygulamanızı daha önceki bir duruma döndüremezsiniz.

Yürütme akışını değiştirme hakkında daha fazla bilgi için, bkz. [yürütme akışını değiştirmek için Işaretçiyi taşıma](/visualstudio/debugger/navigating-through-code-with-the-debugger?view=vs-2022#BKMK_Set_the_next_statement_to_execute&preserve-view=true).

Tebrikler, bu öğreticiyi tamamlama!

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
