---
title: Visual Basic ile ilk konsol uygulamanızı oluşturun
description: Visual Studio'da Visual Basic ile adım adım basit bir Hello World konsol uygulaması oluşturmayı öğrenin.
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
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34f3dc8642e2cf8e965e2ad303bed79931d2645c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579503"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Quickstart: Visual Basic ile Visual Studio'da ilk konsol uygulamanızı oluşturun

Visual Studio entegre geliştirme ortamına (IDE) 5-10 dakikalık bu girişte, konsolda çalışan basit bir Visual Basic uygulaması oluşturursunuz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Visual Basic uygulama projesi oluşturursunuz. Proje türü, daha bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

3. Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual Basic'i**genişletin ve **ardından .NET Core'u**seçin. Orta bölmede Konsol **Uygulaması'nı (.NET Core)** seçin. Sonra proje *HelloWorld*adını .

   ![Visual Studio IDE'deki Yeni Proje iletişim kutusunda Konsol Uygulaması (.NET Core) proje şablonu](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     **Konsol Uygulaması (.NET Core)** proje şablonunu görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** Aç bağlantısını tıklatın.

   ![Yeni Proje iletişim kutusundan Görsel Stüdyo Yükleyiciaç'ı Aç bağlantısını tıklayın](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

     ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Bu Quickstart'taki ekran ekranlarından bazıları karanlık teonu kullanır. Karanlık temayı kullanmıyorsanız ancak kullanmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio IDE ve Editor](quickstart-personalize-the-ide.md) sayfasını Kişiselleştir sayfasına bakın.

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *konsol* girin veya yazın. Ardından, Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesinden **Windows'u** seçin. 

   Dil ve platform filtrelerini uyguladıktan sonra **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **sonra İleri'yi**seçin.

   ![Konsol Uygulaması için Visual Basic şablonu (.NET Framework) seçeneğini seçin](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **Konsol Uygulaması (.NET Core)** şablonunu görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Installer'da **.NET Core çapraz platform geliştirme** iş yükünü seçin.
   >
   > ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *WhatIsYourName* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'WhatIsYourName' adını](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio yeni projenizi açıyor.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

Visual Basic proje şablonunuzu seçtikten ve projenize isim verdikten sonra Visual Studio sizin için basit bir "Hello World" uygulaması oluşturur. Bu kelime <xref:System.Console.WriteLine%2A> dizesini görüntülemek için yöntem çağırır "Merhaba Dünya!" konsol penceresinde.

![Varsayılan Hello World kodunu şablondan görüntüleme](../ide/media/vb-console-helloworld-template.png)

IDE'deki **HelloWorld** düğmesini tıklatırsanız, programı Hata Ayıklama modunda çalıştırabilirsiniz.

  ![Programı Hata Ayıklama modunda çalıştırmak için Merhaba Dünya düğmesini tıklatın](../ide/media/vb-console-hello-world-button.png)

Bunu yaptığınızda, konsol penceresi kapanmadan önce yalnızca bir an görünür. Yöntem, tek `Main` bir deyim yürütülmeden sonra sona erdirir ve böylece uygulama sona erer, çünkü bu olur.

### <a name="add-some-code"></a>Bazı kod ekleme

Uygulamayı duraklatmak için bazı kodlar ekleyelim ve ardından kullanıcı girişi isteyelim.

1. <xref:System.Console.WriteLine%2A> Aramadan hemen sonra yönteme aşağıdaki kodu ekleyin:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Bu, bir tuşa basana kadar programı duraklatlar.

2. Menü çubuğunda **Yapı** > **Çözümünü**seçin.

   Bu, programınızı tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülen bir ara dile (IL) dönüştürür.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Araç çubuğundaki **HelloWorld** düğmesini tıklatın.

   ![Programı araç çubuğundan çalıştırmak için Hello World düğmesini tıklatın](../ide/media/vb-console-hello-world-button.png)

2. Konsol penceresini kapatmak için herhangi bir tuşa basın.

   ![Hello World'u gösteren konsol penceresi ve devam etmek için herhangi bir tuşa basın](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Sonraki adımlar

Bu Quickstart'ı tamamladığınız için tebrikler! Biz Visual Basic ve Visual Studio IDE hakkında biraz öğrendim umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiye devam edin.

> [!div class="nextstepaction"]
> [Visual Studio'da Visual Basic ile başlayın](../get-started/visual-basic/tutorial-console.md)
