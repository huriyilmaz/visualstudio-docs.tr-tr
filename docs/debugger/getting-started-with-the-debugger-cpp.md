---
title: 'Öğretici: C++ kodunda hata ayıklama'
description: Visual Studio hata ayıklayıcının özelliklerini ve hata ayıklayıcıyı başlatma, kod adım adım ve bir C++ uygulamasındaki verileri İnceleme hakkında bilgi edinin.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cc5d0b85ac1406f214784976ca23467a0e0eb6c
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847102"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C++ kodunda hata ayıklamayı öğrenin

Bu makalede, adım adım bir yönergede Visual Studio hata ayıklayıcının özellikleri tanıtılmaktadır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md). Uygulamanızda *hata ayıklarken*, genellikle uygulamanızı hata ayıklayıcı eklenmiş şekilde çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı kodun çalışırken ne yaptığını görmek için birçok yol sunar. Kodunuzda saklanan değerlere bakabilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerlerin ne zaman değişenleri görebileceğiniz, kodunuzun yürütme yolunu inceleyebileceğiniz, kodun bir dalında çalışıp çalışmadığını ve bu şekilde devam edebilirsiniz. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md) işlemini okumak isteyebilirsiniz.

Tanıtım uygulaması C++ olsa da, özelliklerin çoğu C#, Visual Basic, F #, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F #, Düzenle ve devam et ' i desteklemez. F # ve JavaScript, **oto** penceresini desteklemez). Ekran görüntüleri C++ ' da bulunur.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktalarını isabet edin.
> * Hata Ayıklayıcıdaki kodu adım adım ilerme komutlarını öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı Windows 'da değişkenleri İnceleme
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Ön koşullar

::: moniker range=">=vs-2019"

Visual Studio 2019 ' nin yüklü olması ve C++ iş yüküyle **masaüstü geliştirmesi** olması gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 ' nin yüklü olması ve C++ iş yüküyle **masaüstü geliştirmesi** olması gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

İş yükünü yüklemeniz gerekir, ancak zaten Visual Studio 'ya sahipseniz **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açılır. Visual Studio Yükleyicisi başlatılır. C++ iş yükü **Ile masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C++ konsol uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

3. Sol bölmedeki **Yeni proje** iletişim kutusunda **Visual C++** ' ı genişletin ve ardından **Windows Masaüstü**' nu seçin. Orta bölmede **Windows konsol uygulaması**' nı seçin. Ardından Proje *Get-Started-hata ayıklama* adını adlandırın.

     **Konsol uygulaması** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

4. **Tamam**’a tıklayın.

   Visual Studio yeni projenizi açar.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil listesinden **C++** ' ı seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması için C++ şablonunu seçin](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Ardından Visual Studio Yükleyicisi, C++ iş yüküyle **Masaüstü geliştirmeyi** seçin.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *Get-Started-Debugging* yazın veya girin. Ardından **Oluştur**' u seçin.

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

1. *Get-Started-Debugging. cpp*' de, varsayılan tüm kodu bunun yerine aşağıdaki kodla değiştirin:

    ```cpp
    #include <string>
    #include <vector>
    #include <iostream>

    void SendMessage(const std::wstring& name, int msg)
    {
        std::wcout << L"Hello, " << name << L"! Count to " << msg << std::endl;
    }

    int main()
    {
        std::vector<wchar_t> letters = { L'f', L'r', L'e', L'd', L' ', L's', L'm', L'i', L't', L'h' };
        std::wstring name = L"";
        std::vector<int> a(10);
        std::wstring key = L"";

        for (int i = 0; i < letters.size(); i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        std::wcin >> key;
        return 0;
    }
    ```

## <a name="start-the-debugger"></a>Hata ayıklayıcıyı başlatın!

1. Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata **Ayıkla > Başlat**) ![veya hata](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

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

2. Kırmızı durma ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") düğmesine (**SHIFT**  +  **F5**) basarak hata ayıklayıcıyı durdurun.

3. Konsol penceresinde, bir tuşa basarak konsol penceresini kapatmak için **ENTER** tuşuna basın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

1. `for` `main` İşlevin döngüsünde, aşağıdaki kod satırının sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktasını ayarladığınız yerde kırmızı bir daire ![kesme noktası](../debugger/media/dbg-breakpoint.png "Ilı") belirir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

2. **F5** tuşuna basın veya hata **ayıklamayı Başlat** ![düğmesine basın](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat"), uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../debugger/media/get-started-set-breakpoint-cpp.png)

    Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

     Uygulama henüz çalışmıyorsa, **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır. Aksi halde, **F5** uygulamayı bir sonraki kesme noktasına çalıştırmaya devam eder.

    Kod satırını veya kodun ayrıntılı olarak incelemek istediğiniz bölümünü bildiğiniz kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinin

Çoğu durumda buradaki klavye kısayollarını kullanıyoruz. Bu, uygulamanızı hata ayıklayıcıda yürütmek için iyi bir yoldur (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. `for`Yöntem içindeki döngüde duraklalarken `main` , yöntem çağrısına Ilerlemek için **F11** tuşuna basın (veya **hata ayıklama > adımla**) seçeneğini iki kez yapın `SendMessage` .

     **F11** tuşuna iki kez bastıktan sonra şu kod satırında olmalısınız:

     `SendMessage(name, a[i]);`

1. Yönteme adım eklemek için bir kez daha **F11** tuşuna basın `SendMessage` .

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     ![Koda geçmek için F11 kullanın](../debugger/media/get-started-f11-cpp.png "F10 adımla")

     F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../debugger/just-my-code.md)).

     Yöntemi incelemeyi bitirdiğinizde `SendMessage` ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **SHIFT**  +  **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     Yöntem `for` çağrısında duraklamış olması için, yöntemde döngüde geri dönüş yapmanız gerekir `main` `SendMessage` .

1. Yöntem çağrısına tekrar geri gelene kadar **F11** tuşuna birkaç kez basın `SendMessage` .

1. Yöntem çağrısında duraklalarken **F10** tuşuna basın (veya bir kez **Hata Ayıkla > adımla**).

     ![Kod üzerinde adımla F10 kullanın](../debugger/media/get-started-step-over-cpp.png "F10 adımla")

     Hata ayıklayıcının yönteme adımla ilgili bu zamana dikkat edin `SendMessage` . **F10** uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). Yöntem çağrısında **F10** tuşuna basarak `SendMessage` ( **F11** yerine), için uygulama kodu atlandık `SendMessage` (Bu, şu anda ilgilenmiyor olabilir). Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Çalıştırmak için Çalıştır 'ı kullanarak kodu gezin

