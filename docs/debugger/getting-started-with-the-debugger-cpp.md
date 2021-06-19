---
title: 'Öğretici: C++ kodunda hata ayıklama'
description: Hata ayıklayıcısının Visual Studio hata ayıklayıcısını başlatmayı, kodda adım adım incelemeyi ve C++ uygulamasındaki verileri incelemeyi öğrenin.
ms.custom: debug-experiment,  get-started
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
ms.openlocfilehash: 8abb517103254aa1e0c89a02b0dc81b38af3ecee
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385259"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak C++ kodunda hata ayıklamayı Visual Studio

Bu makalede, Visual Studio hata ayıklayıcısının özellikleri adım adım izlenecek yol açıklanmıştır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü almak için [bkz. İlk olarak hata ayıklayıcıya bakın.](../debugger/debugger-feature-tour.md) Uygulamanıza *hata ayıklarken,* genellikle hata ayıklayıcı eklenmiş olarak çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişip değişmeyişini görmek için değişkenler üzerinde izlemeler ayarlayın, kodunuzun yürütme yolunu inceleyebilirsiniz, bir kod dalını çalıştırıp çalıştırmama gibi. İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi okumadan önce yeni başlayanlar için [hata](../debugger/debugging-absolute-beginners.md) ayıklama makalesine bakabilirsiniz.

Tanıtım uygulaması C++ olsa da özelliklerin çoğu C#, Visual Basic, F#, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F# Düzenle ve devamını desteklemez). F# ve JavaScript, Otomatikler **penceresini desteklemez).** Ekran görüntüleri C++ içindedir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlat ve kesme noktalarına isabet.
> * Hata ayıklayıcıda kodda adım adım ilerlerken gereken komutları öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı pencerelerde değişkenleri inceleme
> * Çağrı yığınını inceleme

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

2019'Visual Studio ve C++ ile Masaüstü geliştirme **iş yükünüz yüklü** olması gerekir.

::: moniker-end
::: moniker range="vs-2017"

2017'Visual Studio ve C++ ile Masaüstü geliştirme **iş yükünüz yüklü** olması gerekir.

::: moniker-end

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **C++ ile masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir C++ konsol uygulaması projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

3. Sol **bölmede Yeni** Proje iletişim kutusunda, **Visual C++'ı genişletin ve** ardından Windows **Masaüstü'nü seçin.** Orta bölmede Windows Konsol **Uygulaması'ı seçin.** Ardından projeye *get-started-debugging adını girin.*

     Konsol Uygulaması proje şablonunu **görmüyorsanız** Yeni Proje iletişim kutusunun **sol bölmesinde Visual Studio Yükleyicisi** Aç **bağlantısını** seçin. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

4. **Tamam**'a tıklayın.

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2019"

