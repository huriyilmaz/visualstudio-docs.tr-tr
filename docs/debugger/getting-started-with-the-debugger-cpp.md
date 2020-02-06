---
title: 'Öğretici: hata C++ ayıklama kodu'
description: Kodu adımlayın Visual Studio hata ayıklayıcısını başlatın ve veri İnceleme hakkında bilgi edinin.
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
ms.openlocfilehash: 96c928606c0fbc306a72347f85841677d0f69ec8
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027357"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: C++ kodunuzu Visual Studio kullanarak hata ayıklamayı öğrenin

Bu makalede, Visual Studio hata ayıklayıcı adım adım kılavuzda özelliklerini tanıtır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md). Uygulamanızda *hata ayıklarken*, genellikle uygulamanızı hata ayıklayıcı eklenmiş şekilde çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı, kodunuzun ne yaptığını görmek için birçok yol sağlar. çalışırken. Kodunuzda adım adım ve değişkenlerinde depolanan değerleri bakmak, gözcüler ayarlayabilirsiniz değerleri değiştiğinde görmek için değişkenlerini kodunuzun yürütme yolunu inceleyin, bir dal kod çalıştırma, vb. olup olmadığını. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md) işlemini okumak isteyebilirsiniz.

Tanıtım uygulaması C++olsa da özelliklerin çoğu, Visual Studio tarafından desteklenen Visual Basic, C# F#, Python, JavaScript ve diğer diller için geçerlidir (F# düzenleme ve devam etmeyi desteklemez). F#ve JavaScript, **oto** penceresini desteklemez). Ekran görüntüleri ' de C++bulunur.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktaları isabet.
> * Hata ayıklayıcı kodda adım adım için komutları öğrenin
> * Veri ipuçları ve hata ayıklayıcı pencereleri değişkenler inceleyin
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

Visual Studio 2019 ' nin yüklü olması ve iş yüküyle **Masaüstü C++ geliştirmesi** olması gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 ' nin yüklü olması ve iş yüküyle **Masaüstü C++ geliştirmesi** olması gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Visual Studio Yükleyicisi'ni başlatır. İş yüküyle **Masaüstü geliştirmeyi C++**  seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C++ konsol uygulaması projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin.

3. Sol bölmedeki **Yeni proje** iletişim kutusunda, **görsel C++**  ' i genişletin ve ardından **Windows Masaüstü**' ne tıklayın. Orta bölmede **Windows konsol uygulaması**' nı seçin. Ardından Proje *Get-Started-hata ayıklama*adını adlandırın.

     **Konsol uygulaması** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusunun sol bölmesindeki **Visual Studio yükleyicisi aç** bağlantısını seçin.

     Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

   Başlangıç penceresi açık değilse **dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil **C++** listesinden seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması C++ şablonunu seçin](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. Ardından Visual Studio yükleyicisi, iş yüküyle **Masaüstü geliştirmeyi C++**  seçin.

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

1. Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata**Ayıkla > Başlat**) ![veya hata](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

     **F5** uygulama işlemine eklenen hata ayıklayıcı ile uygulamayı başlatır, ancak şimdi kodu incelemek için özel bir şey yapmadık. Bu nedenle yalnızca uygulamayı yükler ve konsol çıktısı görürsünüz.

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

2. Kırmızı durma ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "Hata ayıklamayı Durdur") düğmesine (**SHIFT** + **F5**) basarak hata ayıklayıcıyı durdurun.

3. Konsol penceresinde, bir tuşa basarak konsol penceresini kapatmak için **ENTER** tuşuna basın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Bir kesme noktası ayarlayın ve hata ayıklayıcıyı başlatın

1. `main` işlevinin `for` döngüsünde, aşağıdaki kod satırının sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktasını ayarladığınız yerde kırmızı bir daire ![kesme noktası](../debugger/media/dbg-breakpoint.png "Kesme noktası") belirir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