1. Kesme noktasına ilerlemek için **F5** tuşuna basın.

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak `std::wcout` düğmeye tıklayarak işlevin üzerine gelin ve `SendMessage` sol tarafta görünen düğmesine ![tıklamak](../debugger/media/dbg-tour-run-to-click.png "RunToClick") için, **Tıklamasız** düğme Çalıştır düğmesine tıklayın. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![Tıklama için Çalıştır özelliğini kullanın](../debugger/media/get-started-run-to-click-cpp.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > **Tıklama Için Çalıştır düğmesi '** de yenidir [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] . (Yeşil ok düğmesini görmüyorsanız, hata ayıklayıcıyı doğru yere ilerletmek için bu örnekte **F11** kullanın.)

2. **Tıklama düğmesine tıklayarak** ![' ye tıklayın.](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcı `std::wcout` işlevine ilerler.

    Bu düğme kullanıldığında geçici bir kesme noktası ayarlamaya benzer. **' I tıklatarak** , uygulama kodunun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır (herhangi bir açık dosyaya tıklayabilirsiniz).

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlıca yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL**  +  **SHIFT**  +  **F5**) düğmesine tıklayın.

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

Hata ayıklayıcı daha önce döngü içinde ayarladığınız kesme noktasında yeniden durmaktadır `for` .

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları ile değişkenleri inceleyin

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en yararlı özelliklerinden biridir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir zamanda sahip olmalarını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz.

1. İfadede duraklalarken `name += letters[i]` , değişkenin üzerine gelin `letters` ve varsayılan değerini görürsünüz `size={10}` .

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

1. Sonra, değişkenin üzerine gelin `name` ve geçerli değerini boş bir dize olarak görürsünüz.

1. Her seferinde birkaç kez yinelemek için **F5** tuşuna basın (veya **hata ayıklama**  >  **devam** edin) `for` , kesme noktasında tekrar duraklamanın ve `name` değeri her seferinde, değişkenin üzerine gelindiğinde.

     ![Veri ipucunu görüntüleme](../debugger/media/get-started-data-tip-cpp.png "Veri Ipucunu görüntüleme")

     Değişkenin değeri, döngü her tekrarında değişir ve `for` değerlerini, sonra, vb. gösterir `f` `fr` `fre` .

     Genellikle, hata ayıklarken, değişkenleri üzerinde özellik değerlerini denetlemeye yönelik hızlı bir yol isteyeceksiniz ve bu değerlerin depolanmasını beklediğinizi ve veri ipuçları bunu yapmanın iyi bir yoludur.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

1. Kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

    Kapatılmışsa, hata ayıklayıcıda **hata ayıklama**  >  **Windows**  >  **oto öğeleri**' ni seçerek açın.

    **Oto** penceresinde, değişkenleri ve bunların geçerli değerlerini görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

1. Ardından, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresine bakın.

1. Değişkenini, `letters` içerdiği öğeleri göstermek için genişletin.

     ![Locals penceresinde değişkenleri İnceleme](../debugger/media/get-started-locals-window-cpp.png "Yereller penceresi")

    **Yereller** penceresi, geçerli yürütme bağlamı olan geçerli [kapsamda](https://www.wikipedia.org/wiki/Scope_(computer_science))olan değişkenleri gösterir.

## <a name="set-a-watch"></a>İzleme ayarlama

1. Ana kod Düzenleyicisi penceresinde değişkene sağ tıklayın `name` ve **Gözcü Ekle**' yi seçin.

    **İzleme** penceresi, kod düzenleyicisinin en altında açılır. Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz.

    Artık değişkende bir izleme kümesi vardır `name` ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Gözcü** penceresi her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte gösterilir).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

1. Döngüde durakladığında `for` , varsayılan olarak sağ alt bölmede açık olan **çağrı yığını** penceresine tıklayın.

    Kapatılmışsa, hata ayıklayıcıda hata **Ayıkla**  >  **Windows**  >  **çağrı yığını**' nı seçerek dosyayı açın.

2. Yöntemde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın `SendMessage` . **Çağrı yığını** penceresine bakın.

    ![Çağrı yığınını inceleyin](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `SendMessage` Bu uygulamadaki yöntemi) gösterilir. İkinci satır, `SendMessage` `main` yönteminden çağrılan ve bu şekilde devam eden gösterir.

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

    Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu eylem, hata ayıklayıcıyı ilerlemez.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilir, çalışma hata ayıklayıcıyı kullanarak Imleç ' i **Imlece** ilerletebilirsiniz ve kaynak kodu İnceleme ' ye gidebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

1. İşlevi çalıştırmak için **F11** tuşuna iki kez basın `std::wcout` .

1. Yöntem çağrısında hata ayıklayıcı duraklatıldığında `SendMessage` , sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve sarı oku bir satır yukarı doğru aşağı taşıyın `std::wcout` .

1. **F11** tuşuna basın.

    Hata ayıklayıcı işlevi yeniden çalıştırır `std::wcout` (bunu konsol penceresi çıktısında görürsünüz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etme veya hata ayıklayıcıyı yeniden başlatmanıza gerek kalmadan kodu yeniden çalıştırma gibi işlemleri yapabilirsiniz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmanız ve araç ipucunda bir uyarı görmeniz gerekir. Diğer uyarıları da görebilirsiniz. İşaretçinin taşınması uygulamanızı önceki bir uygulama durumuna döndüremezsiniz.

1. Uygulamayı çalıştırmaya devam etmek için **F5** tuşuna basın.

    Tebrikler, bu öğreticiyi tamamlama!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm sağlamak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)

