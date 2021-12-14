---
title: 'Öğretici: Kodda Visual Basic ayıklama'
description: Visual Studio hata ayıklayıcısının özelliklerini ve hata ayıklayıcıyı başlatmayı, kodda adım adım incelemeyi ve Visual Basic öğrenin.
ms.custom: debug-experiment, vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- VB
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: afcd355961eddd16f2e615473d4496139ef96efb
ms.sourcegitcommit: 5178819f49bb92995bca5c90c90e5fc5a1e04681
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2021
ms.locfileid: "134938275"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak Visual Basic hata ayıklamayı Visual Studio

Bu makalede, Visual Studio hata ayıklayıcısının özellikleri adım adım izlenecek yol açıklanmıştır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü almak için [bkz. İlk olarak hata ayıklayıcıya bakın.](../../debugger/debugger-feature-tour.md) Uygulamanıza *hata ayıklarken* genellikle hata ayıklayıcı eklenmiş olarak çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişip değişmeyişini görmek için değişkenler üzerinde izlemeler ayarlayın, kodunuzun yürütme yolunu inceleyebilirsiniz, bir kod dalını çalıştırıp çalıştırmama gibi. İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi okumadan önce yeni başlayanlar için [hata](../../debugger/debugging-absolute-beginners.md) ayıklama makalesine bakabilirsiniz.

Tanıtım uygulaması Visual Basic olsa da, özelliklerin çoğu C#, C++, F#, Python, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (F# Düzenle ve devamını desteklemez). F# ve JavaScript, Otomatikler **penceresini desteklemez).** Ekran görüntüleri Visual Basic.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Hata ayıklayıcıyı başlat ve kesme noktalarına isabet.
> * Hata ayıklayıcıda kodda adım adım ilerlerken gereken komutları öğrenin
> * Veri ipuçlarında ve hata ayıklayıcı pencerelerde değişkenleri inceleme
> * Çağrı yığınını inceleme

## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

2019 Visual Studio **ve .NET Core** platformlar arası geliştirme iş yükünüz olması gerekir.

::: moniker-end
::: moniker range="vs-2017"

2017 Visual Studio ve .NET Core platformlar arası **geliştirme iş yükünüz olması** gerekir.