1. 2019 Visual Studio açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C++** 'ı ve ardından Platform **listesinden Windows'u** seçin. 

   Dil ve platform filtrelerini uyguladikten sonra Konsol Uygulaması **şablonunu ve** ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması için C++ şablonunu seçin](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **C++ ile masaüstü geliştirme iş yükünü** seçin.

1. Yeni **projenizi yapılandır penceresinde** Proje adı kutusuna *get-started-debugging* **yazın veya** girin. Ardından **Oluştur'a seçin.**

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

1. *get-started-debugging.cpp* dosyasında varsayılan kodun hepsini aşağıdaki kodla değiştirin:

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

## <a name="start-the-debugger"></a>Hata ayıklayıcıyı başlatma!

1. **F5** (**Hata Ayıklama > Başlat**) veya Hata Ayıklama ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") Araç Çubuğunda Hata Ayıklamayı Başlat düğmesine basın. 

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

     Bu öğreticide, hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından bakacak ve hata ayıklayıcı özelliklerine göz atacak.

2. Hata ayıklamayı kırmızı durdur Hata Ayıklamayı Durdur düğmesine basarak hata ![ayıklayıcıyı durdurun](../debugger/media/dbg-tour-stop-debugging.png "Hata Ayıklamayı Durdurma") (**Shift**  +  **F5**).

3. Konsol penceresinde bir tuşa ve Enter tuşuna **basarak** konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

1. işlevinin `for` `main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters[i];`

    Kesme noktası ![ayarda kırmızı](../debugger/media/dbg-breakpoint.png "Kesme noktası") bir daire Kesme Noktası görüntülenir.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerindendir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

2. **F5 tuşuna** **veya** Hata ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat")Ayıklamayı Başlat düğmesine Bastığınızda Hata Ayıklamayı Başlat düğmesi uygulama başlatılır ve hata ayıklayıcı kesme noktası ayarlayıcının ayar bulunduğu kod satırına çalışır.

    ![Kesme noktası ayarlama ve isabet](../debugger/media/get-started-set-breakpoint-cpp.png)

    Sarı ok, aynı noktada uygulama yürütmeyi de askıya alan (bu deyim henüz yürütülmedi) hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur. Aksi **takdirde, F5** uygulamayı bir sonraki kesme noktasıyla çalıştırmaya devam eder.

    Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Ayar yalnızca koşullu kesme noktaları gibi farklı kesme noktası türleri hakkında bilgi için [bkz. Kesme noktaları kullanma.](../debugger/using-breakpoints.md)

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinme

Genellikle burada klavye kısayollarını kullanırız çünkü bu, uygulamanızı hata ayıklayıcısında yürütmeyi hızlı bir şekilde yürütmenin iyi bir yolu olduğundan (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. yönteminde döngüsünde duraklatılmışken, yöntem çağrısına ilerlemek için F11 tuşuna basın (veya hata ayıkla > `for` `main` **Adımla)**  `SendMessage` seçin.

     **F11'e** iki kez bas olduktan sonra şu kod satırına basabilirsiniz:

     `SendMessage(name, a[i]);`

1. yöntemine **adımını atarak F11'e** bir kez daha `SendMessage` basın.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     ![Koda Adımını At için F11 kullanma](../debugger/media/get-started-f11-cpp.png "F10 Içine Adımla")

     F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. (Kodda daha hızlı hareket etmek için size başka seçenekler de gösteriyoruz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../debugger/just-my-code.md)

     Yöntemini incelemeyi tamamlaya kadar yöntemin dışında kalmak ancak hata `SendMessage` ayıklayıcıda kalmak istediğinizi diyelim. Bunu Yapmak için Dışarı **Adımla komutunu kullanın.**

1. Shift   +  **F11 tuşuna** basın (veya **> Adım At) tuşlarına basın.**

     Bu komut, geçerli yöntem veya işlev döndürene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

     yöntem çağrısında `for` duraklatılmış `main` yönteminde döngüsüne geri `SendMessage` dönmeniz gerekir.

1. Yöntem çağrısına geri dönene kadar **F11'e** `SendMessage` birkaç kez basın.

1. Yöntem çağrısında duraklatılmışken, **F10** tuşuna basın (veya Hata ayıkla'> Adım At ) **seçin.**

     ![F10 kullanarak kodun üzerinden adım atma](../debugger/media/get-started-step-over-cpp.png "F10 Adım At")

     Bu kez hata ayıklayıcının yöntemine adım atmalarına dikkat `SendMessage` edin. **F10,** uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı ilerletmektedir (kod yürütülmektedir). Yöntem **çağrısında F10** tuşuna basarak `SendMessage` **(F11** yerine), uygulama kodunu atlamıştık (şu anda `SendMessage` ilgilenmediğimiz bir şey olabilir). Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Tıklarken Çalıştır'ı kullanarak kodda gezinme

1. Kesme **noktasıyla ilerlemek** için F5 tuşuna basın.

1. Kod düzenleyicisinde aşağı kaydırın ve sol tarafta tıklanacak şekilde çalıştır yeşil renkli Tıklanacak Şekilde Çalıştır düğmesi görünene kadar yönteminde `std::wcout` `SendMessage` işlevinin üzerine gelin.  ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick") Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

     ![Tıklarken Çalıştır özelliğini kullanma](../debugger/media/get-started-run-to-click-cpp.png "Tıklanan Satıra Kadar Çalıştır")

   > [!NOTE]
   > Tıklayarak **Çalıştır düğmesi** içinde [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] yenidir. (Yeşil ok düğmesini görmüyorsanız hata ayıklayıcıyı doğru yere ilerlemek için bu örnekte **F11** kullanın.)

2. **Tıklarken Çalıştır düğmesine Tıklayarak** ![Çalıştır'a tıklayın.](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Hata ayıklayıcısı işlevine `std::wcout` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklarken Çalıştır,** uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") Yeniden Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**).

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı, daha önce döngü içinde ayaranı kesme noktası sırasında yeniden `for` durur.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçlarıyla değişkenleri inceleme

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerindendir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. deyimini `name += letters[i]` duraklatırken değişkeninin üzerine `letters` gelin ve varsayılan değeri olduğunu `size={10}` görüyorsunuz.

1. Değişkenin `letters` içerdiği tüm öğeleri içeren özelliklerini görmek için değişkeni genişletin.

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Döngüde birkaç kez tekrarlama, kesme noktası üzerinde yeniden duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F5** 'e (veya Devam Et)'e birkaç kez  >   `for` `name` basın.

     ![Veri ipucu görüntüleme](../debugger/media/get-started-data-tip-cpp.png "Veri İpucu Görüntüleme")

     Değişkenin değeri döngüde her yineleme ile birlikte değişir ve ardından `for` , ardından , ve gibi değerleri `f` `fr` `fre` gösterir.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin, depolamasını beklediğiniz değerleri depolayarak depolamalarının gerekip gerek olmadığını ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek için hızlı bir yol gerekir.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

1. Kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

    Kapalı ise, Hata Ayıkla Windows Autos 'u seçerek hata ayıklayıcıda **duraklatılmış**  >    >  **şekilde açın.**

    Otomatikler **penceresinde** değişkenleri ve bunların geçerli değerini görebilirsiniz. Otomatikler **penceresinde** geçerli satırda veya önceki satırda kullanılan tüm değişkenler gösterilir (Dile özgü davranış için belgeleri kontrol edin).

1. Ardından, Otomatikler **penceresinin** yanındaki sekmede Yereller **penceresine** bakın.

1. Içerdiği `letters` öğeleri göstermek için değişkeni genişletin.

     ![YerelLer Penceresinde değişkenleri inceleme](../debugger/media/get-started-locals-window-cpp.png "YerelLer Penceresi")

    **YerelLer** penceresi, geçerli kapsamda olan, yani [geçerli](https://www.wikipedia.org/wiki/Scope_(computer_science))yürütme bağlamındaki değişkenleri gösterir.

## <a name="set-a-watch"></a>Saat ayarlama

1. Ana kod düzenleyicisi penceresinde değişkenine sağ tıklayın ve İzleme `name` **Ekle'yi seçin.**

    Kod  düzenleyicisinin alt kısmında İzleme penceresi açılır. İzleme penceresi **kullanarak** göz tutmak istediğiniz bir değişken (veya ifade) belirtebilirsiniz.

    Artık değişkende bir izleme kümemiz var ve hata ayıklayıcıda ilerlerken `name` değerinin değişti olduğunu görüyorsunuz. Diğer değişken pencerelerinin aksine, **İzleme** penceresi her zaman izlediğiniz değişkenleri gösterir (kapsam dışında olduğunda bunlar gri renkte olur).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleme

1. Döngüde duraklatılmışken, varsayılan olarak sağ alt bölmede açık `for` olan Çağrı Yığını penceresine tıklayın. 

    Kapalı ise, Windows Çağrı Yığınında Hata Ayıkla'yı seçerek hata ayıklayıcıda **duraklatılmış**  >    >  **şekilde açın.**

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

