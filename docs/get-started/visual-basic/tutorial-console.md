---
title: 'Öğretici: Kullanmaya başlayın ile Visual Basic'
description: Visual Basic adım Visual Studio konsol uygulamaları oluşturma hakkında bilgi edinin.
ms.custom: vs-acquisition,  get-started
ms.date: 02/10/2021
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
ms.openlocfilehash: a9d8236a1448e61e451e30a7a3c77c6c327ebe03ee195bdf34acb642702dd0ec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121273155"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Öğretici: Kullanmaya başlayın Visual Basic ile Visual Studio

Visual Basic (VB) için bu öğreticide, Visual Studio kullanarak birkaç farklı konsol uygulaması oluşturacak ve çalıştıracak ve siz bunu yaparken Visual Studio tümleşik geliştirme [ortamının (IDE)](visual-studio-ide.md) bazı özelliklerini keşfedebilirsiniz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir uygulama projesi Visual Basic oluşturuz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda, Visual Basic'yi **genişletin** ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *WhatIsYourName adını girin.*

   ![Visual Studio IDE'de Yeni Project iletişim kutusundaki Konsol Uygulaması (.NET Core) Visual Studio şablonu](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,.NET Core platformlar arası geliştirme iş yükünü ekleyerek bu şablonu **edinebilirsiniz.** Makinenize 2017 güncelleştirmelerinin hangi Visual Studio bağlı olarak bu iş yükünü aşağıdaki yöntemlerden birini kullanabilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Project iletişim kutusunu kullanın

1. Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol bölmesindeKimlik aç **Project** tıklayın.

   ![Yeni Dosya iletişim Visual Studio Yükleyicisi Aç bağlantısına Project tıklayın](../media/vs-open-visual-studio-installer-generic.png)

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Görünüm iletişim **kutusundan Project** ve üst menü çubuğunda  Araçlar Araçları ve Özellikleri > **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından, **Windows** listesinden Platform listesinden **Ve Konsol'dan** Seç'i seçin.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Konsol uygulaması Visual Basic şablon seçme":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *WhatIsYourName* yazın **veya Project** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'WhatIsYourName' adını girin":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"Adınız Nedir?" uygulaması oluşturma

Şimdi sizden adınız istenen ve bunu tarih ve saatle birlikte görüntüleyen bir uygulama oluştur bakalım. Aşağıdaki adımları uygulayın:

 ::: moniker range="vs-2017"

1. Henüz açık değilse *WhatIsYourName projenizi* açın.

1. Satırdan sonra Visual Basic köşeli ayraç sonra ve satırdan önce `Sub Main(args As String())` aşağıdaki kodu `End Sub` girin:

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

::: moniker range=">=vs-2019"

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

   ![Adınız Nedir kodunu gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı **derlemek** ve çalıştırmak için yeşil Başlat düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında, adınız girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

   ![Adınız, saat ve tarih'i gösteren Konsol penceresi ve devam etmek için herhangi bir tuşa basın iletisi](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Bunu Hesapla" uygulaması oluşturma

::: moniker range="vs-2017"

1. 2017 Visual Studio i açın ve üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

1. Sol **bölmede yeni Project** iletişim kutusunda, Visual Basic'yi **genişletin** ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından dosyaya *CalculateThis adını girin.*

1. Satır ile satır arasına `Module Program` aşağıdaki kodu `End Module` girin:

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

   Kod pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

   ![CalculateThis kodunu gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı **çalıştırmak için CalculateThis** 'e tıklayın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

    ![Hangi eylemlerin gerçekleştir merkezlerine ek olarak CalculateThis uygulamasını gösteren konsol penceresi.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.** 

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından, **Windows** listesinden Platform listesinden **Ve Konsol'dan** Seç'i seçin.

1. Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   Ardından, Yeni **projenizi yapılandır penceresine** Hesap adı kutusuna *CalculateThis* **Project girin.** Ardından, **Sonraki'yi seçin.**

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

1. Satır ile satır arasına `Module Program` aşağıdaki kodu `End Module` girin:

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

   Kod pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

   ![CalculateThis kodunu gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı **çalıştırmak için CalculateThis** 'e tıklayın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer şekilde görünür:

    ![CalculateThis uygulamasını gösteren konsol penceresi, hangi eylemlerin ele alındığı hakkında istemleri içerir.](media/vb-console-calculate-this.png)

::: moniker-end

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
