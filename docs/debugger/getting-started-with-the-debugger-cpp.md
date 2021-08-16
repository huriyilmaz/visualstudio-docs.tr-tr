---
title: 'Öğretici: C++ kodunda hata ayıklama'
description: Visual Studio hata ayıklayıcının özelliklerini ve hata ayıklayıcıyı başlatma, kod içinde adım adım ve bir C++ uygulamasındaki verileri inceleme hakkında bilgi edinin.
ms.custom: debug-experiment,  vs-acquisition, get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d24d1e00aac690976eb17fde0f1f89f7d102982b0e5c3ca2822b4e659eeae226
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454437"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C++ kodunun hatalarını ayıklamayı öğrenin

bu makalede, adım adım izlenecek yol Visual Studio hata ayıklayıcının özellikleri tanıtılmaktadır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü istiyorsanız, bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md). Uygulamanızda *hata ayıklarken*, genellikle uygulamanızı hata ayıklayıcı eklenmiş şekilde çalıştırdığınız anlamına gelir. Bunu yaptığınızda, hata ayıklayıcı kodun çalışırken ne yaptığını görmek için birçok yol sunar. Kodunuzda saklanan değerlere bakabilir ve değişkenlerde depolanan değerlere bakabilirsiniz, değerlerin ne zaman değişenleri görebileceğiniz, kodunuzun yürütme yolunu inceleyebileceğiniz, kodun bir dalında çalışıp çalışmadığını ve bu şekilde devam edebilirsiniz. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md) işlemini okumak isteyebilirsiniz.

tanıtım uygulaması C++ olsa da, özelliklerin çoğu C#, Visual Basic, F #, Python, JavaScript ve Visual Studio tarafından desteklenen diğer dillere uygulanabilir (F #, düzenle ve devam et 'i desteklemez). F # ve JavaScript, **oto** penceresini desteklemez). Ekran görüntüleri C++ ' da bulunur.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlatın ve kesme noktalarını isabet edin.
> * Hata Ayıklayıcıdaki kodu adım adım ilerme komutlarını öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı Windows 'da değişkenleri İnceleme
> * Çağrı yığınını inceleyin

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

Visual Studio 2019 yüklü ve C++ iş yüküyle **masaüstü geliştirmeye** sahip olmanız gerekir.

::: moniker-end
::: moniker range="vs-2017"

Visual Studio 2017 yüklü ve C++ iş yüküyle **masaüstü geliştirmeye** sahip olmanız gerekir.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. Visual Studio Yükleyicisi başlatılır. C++ iş yükü **Ile masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C++ konsol uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

3. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual C++** ' i genişletin ve ardından **masaüstü Windows**' yı seçin. orta bölmede **Windows konsol uygulaması**' nı seçin. Ardından Proje *Get-Started-hata ayıklama* adını adlandırın.

     **konsol uygulaması** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

4. **Tamam**'a tıklayın.

   Visual Studio yeni projenizi açar.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio 2019 ' i açın.

   Başlangıç penceresi açık değilse **Dosya** > **Başlangıç penceresi**' ni seçin.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C++** ' ı seçin ve ardından Platform listesinden **Windows** ' yi seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması için C++ şablonunu seçin](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın. ardından Visual Studio Yükleyicisi, C++ iş yüküyle **masaüstü geliştirmeyi** seçin.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *get-started-debugging* yazın veya girin. Ardından **Oluştur**' u seçin.

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

1. Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata **Ayıkla > Başlat**) ![veya hata](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

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

2. Kırmızı durma ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") düğmesine (**SHIFT**  +  **F5**) basarak hata ayıklayıcıyı durdurun.

3. Konsol penceresinde, bir tuşa basarak konsol penceresini kapatmak için **ENTER** tuşuna basın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

1. `for` `main` İşlevin döngüsünde, aşağıdaki kod satırının sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktasını ayarladığınız yerde kırmızı bir daire ![kesme noktası](../debugger/media/dbg-breakpoint.png "Kesme noktası") belirir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede askıya alınacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

2. **F5** tuşuna basın veya hata **ayıklamayı Başlat** ![düğmesine basın](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat"), uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

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

     ![Koda geçmek için F11 kullanın](../debugger/media/get-started-f11-cpp.png "F10 Içine Adımla")

     F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../debugger/just-my-code.md)).

     Yöntemi incelemeyi bitirdiğinizde `SendMessage` ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **SHIFT**  +  **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     Yöntem `for` çağrısında duraklamış olması için, yöntemde döngüde geri dönüş yapmanız gerekir `main` `SendMessage` .

1. Yöntem çağrısına tekrar geri gelene kadar **F11** tuşuna birkaç kez basın `SendMessage` .

1. Yöntem çağrısında duraklalarken **F10** tuşuna basın (veya bir kez **Hata Ayıkla > adımla**).

     ![Kod üzerinde adımla F10 kullanın](../debugger/media/get-started-step-over-cpp.png "F10 Adım At")

     Hata ayıklayıcının yönteme adımla ilgili bu zamana dikkat edin `SendMessage` . **F10** uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). Yöntem çağrısında **F10** tuşuna basarak `SendMessage` ( **F11** yerine), için uygulama kodu atlandık `SendMessage` (Bu, şu anda ilgilenmiyor olabilir). Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Çalıştırmak için Çalıştır 'ı kullanarak kodu gezin

