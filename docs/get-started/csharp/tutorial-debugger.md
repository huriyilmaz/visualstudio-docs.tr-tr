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
ms.openlocfilehash: 5a6bc40fc19dd36c7cfae35e33b94c6c27a348e5
ms.sourcegitcommit: bfae1f88c278835e26f3200cfced769be3191fc4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2021
ms.locfileid: "132535314"
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

1. **Ek bilgi** penceresinde, **Framework** açılan menüsünde **.net 6,0** ' ın seçildiğinden emin olun ve ardından **Oluştur**' u seçin.

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

1. **F5** tuşuna basın veya ![' hata ayıklamayı Başlat ' düğmesinin ekran görüntüsünü](../../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") **başlatın** ., uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../csharp/media/get-started-set-breakpoint.gif)

    Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

     Uygulama henüz çalışmıyorsa, **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır. Aksi halde, **F5** uygulamayı bir sonraki kesme noktasına çalıştırmaya devam eder.

    Kod satırını veya kodun ayrıntılı olarak incelemek istediğiniz bölümünü bildiğiniz kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../../debugger/using-breakpoints.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. `for` `Main` İşlevin döngüsünde, aşağıdaki kod satırının sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktasını ayarladığınız yerde kırmızı bir daire görünür.

    :::image type="content" source="media/vs-2022/dbg-tour-breakpoint.png" alt-text="Visual Studio 2022 ' de bir kesme noktasının ekran görüntüsü."::: 

    Kesme noktaları, güvenilir bir hata ayıklama için önemli bir özelliktir. değişkenlerin değerlerine veya bellek davranışına bakabilmeniz veya kodun bir dalının çalıştırılıp çalıştırılmadığını bilmeniz için, Visual Studio çalışan kodunuzu duraklatmayı istediğiniz noktaları ayarlayabilirsiniz.

1. Hata ayıklamayı başlatmak için **F5**' i seçin veya Standart araç çubuğunda **hedefi Ayıkla** ' yı seçin veya hata ayıklama araç çubuğunda Hata **ayıklamayı** Başlat düğmesini seçin veya menü çubuğunda hata ayıklamayı Başlat ' **ı seçin**  >   . Uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    :::image type="content" source="media/vs-2022/get-started-set-breakpoint.png" alt-text="Visual Studio 2022 ' nin kod düzenleyicisinde bir kesme noktasını gösteren ekran görüntüsü, kod yürütme kesme noktasında duraklatıldı.":::

    Sarı ok, hata ayıklayıcının duraklatıldığı ifadeye işaret eder. Uygulama yürütmesi, deyimin henüz yürütülmemiş olduğu bir noktada duraklatılır.

    Uygulama çalışmadığı zaman, **F5** , ilk kesme noktasına ulaşıncaya kadar uygulamayı çalıştıracak hata ayıklayıcıyı başlatır. Uygulama bir kesme noktasında duraklatıldığında, **F5** bir sonraki kesme noktasına ulaşıncaya kadar uygulamayı çalıştırmaya devam edecektir.

    Ayrıntılı olarak incelemek istediğiniz kod satırını veya bölümünü bildiğiniz kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında daha fazla bilgi için bkz. [kesme noktaları kullanma](../../debugger/using-breakpoints.md).

::: moniker-end

## <a name="navigate-code-and-inspect-data-by-using-data-tips"></a>Veri ipuçlarını kullanarak kodda gezinin ve verileri inceleyin

::: moniker range="<=vs-2019"

Çoğu durumda buradaki klavye kısayollarını kullanıyoruz. Bu, uygulamanızı hata ayıklayıcıda yürütmek için iyi bir yoldur (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. İfadede duraklalarken `name += letters[i]` , değişkenin üzerine gelin `letters` ve varsayılan değerini, dizideki ilk öğenin değerini görürsünüz `char[10]` .

     Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en yararlı özelliklerinden biridir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir zamanda sahip olmalarını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

     ![Hata ayıklayıcının ' name + = harfler [I] ' deyimindeki durakladığı ekran görüntüsü.](../csharp/media/get-started-view-data-tip.png)

1. Sonra, değişkenin üzerine gelin `name` ve geçerli değerini boş bir dize olarak görürsünüz.

1. Yöntem çağrısına ilerlemek için **F10** tuşuna basın (veya **hata ayıklama > Adımlama**' i seçin) `SendMessage` ve ardından **F10** bir kez daha tuşuna basın.

     F10 hata ayıklayıcıyı, uygulama kodunuzda işlevlere veya yöntemlere adımla bir sonraki ifadeye ilerletir (kod yine de çalıştırılır). Yöntem çağrısında F10 tuşuna basarak `SendMessage` , için uygulama kodu atlandık `SendMessage` (Bu, şu anda ilgilentik olabilir).

1. Bir  kez döngü aracılığıyla  > birkaç kez yineleyebilir `for` , kesme noktasında tekrar duraklatarak ve `name` değerini denetlemek için her seferinde üzerine gelindiğinde, F10 tuşuna basın (veya hata ayıklama adımından).

     ![Visual Studio hata ayıklayıcının, F10 tuşuna basarak "adımla" ve hata ayıklama sırasında bir döngüde yineleme etkisini gösteren animasyonlu bir ekran görüntüsü.](../csharp/media/get-started-data-tip.gif)

     Değişkenin değeri, döngü her tekrarında değişir ve `for` değerlerini, sonra, vb. gösterir `f` `fr` `fre` . Bu senaryoda hata ayıklayıcıyı daha hızlı bir şekilde ilerletmek için **F5** tuşuna basabilir (veya **Hata Ayıkla**  >  **devam et**' i seçebilirsiniz), bunun yerine bir sonraki ifade yerine kesme noktasına ilerletebilirsiniz.

     Genellikle, hata ayıklarken, değişkenleri üzerinde özellik değerlerini denetlemeye yönelik hızlı bir yol isteyeceksiniz ve bu değerlerin depolanmasını beklediğinizi ve veri ipuçları bunu yapmanın iyi bir yoludur.

1. Metodun döngüsünde hala duraklatıldıktan `for` `Main` sonra, yöntem çağrısında duraklamadan **F11** tuşuna basın (veya **Hata Ayıkla > adımla**' yı seçin) `SendMessage` .

     Şu kod satırında olmalısınız:

     `SendMessage(name, a[i]);`

1. Yönteme adım eklemek için bir kez daha **F11** tuşuna basın `SendMessage` .

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     ![' SendMessage ' yöntemindeki yürütme işaretçisinin ekran görüntüsü.](../csharp/media/get-started-f11.png "F10 adımla")

     F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md)).

     Yöntemi incelemeyi bitirdiğinizde `SendMessage` ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **SHIFT** + **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     Yöntem `for` çağrısında duraklamış olması için, yöntemde döngüde geri dönüş yapmanız gerekir `Main` `SendMessage` . Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../../debugger/navigating-through-code-with-the-debugger.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. İfadede duraklalarken `name += letters[i]` , `letters` dizi boyutunu ve öğe türünü gösteren bir veri ipucu görmek için değişkenin üzerine gelin `char[10]` .

    > [!NOTE]
    > Hata ayıklayıcının en faydalı özelliklerinden biri bir değişkeni İnceleme olanağıdır. Genellikle, bir sorunu ayıklamaya çalışırken, değişkenlerin belirli bir zamanda beklediğinizi belirten değerlere sahip olup olmadığını bulmaya çalışıyorsunuz. Veri ipuçlarını görüntüleme, bunu denetlemek için iyi bir yoldur.

1. `letters`Tüm dizi öğelerini ve bunların değerlerini görüntülemek için değişkeni genişletin.

    :::image type="content" source="media/vs-2022/get-started-view-data-tip.png" alt-text="Visual Studio 2022 ' de, ' harfler ' dizi değişkeninin öğe değerlerini gösteren bir hata ayıklayıcı veri ipucu ekran görüntüsü.":::

1. `name`Boş bir dize olan geçerli değerini görmek için değişkenin üzerine gelin.

1. Hata ayıklayıcıyı sonraki ifadeye ilerletmek için **F10**' i seçin veya hata ayıklama araç çubuğunda **adım adım** düğmesini seçin ya da menü çubuğunda **hata ayıklama**  >  **adımı** ' nı seçin. Yöntem çağrısının ötesine geçmek için **F10** iki kez daha seçin `SendMessage` . 

    **F10** , kod ya da yöntemlere adımla hata ayıklayıcıyı ilerletir, ancak kodu hala yürütülür. Bu şekilde, `SendMessage` Şu anda ilgilendiğimiz yöntemde kodda hata ayıklamayı atladık.

1. `for`Döngüyü birkaç kez yinelemek Için **F10** ' i tekrar tekrar seçin. Her döngü yinelemesi sırasında kesme noktasında duraklatın ve sonra `name` veri ipucunda değerini denetlemek için değişkenin üzerine gelin.

    :::image type="content" source="media/vs-2022/get-started-data-tip.png" alt-text="Visual Studio 2022 ' de hata ayıklayıcı veri ipucunun ekran görüntüsü ' name ' değişkeninin dize değerini gösterir.":::

    Değişkenin değeri, döngü her tekrarında değişir ve `for` değerlerini, sonra, vb. gösterir `f` `fr` `fre` . Hata ayıklayıcıyı daha hızlı bir şekilde ilerletmek için, bunun yerine **F5** ' i seçin. Bu, sonraki bildiri yerine kesme noktasına ilerletir.

1. Metodun döngüsünde durakladığında `for` `Main` , **F11**' ı seçin veya hata ayıklama araç çubuğundan **adımla** düğmesine basın veya menü çubuğunda **Hata Ayıkla** > **adımla** ' i seçerek `SendMessage` yöntem çağrısına erişin.

     Hata ayıklayıcı bu kod satırında duraklamalıdır:

     `SendMessage(name, a[i]);`

1. Yöntemine dönmek için `SendMessage` **F11** ' i yeniden seçin.

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     :::image type="content" source="media/vs-2022/get-started-f11.png" alt-text="' SendMessage ' yöntemi içindeki hata ayıklayıcının yürütme işaretçisini gösteren ekran görüntüsü.":::

     **F11** , kodunuzun yürütme akışını daha ayrıntılı bir şekilde incelemenize yardımcı olur. Yöntem çağrısından bir yönteme geçmek için **F11**' i seçin. Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan yöntemlere adımlamayı atlar. Kullanıcı olmayan koddan hata ayıklama hakkında bilgi edinmek için bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md).

     Yöntemi hata ayıklamayı tamamladıktan sonra `SendMessage` , yönteminin döngüsüne geri dönmek için hazırsınız demektir `for` `main` .

1. Yöntemi bırakmak için `SendMessage` **SHIFT + F11**' i seçin veya hata ayıklama araç çubuğundaki **Step Out** (Hata Ayıkla) düğmesini seçin veya menü çubuğunda **Hata Ayıkla** seçeneğini belirleyin >  .

     **Adımla** , uygulama yürütmeye devam eder ve geçerli yöntem veya işlev dönene kadar hata ayıklayıcıyı ilerletir.

     Yöntemin döngüsünde sarı işaretçiyi geri görürsünüz `for` `Main` ve `SendMessage` Yöntem çağrısında duraklatılabilir. Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../../debugger/navigating-through-code-with-the-debugger.md).

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Çalıştırmak için Çalıştır 'ı kullanarak kodu gezin

::: moniker range="<=vs-2019"

1. Kesme noktasına yeniden ilerlemek için **F5** ' i seçin.

1. Kod Düzenleyicisi 'nde aşağı kaydırın ve `Console.WriteLine` `SendMessage` ![' tıklamak üzere Çalıştır ' düğmesinin](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") düğmesine **tıklayana** kadar, yöntemin içindeki yöntemin üzerine gelin. Sol tarafta görüntülenir. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![' Tıklama için Çalıştır ' düğmesinin ekran görüntüsü.](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > **Tıklama Için Çalıştır düğmesi '** de yenidir [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Yeşil ok düğmesini görmüyorsanız, hata ayıklayıcıyı doğru yere ilerletmek için bu örnekte **F11** kullanın.)

1. ![' Tıklamanız Için Çalıştır ' düğmesinin](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")düğmesine **tıklayarak Çalıştır** ' a tıklayın.

    Hata ayıklayıcı `Console.WriteLine` yöntemine ilerler.

    Bu düğme kullanıldığında geçici bir kesme noktası ayarlamaya benzer. **' I tıklatarak** , uygulama kodunun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır (herhangi bir açık dosyaya tıklayabilirsiniz).

::: moniker-end

::: moniker range=">=vs-2022"

1. Kesme noktasına yeniden ilerlemek için **F5** ' i seçin.

1. Kod Düzenleyicisi 'nde, `Console.WriteLine` `SendMessage` **tıklama düğmesine Çalıştır** düğmesi solda görüntülenene kadar yöntemindeki yöntem çağrısının üzerine gelin. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

    :::image type="content" source="media/vs-2022/get-started-run-to-click.png" alt-text="Visual Studio 2022 ' de ' tıklama için çalıştır ' düğmesini gösteren ekran görüntüsü.":::

1. **Tıklama Için Çalıştır** düğmesini seçin. Alternatif olarak, imlecinizin `Console.WriteLine` Ifadesinde **CTRL + F10**' i seçin. Ya da yöntem çağrısına sağ tıklayın `Console.WriteLine` ve bağlam menüsünden **Imlece Çalıştır** ' ı seçin.

    Hata ayıklayıcı `Console.WriteLine` yöntem çağrısına ilerler.

    **Tıklama Için Çalıştır** düğmesinin kullanılması, geçici bir kesme noktası ayarlamaya benzer ve açık bir dosyada uygulama kodunuzun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır.

::: moniker-end

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlıca yeniden başlatın

::: moniker range="<=vs-2019"

![' Uygulamayı yeniden Başlat ' düğmesinin](../../debugger/media/dbg-tour-restart.png "RestartApp") **yeniden başlatma** görüntüsü ' ne tıklayın. düğmesini ayıklayın (**CTRL**  +  **SHIFT**  +  **F5**).

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

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

     ![Visual Studio 'teki Yereller penceresinin ekran görüntüsü.](../csharp/media/get-started-locals-window.png "Yereller penceresi")

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
