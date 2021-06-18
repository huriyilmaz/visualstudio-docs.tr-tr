---
title: Visual Basic ile ilk konsol Visual Basic
description: Visual Basic adım bir Merhaba Dünya kullanarak Visual Studio bir konsol uygulaması oluşturma hakkında bilgi edinin.
ms.custom: acquisition, seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 7272e02ebfba084bdbe311d10b69d7b41fade0e1
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307914"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Hızlı Başlangıç: Visual Basic ile Visual Studio konsol Visual Basic

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte, konsolunda çalışan basit Visual Basic bir Visual Basic uygulaması oluşturabilirsiniz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir uygulama projesi Visual Basic oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

3. Sol **bölmede Yeni** Proje iletişim kutusunda, Visual Basic genişletin **ve** **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *HelloWorld adını girin.*

   ![Visual Studio IDE'de Yeni Proje iletişim kutusundaki Konsol Uygulaması (.NET Core) proje şablonu](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız, Yeni **Proje iletişim** kutusunun sol bölmesinde Visual Studio Yükleyicisi Aç **bağlantısına** tıklayın.

   ![Yeni Proje Visual Studio Yükleyicisi Aç bağlantısına tıklayın](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

     ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Bu Hızlı Başlangıçtaki ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanmadıysanız ama bunu öğrenmek için Visual Studio [IDE](quickstart-personalize-the-ide.md) ve Düzenleyici sayfasını kişiselleştirme sayfasına bakın.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** Dil **listesinden Visual Basic'yi** seçin. Ardından Platform **listesinden Windows'u** ve proje **türleri** listesinden Konsol'u seçin.

   Dil, platform ve proje türü filtrelerini uygulayan Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Konsol Visual Basic için uygulama şablonunu seçin":::

   > [!NOTE]
   > Konsol Uygulaması şablonunu **görmüyorsanız,** Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Proje adı kutusuna *WhatIsYourName* **yazın veya** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'WhatIsYourName' adını girin":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

Uygulama proje şablon Visual Basic ve projenize bir ad verdikten Visual Studio sizin için basit bir "Merhaba Dünya" uygulaması oluşturur. "Merhaba Dünya!" değişmez dizesini <xref:System.Console.WriteLine%2A> görüntülemek için yöntemini Merhaba Dünya. seçin.

![Şablondan varsayılan Merhaba Dünya kodunu görüntüleme](../ide/media/vb-console-helloworld-template.png)

IDE'de **HelloWorld** düğmesine tıklarsanız programı Hata Ayıklama modunda çalıştırabilirsiniz.

  ![Programı Merhaba Dünya modunda çalıştırmak için Merhaba Dünya düğmesine tıklayın](../ide/media/vb-console-hello-world-button.png)

Bunu yapmak için konsol penceresi kapanmadan önce yalnızca bir dakika görünür. Bunun nedeni `Main` yöntemin tek deyimi yürütülürken sonlandırılır ve bu nedenle uygulama sona erer.

### <a name="add-some-code&quot;></a>Kod ekleme

Uygulamayı duraklatmak ve ardından kullanıcı girişi istemek için biraz kod ek o zaman.

1. yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu <xref:System.Console.WriteLine%2A> ekleyin:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

    Bu, siz bir tuşa basana kadar programı duraklatıyor.

2. Menü çubuğunda Derleme   >  **Çözümü'yü seçin.**

   Bu, programınızı tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülen bir ara dil (IL) olarak derler.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Araç çubuğunda **HelloWorld** düğmesine tıklayın.

   ![Programı Merhaba Dünya araç çubuğundan çalıştırmak için Merhaba Dünya düğmesine tıklayın](../ide/media/vb-console-hello-world-button.png)

2. Konsol penceresini kapatmak için herhangi bir tuşa basın.

   ![Devam etmek için Merhaba Dünya tuşuna basın ve](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! Visual Basic ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin.

> [!div class="nextstepaction"]
> [Kullanmaya başlayın Visual Basic ile Visual Studio](../get-started/visual-basic/tutorial-console.md)