1. Kesme noktasına ilerlemek için **F5** tuşuna basın.

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak `std::wcout` düğmeye tıklayarak işlevin üzerine gelin ve `SendMessage` sol tarafta görünen düğmesine ![tıklamak](../debugger/media/dbg-tour-run-to-click.png "RunToClick") için, **Tıklamasız** düğme Çalıştır düğmesine tıklayın. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

     ![Tıklama için Çalıştır özelliğini kullanın](../debugger/media/get-started-run-to-click-cpp.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > Tıklayarak **Çalıştır düğmesi** içinde [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] yenidir. (Yeşil ok düğmesini görmüyorsanız hata ayıklayıcıyı doğru yere ilerlemek için bu örnekte **F11** kullanın.)

2. **Tıklarken Çalıştır düğmesine Tıklayarak** ![Çalıştır'a tıklayın.](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcısı işlevine `std::wcout` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklamak için** Çalıştır, uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı Yeniden](../debugger/media/dbg-tour-restart.png "RestartApp") Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**).

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı, daha önce döngü içinde ayaranı kesme noktası sırasında yeniden `for` durur.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçlarıyla değişkenleri inceleme

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerinden birisidir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. deyimini `name += letters[i]` duraklatırken değişkeninin üzerine `letters` gelin ve varsayılan değeri olduğunu `size={10}` görüyorsunuz.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Döngüde birkaç kez tekrarlama, kesme noktası üzerinde yeniden duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F5** 'e (veya Devam Et)'e birkaç kez  >   `for` `name` basın.

     ![Veri ipucu görüntüleme](../debugger/media/get-started-data-tip-cpp.png "Veri İpucu Görüntüleme")

     Değişkenin değeri, döngüde her yineleme ile birlikte değişir ve ardından `for` , ve gibi değerleri `f` `fr` `fre` gösterir.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin, depolamasını beklediğiniz değerleri depolayarak depolamalarının gerekip gerek olmadığını ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek için hızlı bir yol gerekir.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

1. Kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

    Kapalı ise, Hata Ayıkla'ya ve Otomatikler'e göre hata **ayıkla'Windows**  >    >  **açın.**

    Otomatikler **penceresinde** değişkenleri ve bunların geçerli değerini görebilirsiniz. Otomatikler **penceresinde** geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (Dile özgü davranış için belgeleri kontrol edin).

1. Ardından, Otomatikler **penceresinin** yanındaki sekmede Yereller **penceresine** bakın.

1. Içerdiği `letters` öğeleri göstermek için değişkeni genişletin.

     ![YerelLer Penceresinde değişkenleri inceleme](../debugger/media/get-started-locals-window-cpp.png "YerelLer Penceresi")

    **YerelLer** penceresi, geçerli kapsamda olan, yani [geçerli](https://www.wikipedia.org/wiki/Scope_(computer_science))yürütme bağlamındaki değişkenleri gösterir.

## <a name="set-a-watch"></a>Saat ayarlama

1. Ana kod düzenleyicisi penceresinde değişkenine sağ tıklayın ve İzleme `name` **Ekle'yi seçin.**

    Kod  düzenleyicisinin alt kısmında İzleme penceresi açılır. İzleme penceresi **kullanarak** göz tutmak istediğiniz bir değişken (veya ifade) belirtebilirsiniz.

    Artık değişkende bir izleme kümemiz var ve hata ayıklayıcıda ilerlerken `name` değerinin değişti olduğunu görüyorsunuz. Diğer değişken pencerelerinin aksine, **İzle** penceresi her zaman izlediğiniz değişkenleri gösterir (kapsam dışındayken bunlar gri renkte olur).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleme

1. Döngüde duraklatılmışken, varsayılan olarak sağ alt bölmede açık `for` olan Çağrı Yığını penceresine tıklayın. 

    Kapalı ise, Çağrı Yığınında Hata Ayıkla'yı seçerek hata **ayıklayıcıda**  >  **duraklatılmış Windows**  >  **açın.**

2. Yönteminde hata ayıklayıcının duraklatılmış olduğunu görene kadar **F11'e** birkaç kez `SendMessage` tıklayın. Çağrı Yığını **penceresine** bakın.

    ![Çağrı yığınını inceleme](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Üst satır geçerli işlevi (bu `SendMessage` uygulamanın yöntemi) gösterir. İkinci satırda `SendMessage` yönteminden `main` çağrıldı ve bu şekilde devam etti.

   > [!NOTE]
   > Çağrı **Yığını penceresi,** Eclipse gibi bazı IDE'lerde Hata Ayıklama perspektifi ile benzerdir.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yol sağlar.

    Bir kod satırına çift tıklar ve bu koda göz atabilir ve hata ayıklayıcı tarafından denetlenen geçerli kapsamı da değiştirir. Bu eylem hata ayıklayıcıyı ilerleten bir eylem değildir.

    Başka şeyler yapmak için Çağrı Yığını penceresinden sağ **tıklama** menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları eklemek, İmleçte Çalıştır'ı kullanarak hata ayıklayıcıyı **ilerletin** ve kaynak kodu incelemeye gidebilirsiniz. Daha fazla bilgi için, [bkz. How to: Examine the Call Stack](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

1. İşlevi **çalıştırmak için F11'e** iki kez `std::wcout` basın.

1. Hata ayıklayıcı yöntem çağrısında duraklatılmış şekilde, fareyle sol tarafta sarı oku (yürütme işaretçisi) alıp sarı oku bir satır yukarı, geri `SendMessage` doğru hareket `std::wcout` ettirin.

1. **F11 tuşuna basın.**

    Hata ayıklayıcısı işlevi yeniden `std::wcout` çalıştırıyor (konsol penceresi çıkışında bunu görüyorsunuz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etmek veya hata ayıklayıcıyı yeniden başlatmadan kodu yeniden çalıştırma gibi şeyler yapabiliriz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmalısınız ve araç ipucunda bir uyarı görüyorsunuz. Başka uyarılar da görebilir. İşaretçiyi taşıma, uygulamanızı önceki bir uygulama durumuna döndürebilir.

1. Uygulamayı **çalıştırmaya devam** etmek için F5 tuşuna basın.

    Tebrikler, bu öğreticiyi tamamladıktan sonra!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklayıcıyı başlatmayı, kodu adım adım incelemeyi ve değişkenleri incelemeyi öğrendiniz. Daha fazla bilgi için bağlantılarla birlikte hata ayıklayıcı özelliklerine üst düzey bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)

