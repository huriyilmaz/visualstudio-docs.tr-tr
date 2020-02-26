---
title: 'Öğretici: Visual Basic kullanmaya başlayın'
description: Visual Studio 'da Visual Basic konsol uygulamaları oluşturmayı öğrenin, adım adım.
ms.custom: seodec18, get-started
ms.date: 09/11/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 279bfb00a2466120d21c5c868c0987ec19202acc
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579940"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Öğretici: Visual Studio 'da Visual Basic kullanmaya başlayın

Visual Basic (VB) için bu öğreticide, Visual Studio 'Yu kullanarak birkaç farklı konsol uygulaması oluşturup çalıştırabilir ve bunu yaparken [Visual Studio tümleşik geliştirme ortamının (IDE)](visual-studio-ide.md) bazı özelliklerini keşfedebilirsiniz.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, Visual Basic bir uygulama projesi oluşturacağız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin.

3. Sol bölmedeki **Yeni proje** iletişim kutusunda **Visual Basic**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından projeyi *WhatIsYourName*olarak adlandırın.

   ![Visual Studio IDE 'de yeni proje iletişim kutusundaki konsol uygulaması (.NET Core) proje şablonu](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core platformlar arası geliştirme** iş yükünü ekleyerek buna ulaşabilirsiniz. Makinenizde hangi Visual Studio 2017 güncelleştirmelerinin yüklü olduğuna bağlı olarak, aşağıdaki iki şekilde bu iş yükünü ekleyebilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: yeni proje iletişim kutusunu kullanma

1. **Yeni proje** iletişim kutusunun sol bölmesindeki **Aç Visual Studio yükleyicisi** bağlantısına tıklayın.

   ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi aç bağlantısına tıklayın](../media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2\. seçenek: Araçlar menü çubuğunu kullanma

1. **Yeni proje** iletişim kutusunu iptal edin ve üst menü çubuğundan Araçlar **ve Özellikler al**> **Araçlar** ' ı seçin.

1. Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. Koyu tema kullanmıyorsanız, ancak isterseniz, nasıl yapılacağını öğrenmek için [Visual STUDIO IDE ve düzenleyici 'Yi kişiselleştirme](../../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **Windows** ' u seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması için Visual Basic şablonu seçin (.NET Framework)](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol uygulaması (.NET Core)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Sonra, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *WhatIsYourName* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, ' WhatIsYourName ' projenizi adlandırın](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"Adınız nedir" uygulamanız oluşturun

Sizden adınızı girmenizi isteyen bir uygulama oluşturalım ve Tarih ve saat ile birlikte görüntülüyor. Bunu yapmak için:

 ::: moniker range="vs-2017"

1. Zaten açık değilse *WhatIsYourName* projenizi açın.

1. Aşağıdaki Visual Basic kodunu, `Sub Main(args As String())` satırını izleyen ve `End Sub` satırından önce gelen köşeli ayracından hemen sonra girin:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod, mevcut <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>ve <xref:System.Console.ReadKey%2A> deyimlerinin yerini alır.

   ![Ad kodunuzun ne olduğunu gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı derlemek ve çalıştırmak için yeşil **Başlat** düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

   ![Ne adınız, saat ve tarihin ne olduğunu gösteren konsol penceresi ve ileti devam etmek için herhangi bir tuşa basın](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range="vs-2019"

1. *WhatIsYourName* projesinde, aşağıdaki Visual Basic kodunu, `Sub Main(args As String())` satırını izleyen ve `End Sub` satırından önce olan açılış ayracından hemen sonra girin:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod, mevcut <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>ve <xref:System.Console.ReadKey%2A> deyimlerinin yerini alır.

   ![Ad kodunuzun ne olduğunu gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı derlemek ve çalıştırmak için yeşil **Başlat** düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

   ![Ne adınız, saat ve tarihin ne olduğunu gösteren konsol penceresi ve ileti devam etmek için herhangi bir tuşa basın](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Bu uygulamayı hesapla" uygulamasını oluştur

::: moniker range="vs-2017"

1. Visual Studio 2017 ' i açın ve üst menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin.

1. Sol bölmedeki **Yeni proje** iletişim kutusunda **Visual Basic**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Sonra dosyayı *CalculateThis*olarak adlandırın.

1. `Module Program` satırı ve `End Module` satırı arasına aşağıdaki kodu girin:

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

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **Windows** ' u seçin. 

1. Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   Ardından, **yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *CalculateThis* yazın veya girin. Sonra **Oluştur**' u seçin.

1. `Module Program` satırı ve `End Module` satırı arasına aşağıdaki kodu girin:

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

## <a name="quick-answers-faq"></a>Hızlı yanıtlar SSS

İşte bazı temel kavramları vurgulamak için hızlı bir SSS.

### <a name="what-is-visual-basic"></a>Visual Basic nedir?

Visual Basic, kolayca öğrenilmesi için tasarlanan tür açısından güvenli bir programlama dilidir. TEMEL öğesinden türetilir, bu, "acemi 'ın tüm" bir sembolik yönerge kodu "anlamına gelir.

### <a name="what-is-visual-studio"></a>Visual Studio nedir?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları paketidir. Program ve uygulamalar oluşturmak için kullanabileceğiniz bir program olarak düşünün.

### <a name="what-is-a-console-app"></a>Konsol uygulaması nedir?

Konsol uygulaması giriş alır ve çıktıyı bir komut satırı penceresinde görüntüler, deyişle bir konsol.

### <a name="what-is-net-core"></a>.NET Core nedir?

.NET Core .NET Framework bir sonraki adımdır. .NET Framework, programlama dilleri arasında kod paylaşmanıza izin verdiği durumlarda .NET Core, platformlar arasında kod paylaşma özelliği ekler. Daha da iyisi açık kaynaktır. (Hem .NET Framework hem de .NET Core, önceden oluşturulmuş işlevselliğin kitaplıklarını ve kodunuzun çalıştırılacağı sanal makine görevi gören ortak dil çalışma zamanını (CLR) içerir.)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticiyi tamamlamak Tebrikler! Daha da fazla bilgi edinmek için aşağıdaki öğreticiye bakın.

> [!div class="nextstepaction"]
> [Visual Studio 'da Visual Basic ve .NET Core SDK ile kitaplık oluşturma](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Basic dil izlenecek yolları](/dotnet/visual-basic/walkthroughs)
* [Visual Basic dil başvurusu](/dotnet/visual-basic/language-reference/index)
* [Visual Basic kod dosyaları için IntelliSense](../../ide/visual-basic-specific-intellisense.md)
