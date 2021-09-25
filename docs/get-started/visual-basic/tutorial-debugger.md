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
ms.openlocfilehash: cf02a169d775c2fb8391ee3c700f726c7462c660
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429626"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Öğretici: Visual Studio kullanarak Visual Basic hata ayıklamayı Visual Studio

Bu makalede, Visual Studio hata ayıklayıcısının özellikleri adım adım izlenecek yol açıklanmıştır. Hata ayıklayıcı özelliklerinin daha üst düzey bir görünümünü almak için [bkz. İlk olarak hata ayıklayıcıya bakın.](../../debugger/debugger-feature-tour.md) Uygulamanıza *hata ayıklarken,* genellikle hata ayıklayıcı eklenmiş olarak çalıştırabilirsiniz. Bunu yaparken hata ayıklayıcı, kodunuzun çalışırken ne yaptığını görmek için birçok yol sağlar. Kodunuzu adım adım inceleyebilirsiniz ve değişkenlerde depolanan değerlere göz atabilir, değerlerin ne zaman değişip değişmeyişini görmek için değişkenler üzerinde izlemeler ayarlayın, kodunuzun yürütme yolunu inceleyebilirsiniz, bir kod dalını çalıştırıp çalıştırmama gibi. İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi okumadan önce yeni başlayanlar için [Hata](../../debugger/debugging-absolute-beginners.md) Ayıklama makalesine bakabilirsiniz.

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

2017 Visual Studio ve .NET Core platformlar arası geliştirme **iş yükünüz olması** gerekir.

::: moniker-end

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2022"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir .NET Core konsol uygulaması projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda, Visual Basic'yi **genişletin** ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *get-started-debugging adını girin.*

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,  Yeni Visual Studio Yükleyicisi iletişim kutusunun sol bölmesindeki  Açık Project seçin.

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya girin. Ardından Dil **Visual Basic'yi** seçin ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   ![Arama kutusunda 'konsol' ve Dil ve Platform filtreleri için 'Visual Basic' ve 'Windows' seçilmiş yeni proje oluştur penceresini gösteren ekran görüntüsü. Konsol Uygulaması proje şablonu seçilidir.](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** *get-started-debugging yazın* **veya Project girin.** Ardından, **Sonraki'yi seçin.**

1. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   Visual Studio projenizi açar.
   
::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

   Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne** > **tıklayın.**

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya girin. Ardından Dil **Visual Basic'yi** seçin ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uygulayan .NET Core **için Konsol** Uygulaması şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/get-started-create-console-project.png" alt-text="Arama kutusunda 'konsol' ve Dil ve Platform filtreleri için 'Visual Basic' ve 'Windows' seçilmiş yeni proje oluştur penceresini gösteren ekran görüntüsü. Konsol Uygulaması proje şablonu seçilidir.":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin. Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.

1. Yeni **projenizi yapılandır penceresine** *get-started-debugging yazın* **veya Project girin.** Ardından, **Sonraki'yi seçin.**

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

1. **F5** (**Hata Ayıklama > Hata Ayıklamayı** Başlat ) veya Hata Ayıklama Araç Çubuğunda Hata  :::image type="icon" source="../../debugger/media/dbg-tour-start-debugging.png"::: Ayıklamayı Başlat düğmesine basın.

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

     Bu öğreticide hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından bakacak ve hata ayıklayıcı özelliklerine göz atalım.

2. Kırmızı durdurma düğmesine basarak hata ayıklayıcıyı :::image type="icon" source="../../debugger/media/dbg-tour-stop-debugging.png"::: durdurun (**Shift** + **F5**).

3. Konsol penceresinde, konsol penceresini kapatmak için bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2022"

1. **F5 tuşuna** basın (**Hata > Hata Ayıklamayı** Başlat ) veya Hata Ayıklama Araç Çubuğundaki Yeşil Hata Ayıklamayı Başlat düğmesini seçin. 

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

    Bu öğreticide hata ayıklayıcıyı kullanarak bu uygulamaya daha yakından bakacak ve hata ayıklayıcı özelliklerine göz atalım.

