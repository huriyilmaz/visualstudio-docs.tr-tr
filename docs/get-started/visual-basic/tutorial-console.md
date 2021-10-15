---
title: 'Öğretici: Kullanmaya başlayın ile Visual Basic'
description: Visual Basic adım Visual Studio konsol uygulamaları oluşturma hakkında bilgi edinin.
ms.custom: vs-acquisition,  get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 2729900aa714e906a4dc32c2fa0d9a8985eb4d47
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431557"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Öğretici: Kullanmaya başlayın Visual Basic ile Visual Studio

Visual Basic (VB) için bu öğreticide, Visual Studio kullanarak birkaç farklı konsol uygulaması oluşturacak ve çalıştıracak ve siz bunu yaparken Visual Studio tümleşik geliştirme [ortamının (IDE)](visual-studio-ide.md) bazı özelliklerini keşfedebilirsiniz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir uygulama projesi Visual Basic oluşturuz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda, Visual Basic genişletin ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *WhatIsYourName adını girin.*

   ![Visual Studio IDE'de Yeni Project iletişim kutusundaki Konsol Uygulaması (.NET Core) Visual Studio şablonu](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,.NET Core platformlar arası geliştirme iş yükünü ekleyerek bu şablonu **edinebilirsiniz.** Makinenize 2017 güncelleştirmelerinin hangi Visual Studio bağlı olarak bu iş yükünü aşağıdaki yöntemlerden birini kullanabilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Project iletişim kutusunu kullanın

1. Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol bölmesindeKimlik aç **Project** tıklayın.

   ![Yeni Visual Studio Yükleyicisi iletişim kutusundan Dosya aç Project tıklayın](../media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Görünüm iletişim **kutusundan Project** ve üst menü çubuğunda Araçlar Araçları **ve** Özellikleri > **Al'ı seçin.**

1. Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje Visual Studio' seçili olarak başlangıç penceresini gösteren ekran görüntüsü.](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından, **Windows** listesinden Platform **listesinden Ve Konsol'dan** Seç'i seçin.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Dil, Platform ve Project Tür filtrelerinde 'Visual Basic', 'Windows', 'Konsol' ve 'Konsol' seçiliyken 'Yeni proje oluştur' penceresini gösteren ekran görüntüsü.":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *WhatIsYourName* yazın **veya Project** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="'Yeni projenizi yapılandır' penceresini, Project alanı 'WhatIsYourName' olarak ayarlanmış şekilde gösteren ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="Hedef Çerçeve alanında .NET Core 3.1'in seçili olduğu 'Ek bilgiler' penceresini gösteren ekran görüntüsü.":::

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="'Yeni proje Visual Studio' seçili olarak başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından, **Windows** türleri listesinden Platform **listesinden** ve Konsol'dan Project seçin.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/vb-create-new-project-console-net-core.png" alt-text="Dil, Platform ve Project Tür filtrelerinde 'Visual Basic', 'Windows', 'Konsol' ve 'Konsol' seçiliyken 'Yeni proje oluştur' penceresini gösteren ekran görüntüsü.":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="'Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi .NET masaüstü **geliştirme iş yükünü** seçin.
   >
   > :::image type="content" source="media/vs-2022/dot-net-core-xplat-dev-workload.png" alt-text="Uygulamanın .NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *WhatIsYourName* yazın **veya Project** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="media/vs-2022/vb-name-your-project-whatname.png" alt-text="'Yeni projenizi yapılandır' penceresini, Project alanı 'WhatIsYourName' olarak ayarlanmış şekilde gösteren ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET 6.0** zaten seçilmiş olması gerekir. Yoksa **.NET 6.0'ı seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="media/vs-2022/vb-target-framework.png" alt-text="Çerçeve alanında .NET 6.0'ın seçili olduğu 'Ek bilgiler' penceresini gösteren ekran görüntüsü.":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"Adınız Nedir?" uygulaması oluşturma

Şimdi sizden adınız istenen ve bunu tarih ve saatle birlikte görüntüleyen bir uygulama oluştur bakalım. Aşağıdaki adımları uygulayın:

 ::: moniker range="vs-2017"

1. Henüz açık değilse *WhatIsYourName projenizi* açın.

1. Satırı takip eden Visual Basic hemen sonra ve satırdan önce aşağıdaki kodu `Sub Main(args As String())` `End Sub` girin:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod, mevcut <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> ve <xref:System.Console.ReadKey%2A> deyimlerini değiştirir.

   ![Adınız Nedir kodunu gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı **derlemek** ve çalıştırmak için yeşil Başlat düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında, adınız girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

   ![Adınız, saat ve tarih'i gösteren Konsol penceresi ve devam etmek için herhangi bir tuşa basın iletisi](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range="vs-2019"

1. *WhatIsYourName projesine,* satırı izleyen açma Visual Basic hemen sonra ve satırdan önce aşağıdaki kodu `Sub Main(args As String())` `End Sub` girin:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod, mevcut <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> ve <xref:System.Console.ReadKey%2A> deyimlerini değiştirir.

   ![Uygulama kodu düzenleyicisine yüklenen 'WhatIsYourName' projesinde 'Program.vb' dosyasının Visual Basic ekran görüntüsü.](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı **derlemek** ve çalıştırmak için yeşil Başlat düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında, adınız girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

   ![Adınız Nedir, saat ve tarih ve herhangi bir tuşa basarak iletileri devam etmek için Konsol penceresini gösteren ekran görüntüsü.](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

::: moniker range=">=vs-2022"

1. *WhatIsYourName* projesine, *program.vb* Visual Basic satırı takip eden açma köşeli ayraçlarının hemen ardından ve satırdan önce aşağıdaki kod `Sub Main(args As String())` kodunu `End Sub` girin:

   ```vb
   Console.WriteLine(vbCrLf + "What is your name? ")
   Dim name = Console.ReadLine()
   Dim currentDate = DateTime.Now
   Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
   Console.Write(vbCrLf + "Press any key to exit... ")
   Console.ReadKey(True)
   ```

   Bu kod, mevcut deyiminin yerini <xref:System.Console.WriteLine%2A> almaktadır.

   :::image type="content" source="media/vs-2022/vb-codewindow-what-name-dark.png" alt-text="Visual Basic kod düzenleyicisinde yüklenen ' WhatIsYourName ' projesindeki ' Program. vb ' dosyası için kodu gösteren ekran görüntüsü.":::

1. İlk uygulamanızı derlemek ve çalıştırmak için yeşil **Başlat** düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

   :::image type="content" source="media/vs-2022/vb-console-what-name.png" alt-text="Konsol penceresine, adınız, saat ve tarihin ne olduğunu gösteren ekran görüntüsü ve iletilere devam etmek için herhangi bir tuşa basın.":::

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Bu uygulamayı hesapla" uygulamasını oluştur

::: moniker range="vs-2017"

1. Visual Studio 2017 ' i açın ve üst menü çubuğundan **dosya** > **yeni** > **Project**' ni seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual Basic**' i genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Sonra dosyayı *CalculateThis* olarak adlandırın.

1. Çizgi ve satır arasında aşağıdaki kodu girin `Module Program` `End Module` :

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Kod pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   ![CalculateThis kodunu gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı çalıştırmak için **CalculateThis** ' a tıklayın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![CalculateThis uygulamasını gösteren konsol penceresi, hangi eylemlerin ele alındığı hakkında istemleri içerir.](media/vb-console-calculate-this.png)

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **yeni proje oluştur** penceresinde, dil listesinden **Visual Basic** ' yi seçin. ardından, proje türleri listesinden Platform listesinden ve **konsolundan** **Windows** ' yi seçin.

1. Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ardından, **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *CalculateThis* yazın veya girin. Ardından **İleri**' yi seçin.

1. **Ek bilgi** penceresinde **.NET Core 3,1** , hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.NET Core 3,1**' i seçin. Ardından **Oluştur**' u seçin.

1. Çizgi ve satır arasına aşağıdaki kodu girin `Module Program` `End Module` :

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Kod pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   ![Visual Basic kod düzenleyicisinde yüklenen ' CalculateThis ' projesindeki ' Program. vb ' dosyası için kodu gösteren ekran görüntüsü.](media/vb-codewindow-calculate-this.png)

1. Programınızı çalıştırmak için **CalculateThis** ' a tıklayın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![CalculateThis uygulamasının konsol penceresini gösteren ekran görüntüsü; bu, hangi eylemlerin ele alındığı hakkında istemleri içerir.](media/vb-console-calculate-this.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **yeni proje oluştur** penceresinde, dil listesinden **Visual Basic** ' yi seçin. sonra, Project türleri listesinden Platform listesinden ve **konsolundan** **Windows** ' yi seçin.

1. Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ardından, **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *CalculateThis* yazın veya girin. Ardından **İleri**' yi seçin.

1. **Ek bilgi** penceresinde, **.net 6,0** hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.net 6,0**' i seçin. Ardından **Oluştur**' u seçin.

1. *Program. vb*' de `Module Program` çizgi ve satır arasına aşağıdaki kodu girin `End Module` :

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Kod pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   :::image type="content" source="media/vs-2022/vb-codewindow-calculate-this.png" alt-text="Visual Basic kod düzenleyicisinde yüklenen ' CalculateThis ' projesindeki ' Program. vb ' dosyası için kodu gösteren ekran görüntüsü.":::

1. Programınızı çalıştırmak için **CalculateThis** ' ın yanındaki yeşil Başlat düğmesini seçin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

   :::image type="content" source="media/vs-2022/vb-console-calculate-this.png" alt-text="CalculateThis uygulamasının konsol penceresini gösteren ekran görüntüsü; bu, hangi eylemlerin ele alındığı hakkında istemleri içerir.":::

::: moniker-end

[!INCLUDE[../includes/git-source-control.md](../includes/git-source-control.md)]

## <a name="quick-answers-faq"></a>Hızlı yanıtlar SSS

İşte bazı temel kavramları vurgulamak için hızlı bir SSS.

### <a name="what-is-visual-basic"></a>Visual Basic nedir?

Visual Basic, kolayca öğrenilmesi için tasarlanan tür açısından güvenli bir programlama dilidir. TEMEL öğesinden türetilir, bu, "acemi 'ın tüm" bir sembolik yönerge kodu "anlamına gelir.

### <a name="what-is-visual-studio"></a>Visual Studio nedir?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları paketidir. Program ve uygulamalar oluşturmak için kullanabileceğiniz bir program olarak düşünün.

### <a name="what-is-a-console-app"></a>Konsol uygulaması nedir?

Konsol uygulaması giriş alır ve çıktıyı konsol olarak da bilinen bir komut satırı penceresinde görüntüler.

### <a name="what-is-net-core"></a>.NET Core nedir?

.NET Core .NET Framework bir sonraki adımdır. .NET Framework, programlama dilleri arasında kod paylaşmanıza izin verdiği durumlarda .net Core, platformlar arasında kod paylaşma özelliği ekler. Daha da iyisi açık kaynaktır. (hem .NET Framework hem de .net Core, önceden oluşturulmuş işlevselliğin kitaplıklarını ve kodunuzun çalıştırılacağı sanal makine görevi gören ortak dil çalışma zamanını (CLR) içerir.)

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamlama! Daha da fazla bilgi edinmek için aşağıdaki öğreticiye bakın.

> [!div class="nextstepaction"]
> [Visual Basic ve .NET Core SDK Visual Studio bir kitaplık oluşturun](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Basic dil izlenecek yolları](/dotnet/visual-basic/walkthroughs)
* [Visual Basic dili başvurusu](/dotnet/visual-basic/language-reference/index)
* [Visual Basic kod dosyaları için ıntellisense](../../ide/visual-basic-specific-intellisense.md)
