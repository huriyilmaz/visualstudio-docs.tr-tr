---
title: 'Öğretici: Visual Basic kullanmaya başlayın'
description: Visual Studio 'da Visual Basic konsol uygulamaları oluşturmayı öğrenin, adım adım.
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
ms.openlocfilehash: cc9557c4b7558488fd8757d3c50920debe134568
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112467"
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

2. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

3. Sol bölmedeki **Yeni proje** iletişim kutusunda **Visual Basic**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından projeyi *WhatIsYourName* olarak adlandırın.

   ![Visual Studio IDE 'de yeni proje iletişim kutusundaki konsol uygulaması (.NET Core) proje şablonu](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core platformlar arası geliştirme** iş yükünü ekleyerek buna ulaşabilirsiniz. Makinenizde hangi Visual Studio 2017 güncelleştirmelerinin yüklü olduğuna bağlı olarak, aşağıdaki iki şekilde bu iş yükünü ekleyebilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: yeni proje iletişim kutusunu kullanma

1. **Yeni proje** iletişim kutusunun sol bölmesindeki **Aç Visual Studio yükleyicisi** bağlantısına tıklayın.

   ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi aç bağlantısına tıklayın](../media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. seçenek: Araçlar menü çubuğunu kullanma

1. **Yeni proje** iletişim kutusunu iptal edin ve üst menü çubuğundan **Araçlar** > **Araçlar ve Özellikler al**' ı seçin.

1. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. Koyu tema kullanmıyorsanız, ancak isterseniz, nasıl yapılacağını öğrenmek için [Visual STUDIO IDE ve düzenleyici 'Yi kişiselleştirme](../../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, dil listesinden **Visual Basic** ' yi seçin. Ardından, proje türleri listesinden platform listesinden ve **konsolundan** **Windows** ' u seçin.

   Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Konsol uygulaması için Visual Basic şablonu seçin":::

   > [!NOTE]
   > **Konsol uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Sonra, Visual Studio Yükleyicisi **.NET Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .NET Core platformlar arası geliştirme iş yükü](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *WhatIsYourName* yazın veya girin. Ardından **İleri**' yi seçin.

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="' yeni projenizi yapılandırın ' penceresinde, ' WhatIsYourName ' projenizi adlandırın":::

1. **Ek bilgi** penceresinde **.NET Core 3,1** , hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.NET Core 3,1**' i seçin. Ardından **Oluştur**' u seçin.

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="' Ek bilgi ' penceresinde, .NET Core 3,1 ' ın seçili olduğundan emin olun":::

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"Adınız nedir" uygulamanız oluşturun

Sizden adınızı girmenizi isteyen bir uygulama oluşturalım ve Tarih ve saat ile birlikte görüntülüyor. Aşağıdaki adımları uygulayın:

 ::: moniker range="vs-2017"

1. Zaten açık değilse *WhatIsYourName* projenizi açın.

1. Satırı izleyen açılış ayracından hemen sonra aşağıdaki Visual Basic kodu girin `Sub Main(args As String())` `End Sub` :

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod, var olan <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> ve deyimlerinin yerini alır <xref:System.Console.ReadKey%2A> .

   ![Ad kodunuzun ne olduğunu gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı derlemek ve çalıştırmak için yeşil **Başlat** düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

   ![Ne adınız, saat ve tarihin ne olduğunu gösteren konsol penceresi ve ileti devam etmek için herhangi bir tuşa basın](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range="vs-2019"

1. *WhatIsYourName* projesinde, satırı izleyen açılış ayracından hemen sonra aşağıdaki Visual Basic kodu girin `Sub Main(args As String())` `End Sub` :

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod, var olan <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> ve deyimlerinin yerini alır <xref:System.Console.ReadKey%2A> .

   ![Ad kodunuzun ne olduğunu gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. İlk uygulamanızı derlemek ve çalıştırmak için yeşil **Başlat** düğmesini kullanın veya **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

   ![Ne adınız, saat ve tarihin ne olduğunu gösteren konsol penceresi ve ileti devam etmek için herhangi bir tuşa basın](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Bu uygulamayı hesapla" uygulamasını oluştur

::: moniker range="vs-2017"

1. Visual Studio 2017 ' i açın ve üst menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

1. Sol bölmedeki **Yeni proje** iletişim kutusunda **Visual Basic**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Sonra dosyayı *CalculateThis* olarak adlandırın.

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

   ![CalculateThis kodunu gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı çalıştırmak için **CalculateThis** ' a tıklayın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![CalculateThis uygulamasını gösteren konsol penceresi, hangi eylemlerin ele alındığı hakkında istemleri içerir.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin. 

1. **Yeni proje oluştur** penceresinde, dil listesinden **Visual Basic** ' yi seçin. Ardından, proje türleri listesinden platform listesinden ve **konsolundan** **Windows** ' u seçin.

1. Dili, platformu ve proje türü filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   Ardından, **yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *CalculateThis* yazın veya girin. Ardından **İleri**' yi seçin.

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

   ![CalculateThis kodunu gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı çalıştırmak için **CalculateThis** ' a tıklayın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer görünmelidir:

    ![CalculateThis uygulamasını gösteren konsol penceresi, hangi eylemlerin ele alındığı hakkında istemleri içerir.](media/vb-console-calculate-this.png)

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

.NET Core, bir sonraki adımdır ve .NET Framework. .NET Core.NET Framework programlama dilleri arasında kod paylaşma iznini verdi. .NET Core, farklı platformlarda kod paylaşma olanağı sunar. Daha da iyisi açık kaynaktır. (Hem .NET Framework hem de .NET Core, önceden oluşturulmuş işlevsellik kitaplıklarının yanı sıra kodunuzun çalıştırılyacağı bir sanal makine işlevi de içeren ortak dil çalışma zamanı (CLR) içerir.)

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! Daha da fazla bilgi edinmek için aşağıdaki öğreticiye bakın.

> [!div class="nextstepaction"]
> [.NET Core SDK'de Visual Basic ve .NET Core SDK kitaplık Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Basic dil kılavuzlar](/dotnet/visual-basic/walkthroughs)
* [Visual Basic dili başvurusu](/dotnet/visual-basic/language-reference/index)
* [Kod dosyalarını Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md)