::: moniker-end

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidip ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [Visual Studio](https://visualstudio.microsoft.com/downloads) sayfasına gidip ücretsiz yükleyin.

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2022"

Daha önce yüklememiş Visual Studio indirmeler [Visual Studio](https://visualstudio.microsoft.com/downloads) sayfasına gidip ücretsiz yükleyin.

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir .NET Core konsol uygulaması projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda, Visual Basic'yi **genişletin** ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *get-started-debugging adını girin.*

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,  Yeni Visual Studio Yükleyicisi iletişim kutusunun sol bölmesindeki Açık Project **bağlantısını** seçin.

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya girin. Ardından Dil **Visual Basic'yi** seçin ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   ![Arama kutusunda 'konsol' ile yeni proje oluştur penceresini ve Dil ve Platform filtreleri için 'Visual Basic' ve 'Windows' seçili olduğunu gösteren ekran görüntüsü. Konsol Uygulaması proje şablonu seçilidir.](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** *get-started-debugging yazın* **veya Project** girin. Ardından, **Sonraki'yi seçin.**

1. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   Visual Studio projenizi açar.
   
::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya girin. Ardından Dil **Visual Basic'yi** seçin ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uygulayan .NET Core için **Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/get-started-create-console-project.png" alt-text="Arama kutusunda 'konsol' ile yeni proje oluştur penceresini ve Dil ve Platform filtreleri için 'Visual Basic' ve 'Windows' seçili olduğunu gösteren ekran görüntüsü. Konsol Uygulaması proje şablonu seçilidir.":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** *get-started-debugging yazın* **veya Project** girin. Ardından, **Sonraki'yi seçin.**

1. Ek Bilgiler **penceresinde önerilen** hedef çerçevenin (.NET 6.0) olduğundan emin oldu ve oluştur'a **tıklayın.**

   Visual Studio projenizi açar.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

1. *Program.vb içinde,* varsayılan kodun hepsini aşağıdaki kodla değiştirin:

    ```vb
    Imports System

    Class ArrayExample
        Public Shared Sub Main()
            Dim letters As Char() = {"f"c, "r"c, "e"c, "d"c, " "c, "s"c, "m"c, "i"c, "t"c, "h"c}
            Dim name As String = ""
            Dim a As Integer() = New Integer(9) {}

            For i As Integer = 0 To letters.Length - 1
                name += letters(i)
                a(i) = i + 1
                SendMessage(name, a(i))
            Next

            Console.ReadKey()
        End Sub

        Private Shared Sub SendMessage(ByVal name As String, ByVal msg As Integer)
            Console.WriteLine("Hello, " & name & "! Count to " & msg)
        End Sub
    End Class
    ```

## <a name="start-the-debugger"></a>Hata ayıklayıcıyı başlatma!

::: moniker range="<=vs-2019"

1. **F5** (**Hata Ayıklama > Başlat**) veya Hata Ayıklama Araç Çubuğunda Hata  :::image type="icon" source="../../debugger/media/dbg-tour-start-debugging.png"::: Ayıklamayı Başlat düğmesine basın.

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

2. Kırmızı durdurma düğmesine basarak hata ayıklayıcıyı :::image type="icon" source="../../debugger/media/dbg-tour-stop-debugging.png"::: durdurun (**Shift** + **F5**).

3. Konsol penceresinde, konsol penceresini kapatmak için bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2022"

1. **F5** (**Hata Ayıklama > Başlat**) tuşuna basın veya Hata Ayıklama Araç Çubuğundaki Yeşil Hata Ayıklamayı Başlat düğmesini seçin. 

    :::image type="content" source="media/vs-2022/debug-toolbar-start-button.png" alt-text="Yeşil renkli 'Hata Ayıklamayı Başlat' düğmesinin vurgulanmış olduğu Hata Ayıklama Araç Çubuğunu gösteren ekran görüntüsü.":::

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

2. (**Shift** F5 ) tuşlarına basarak veya Hata Ayıklama Araç Çubuğundaki kırmızı Hata Ayıklamayı + Durdur düğmesini seçerek hata ayıklayıcıyı durdurun. 

    :::image type="content" source="media/vs-2022/debug-toolbar-stop-button.png" alt-text="Kırmızı 'Hata Ayıklamayı Durdur' düğmesinin vurgulanmış olduğu Hata Ayıklama Araç Çubuğunu gösteren ekran görüntüsü.":::

3. Konsol penceresinde, konsol penceresini kapatmak için bir tuşa basın.

::: moniker-end
## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

::: moniker range="<=vs-2019"

1. işlevinin `For` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters(i)`

    Kesme noktası :::image type="icon" source="../../debugger/media/dbg-breakpoint.png"::: ayar yakın bir yerde kırmızı bir daire görünür.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerindendir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

2. **F5** tuşuna **basın** veya Hata Ayıklamayı Başlat düğmesine basın; uygulama başlatılır ve hata ayıklayıcı kesme noktası ayarlayıcının ayar bulunduğu :::image type="icon" source="../../debugger/media/dbg-tour-start-debugging.png"::: kod satırına çalışır.

    ![Yürütmenin kesme Visual Studio durdurulmuş kod düzenleyicisi penceresini gösteren ekran görüntüsü.](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Sarı ok, hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (bu deyim henüz yürütülmedi).

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur. Aksi **takdirde, F5** uygulamayı bir sonraki kesme noktasıyla çalıştırmaya devam eder.

    Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Ayar yalnızca koşullu kesme noktaları gibi farklı kesme noktası türleri hakkında bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

::: moniker-end

::: moniker range=">=vs-2022"

1. işlevinin `For` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters(i)`

    Kesme noktası ayar yakın bir yerde kırmızı bir daire görünür.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerinden biridir. bir kesme noktası Visual Studio, çalışan kodunuzun nerede askıya alınacağını gösterir; böylece değişkenlerin değerlerine veya bellek davranışına ya da kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

2. Hata ayıklama araç çubuğundaki **F5** (**Hata Ayıkla > Başlat**) veya hata **ayıklamayı Başlat** düğmesine basın, uygulama başlar ve hata ayıklayıcı, kesme noktasını ayarladığınız kod satırına çalışır.

    :::image type="content" source="media/vs-2022/get-started-hit-breakpoint-vb.png" alt-text="bir kesme noktasında durdurulan Visual Studio kod düzenleyici penceresini gösteren ekran görüntüsü.":::

    Sarı ok, hata ayıklayıcının duraklatıldığı ifadeyi temsil eder ve aynı noktada uygulama yürütmeyi de askıya alır (Bu bildirim henüz yürütülmemiştir).

    Uygulama henüz çalışmıyorsa, **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktasında durmaktadır. Aksi halde, **F5** uygulamayı bir sonraki kesme noktasına çalıştırmaya devam eder.

    Kod satırını veya kodun ayrıntılı olarak incelemek istediğiniz bölümünü bildiğiniz kesme noktaları yararlı bir özelliktir. Koşullu kesme noktaları gibi ayarlayabileceğiniz farklı kesme noktaları türleri hakkında bilgi için bkz. [kesme noktaları kullanma](../../debugger/using-breakpoints.md).

::: moniker-end
## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinin

::: moniker range="<=vs-2019"

Çoğu durumda buradaki klavye kısayollarını kullanıyoruz. Bu, uygulamanızı hata ayıklayıcıda yürütmek için iyi bir yoldur (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. Yöntemdeki döngüde durakladığında `For` `Main` , yöntem çağrısına Ilerlemek için **F11** tuşuna basın (veya **hata ayıklama > adımla**) `SendMessage` .

     **F11** tuşuna iki kez bastıktan sonra şu kod satırında olmalısınız:

     `SendMessage(name, a(i))`

1. Yönteme adım eklemek için bir kez daha **F11** tuşuna basın `SendMessage` .

     Sarı işaretçi `SendMessage` yöntemine ilerler.

     ![' SendMessage ' yöntemine adımlandıktan sonra yürütme duraklatılmış Visual Studio kod düzenleyicisinde hata ayıklama oturumu gösteren ekran görüntüsü.](../visual-basic/media/get-started-f11-vb.png)

     F11, **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. F11, yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md)).

     Yöntemi incelemeyi bitirdiğinizde `SendMessage` ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **SHIFT** + **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     Yöntem `For` çağrısında duraklamış olması için, yöntemde döngüde geri dönüş yapmanız gerekir `Main` `SendMessage` .

1. Yöntem çağrısına tekrar geri gelene kadar **F11** tuşuna birkaç kez basın `SendMessage` .

1. Yöntem çağrısında duraklalarken **F10** tuşuna basın (veya bir kez **Hata Ayıkla > adımla**).

     ![' SendMessage ' yöntem çağrısının üzerinde adımladıktan sonra yürütme duraklatılmış Visual Studio kod düzenleyicisinde hata ayıklama oturumu gösteren ekran görüntüsü.](../visual-basic/media/get-started-step-over-vb.png)

     Hata ayıklayıcının yönteme adımla ilgili bu zamana dikkat edin `SendMessage` . **F10** uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). Yöntem çağrısında **F10** tuşuna basarak `SendMessage` ( **F11** yerine), için uygulama kodu atlandık `SendMessage` (Bu, şu anda ilgilenmiyor olabilir). Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../../debugger/navigating-through-code-with-the-debugger.md).

