---
title: 'Öğretici: Kullanmaya başlayın ile Visual Basic'
description: Visual Basic adım Visual Studio konsol uygulamaları oluşturma hakkında bilgi edinin.
ms.custom: acquisition, seodec18, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 8491869f5c0d518b394c0baa6a6da91bfeb6c7a3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308382"
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

2. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

3. Sol **bölmede Yeni** Proje iletişim kutusunda, Visual Basic genişletin **ve** **ardından .NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *WhatIsYourName adını girin.*

   ![Visual Studio IDE'de Yeni Proje iletişim kutusundaki Konsol Uygulaması (.NET Core) proje şablonu](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,.NET Core platformlar arası geliştirme iş yükünü ekleyerek bu şablonu **edinebilirsiniz.** Makinenize 2017 güncelleştirmelerinin hangi Visual Studio bağlı olarak bu iş yükünü aşağıdaki yöntemlerden birini kullanabilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Proje iletişim kutusunu kullan

1. Yeni **Proje Visual Studio Yükleyicisi** bölmesinin Sol bölmesindeKimlik aç **bağlantısına** tıklayın.

   ![Yeni Proje Visual Studio Yükleyicisi Aç bağlantısına tıklayın](../media/vs-open-visual-studio-installer-generic.png)

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Proje iletişim **kutusundan iptal** edin ve üst menü çubuğunda Araçlar Araçları ve **Özellikleri** > **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından, Platform **listesinden Windows'u** ve **proje** türleri listesinden Konsol'u seçin.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Konsol Visual Basic için uygulama şablonunu seçin":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; varsa, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Proje adı kutusuna *WhatIsYourName* **yazın veya** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'WhatIsYourName' adını girin":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"Adınız Nedir?" uygulaması oluşturma

Şimdi sizden adınız istenen ve bunu tarih ve saatle birlikte görüntüleyen bir uygulama oluştur bakalım. Aşağıdaki adımları uygulayın:

 ::: moniker range="vs-2017"

1. Henüz açık değilse *WhatIsYourName projenizi* açın.

1. Aşağıdaki kodu Visual Basic sonra, satırı takip eden köşeli ayraç ve `Sub Main(args As String())` satırdan önce `End Sub` girin:

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

   ![Adınız, saat ve tarihi gösteren Konsol penceresi ve devam etmek için herhangi bir tuşa basın iletisi](media/vb-console-what-name.png)

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

   ![Adınız, saat ve tarihi gösteren Konsol penceresi ve devam etmek için herhangi bir tuşa basın iletisi](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Bunu Hesapla" uygulaması oluşturma

::: moniker range="vs-2017"

1. 2017 Visual Studio i açın ve üst menü çubuğundan  Dosya Yeni > **Proje'yi** > **seçin.**

1. Sol **bölmede Yeni** Proje iletişim kutusunda, Visual Basic genişletin **ve** **ardından .NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından dosyaya *CalculateThis adını girin.*

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

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından, Platform **listesinden Windows'u** ve **proje** türleri listesinden Konsol'u seçin.

1. Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   Ardından, Yeni **projenizi yapılandır penceresine** Proje adı kutusuna *CalculateThis* **yazın veya** girin. Ardından, **Sonraki'yi seçin.**

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

    ![Hangi eylemlerin gerçekleştir merkezlerine ek olarak CalculateThis uygulamasını gösteren konsol penceresi.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar hakkında SSS

Bazı temel kavramları vurgulamak için burada hızlı bir SSS bulabilirsiniz.

### <a name="what-is-visual-basic"></a>Hangi Visual Basic?

Visual Basic kolay öğrenilen bir programlama dilidir. BASIC'den türetilen bu, "Yeni Başlayanlar için Çok Amaçlı Sembolik Yönerge Kodu" anlamına gelir.

### <a name="what-is-visual-studio"></a>Hangi Visual Studio?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları geliştirme paketidir. Bunu program ve uygulama oluşturmak için kullanabileceğiniz bir program olarak düşün.

### <a name="what-is-a-console-app"></a>Konsol uygulaması nedir?

Konsol uygulaması girişi alır ve çıkışı konsol olarak da bilinen bir komut satırı penceresinde görüntüler.

### <a name="what-is-net-core"></a>.NET Core nedir?

.NET Core, bir sonraki adımdır ve .NET Framework. .NET Core.NET Framework programlama dillerinde kod paylaşma iznini verdi. .NET Core, farklı platformlarda kod paylaşma olanağı sunar. Daha da iyisi açık kaynaktır. (Hem .NET Framework hem de .NET Core, önceden oluşturulmuş işlevsellik kitaplıklarının yanı sıra kodunuzun çalıştırılyacağı bir sanal makine işlevi de içeren ortak dil çalışma zamanı (CLR) içerir.)

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! Daha da fazla bilgi edinmek için aşağıdaki öğreticiye bakın.

> [!div class="nextstepaction"]
> [.NET Core SDK'de Visual Basic ve .NET Core SDK kitaplık Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Basic dil kılavuzlar](/dotnet/visual-basic/walkthroughs)
* [Visual Basic dili başvurusu](/dotnet/visual-basic/language-reference/index)
* [Kod dosyalarını Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md)
