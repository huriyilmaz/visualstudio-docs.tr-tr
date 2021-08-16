---
title: 'Öğretici: C# kodunda hata ayıklama'
description: Visual Studio hata ayıklayıcının özelliklerini ve hata ayıklayıcıyı nasıl başlatacağınızı, kodda adım adım ilerleyeceğinizi ve bir C# uygulamasındaki verileri incelemeyi öğrenin.
ms.custom: debug-experiment, vs-acquisition, get-started
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
ms.openlocfilehash: 34d14c77eff7166373bee825720e46251ab9bc79f8628d4eb5a1adbf7d0a6a3a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374229"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C# kodunun hatalarını ayıklamayı öğrenin

bu makalede, adım adım izlenecek yol Visual Studio hata ayıklayıcının özellikleri tanıtılmaktadır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md). Uygulamanızda *hata ayıklarken*, genellikle uygulamanızı hata ayıklayıcı eklenmiş şekilde çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı kodun çalışırken ne yaptığını görmek için birçok yol sunar. Kodunuzda saklanan değerlere bakabilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerlerin ne zaman değişenleri görebileceğiniz, kodunuzun yürütme yolunu inceleyebileceğiniz, kodun bir dalında çalışıp çalışmadığını ve bu şekilde devam edebilirsiniz. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce [mutlak yeni başlayanlar Için hata ayıklama](../../debugger/debugging-absolute-beginners.md) işlemini okumak isteyebilirsiniz.

tanıtım uygulaması C# olsa da, özelliklerin çoğu C++, Visual Basic, F #, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F # düzenle ve devam et ' i desteklemez. F # ve JavaScript, **oto** penceresini desteklemez). Ekran görüntüleri C# ' de bulunur.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktalarını isabet edin.
> * Hata Ayıklayıcıdaki kodu adım adım ilerme komutlarını öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı Windows 'da değişkenleri İnceleme
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

Visual Studio 2019 yüklü ve **.net Core platformlar arası geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 yüklü ve **.net Core platformlar arası geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir .NET Core konsol uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

3. sol bölmedeki **yeni Project** iletişim kutusunda **C#**' ı genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından Proje *Get-Started-hata ayıklama* adını adlandırın.

     **konsol uygulaması (.net Core)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin.

     Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra .NET Core **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması için C# şablonunu seçin](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. sonra, Visual Studio Yükleyicisi **.net Core platformlar arası geliştirme** iş yükünü seçin.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *getstarteddebugging* yazın veya girin. Ardından **İleri**' yi seçin.

1. Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

1. *Program. cs*' de, tüm varsayılan kodu bunun yerine aşağıdaki kodla değiştirin:

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

1. Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata **Ayıkla > Başlat**) ![veya hata](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

     **F5** uygulama işlemine eklenen hata ayıklayıcı ile uygulamayı başlatır, ancak şimdi kodu incelemek için özel bir şey yapmadık. Bu nedenle uygulama yalnızca konsol çıkışını görür ve görürsünüz.

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

2. Kırmızı durma ![hata ayıklamayı Durdur](../../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") düğmesine (**SHIFT**  +  **F5**) basarak hata ayıklayıcıyı durdurun.

3. Konsol penceresinde bir tuşa basarak konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

1. `for` `Main` İşlevin döngüsünde, aşağıdaki kod satırının sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktasını ayarladığınız yerde kırmızı bir daire ![kesme noktası](../../debugger/media/dbg-breakpoint.png "Kesme noktası") belirir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede askıya alınacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

2. **F5** tuşuna basın veya hata **ayıklamayı Başlat** ![düğmesine basın](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat"), uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../csharp/media/get-started-set-breakpoint.gif)

    Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

     Uygulama henüz çalışmıyorsa, **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır. Aksi halde, **F5** uygulamayı bir sonraki kesme noktasına çalıştırmaya devam eder.

    Kod satırını veya kodun ayrıntılı olarak incelemek istediğiniz bölümünü bildiğiniz kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../../debugger/using-breakpoints.md).

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Veri ipuçlarını kullanarak kodda gezinin ve verileri inceleyin

Çoğu durumda buradaki klavye kısayollarını kullanıyoruz. Bu, uygulamanızı hata ayıklayıcıda yürütmek için iyi bir yoldur (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. İfadede duraklalarken `name += letters[i]` , değişkenin üzerine gelin `letters` ve varsayılan değerini, dizideki ilk öğenin değerini görürsünüz `char[10]` .

     Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en yararlı özelliklerinden biridir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir zamanda sahip olmalarını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

     ![' name + = harfler [I] ' ifadesiyle vurgulanan Visual Studio hata ayıklayıcının ekran görüntüsü ve harfler dizisindeki öğeleri gösteren açılan liste.](../csharp/media/get-started-view-data-tip.png)

1. Sonra, değişkenin üzerine gelin `name` ve geçerli değerini boş bir dize olarak görürsünüz.

1. Yöntem çağrısına ilerlemek için **F10** tuşuna basın (veya **hata ayıklama > Adımlama**' i seçin) `SendMessage` ve ardından **F10** bir kez daha tuşuna basın.

     F10 hata ayıklayıcıyı, uygulama kodunuzda işlevlere veya yöntemlere adımla bir sonraki ifadeye ilerletir (kod yine de çalıştırılır). Yöntem çağrısında F10 tuşuna basarak `SendMessage` , için uygulama kodu atlandık `SendMessage` (Bu, şu anda ilgilentik olabilir).

1. Bir  kez döngü aracılığıyla   >  birkaç kez yineleyebilir `for` , kesme noktasında tekrar duraklatarak ve `name` değerini denetlemek için her seferinde üzerine gelindiğinde, F10 tuşuna basın (veya hata ayıklama adımından).

     ![Visual Studio hata ayıklayıcının, F10 tuşuna basarak "adımla" ve hata ayıklama sırasında bir döngüde yineleme etkisini gösteren animasyonlu bir ekran görüntüsü.](../csharp/media/get-started-data-tip.gif)

     Değişkenin değeri, döngü her tekrarında değişir ve `for` değerlerini, sonra, vb. gösterir `f` `fr` `fre` . Bu senaryoda hata ayıklayıcıyı daha hızlı bir şekilde ilerletmek için **F5** tuşuna basabilir (veya **Hata Ayıkla**  >  **devam et**' i seçebilirsiniz), bunun yerine bir sonraki ifade yerine kesme noktasına ilerletebilirsiniz.

     Genellikle, hata ayıklarken, değişkenleri üzerinde özellik değerlerini denetlemeye yönelik hızlı bir yol isteyeceksiniz ve bu değerlerin depolanmasını beklediğinizi ve veri ipuçları bunu yapmanın iyi bir yoludur.

1. Metodun döngüsünde hala duraklatıldıktan `for` `Main` sonra, yöntem çağrısında duraklamadan **F11** tuşuna basın (veya **Hata Ayıkla > adımla**' yı seçin) `SendMessage` .

     Şu kod satırında olmalısınız:

     `SendMessage(name, a[i]);`

1. Yönteme adım eklemek için bir kez daha **F11** tuşuna basın `SendMessage` .

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     ![Koda geçmek için F11 kullanın](../csharp/media/get-started-f11.png "F10 Içine Adımla")

     F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md)).

     Yöntemi incelemeyi bitirdiğinizde `SendMessage` ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **SHIFT**  +  **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     yöntem çağrısında `for` duraklatılmış `Main` yönteminde döngüsüne geri `SendMessage` dönmeniz gerekir. Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Tıklarken Çalıştır'ı kullanarak kodda gezinme

1. Kesme **noktası tekrar ilerlemek** için F5 tuşuna basın.

1. Kod düzenleyicisinde aşağı kaydırın ve sol tarafta tıklanacak şekilde çalıştır yeşil renkli Tıklanacak Şekilde Çalıştır düğmesi görünene kadar `Console.WriteLine` `SendMessage` yönteminde yönteminin üzerine gelin.  ![](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

     ![Tıklarken Çalıştır özelliğini kullanma](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > Tıklayarak **Çalıştır düğmesi** içinde [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] yenidir. (Yeşil ok düğmesini görmüyorsanız hata ayıklayıcıyı doğru yere ilerlemek için bu örnekte **F11** kullanın.)

2. **Tıklarken Çalıştır düğmesine Tıklayarak** ![Çalıştır'a tıklayın.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcısı yöntemine `Console.WriteLine` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklamak için** Çalıştır, uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı Yeniden](../../debugger/media/dbg-tour-restart.png "RestartApp") Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**).

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı, daha önce döngü içinde ayaranı kesme noktası sırasında yeniden `for` durur.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

1. Kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

    Kapalı ise, Hata Ayıkla'ya ve Otomatikler'e göre hata **ayıkla'Windows**  >    >  **açın.**

    Otomatikler **penceresinde** değişkenleri ve bunların geçerli değerini görebilirsiniz. Otomatikler **penceresinde** geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (Dile özgü davranış için belgeleri kontrol edin).

1. Ardından, Otomatikler **penceresinin** yanındaki sekmede Yereller **penceresine** bakın.

1. Içerdiği `letters` öğeleri göstermek için değişkeni genişletin.

     ![YerelLer Penceresinde değişkenleri inceleme](../csharp/media/get-started-locals-window.png "YerelLer Penceresi")

    **YerelLer** penceresi, geçerli kapsamda olan, yani [geçerli](https://www.wikipedia.org/wiki/Scope_(computer_science))yürütme bağlamındaki değişkenleri gösterir.

## <a name="set-a-watch"></a>Saat ayarlama

1. Ana kod düzenleyicisi penceresinde değişkenine sağ tıklayın ve İzleme `name` **Ekle'yi seçin.**

    Kod  düzenleyicisinin alt kısmında İzleme penceresi açılır. İzleme penceresi **kullanarak** göz tutmak istediğiniz bir değişken (veya ifade) belirtebilirsiniz.

    Artık değişkende bir izleme kümemiz var ve hata ayıklayıcıda ilerlerken `name` değerinin değişti olduğunu görüyorsunuz. Diğer değişken pencerelerinin aksine, **İzle** penceresi her zaman izlediğiniz değişkenleri gösterir (kapsam dışındayken bunlar gri renkte olur).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleme

1. Döngüde duraklatılmışken, varsayılan olarak sağ alt bölmede açık `for` olan Çağrı Yığını penceresine tıklayın. 

    Kapalı ise, Çağrı Yığınında Hata Ayıkla'yı seçerek hata **ayıklayıcıda**  >  **duraklatılmış Windows**  >  **açın.**

2. Yönteminde hata ayıklayıcının duraklatılmış olduğunu görene kadar **F11'e** birkaç kez `SendMessage` tıklayın. Çağrı Yığını **penceresine** bakın.

    ![Çağrı yığınını inceleme](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Üst satır geçerli işlevi (bu `SendMessage` uygulamanın yöntemi) gösterir. İkinci satırda `SendMessage` yönteminden `Main` çağrıldı ve bu şekilde devam etti.

   > [!NOTE]
   > Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yol sağlar.

    Bir kod satırına çift tıklar ve bu koda göz atabilir ve hata ayıklayıcı tarafından denetlenen geçerli kapsamı da değiştirir. Bu eylem hata ayıklayıcıyı ilerleten bir eylem değildir.

    Başka şeyler yapmak için Çağrı Yığını penceresinden sağ **tıklama** menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları eklemek, İmleçte Çalıştır'ı kullanarak hata ayıklayıcıyı **ilerletin** ve kaynak kodu incelemeye gidebilirsiniz. Daha fazla bilgi için, [bkz. How to: Examine the Call Stack](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

1. yöntemini **çalıştırmak için F11'e** iki kez `Console.WriteLine` basın.

1. Hata ayıklayıcı yöntem çağrısında duraklatılmış şekilde, fareyle sol tarafta sarı oku (yürütme işaretçisi) alıp sarı oku bir satır yukarı, geri `SendMessage` doğru hareket `Console.WriteLine` ettirin.

1. **F11 tuşuna basın.**

    Hata ayıklayıcısı yöntemini yeniden `Console.WriteLine` çalıştırıyor (konsol penceresi çıkışında bunu görüyorsunuz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etmek veya hata ayıklayıcıyı yeniden başlatmadan kodu yeniden çalıştırma gibi şeyler yapabiliriz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmalısınız ve araç ipucunda bir uyarı görüyorsunuz. Başka uyarılar da görebilir. İşaretçiyi hareket ettiren uygulama önceki bir uygulama durumuna geri döndürülebilir.

1. Uygulamayı **çalıştırmaya devam** etmek için F5 tuşuna basın.

    Tebrikler, bu öğreticiyi tamamladıktan sonra!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklayıcıyı başlatmayı, kodu adım adım incelemeyi ve değişkenleri incelemeyi öğrendiniz. Daha fazla bilgi için bağlantılarla birlikte hata ayıklayıcı özelliklerine üst düzey bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