::: moniker-end

::: moniker range=">=vs-2022"

Bu makalede, klavye kısayollarını kullanacağız, çünkü uygulamanızı hata ayıklayıcıda yürütmek için hızlı bir yoldur (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. Yöntemdeki döngüde durakladığında `For` `Main` , yöntem çağrısına Ilerlemek için **F11** tuşuna basın (veya **hata ayıklama > adımla**) `SendMessage` .

     **F11** tuşuna iki kez bastıktan sonra şu kod satırında olmalısınız:

     `SendMessage(name, a(i))`

1. Yönteme adım eklemek için bir kez daha **F11** tuşuna basın `SendMessage` .

     Sarı işaretçi `SendMessage` yöntemine ilerler.

    :::image type="content" source="media/vs-2022/get-started-f11-vb.png" alt-text="' SendMessage ' yöntemine adımlandıktan sonra yürütme duraklatılmış Visual Studio kod düzenleyicisinde hata ayıklama oturumu gösteren ekran görüntüsü.":::

     **F11** , **adımla** komutuna ve aynı anda uygulama yürütmeyi tek bir ifadeye ilerletir. **F11** , yürütme akışını en ayrıntılı incelemek için iyi bir yoldur. (Kod aracılığıyla daha hızlı hareket etmek için diğer bazı seçenekleri de göstereceğiz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan koddan atlar (daha fazla ayrıntı istiyorsanız, bkz. [yalnızca kendi kodum](../../debugger/just-my-code.md)).

     Yöntemi incelemeyi bitirdiğinizde `SendMessage` ve yönteminden yararlanmak ve hata ayıklayıcıda kalmak istediğinizi varsayalım. Bunu, **Step Out** komutunu kullanarak yapabilirsiniz.

1. **SHIFT** + **F11** tuşuna basın (veya **hata ayıklama > Step Out**).

     Bu komut, geçerli yöntem veya işlev dönene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerletir).

     Yöntem `For` çağrısında duraklamış olması için, yöntemde döngüde geri dönüş yapmanız gerekir `Main` `SendMessage` .

1. Yöntem çağrısına tekrar geri gelene kadar **F11** tuşuna birkaç kez basın `SendMessage` .

1. Yöntem çağrısında duraklalarken **F10** tuşuna basın (veya bir kez **Hata Ayıkla > adımla**).

    :::image type="content" source="media/vs-2022/get-started-step-over-vb.png" alt-text="' SendMessage ' yöntem çağrısının üzerinde adımladıktan sonra yürütme duraklatılmış Visual Studio kod düzenleyicisinde hata ayıklama oturumu gösteren ekran görüntüsü.":::

     Hata ayıklayıcının yönteme adımla ilgili bu zamana dikkat edin `SendMessage` . **F10** uygulama kodunuzda işlevlere veya yöntemlere adımla hata ayıklayıcıyı ilerletir (kod yine de çalıştırılır). Yöntem çağrısında **F10** tuşuna basarak `SendMessage` ( **F11** yerine), için uygulama kodu atlandık `SendMessage` (Bu, şu anda ilgilenmiyor olabilir). Kodunuzda taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [hata ayıklayıcıdaki koda gitme](../../debugger/navigating-through-code-with-the-debugger.md).

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Çalıştırmak için Çalıştır 'ı kullanarak kodu gezin

::: moniker range="<=vs-2019"

1. Kesme noktasına tekrar ilerlemek için **F5** tuşuna basın.

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak düğmenin üzerine gelin ve `Console.WriteLine` `SendMessage` sol tarafta görünen yeşil **çalışma** düğmesine kadar yöntemin üzerine gelin :::image type="icon" source="../../debugger/media/dbg-tour-run-to-click.png"::: . Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

   ![Kod Düzenleyicisi penceresinin sol tarafında bulunan araç ipucuyla birlikte tıklamakta Çalıştır düğmesini gösteren ekran görüntüsü.](../visual-basic/media/get-started-run-to-click-vb.png)

   > [!NOTE]
   > **Tıklama Için Çalıştır düğmesi '** de yenidir [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Yeşil ok düğmesini görmüyorsanız, hata ayıklayıcıyı doğru yere ilerletmek için bu örnekte **F11** kullanın.)

2. **Tıklama Için Çalıştır** düğmesine tıklayın :::image type="icon" source="../../debugger/media/dbg-tour-run-to-click.png"::: .

    Hata ayıklayıcı `Console.WriteLine` yöntemine ilerler.

    Bu düğme kullanıldığında geçici bir kesme noktası ayarlamaya benzer. **' I tıklatarak** , uygulama kodunun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır (herhangi bir açık dosyaya tıklayabilirsiniz).

::: moniker-end

::: moniker range=">=vs-2022"

1. Kesme noktasına tekrar ilerlemek için **F5** tuşuna basın.

1. Kod Düzenleyicisi 'nde, aşağı kaydırarak düğmenin üzerine gelin ve `Console.WriteLine` `SendMessage` sol tarafta görünen yeşil **çalışma** düğmesine kadar yöntemin üzerine gelin. Düğme araç ipucu "yürütmeyi buraya kadar Çalıştır" gösterir.

   :::image type="content" source="media/vs-2022/get-started-run-to-click-vb.png" alt-text="Kod Düzenleyicisi penceresinin sol tarafında bulunan araç ipucuyla birlikte tıklamakta Çalıştır düğmesini gösteren ekran görüntüsü.":::

2. **Tıklama Için Çalıştır** düğmesini seçin.

    Hata ayıklayıcı `Console.WriteLine` yöntemine ilerler.

    Bu düğme kullanıldığında geçici bir kesme noktası ayarlamaya benzer. **' I tıklatarak** , uygulama kodunun görünür bir bölgesi içinde hızlıca elde etmek için kullanışlıdır (herhangi bir açık dosyaya tıklayabilirsiniz).

::: moniker-end

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlıca yeniden başlatın

::: moniker range="<=vs-2019"

 :::image type="icon" source="../../debugger/media/dbg-tour-restart.png"::: Hata ayıklama araç çubuğundaki yeniden Başlat düğmesine tıklayın (**CTRL** + **SHIFT** + **F5**).

**Yeniden Başlat**'a bastığınızda, uygulamanın durdurulması ve hata ayıklayıcının yeniden başlatılması ile zaman kazandırır. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

Hata ayıklayıcı daha önce döngü içinde ayarladığınız kesme noktasında yeniden durmaktadır `For` .

::: moniker-end

::: moniker range=">=vs-2022"

Uygulamanızı yeniden başlatmak için **CTRL**  +  **SHIFT**  +  **F5** tuş birleşimine basın, uygulamayı durdurup hata ayıklayıcıyı yeniden başlatarak zamandan tasarruf edin. Hata ayıklayıcı, kodu yürüterek vuran ilk kesme noktasında duraklatılır.

Hata ayıklayıcı daha önce döngü içinde ayarladığınız kesme noktasında yeniden durmaktadır `For` .

::: moniker-end

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları ile değişkenleri inceleyin

::: moniker range="<=vs-2019"

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en yararlı özelliklerinden biridir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir zamanda sahip olmalarını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz.

1. İfadede duraklalarken `name += letters[i]` , değişkenin üzerine gelin `letters` ve varsayılan değerini, dizideki ilk öğenin değerini görürsünüz `"f"c` .

1. Sonra, değişkenin üzerine gelin `name` ve geçerli değerini boş bir dize olarak görürsünüz.

1. Her seferinde birkaç kez yinelemek için **F5** tuşuna basın (veya **hata ayıklama** > **devam** edin) `For` , kesme noktasında tekrar duraklamanın ve `name` değeri her seferinde, değişkenin üzerine gelindiğinde.

     ![' Name ' değişkeni vurgulanmış ve ' fre ' olarak değeri gösteren bir veri ipucu olan kod düzenleyicisinde hata ayıklama yürütmesinin durdurulduğunu gösteren ekran görüntüsü.](../visual-basic/media/get-started-data-tip-vb.png)

     Değişkenin değeri, döngü her tekrarında değişir ve `For` değerlerini, sonra, vb. gösterir `f` `fr` `fre` .

     Genellikle, hata ayıklarken, değişkenleri üzerinde özellik değerlerini denetlemeye yönelik hızlı bir yol isteyeceksiniz ve bu değerlerin depolanmasını beklediğinizi ve veri ipuçları bunu yapmanın iyi bir yoludur.

::: moniker-end

::: moniker range=">=vs-2022"

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en yararlı özelliklerinden biridir ve bunu yapmak için farklı yollar vardır. Genellikle, bir sorunu ayıklamaya çalıştığınızda, değişkenlerin belirli bir zamanda sahip olmalarını istediğiniz değerleri depolayıp depoladığını bulmaya çalışıyorsunuz.

1. İfadede duraklalarken `name += letters[i]` , değişkenin üzerine gelin `letters` ve varsayılan değerini, dizideki ilk öğenin değerini görürsünüz `"f"c` .

1. Sonra, değişkenin üzerine gelin `name` ve geçerli değerini boş bir dize olarak görürsünüz.

1. Her seferinde birkaç kez yinelemek için **F5** tuşuna basın (veya **hata ayıklama** > **devam** edin) `For` , kesme noktasında tekrar duraklamanın ve `name` değeri her seferinde, değişkenin üzerine gelindiğinde.

     :::image type="content" source="media/vs-2022/get-started-data-tip-vb.png" alt-text="' Name ' değişkeni vurgulanmış ve ' fre ' olarak değeri gösteren bir veri ipucu olan kod düzenleyicisinde hata ayıklama yürütmesinin durdurulduğunu gösteren ekran görüntüsü.":::

     Değişkenin değeri, döngü her tekrarında değişir ve `For` değerlerini, sonra, vb. gösterir `f` `fr` `fre` .

     Genellikle, hata ayıklarken, değişkenleri üzerinde özellik değerlerini denetlemeye yönelik hızlı bir yol isteyeceksiniz ve bu değerlerin depolanmasını beklediğinizi ve veri ipuçları bunu yapmanın iyi bir yoludur.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

::: moniker range="<=vs-2019"

1. Kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

    kapatılmışsa, **hata ayıklayıcıda hata ayıkla** > **Windows** > **oto**' yi seçerek açın.

    **Oto** penceresinde, değişkenleri ve bunların geçerli değerlerini görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

1. Ardından, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresine bakın.

1. Değişkenini, `letters` içerdiği öğeleri göstermek için genişletin.

     ![İçerdiği öğelerin değer ve türünü göstermek için genişletilmiş ' harfler ' değişkeni ile Yereller penceresini gösteren ekran görüntüsü.](../visual-basic/media/get-started-locals-window-vb.png)

    **Yereller** penceresi, geçerli yürütme bağlamı olan geçerli [kapsamda](https://www.wikipedia.org/wiki/Scope_(computer_science))olan değişkenleri gösterir.

::: moniker-end

::: moniker range=">=vs-2022"

1. Kod düzenleyicisinin alt kısmındaki **oto** penceresine bakın.

    kapatılmışsa, **hata ayıklayıcıda hata ayıkla** > **Windows** > **oto**' yi seçerek açın.

    **Oto** penceresinde, değişkenleri ve bunların geçerli değerlerini görürsünüz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

1. Ardından, **Yereller** penceresinin yanındaki bir sekmede **Locals** penceresine bakın.

1. Değişkenini, `letters` içerdiği öğeleri göstermek için genişletin.

    :::image type="content" source="media/vs-2022/get-started-locals-window-vb.png" alt-text="İçerdiği öğelerin değer ve türünü göstermek için genişletilmiş ' harfler ' değişkeni ile Yereller penceresini gösteren ekran görüntüsü.":::

    **Yereller** penceresi, geçerli yürütme bağlamı olan geçerli [kapsamda](https://www.wikipedia.org/wiki/Scope_(computer_science))olan değişkenleri gösterir.

::: moniker-end

## <a name="set-a-watch"></a>İzleme ayarlama

1. Ana kod Düzenleyicisi penceresinde değişkene sağ tıklayın `name` ve **Gözcü Ekle**' yi seçin.

    **İzleme** penceresi, kod düzenleyicisinin en altında açılır. Bir gözü tutmak istediğiniz bir değişken (veya bir ifade) belirtmek için bir **Gözcü** penceresi kullanabilirsiniz.

    Artık değişkende bir izleme kümesi vardır `name` ve hata ayıklayıcıda geçiş yaparken değer değişikliğini görebilirsiniz. Diğer değişken pencerelerinin aksine, **Gözcü** penceresi her zaman izlemekte olduğunuz değişkenleri gösterir (kapsam dışında gri renkte gösterilir).

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

::: moniker range="<=vs-2019"

1. Döngüde durakladığında `For` , varsayılan olarak sağ alt bölmede açık olan **çağrı yığını** penceresine tıklayın.

    kapalıysa, **hata** ayıklayıcı > **Windows** > **çağrı yığını**' nı seçerek hata ayıklayıcıda duraklalarken açın.

2. Yöntemde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın `SendMessage` . **Çağrı yığını** penceresine bakın.

    ![en üst satırda bir SendMessage yöntemi çağrısıyla vurgulanan Visual Studio çağrı yığını penceresini gösteren ekran görüntüsü.](../visual-basic/media/get-started-call-stack-vb.png)

    Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `SendMessage` Bu uygulamadaki yöntemi) gösterilir. İkinci satır, `SendMessage` `Main` yönteminden çağrılan ve bu şekilde devam eden gösterir.

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

    Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu eylem, hata ayıklayıcıyı ilerlemez.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilir, çalışma hata ayıklayıcıyı kullanarak Imleç ' i **Imlece** ilerletebilirsiniz ve kaynak kodu İnceleme ' ye gidebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. Döngüde durakladığında `For` , alt sağ bölmede varsayılan olarak açık olan **çağrı yığını** penceresine tıklayın.

    kapalıysa, **hata** ayıklayıcı > **Windows** > **çağrı yığını**' nı seçerek hata ayıklayıcıda duraklalarken açın.

2. Yöntemde hata ayıklayıcı duraklatıldığını görene kadar birkaç kez **F11** ' e tıklayın `SendMessage` . **Çağrı yığını** penceresine bakın.

    :::image type="content" source="media/vs-2022/get-started-call-stack-vb.png" alt-text="en üst satırda bir SendMessage yöntemi çağrısıyla vurgulanan Visual Studio çağrı yığını penceresini gösteren ekran görüntüsü.":::

    Çağrı yığını penceresi, yöntemlerin ve işlevlerin hangi sırada **çağrılacağını** gösterir. Üstteki satırda geçerli işlev ( `SendMessage` Bu uygulamadaki yöntemi) gösterilir. İkinci satır, `SendMessage` `Main` yönteminden çağrılan ve bu şekilde devam eden gösterir.

   > [!NOTE]
   > **Çağrı yığını** penceresi, tutulma gibi bazı NDES 'Teki hata ayıklama perspektifine benzer.

    Çağrı yığını, bir uygulamanın yürütme akışını incelemek ve anlamak için iyi bir yoldur.

    Bir kod satırına çift tıklayarak bu kaynak koda bakabilir ve ayrıca hata ayıklayıcı tarafından incelenen geçerli kapsamı da değiştirebilirsiniz. Bu eylem, hata ayıklayıcıyı ilerlemez.

    Ayrıca, **çağrı yığını** penceresindeki diğer işlemleri yapmak için sağ tıklama menülerini de kullanabilirsiniz. Örneğin, belirtilen işlevlere kesme noktaları ekleyebilir, çalışma hata ayıklayıcıyı kullanarak Imleç ' i **Imlece** ilerletebilirsiniz ve kaynak kodu İnceleme ' ye gidebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığınını İnceleme](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

## <a name="change-the-execution-flow"></a>Yürütme akışını değiştirme

1. Yöntemi çalıştırmak için **F11** tuşuna iki kez basın `Console.WriteLine` .

1. Yöntem çağrısında hata ayıklayıcı duraklatıldığında `SendMessage` , sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve bir satır aşağı taşıyın `Console.WriteLine` .

1. **F11** tuşuna basın.

    Hata ayıklayıcı yöntemini yeniden çalıştırır `Console.WriteLine` (bunu konsol penceresi çıktısında görürsünüz).

    Yürütme akışını değiştirerek, farklı kod yürütme yollarını test etme veya hata ayıklayıcıyı yeniden başlatmanıza gerek kalmadan kodu yeniden çalıştırma gibi işlemleri yapabilirsiniz.

    > [!WARNING]
    > Genellikle bu özellikle dikkatli olmanız ve araç ipucunda bir uyarı görmeniz gerekir. Diğer uyarıları da görebilirsiniz. İşaretçinin taşınması uygulamanızı önceki bir uygulama durumuna döndüremezsiniz.

1. Uygulamayı çalıştırmaya devam etmek için **F5** tuşuna basın.

    Tebrikler, bu öğreticiyi tamamlama!

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm sağlamak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
