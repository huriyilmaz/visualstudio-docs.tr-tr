---
title: 'Öğretici: Visual Studio C# konsol uygulaması oluşturma'
titleSuffix: ''
description: C# ile Visual Studio basit Merhaba Dünya konsol uygulamasının nasıl oluşturulduğunu adım adım öğrenin.
ms.custom: vs-acquisition
ms.date: 09/14/2021
ms.topic: quickstart
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: ca9dbaba1ddb1ea94e801c497aa3c6d3176b7c1b
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132880041"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>hızlı başlangıç: ilk C# konsol uygulamanızı oluşturmak için Visual Studio kullanın

bu 5-10 dakika içinde Visual Studio tümleşik geliştirme ortamına (ıde) giriş yaparken, konsolunda çalışan basit bir C# uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda **C#**' ı genişletin ve ardından **.net Core**' u seçin. Orta bölmede **konsol uygulaması (.NET Core)** öğesini seçin. Ardından projeyi *HelloWorld* olarak adlandırın.

   ![Visual Studio ıde 'deki yeni Project iletişim kutusunda konsol uygulaması (.net Core) proje şablonunun ekran görüntüsü.](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     **konsol uygulaması (.net Core)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin.

   ![yeni Project iletişim kutusundan ' açık Visual Studio Yükleyicisi ' bağlantısının ekran görüntüsü.](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünün ekran görüntüsü.](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması (.NET Framework) için C# şablonunun ekran görüntüsü.](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol uygulaması (.NET Core)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklediklerinizi ' iletisinin ekran görüntüsü.](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > sonra, Visual Studio Yükleyicisi **.net Core platformlar arası geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünün ekran görüntüsü.](./media/dot-net-core-xplat-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' Yeni projenizi yapılandırın ' penceresinin ekran görüntüsü, projenizi ' HelloWorld ' olarak adlandırın.](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![Visual Studio 2022 ' de ' yeni proje oluştur ' penceresinin ekran görüntüsü.](media/vs-2022/start-window-create-new-project.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. ardından, dil listesinden **C#** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması (.NET Core) için C# şablonunun ekran görüntüsü.](media/vs-2022/quickstart-csharp-create-new-project.png)

   > [!NOTE]
   > .NET Core için **konsol uygulaması** şablonunu görmüyorsanız, bunu **Yeni proje oluştur** penceresinden yükleyebilirsiniz:
   > - **aradığınızı bulamıyor musunuz?** iletisi, Visual Studio Yükleyicisi başlatmak için **daha fazla araç ve özellik yüklein** bağlantısını seçin.
   >
   >    ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklediklerinizi ' iletisinin ekran görüntüsü.](media/vs-2022/not-finding-what-looking-for.png)
   > 
   > - Visual Studio Yükleyicisi’nde:
   >   - **.Net masaüstü geliştirme** iş yükünü seçin.
   >
   >      ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünün ekran görüntüsü.](media/vs-2022/dot-net-core-desktop-dev-workload.png)
   >
   >   - **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. 
   >   - İş yükünü yüklemek için **devam** ' ı seçin.
   > - Bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **İleri**' yi seçin.

   ![Visual Studio 2022 ' deki ' yeni projeyi yapılandır ' penceresinin ekran görüntüsü, proje adı ' HelloWorld ' olarak ayarlanmıştır.](media/vs-2022/csharp-name-your-helloworld-project.png)

1. **Ek bilgi** penceresinde, **Framework** açılan menüsünde **.net 6,0** ' ın seçildiğinden emin olun ve ardından **Oluştur**' u seçin.

   ![Framework ' .net 6,0 ' olarak ayarlanan Visual Studio 2022 ' de ' ek bilgi ' penceresinin ekran görüntüsü.](media/vs-2022/create-project-additional-info.png)

   Visual Studio yeni projenizi açar.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

::: moniker range="vs-2017"

C# proje şablonunuzu seçip projenizi adlandırın Visual Studio, sizin için basit bir "Merhaba Dünya" uygulaması oluşturur.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio, projenize varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio, projenize varsayılan "Merhaba Dünya" kodunu içerir. Düzenleyicide görüntülemek için, genellikle Visual Studio sağ tarafında olan Çözüm Gezgini penceresinde kod dosyası *program. cs* ' yi seçin.

::: moniker-end

::: moniker range="<=vs-2019"

(Bunu yapmak için, <xref:System.Console.WriteLine%2A> "Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağırır. Konsol penceresinde.)

   ![Şablondaki varsayılan Merhaba Dünya kodunun ekran görüntüsü.](../ide/media/csharp-console-helloworld-template.png)

**F5** tuşuna basarsanız, programı hata ayıklama modunda çalıştırabilirsiniz. Ancak, konsol penceresi kapanmadan önce yalnızca bir süre görünür.

(Bu davranış, `Main` yöntemi tek ifadesinin yürütüldükten sonra sonlandırdığı ve bu nedenle uygulama sona erdiğinde oluşur.)

::: moniker-end

::: moniker range=">=vs-2022"

Tek Code deyimleri, <xref:System.Console.WriteLine%2A> "Hello, World!" sabit dizesini göstermek için yöntemini çağırır Konsol penceresinde.

   ![Şablondaki varsayılan Merhaba Dünya kodunun ekran görüntüsü.](media/vs-2022/csharp-console-helloworld-template.png)

**F5** tuşuna basarsanız, programı hata ayıklama modunda çalıştırabilirsiniz. Uygulama hata ayıklayıcıda çalıştıktan sonra konsol penceresi açık kalır. Ancak, uygulama hata ayıklayıcı dışında çalıştırılmışsa, konsol penceresi kapanmadan önce yalnızca bir süre görünür hale gelir. Bunun nedeni, `Main` yönteminin tek kod deyimleri yürütüldükten sonra sonlandırılırsa ve uygulama sona erer. Hata ayıklayıcı dışında bir konsol uygulaması çalıştırma hakkında daha fazla bilgi için bkz. [.NET konsol uygulaması yayımlama](/dotnet/core/tutorials/publishing-with-visual-studio).

> [!NOTE]
> Düzenleyicideki tek kod satırı C# [üst düzey deyimidir](/dotnet/csharp/whats-new/csharp-9#top-level-statements)ve ortak [ana](/dotnet/csharp/fundamentals/program-structure/main-command-line) yöntemin basitleştiridir.

::: moniker-end

### <a name="add-some-code"></a>Kod ekleme

::: moniker range="<=vs-2019"

Uygulamayı duraklatmak için, **ENTER** tuşuna basarak konsol penceresinin kapanmaması için bazı kodlar ekleyelim.

1. Yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine%2A> :

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde şöyle göründüğünü doğrulayın:

   ![Merhaba Dünya uygulamasını duraklatmak için yeni eklenen kodun ekran görüntüsü.](../ide/media/csharp-console-helloworld-add-code.png)

::: moniker-end

::: moniker range=">=vs-2022"

`main`Yöntemin, **ENTER** tuşuna basarak sona ermesini sağlamak üzere uygulamayı duraklatmak için bazı kodlar ekleyelim.

1. Yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine%2A> :

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde şöyle göründüğünü doğrulayın:

   ![Merhaba Dünya uygulamasını duraklatmak için yeni eklenen kodun ekran görüntüsü.](media/vs-2022/csharp-console-helloworld-add-code.png)

::: moniker-end

## <a name="run-the-application"></a>Uygulamayı çalıştırma

::: moniker range="<=vs-2019"

1. Uygulamayı hata ayıklama modunda çalıştırmak için araç çubuğunda **HelloWorld** düğmesini seçin. İsterseniz **F5**'e de basabilirsiniz.

   ![Araç çubuğundan uygulamayı çalıştıran Merhaba Dünya düğmesinin ekran görüntüsü.](../ide/media/csharp-console-hello-world-button.png)

1. Uygulamanızı konsol penceresinde görüntüleyin.

   ![Konsol penceresinin ' Merhaba Dünya! ' gösteren ekran görüntüsü iletisi döndürmektedir.](../ide/media/csharp-console-hello-world.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Uygulamayı hata ayıklama modunda çalıştırmak için araç çubuğunda **HelloWorld** düğmesini seçin. (Veya **F5** tuşuna basabilirsiniz.)

   ![Araç çubuğundan uygulamayı çalıştıran Merhaba Dünya düğmesinin ekran görüntüsü.](media/vs-2022/csharp-console-hello-world-button.png)

1. Uygulamanızı konsol penceresinde görüntüleyin.

   ![' Hello, World! ' gösteren konsol penceresinin ekran görüntüsü iletisi döndürmektedir.](media/vs-2022/csharp-console-hello-world.png)

::: moniker-end

### <a name="close-the-application"></a>Uygulamayı kapat

::: moniker range="<=vs-2019"

1. Konsol penceresini kapatmak için **ENTER** tuşuna basın.

1. Visual Studio **Çıkış** bölmesini kapatın.

   ![Visual Studio çıkış bölmesinin ekran görüntüsü.](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio’yu kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

1. Yöntemi sonlandırmak için **ENTER** tuşuna basın `main` ve ardından yeniden ENTER  tuşuna basarak konsol penceresini kapatın.

1. Visual Studio **Çıkış** bölmesini kapatın.

   ![Visual Studio 2022 ' deki çıkış bölmesinin ekran görüntüsü.](media/vs-2022/csharp-hello-world-close-output-pane.png)

1. Visual Studio’yu kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! C# ve Visual Studio ıde hakkında biraz bilgi edindiniz. Daha fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Visual Studio bir C# konsol uygulaması ile çalışmaya başlama](../get-started/csharp/tutorial-console.md)
