---
title: 'Öğretici: hata C# ayıklama kodu'
description: Kodu adımlayın Visual Studio hata ayıklayıcısını başlatın ve veri İnceleme hakkında bilgi edinin.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 01/31/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2890ee9879d3cab2ff134fdbfcd4edabb36d512
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76923249"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: hata ayıklamayı öğrenin C# kullanarak Visual Studio code

Bu makalede, Visual Studio hata ayıklayıcı adım adım kılavuzda özelliklerini tanıtır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md). Olduğunda, *uygulamanızda hata ayıklama*, hata ayıklayıcısı ekli, uygulamanızın çalıştığını genellikle anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı, kodunuzun ne yaptığını görmek için birçok yol sağlar. çalışırken. Kodunuzda adım adım ve değişkenlerinde depolanan değerleri bakmak, gözcüler ayarlayabilirsiniz değerleri değiştiğinde görmek için değişkenlerini kodunuzun yürütme yolunu inceleyin, bir dal kod çalıştırma, vb. olup olmadığını. Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [yeni başlayanlar için hata ayıklama](../../debugger/debugging-absolute-beginners.md) bu makalede geçmeden önce.

Tanıtım uygulamasını olmasına rağmen C#, özelliklerin çoğunu Visual Basic, C++ için uygun F#, Python, JavaScript ve Visual Studio tarafından desteklenen diğer dillerde (F# Düzenle ve devam et desteklemez. F#ve JavaScript desteği **Otolar** pencere). Ekran görüntüleri C# ' de var.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktaları isabet.
> * Hata ayıklayıcı kodda adım adım için komutları öğrenin
> * Veri ipuçları ve hata ayıklayıcı pencereleri değişkenler inceleyin
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"

Visual Studio 2019 ' nin yüklü olması ve **.NET Core platformlar arası geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 ' nin yüklü olması ve **.NET Core platformlar arası geliştirme** iş yüküne sahip olmanız gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-project"></a>Proje oluştur

İlk olarak, bir .NET Core konsol uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin.

3. Sol bölmedeki **Yeni proje** iletişim kutusunda, öğesini genişletin **C#** ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından Proje *Get-Started-hata ayıklama*adını adlandırın.

     **Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin.

     Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

   Başlangıç penceresi açık değilse **dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil **C#** listesinden seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması C# için şablonu seçin (.NET Core)](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > **Konsol uygulaması (.NET Core)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Sonra, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme** iş yükünü seçin.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *Get-Started-Debugging* yazın veya girin. Ardından **Oluştur**' u seçin.

   Visual Studio yeni projenizi açar.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

1. *Program.cs*' de, tüm varsayılan kodu bunun yerine aşağıdaki kodla değiştirin:

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

1. Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata**Ayıkla > Başlat**) ![veya hata](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

     **F5** başladığında hata ayıklayıcının uygulamayla uygulamaya bağlı işlem ancak biz kodunu incelemek için özel bir şey yapmadınız hemen. Bu nedenle yalnızca uygulamayı yükler ve konsol çıktısı görürsünüz.

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

     Bu öğreticide, biz hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından göz atın ve hata ayıklayıcı göz özelliklerini elde etmek.

2. Kırmızı durma ![hata ayıklamayı Durdur](../../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") düğmesine (**SHIFT** + **F5**) basarak hata ayıklayıcıyı durdurun.

3. Konsol penceresinde bir tuşa basarak konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Bir kesme noktası ayarlayın ve hata ayıklayıcıyı başlatın

1. İçinde `for` , döngü `Main` işlev, aşağıdaki kod satırının sol kenar boşluğunu tıklayarak kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktasını ayarladığınız yerde kırmızı bir daire ![kesme noktası](../../debugger/media/dbg-breakpoint.png "Kesme noktası") belirir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

2. **F5** tuşuna basın veya hata **ayıklamayı Başlat** ![düğmesine basın](../../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat"), uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Ayarlayın ve bir kesme noktası isabet](../csharp/media/get-started-set-breakpoint.png)

    Sarı ok, aynı zamanda aynı noktayı (Bu bildirimi henüz çalıştırılmadı) uygulama yürütmeyi askıya alır, hata ayıklayıcı durduruldu, deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durur. Aksi takdirde, **F5** uygulamayı sonraki kesme noktasına kadar çalışmaya devam eder.

    Kod satırının veya ayrıntılı olarak incelemek istediğiniz kod bölümünün bildiğiniz durumlarda kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Kod adım komutları kullanarak hata ayıklayıcısında gidin

Almak için en iyi yolu olduğundan bu çoğunlukla, klavye kısayollarını Burada, kullandığımız hata ayıklayıcı (komutları parantez içinde gösterilen eşdeğer komutları menüsü gibi) uygulamanız çalıştırma sırasında hızlı.

1. `Main` yönteminde `for` döngüsünde duraklatıldıktan sonra, `SendMessage` yöntem çağrısına ilerlemek için **F11** tuşuna basın (veya **hata ayıklama > adımla**) seçeneğini belirleyin.

     **F11** tuşuna iki kez bastıktan sonra şu kod satırında olmalısınız:

     `SendMessage(name, a[i]);`

2. `SendMessage` metoduna geçmek için bir kez daha **F11** tuşuna basın.

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     ![Koda geçmek için F11 kullanın](../csharp/media/get-started-f11.png "F10 adımla")

     F11 olan **içine adımla** komut ve aynı anda uygulama yürütme bir deyim ilerler. F11 çoğu ayrıntılı yürütme akışı incelemek için iyi bir yoludur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md)).

     `SendMessage` yöntemini incelemeyi bitirdiğinizde ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu kullanarak yapabilirsiniz **Step Out** komutu.

1. Tuşuna **Shift** + **F11** (veya **hata ayıklama > dışarı adımla**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     `Main` yönteminde `for` döngüsünde geri almanız gerekir, `SendMessage` Yöntem çağrısında duraklatılabilir.

3. Yöntem çağrısında duraklalarken **F10** tuşuna basın (veya bir kez **Hata Ayıkla > adımla**).

     ![Kod üzerinde adımla F10 kullanın](../csharp/media/get-started-step-over.png "F10 adımla")

     Hata ayıklayıcının `SendMessage` yöntemine adım yapmadığından bu zamana dikkat edin. **F10** işlevleri veya yöntemleri (kod hala çalışır), uygulama kodunuzda içine Adımlama olmadan, hata ayıklayıcı ilerler. `SendMessage` Yöntem çağrısında **F10** tuşuna basarak ( **F11**yerine), `SendMessage` için uygulama kodu atlandık (Bu, şu anda ilgilentik olabilir). Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Tıkla Çalıştır'ı kullanarak kod gidin

1. Kod Düzenleyicisi 'nde aşağı kaydırın ve `SendMessage` iletisinde `Console.WriteLine` yönteminin üzerine gelin ve sol tarafta görüntülenen düğmesine ![tıklamak](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") üzere **düğme** Çalıştır düğmesine tıklayın. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![Tıklama için Çalıştır özelliğini kullanın](../csharp/media/get-started-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > **Tıklanan satıra kadar Çalıştır** düğmesidir yeni [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. (Yeşil ok düğmesini görmüyorsanız, hata ayıklayıcıyı doğru yere ilerletmek için bu örnekte **F11** kullanın.)

2. **Tıklama düğmesine tıklayarak** ![' ye tıklayın.](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcı `Console.WriteLine` yöntemine ilerler.

    Bu düğmeyi kullanarak geçici bir kesme noktası ayarlayarak benzer. **Tıklanan satıra kadar Çalıştır** (herhangi bir açık dosyayı tıklayabilirsiniz) uygulama kodu görünür bir bölge içinde hızla dolaşma için kullanışlıdır.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlı bir şekilde yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

Bastığınızda **yeniden**, uygulama durdurup hata ayıklayıcı yerine zaman kaydeder. İlk kesme noktasına isabet kodu yürüterek, hata ayıklayıcı duraklatır.

Hata ayıklayıcı daha önce `for` döngüsünde ayarladığınız kesme noktasında yeniden durmaktadır.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları değişkenlerle inceleyin

Değişkenleri incelemek özellik hata ayıklayıcının en kullanışlı özellikler biridir ve bunu yapmanın farklı yolu vardır. Genellikle, hata ayıklama bir sorun açmayı denediğinde, belirli bir zamanda sahip olmalarını beklediğiniz değerleri değişkenleri olup depoladığını kullanıma bulmak çalışıyorsunuz.

1. `name += letters[i]` bildiriminde duraklalarken, `letters` değişkeninin üzerine gelin ve varsayılan değeri, dizideki ilk öğenin değeri olan `char[10]`görürsünüz.

1. Değişkenin içerdiği tüm öğeleri içeren özelliklerini görmek için `letters` değişkenini genişletin.

1. Sonra, `name` değişkeninin üzerine gelin ve geçerli değerini boş bir dize olarak görürsünüz.

1. **F5** tuşuna basın (veya **hata ayıklama** > **devam et**) birkaç kez `for` döngüsünde birkaç kez yineleyebilir, kesme noktasında tekrar duraklamalısınız ve değeri her seferinde `name` değişkeninin üzerine gelin.

     ![Veri ipucunu görüntüleme](../csharp/media/get-started-data-tip.gif "Veri Ipucunu görüntüleme")

     Değişkenin değeri `for` döngüsünün her yinelemeyle değişir, `f`değerlerini gösterir, sonra da `fr`, sonra `fre`vb.

     Genellikle, hata ayıklama sırasında istediğiniz değişkenlerde depolamak için bunları beklediğiniz değerleri depolamak olup olmadığını görmek için özellik değerlerini denetlemek için hızlı bir yol ve veri ipuçları yapmak için iyi bir yoludur.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde değişkenlerle inceleyin

1. Bakmak **Otolar** altındaki kod düzenleyicisi penceresi.

    Kapalıysa, hata ayıklayıcıda seçerek duraklatıldığı sırada açmak **hata ayıklama** > **Windows** > **Otolar**.

    İçinde **Otolar** penceresi değişkenleri ve bunların geçerli değerini görürsünüz. **Otolar** penceresi, geçerli veya önceki satırındaki (dile özgü davranışı için belgeleri denetleyin) kullanılan tüm değişkenleri gösterir.

1. Ardından, bakmak **Yereller** penceresinde ileri bir sekmeye **Otolar** penceresi.

1. İçerdiği öğeleri göstermek için `letters` değişkenini genişletin.

     ![Oto penceresindeki değişkenleri İncele](../csharp/media/get-started-locals-window.png "Oto penceresi")

    **Yereller** penceresi gösterir, geçerli olan değişkenlere [kapsam](https://www.wikipedia.org/wiki/Scope_(computer_science)), diğer bir deyişle, geçerli yürütme bağlamı.

## <a name="set-a-watch"></a>Bir izleme ayarlayın

1. Ana kod Düzenleyicisi penceresinde `name` değişkenine sağ tıklayıp **Gözcü Ekle**' yi seçin.

    **Watch** Kod Düzenleyicisi sayfanın en penceresi açılır. Kullanabileceğiniz bir **Watch** penceresinin bir değişken (veya bir ifade) takip etmek istediğinizi belirtin.

    Artık `name` değişkeninde bir izleme ayarlamış olursunuz ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerini aksine **Watch** penceresi her zaman, izlerken değişkenleri gösterir (bunlar zaman kapsam dışına renkte).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

1. İçinde duraklatıldığı sırada `for` döngüsünde, tıklayın **çağrı yığını** varsayılan alt sağ bölmede açık olarak penceresinde.

    Kapalıysa, hata ayıklayıcıda seçerek duraklatıldığı sırada açmak **hata ayıklama** > **Windows** > **çağrı yığını**.

2. `SendMessage` yönteminde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın. Bakmak **çağrı yığını** penceresi.

    ![Çağrı yığınını inceleyin](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    **Çağrı yığını** penceresi, yöntemleri ve işlevleri çağrılır sırasını gösterir. Geçerli işlev en üst satırına gösterir ( `SendMessage` bu uygulamada yöntemi). İkinci satır gösteren `SendMessage` çağırıldığı `Main` yöntemi ve benzeri.

   > [!NOTE]
   > **Çağrı yığını** penceresi benzer hata ayıklama perspektifi için Eclipse gibi bazı IDE içinde.

    Çağrı yığınını inceleyebilir ve bir uygulamanın yürütme akışını anlamanıza için iyi bir yoludur.

    Bir satır kod, kaynak koda bakmaktır gitmek için çift tıklayın ve hata ayıklayıcı tarafından denetlenmekte olan geçerli kapsamını da değişiklikler. Bu eylem, hata ayıklayıcı ilerleyin değil.

    Sağ tıklama menülerden kullanabilirsiniz **çağrı yığını** başka şeyler için pencere. Örneğin, belirtilen işlevlere kesme noktaları ekleme, hata ayıklayıcıyı kullanarak ilerleyin **imlece kadar Çalıştır**ve kaynak kodunu inceleyin. Daha fazla bilgi için [nasıl yapılır: çağrı yığını inceleyin](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışı değiştirme

1. `Console.WriteLine` yöntemini çalıştırmak için **F11** tuşuna iki kez basın.

1. `SendMessage` Yöntem çağrısında hata ayıklayıcı duraklatıldığında, sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve sarı oku bir satır yukarı doğru aşağı doğru aşağı taşıyın ve `Console.WriteLine`.

1. Tuşuna **F11**.

    Hata ayıklayıcıyı yeniden çalıştırır `Console.WriteLine` yöntemi (bunu görmeniz konsol penceresi çıktısı).

    Yürütme akışı değiştirerek farklı kod yürütme yolları test veya hata ayıklayıcı yeniden başlatmadan kodu yeniden gibi işlemler yapabilirsiniz.

    > [!WARNING]
    > Genelde bu özellikle dikkat etmek gerekir ve araç ipucunda bir uyarı görürsünüz. Çok diğer uyarılar görebilirsiniz. İşaretçiyi taşıma uygulamanızı daha önceki bir uygulama durumuna geri alınamaz.

1. Tuşuna **F5** uygulamayı çalıştırmaya devam etmek için.

    Bu öğreticiyi tamamlamak Tebrikler!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