2. **F5** tuşuna basın veya hata **ayıklamayı Başlat** ![düğmesine basın](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat"), uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    ![Ayarlayın ve bir kesme noktası isabet](../debugger/media/get-started-set-breakpoint-cpp.png)

    Sarı ok, aynı zamanda aynı noktayı (Bu bildirimi henüz çalıştırılmadı) uygulama yürütmeyi askıya alır, hata ayıklayıcı durduruldu, deyimi temsil eder.

     Uygulama henüz çalışmıyorsa, **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır. Aksi halde, **F5** uygulamayı bir sonraki kesme noktasına çalıştırmaya devam eder.

    Kod satırının veya ayrıntılı olarak incelemek istediğiniz kod bölümünün bildiğiniz durumlarda kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Kod adım komutları kullanarak hata ayıklayıcısında gidin

Almak için en iyi yolu olduğundan bu çoğunlukla, klavye kısayollarını Burada, kullandığımız hata ayıklayıcı (komutları parantez içinde gösterilen eşdeğer komutları menüsü gibi) uygulamanız çalıştırma sırasında hızlı.

1. `main` yönteminde `for` döngüsünde duraklatıldıktan sonra, `SendMessage` yöntem çağrısına ilerlemek için **F11** tuşuna basın (veya **hata ayıklama > adımla**) seçeneğini belirleyin.

     **F11** tuşuna iki kez bastıktan sonra şu kod satırında olmalısınız:

     `SendMessage(name, a[i]);`

1. `SendMessage` metoduna geçmek için bir kez daha **F11** tuşuna basın.

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     ![Koda geçmek için F11 kullanın](../debugger/media/get-started-f11-cpp.png "F10 adımla")

     F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. F11 çoğu ayrıntılı yürütme akışı incelemek için iyi bir yoludur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../debugger/just-my-code.md)).

     `SendMessage` yöntemini incelemeyi bitirdiğinizde ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **Shıft** + **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     `main` yönteminde `for` döngüsünde geri almanız gerekir, `SendMessage` Yöntem çağrısında duraklatılabilir.

1. `SendMessage` yöntemi çağrısının yeniden geri alınana kadar **F11** tuşuna birkaç kez basın.

1. Yöntem çağrısında duraklalarken **F10** tuşuna basın (veya bir kez **Hata Ayıkla > adımla**).

     ![Kod üzerinde adımla F10 kullanın](../debugger/media/get-started-step-over-cpp.png "F10 adımla")

     Hata ayıklayıcının `SendMessage` yöntemine adım yapmadığından bu zamana dikkat edin. **F10** uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). `SendMessage` Yöntem çağrısında **F10** tuşuna basarak ( **F11**yerine), `SendMessage` için uygulama kodu atlandık (Bu, şu anda ilgilentik olabilir). Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Tıkla Çalıştır'ı kullanarak kod gidin

