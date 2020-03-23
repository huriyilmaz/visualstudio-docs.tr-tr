---
title: İlk C# konsol uygulamanızı oluşturmak için Visual Studio'yı kullanın
titleSuffix: ''
description: Visual Studio'da adım adım C#ile basit bir Hello World konsol uygulaması oluşturmayı öğrenin.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 20b2cf2bf12e9b24ca12d0a73b43e4a56e8246f4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579481"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Quickstart: İlk C# konsol uygulamanızı oluşturmak için Visual Studio'yı kullanın

Visual Studio entegre geliştirme ortamına (IDE) 5-10 dakikalık bu girişte, konsolda çalışan basit bir C# uygulaması oluşturursunuz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturursunuz. Proje türü, daha bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

3. Sol bölmedeki **Yeni Proje** iletişim kutusunda **C#** seçeneğini genişletin ve **ardından .NET Core'u**seçin. Orta bölmede Konsol **Uygulaması'nı (.NET Core)** seçin. Sonra proje *HelloWorld*adını .

   ![Visual Studio IDE'deki Yeni Proje iletişim kutusunda Konsol Uygulaması (.NET Core) proje şablonu](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     **Konsol Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Bulunan Görsel **Stüdyo Yükleyicisi** Açık bağlantısını seçin.

   ![Yeni Proje iletişim kutusundan Open Visual Studio Installer bağlantısını seçin](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

     ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni bir proje oluşturma' penceresi](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Windows'u** seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **sonra İleri'yi**seçin.

   ![Konsol Uygulaması için C# şablonunu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol Uygulaması (.NET Core)** şablonunu görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Installer'da **.NET Core çapraz platform geliştirme** iş yükünü seçin.
   >
   > ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da,** **Project ad** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'HelloWorld' adını](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio yeni projenizi açıyor.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

::: moniker range="vs-2017"

C# proje şablonunuzu seçtikten ve projenize isim verdikten sonra Visual Studio sizin için basit bir "Hello World" uygulaması oluşturur.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio, projenizde varsayılan "Hello World" kodunu içerir.

::: moniker-end

(Bunu yapmak için, <xref:System.Console.WriteLine%2A> gerçek dize görüntülemek için yöntem çağırır "Merhaba Dünya!" konsol penceresinde.)

   ![Varsayılan Hello World kodunu şablondan görüntüleme](../ide/media/csharp-console-helloworld-template.png)

**F5**tuşuna baslarsanız, programı Hata Ayıklama modunda çalıştırabilirsiniz. Ancak konsol penceresi kapanmadan önce yalnızca bir an için görünür.

(Yöntem tek bir `Main` deyim yürütülmeden sonra sona erdiğinden ve böylece uygulama sona erdiğinden bu davranış gerçekleşir.)

### <a name="add-some-code"></a>Bazı kod ekleme

**Enter**tuşuna basana kadar konsol penceresinin kapanmaması için uygulamayı duraklatmak için bazı kodlar ekleyelim.

1. <xref:System.Console.WriteLine%2A> Aramadan hemen sonra yönteme aşağıdaki kodu ekleyin:

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde aşağıdaki gibi göründüğünü doğrulayın:

   ![Hello World uygulamasını duraklatmak için kod ekleme](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı Hata Ayıklama modunda çalıştırmak için araç çubuğundaki **HelloWorld** düğmesini seçin. **(Veya, F5 tuşuna**basabilirsiniz .)

   ![Uygulamayı araç çubuğundan çalıştırmak için Hello World düğmesini seçin](../ide/media/csharp-console-hello-world-button.png)

1. Uygulamanızı konsol penceresinde görüntüleyin.

   ![Merhaba Dünya gösteren konsol penceresi!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Uygulamayı kapatma

1. Konsol penceresini kapatmak için **ENTER** tuşuna basın.

1. Visual Studio'daki **Çıkış** bölmesini kapatın.

   ![Visual Studio'da Çıkış bölmesini kapatın](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio’yu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu Quickstart'ı tamamladığınız için tebrikler! C# ve Visual Studio IDE hakkında biraz bilgi edindiğinizi umuyoruz. Daha fazla bilgi edinmek için aşağıdaki eğitimlerle devam edin.

> [!div class="nextstepaction"]
> [Visual Studio'da C# konsol uygulamasıyla başlayın](../get-started/csharp/tutorial-console.md)