2. (**Shift** F5 ) tuşlarına basarak veya Hata Ayıklama Araç Çubuğundaki kırmızı Hata + Ayıklamayı Durdur düğmesini seçerek hata ayıklayıcıyı durdurun. 

    :::image type="content" source="media/vs-2022/debug-toolbar-stop-button.png" alt-text="Kırmızı 'Hata Ayıklamayı Durdur' düğmesinin vurgulanmış olduğu Hata Ayıklama Araç Çubuğunu gösteren ekran görüntüsü.":::

3. Konsol penceresinde, konsol penceresini kapatmak için bir tuşa basın.

::: moniker-end
## <a name="set-a-breakpoint-and-start-the-debugger"></a>Kesme noktası ayarlama ve hata ayıklayıcıyı başlatma

::: moniker range="<=vs-2019"

1. işlevinin `For` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters(i)`

    Kesme noktası :::image type="icon" source="../../debugger/media/dbg-breakpoint.png"::: ayarda kırmızı bir daire görünür.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerindendir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

2. **F5** tuşuna **basın** veya Hata Ayıklamayı Başlat düğmesine basın; uygulama başlatılır ve hata ayıklayıcı kesme noktası ayarlayıcının ayar bulunduğu :::image type="icon" source="../../debugger/media/dbg-tour-start-debugging.png"::: kod satırına çalışır.

    ![Yürütmenin kesme Visual Studio durdurulmuş kod düzenleyicisi penceresini gösteren ekran görüntüsü.](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Sarı ok, aynı noktada uygulama yürütmeyi de askıya alan (bu deyim henüz yürütülmedi) hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder.

     Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur. Aksi **takdirde, F5** uygulamayı bir sonraki kesme noktasıyla çalıştırmaya devam eder.

    Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Ayar yalnızca koşullu kesme noktaları gibi farklı kesme noktası türleri hakkında bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

::: moniker-end

::: moniker range=">=vs-2022"

1. işlevinin `For` `Main` döngüsünde, aşağıdaki kod satırın sol kenar boşluğuna tıklayarak bir kesme noktası ayarlayın:

    `name += letters(i)`

    Kesme noktası ayarda kırmızı bir daire görünür.

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliklerindendir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

2. **F5** (**Hata Ayıkla >** Hata Ayıklamayı  Başlat ) veya Hata Ayıklama Araç Çubuğunda Hata Ayıklamayı Başlat düğmesine basın, uygulama başlatılır ve hata ayıklayıcı kesme noktası ayar istediğiniz kod satırına çalışır.

    :::image type="content" source="media/vs-2022/get-started-hit-breakpoint-vb.png" alt-text="Yürütmenin kesme Visual Studio durdurulmuş kod düzenleyicisi penceresini gösteren ekran görüntüsü.":::

    Sarı ok, aynı noktada uygulama yürütmeyi de askıya alan (bu deyim henüz yürütülmedi) hata ayıklayıcının duraklatılmış olduğu deyimi temsil eder.

    Uygulama henüz çalışmıyorsa **F5** hata ayıklayıcıyı başlatır ve ilk kesme noktası üzerinde durur. Aksi **takdirde, F5** uygulamayı bir sonraki kesme noktasıyla çalıştırmaya devam eder.

    Kesme noktaları, kod satırı veya ayrıntılı incelemek istediğiniz kod bölümünü biliyorken yararlı bir özelliktir. Ayar yalnızca koşullu kesme noktaları gibi farklı kesme noktası türleri hakkında bilgi için [bkz. Kesme noktaları kullanma.](../../debugger/using-breakpoints.md)

::: moniker-end
## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Adım komutlarını kullanarak hata ayıklayıcıda kodda gezinme

::: moniker range="<=vs-2019"

Genellikle burada klavye kısayollarını kullanırız çünkü bu, uygulamanızı hata ayıklayıcısında yürütmenin hızlı bir yolu olduğundan (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. yönteminde döngüsünde duraklatılmışken, yöntem çağrısına ilerlemek için F11 tuşuna basın (veya hata ayıkla > `For` `Main` **Adımla)**  `SendMessage` seçin.

     **F11'e** iki kez bas olduktan sonra şu kod satırına basabilirsiniz:

     `SendMessage(name, a(i))`

1. yöntemine **adımını atarak F11'e** bir kez daha `SendMessage` basın.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

     !['SendMessage' yöntemine adımlamadan sonra Visual Studio duraklatılmış bir kod düzenleyicisinde hata ayıklama oturumunu gösteren ekran görüntüsü.](../visual-basic/media/get-started-f11-vb.png)

     F11, **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. F11, yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. (Kodda daha hızlı hareket etmek için size başka seçenekler de gösteriyoruz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../../debugger/just-my-code.md)

     Yöntemini incelemeyi tamamlayanın ve yöntemin dışında kalmak ancak hata `SendMessage` ayıklayıcısında kalmak istediğinizi diyelim. Bunu Yapmak için Dışarı **Adımla komutunu kullanın.**

1. Shift  + **F11 tuşuna** basın (veya **> AdımLa) tuşlarına basın.**

     Bu komut, geçerli yöntem veya işlev döndürene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

     yöntem çağrısında `For` duraklatılmış `Main` yönteminde döngüsüne geri `SendMessage` dönmeniz gerekir.

1. Yöntem çağrısına geri dönene kadar **F11'e** `SendMessage` birkaç kez basın.

1. Yöntem çağrısında duraklatılmışken, **F10** tuşuna basın (veya Hata ayıkla'> **Adım At**) seçin.

     !['SendMessage' yöntem çağrısının üzerinden Visual Studio yürütmenin duraklatılmasıyla birlikte kod düzenleyicisinde hata ayıklama oturumunu gösteren ekran görüntüsü.](../visual-basic/media/get-started-step-over-vb.png)

     Bu kez hata ayıklayıcının yöntemine adım atmalarına dikkat `SendMessage` edin. **F10,** uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı ilerletmektedir (kod yürütülmektedir). Yöntem **çağrısında F10'a** basarak `SendMessage` **(F11** yerine), uygulama kodunu atlamıştık (şu anda `SendMessage` ilgilenmediğimiz bir şey olabilir). Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

::: moniker range=">=vs-2022"

Bu makalede, uygulamanızı hata ayıklayıcıda yürütmede hızlı bir şekilde çalışmanın iyi bir yolu olduğundan klavye kısayollarını kullanacağız (menü komutları gibi eşdeğer komutlar parantez içinde gösterilir).

1. yönteminde döngüsünde duraklatılmışken, yöntem çağrısına ilerlemek için F11 tuşuna basın (veya hata ayıkla > `For` `Main` **Adımla)**  `SendMessage` seçin.

     **F11'e** iki kez bas olduktan sonra şu kod satırına basabilirsiniz:

     `SendMessage(name, a(i))`

1. yöntemine **adımını atarak F11'e** bir kez daha `SendMessage` basın.

     Sarı işaretçi yöntemine `SendMessage` ilerler.

    :::image type="content" source="media/vs-2022/get-started-f11-vb.png" alt-text="'SendMessage' yöntemine adımlamadan sonra Visual Studio duraklatılmış bir kod düzenleyicisinde hata ayıklama oturumunu gösteren ekran görüntüsü.":::

     **F11,** **Adımla komutudır** ve uygulama yürütmeyi tek tek bir deyimle ilerleter. **F11,** yürütme akışını en ayrıntılı şekilde incelemek için iyi bir yol sağlar. (Kodda daha hızlı hareket etmek için size başka seçenekler de gösteriyoruz.) Varsayılan olarak, hata ayıklayıcı kullanıcı olmayan kodu atlar (daha fazla ayrıntı için bkz. [Yalnızca kendi kodum).](../../debugger/just-my-code.md)

     Yöntemini incelemeyi tamamlayanın ve yöntemin dışında kalmak ancak hata `SendMessage` ayıklayıcısında kalmak istediğinizi diyelim. Bunu Yapmak için Dışarı **Adımla komutunu kullanın.**

1. Shift  + **F11 tuşuna** basın (veya **> AdımLa) tuşlarına basın.**

     Bu komut, geçerli yöntem veya işlev döndürene kadar uygulama yürütmeyi sürdürür (ve hata ayıklayıcıyı ilerleter).

     yöntem çağrısında `For` duraklatılmış `Main` yönteminde döngüsüne geri `SendMessage` dönmeniz gerekir.

1. Yöntem çağrısına geri dönene kadar **F11'e** `SendMessage` birkaç kez basın.

1. Yöntem çağrısında duraklatılmışken, **F10** tuşuna basın (veya Hata ayıkla'> **Adım At**) seçin.

    :::image type="content" source="media/vs-2022/get-started-step-over-vb.png" alt-text="'SendMessage' yöntem çağrısının üzerinden Visual Studio yürütmenin duraklatılmasıyla birlikte kod düzenleyicisinde hata ayıklama oturumunu gösteren ekran görüntüsü.":::

     Bu kez hata ayıklayıcının yöntemine adım atmalarına dikkat `SendMessage` edin. **F10,** uygulama kodundaki işlevlere veya yöntemlere adımlamadan hata ayıklayıcıyı ilerletmektedir (kod yürütülmektedir). Yöntem **çağrısında F10'a** basarak `SendMessage` **(F11** yerine), uygulama kodunu atlamıştık (şu anda `SendMessage` ilgilenmediğimiz bir şey olabilir). Kodunuz arasında taşımanın farklı yolları hakkında daha fazla bilgi için bkz. [Hata ayıklayıcısında kodda gezinme.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Tıklarken Çalıştır'ı kullanarak kodda gezinme

::: moniker range="<=vs-2019"

1. Kesme **noktası tekrar ilerlemek** için F5 tuşuna basın.

1. Kod düzenleyicisinde aşağı kaydırın ve sol tarafta yeşil Renkli Çalıştır düğmesi görünene kadar yönteminde `Console.WriteLine` `SendMessage`  :::image type="icon" source="../../debugger/media/dbg-tour-run-to-click.png"::: yönteminin üzerine gelin. Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

   ![Kod düzenleyicisi penceresinin sol tarafında araç ipucu vurgulanmış Şekilde Tıklanana Kadar Çalıştır düğmesini gösteren ekran görüntüsü.](../visual-basic/media/get-started-run-to-click-vb.png)

   > [!NOTE]
   > Tıklayarak **Çalıştır düğmesi** içinde [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] yenidir. (Yeşil ok düğmesini görmüyorsanız hata ayıklayıcıyı doğru yere ilerlemek için bu örnekte **F11** kullanın.)

2. **Tıklarken Çalıştır düğmesine** :::image type="icon" source="../../debugger/media/dbg-tour-run-to-click.png"::: tıklayın.

    Hata ayıklayıcısı yöntemine `Console.WriteLine` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklarken Çalıştır,** uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

::: moniker-end

::: moniker range=">=vs-2022"

1. Kesme **noktası tekrar ilerlemek** için F5 tuşuna basın.

1. Kod düzenleyicisinde aşağı kaydırın ve sol tarafta yeşil Renkli Çalıştır düğmesi görünene kadar yönteminde `Console.WriteLine` `SendMessage` yönteminin üzerine gelin.  Düğmenin araç ipucu "Yürütmeyi buraya kadar çalıştır" ifadesini gösterir.

   :::image type="content" source="media/vs-2022/get-started-run-to-click-vb.png" alt-text="Kod düzenleyicisi penceresinin sol tarafında araç ipucu vurgulanmış Şekilde Tıklanana Kadar Çalıştır düğmesini gösteren ekran görüntüsü.":::

2. **Tıklarken Çalıştır düğmesini** seçin.

    Hata ayıklayıcısı yöntemine `Console.WriteLine` ilerler.

    Bu düğmeyi kullanmak, geçici bir kesme noktası ayarlamaya benzer. **Tıklarken Çalıştır,** uygulama kodunun görünür bir bölgesi içinde hızlıca dolaşarak (herhangi bir açık dosyaya tıklarsınız) kullanışlıdır.

::: moniker-end

## <a name="restart-your-app-quickly"></a>Hızlı bir şekilde uygulamayı yeniden başlatın

::: moniker range="<=vs-2019"

Hata Ayıklama **Araç Çubuğunda** Yeniden Başlat düğmesine tıklayın :::image type="icon" source="../../debugger/media/dbg-tour-restart.png"::: (**Ctrl** + **Shift** + **F5**).

Yeniden **Başlat'a bassanız,** uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı, daha önce döngü içinde ayaranı kesme noktası sırasında yeniden `For` durur.

::: moniker-end

::: moniker range=">=vs-2022"

Uygulamanızı yeniden başlatmak için **Ctrl**  +  **Shift**  +  **F5** tuş bileşimine basarak uygulamayı durdurmak ve hata ayıklayıcıyı yeniden başlatmak yerine zamandan tasarruf sağlar. Hata ayıklayıcısı, kod yürüterek isabet alan ilk kesme noktası üzerinde duraklatılır.

Hata ayıklayıcı, daha önce döngü içinde ayaranı kesme noktası sırasında yeniden `For` durur.

::: moniker-end

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçlarıyla değişkenleri inceleme

::: moniker range="<=vs-2019"

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerindendir ve bunu yapmak için farklı yollar vardır. Genellikle bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. deyiminde duraklatılmışken değişkeninin üzerine gelin ve varsayılan değerini( dizideki `name += letters[i]` `letters` ilk öğenin değeri) `"f"c` görüyorsunuz.

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Döngüde birkaç  kez tekrarlama, kesme noktası üzerinde yeniden duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F5** 'e (veya Devam Et)'e birkaç kez >  `For` `name` basın.

     ![Kod düzenleyicisinde 'name' değişkeninin vurgulanmış olduğu ve değerin 'fre' olarak gösteren bir veri ipucuyla durdurulmuş hata ayıklama yürütmeyi gösteren ekran görüntüsü.](../visual-basic/media/get-started-data-tip-vb.png)

     Değişkenin değeri döngüde her yineleme ile birlikte değişir ve ardından `For` , ve gibi değerleri `f` `fr` `fre` gösterir.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin hızlı bir yolunu, depolamasını beklediğiniz değerleri depolayarak depolamalarını isteyip istemediklerini ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek istersiniz.

::: moniker-end

::: moniker range=">=vs-2022"

Değişkenleri incelemenizi sağlayan özellikler, hata ayıklayıcının en kullanışlı özelliklerindendir ve bunu yapmak için farklı yollar vardır. Genellikle bir sorunda hata ayıklamaya çalışırken değişkenlerin belirli bir zamanda sahip olmasını beklediğiniz değerleri depolayarak depolamaya çalışmaya çalıştığınız olur.

1. deyiminde duraklatılmışken değişkeninin üzerine gelin ve varsayılan değerini( dizideki `name += letters[i]` `letters` ilk öğenin değeri) `"f"c` görüyorsunuz.

1. Ardından değişkeninin `name` üzerine gelin ve geçerli değerinin boş bir dize olduğunu görüyorsunuz.

1. Döngüde birkaç  kez tekrarlama, kesme noktası üzerinde yeniden duraklatma ve değerini kontrol etmek için her zaman değişkenin üzerine gelme için **F5** 'e (veya Devam Et)'e birkaç kez >  `For` `name` basın.

     :::image type="content" source="media/vs-2022/get-started-data-tip-vb.png" alt-text="Kod düzenleyicisinde 'name' değişkeninin vurgulanmış olduğu ve değerin 'fre' olarak gösteren bir veri ipucuyla durdurulmuş hata ayıklama yürütmeyi gösteren ekran görüntüsü.":::

     Değişkenin değeri döngüde her yineleme ile birlikte değişir ve ardından `For` , ve gibi değerleri `f` `fr` `fre` gösterir.

     Hata ayıklama sırasında genellikle değişkenlerde özellik değerlerini denetlemenin hızlı bir yolunu, depolamasını beklediğiniz değerleri depolayarak depolamalarını isteyip istemediklerini ve veri ipuçlarının bunu yapmak için iyi bir yol olup olmadığını görmek istersiniz.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencereleriyle değişkenleri inceleme

::: moniker range="<=vs-2019"

1. Kod **düzenleyicisinin en** altındaki Otomatikler penceresine bakın.

    Kapalı ise Hata Ayıkla'ya ve Otomatik'e  göre hata ayıkla'Windows >  > **ayıklayıcıda duraklatılmış olarak açın.**

    Otomatikler **penceresinde** değişkenleri ve bunların geçerli değerini görebilirsiniz. **Oto** penceresi, geçerli satırda veya önceki satırda kullanılan tüm değişkenleri gösterir (dile özgü davranışa yönelik belgelere bakın).

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

1. Yöntem çağrısında hata ayıklayıcı duraklatıldığında `SendMessage` , sol taraftaki sarı oku (yürütme işaretçisi) almak için fareyi kullanın ve taşıyın `Console.WriteLine` .

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