1. Kesme noktasına ilerlemek için **F5** tuşuna basın.

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak `SendMessage` yönteminde `std::wcout` işlevinin üzerine gelin ve sol tarafta görünen düğmesine ![tıklamak](../debugger/media/dbg-tour-run-to-click.png "RunToClick") Için, **Tıklamasız** düğme Çalıştır düğmesine tıklayın. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![Tıklama için Çalıştır özelliğini kullanın](../debugger/media/get-started-run-to-click-cpp.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > **Tıklama Için Çalıştır** düğmesi [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]yeni bir düğmedir. (Yeşil ok düğmesini görmüyorsanız, hata ayıklayıcıyı doğru yere ilerletmek için bu örnekte **F11** kullanın.)

2. **Tıklama düğmesine tıklayarak** ![' ye tıklayın.](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcı `std::wcout` işlevine ilerler.

    Bu düğmeyi kullanarak geçici bir kesme noktası ayarlayarak benzer. **' I tıklatarak** , uygulama kodunun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır (herhangi bir açık dosyaya tıklayabilirsiniz).

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlı bir şekilde yeniden başlatın

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. İlk kesme noktasına isabet kodu yürüterek, hata ayıklayıcı duraklatır.

Hata ayıklayıcı daha önce `for` döngüsünde ayarladığınız kesme noktasında yeniden durmaktadır.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları değişkenlerle inceleyin

Değişkenleri incelemek özellik hata ayıklayıcının en kullanışlı özellikler biridir ve bunu yapmanın farklı yolu vardır. Genellikle, hata ayıklama bir sorun açmayı denediğinde, belirli bir zamanda sahip olmalarını beklediğiniz değerleri değişkenleri olup depoladığını kullanıma bulmak çalışıyorsunuz.

1. `name += letters[i]` bildiriminde duraklalarken, `letters` değişkeninin üzerine gelin ve `size={10}`varsayılan değerini görürsünüz.

1. Değişkenin içerdiği tüm öğeleri içeren özelliklerini görmek için `letters` değişkenini genişletin.

1. Sonra, `name` değişkeninin üzerine gelin ve geçerli değerini boş bir dize olarak görürsünüz.

1. **F5** tuşuna basın (veya **hata ayıklama** > **devam et**) birkaç kez `for` döngüsünde birkaç kez yineleyebilir, kesme noktasında tekrar duraklamalısınız ve değeri her seferinde `name` değişkeninin üzerine gelin.

     ![Veri ipucunu görüntüleme](../debugger/media/get-started-data-tip-cpp.png "Veri Ipucunu görüntüleme")

     Değişkenin değeri `for` döngüsünün her yinelemeyle değişir, `f`değerlerini gösterir, sonra da `fr`, sonra `fre`vb.

     Genellikle, hata ayıklama sırasında istediğiniz değişkenlerde depolamak için bunları beklediğiniz değerleri depolamak olup olmadığını görmek için özellik değerlerini denetlemek için hızlı bir yol ve veri ipuçları yapmak için iyi bir yoludur.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde değişkenlerle inceleyin

1. Kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

    Kapalıysa, **hata** ayıklayıcı > **Windows** > **oto**' ı seçerek hata ayıklayıcıda duraklalarken açın.

    **Oto** penceresinde, değişkenleri ve bunların geçerli değerlerini görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

1. Ardından, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresine bakın.

1. İçerdiği öğeleri göstermek için `letters` değişkenini genişletin.

     ![Locals penceresinde değişkenleri İnceleme](../debugger/media/get-started-locals-window-cpp.png "Yereller penceresi")

    **Yereller** penceresi, geçerli yürütme bağlamı olan geçerli [kapsamda](https://www.wikipedia.org/wiki/Scope_(computer_science))olan değişkenleri gösterir.

## <a name="set-a-watch"></a>Bir izleme ayarlayın

1. Ana kod Düzenleyicisi penceresinde `name` değişkenine sağ tıklayıp **Gözcü Ekle**' yi seçin.

    **İzleme** penceresi, kod düzenleyicisinin en altında açılır. Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz.

    Artık `name` değişkeninde bir izleme ayarlamış olursunuz ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Gözcü** penceresi her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte gösterilir).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

1. `for` döngüsünde duraklatıldığında, varsayılan olarak sağ alt bölmede açık olan **çağrı yığını** penceresine tıklayın.

    Kapalıysa, hata ayıklayıcıda hata **ayıkla** > **Windows** > **çağrı yığını**' nı seçerek açın.

2. `SendMessage` yönteminde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın. **Çağrı yığını** penceresine bakın.

    ![Çağrı yığınını inceleyin](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev (Bu uygulamadaki `SendMessage` yöntemi) gösterilir. İkinci satır `SendMessage` `main` yönteminden çağrıldığını gösterir ve bu şekilde devam eder.

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

    Çağrı yığınını inceleyebilir ve bir uygulamanın yürütme akışını anlamanıza için iyi bir yoludur.

    Bir satır kod, kaynak koda bakmaktır gitmek için çift tıklayın ve hata ayıklayıcı tarafından denetlenmekte olan geçerli kapsamını da değişiklikler. Bu eylem, hata ayıklayıcı ilerleyin değil.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilir, çalışma hata ayıklayıcıyı kullanarak Imleç ' i **Imlece**ilerletebilirsiniz ve kaynak kodu İnceleme ' ye gidebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışı değiştirme

1. `std::wcout` işlevini çalıştırmak için **F11** tuşuna iki kez basın.

1. `SendMessage` Yöntem çağrısında hata ayıklayıcı duraklatıldığında, sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve sarı oku bir satır yukarı doğru aşağı doğru aşağı taşıyın ve `std::wcout`.

1. **F11**tuşuna basın.

    Hata ayıklayıcı `std::wcout` işlevini yeniden çalıştırır (bunu konsol penceresi çıktısında görürsünüz).

    Yürütme akışı değiştirerek farklı kod yürütme yolları test veya hata ayıklayıcı yeniden başlatmadan kodu yeniden gibi işlemler yapabilirsiniz.

    > [!WARNING]
    > Genelde bu özellikle dikkat etmek gerekir ve araç ipucunda bir uyarı görürsünüz. Çok diğer uyarılar görebilirsiniz. İşaretçiyi taşıma uygulamanızı daha önceki bir uygulama durumuna geri alınamaz.

1. Uygulamayı çalıştırmaya devam etmek için **F5** tuşuna basın.

    Bu öğreticiyi tamamlamak Tebrikler!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, kodu adımlayın hata ayıklayıcıyı başlatın ve değişkenleri denetleyin öğrendiniz. Daha fazla bilgi için bağlantılar hata ayıklayıcı özelliklerine genel bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)

