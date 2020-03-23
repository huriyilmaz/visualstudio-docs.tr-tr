---
title: 'Öğretici: Visual Basic ile başlayın'
description: Visual Studio'da Visual Basic konsol uygulamalarını adım adım nasıl oluşturabilirsiniz öğrenin.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579940"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Öğretici: Visual Studio Visual Basic ile başlayın

Visual Basic (VB) için yapılan bu eğitimde, visual studio'yu kullanarak birkaç farklı konsol uygulaması oluşturup çalıştıracaksınız ve bunu yaparken [Visual Studio tümleşik geliştirme ortamının (IDE)](visual-studio-ide.md) bazı özelliklerini keşfedeceksiniz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Visual Basic uygulama projesi oluşturacağız. Proje türü, daha bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

3. Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual Basic'i**genişletin ve **ardından .NET Core'u**seçin. Orta bölmede Konsol **Uygulaması'nı (.NET Core)** seçin. Sonra proje *WhatIsYourName*adını .

   ![Visual Studio IDE'deki Yeni Proje iletişim kutusunda Konsol Uygulaması (.NET Core) proje şablonu](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**Konsol Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **.NET Core çapraz platform geliştirme** iş yükünü ekleyerek bu uygulamayı elde edebilirsiniz. Bu iş yükünü, makinenize hangi Visual Studio 2017 güncelleştirmelerinin yüklendiğine bağlı olarak aşağıdaki iki şekilden birine ekleyebilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: Yeni Proje iletişim kutusunu kullanma

1. **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** aç bağlantısını tıklatın.

   ![Yeni Proje iletişim kutusundan Görsel Stüdyo Yükleyiciaç'ı Aç bağlantısını tıklayın](../media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

   ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Seçenek 2: Araçlar menü çubuğunu kullanma

1. **Yeni Proje** iletişim kutusundan ve üst menü çubuğundan iptal etme, **Araçlar** > **Araçları ve Özellikleri Al'ı**seçin.

1. Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları karanlık teonu kullanır. Karanlık temayı kullanmıyorsanız ancak kullanmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio IDE ve Editor](../../ide/quickstart-personalize-the-ide.md) sayfasını Kişiselleştir sayfasına bakın.

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesinden **Windows'u** seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **sonra İleri'yi**seçin.

   ![Konsol Uygulaması için Visual Basic şablonu (.NET Framework) seçeneğini seçin](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol Uygulaması (.NET Core)** şablonunu görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Installer'da **.NET Core çapraz platform geliştirme** iş yükünü seçin.
   >
   > ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *WhatIsYourName* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'WhatIsYourName' adını](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio yeni projenizi açıyor.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>"Adınız Nedir" uygulaması oluşturma

Adınızı sizden istenilen bir uygulama oluşturalım ve tarih ve saatle birlikte görüntüleyelim. Bunu yapmak için:

 ::: moniker range="vs-2017"

1. Zaten açık değilse, *WhatIsYourName* projenizi açın.

1. `Sub Main(args As String())` Satırı izleyen açılış ayraç'ından hemen sonra ve `End Sub` satırdan önce aşağıdaki Visual Basic kodunu girin:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod varolan <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A>, <xref:System.Console.ReadKey%2A> ve deyimlerin yerini alır.

   ![Ad kodunuz nedir gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Yeşil **Başlat** düğmesini kullanın veya ilk uygulamanızı oluşturmak ve çalıştırmak için **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer olmalıdır:

   ![Adınız Nedir, saat ve tarih ve İletiye devam etmek için herhangi bir tuşa basın](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range="vs-2019"

1. *WhatIsYourName* projesinde, `Sub Main(args As String())` satırı izleyen açılış parantezinden hemen sonra ve satırdan `End Sub` önce aşağıdaki Visual Basic kodunu girin:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Bu kod varolan <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A>, <xref:System.Console.ReadKey%2A> ve deyimlerin yerini alır.

   ![Ad kodunuz nedir gösteren kod penceresi](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Yeşil **Başlat** düğmesini kullanın veya ilk uygulamanızı oluşturmak ve çalıştırmak için **F5** tuşuna basın.

1. Konsol penceresi açıldığında adınızı girin. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer olmalıdır:

   ![Adınız Nedir, saat ve tarih ve İletiye devam etmek için herhangi bir tuşa basın](media/vb-console-what-name.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>"Bunu Hesapla" uygulaması oluşturma

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın ve ardından üst menü çubuğundan **Yeni** > **Dosya** > **Yı**seçin.

1. Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual Basic'i**genişletin ve **ardından .NET Core'u**seçin. Orta bölmede Konsol **Uygulaması'nı (.NET Core)** seçin. Sonra *dosyayı hesapla*bu.

1. `Module Program` Satır ve `End Module` satır arasına aşağıdaki kodu girin:

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

   Kod pencereniz aşağıdaki ekran görüntüsüne benzemelidir:

   ![Bu kodu Hesapla'yı gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı çalıştırmak için **CalculateThis'i** tıklatın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer olmalıdır:

    ![Hangi eylemlerin yapılacağını istemleri içeren CalculateThis uygulamasını günü gösteren konsol penceresi.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin. 

1. Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesinden **Windows'u** seçin. 

1. Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **sonra İleri'yi**seçin.

   Ardından, **yeni proje pencerenizi Yapılandır'** da Proje **adı** kutusuna *CalculateThis* yazın veya girin. Sonra, **Oluştur'u**seçin.

1. `Module Program` Satır ve `End Module` satır arasına aşağıdaki kodu girin:

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

   Kod pencereniz aşağıdaki ekran görüntüsüne benzemelidir:

   ![Bu kodu Hesapla'yı gösteren kod penceresi](media/vb-codewindow-calculate-this.png)

1. Programınızı çalıştırmak için **CalculateThis'i** tıklatın. Konsol pencereniz aşağıdaki ekran görüntüsüne benzer olmalıdır:

    ![Hangi eylemlerin yapılacağını istemleri içeren CalculateThis uygulamasını günü gösteren konsol penceresi.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar SSS

Aşağıda, bazı temel kavramları vurgulamak için hızlı bir SSS'dir.

### <a name="what-is-visual-basic"></a>Visual Basic nedir?

Visual Basic, öğrenmesi kolay olacak şekilde tasarlanmış, tür güvenli bir programlama dilidir. "Başlangıç'ın Çok Amaçlı Sembolik Öğretim Kodu" anlamına gelen BASIC'ten türetilmiştir.

### <a name="what-is-visual-studio"></a>Visual Studio nedir?

Visual Studio, geliştiriciler için entegre bir verimlilik araçları geliştirme paketidir. Bunu programlar ve uygulamalar oluşturmak için kullanabileceğiniz bir program olarak düşünün.

### <a name="what-is-a-console-app"></a>Konsol uygulaması nedir?

Bir konsol uygulaması giriş alır ve çıktıyı komut satırı penceresinde görüntüler, nam-ı diğer. bir konsol.

### <a name="what-is-net-core"></a>.NET Core nedir?

.NET Core, .NET Framework'ün evrimsel bir sonraki adımıdır. .NET Framework'ün programlama dilleri arasında kod paylaşmanıza izin verebildiği durumlarda,.NET Core, kodları platformlar arasında paylaşma olanağı sağlar. Daha da iyisi, açık kaynak. (Hem .NET Framework hem de .NET Core, önceden oluşturulmuş işlevsellik kitaplıklarının yanı sıra kodunuzu çalıştırmak için sanal bir makine görevi gören ortak bir dil çalışma süresi (CLR) içerir.)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğretici tamamladıktan sonra tebrikler! Daha fazla bilgi edinmek için aşağıdaki öğreticiye bakın.

> [!div class="nextstepaction"]
> [Visual Basic ve .NET Core SDK ile Visual Studio'da bir kütüphane oluşturun](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Basic dil geçiş leri](/dotnet/visual-basic/walkthroughs)
* [Visual Basic dili başvurusu](/dotnet/visual-basic/language-reference/index)
* [Visual Basic kod dosyaları için IntelliSense](../../ide/visual-basic-specific-intellisense.md)
