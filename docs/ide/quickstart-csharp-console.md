---
title: 'Öğretici: Visual Studio ile C# konsol uygulaması oluşturma'
titleSuffix: ''
description: C# ile Merhaba Dünya adım Visual Studio basit bir konsol uygulaması oluşturma hakkında bilgi edinin.
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
ms.openlocfilehash: 99a2e2e6ba67d4604b945f61040005f13320fd7b
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431833"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Hızlı Başlangıç: İlk Visual Studio C# konsol uygulamasını oluşturmak için Visual Studio'yi kullanma

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte, konsolunda çalışan basit bir C# uygulaması oluşturabilirsiniz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir C# uygulama projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

1. Sol **bölmede yeni Project** iletişim kutusunda **C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *HelloWorld adını girin.*

   ![IDE'de Yeni Uygulama iletişim kutusundaki Konsol Uygulaması (.NET Core) Project şablonunun Visual Studio görüntüsü.](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,  Yeni Visual Studio Yükleyicisi iletişim kutusunun sol bölmesindeki  Açık Project seçin.

   ![Yeni Uygulama iletişim kutusundaki 'Visual Studio Yükleyicisi aç' bağlantısının Project görüntüsü.](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

     ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünün ekran Visual Studio Yükleyicisi.](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uyguladikten sonra Konsol Uygulaması **(.NET Core)** şablonunu ve ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması için C# şablonunun ekran görüntüsü (.NET Framework.](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Konsol Uygulaması **(.NET Core)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısının ekran görüntüsü.](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünün ekran Visual Studio Yükleyicisi.](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *HelloWorld* yazın veya **Project** girin. Ardından **Oluştur'a seçin.**

   !['Yeni projenizi yapılandır' penceresinin ekran görüntüsü, projenize 'HelloWorld' adını girin.](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   ![Visual Studio 2022'de 'Yeni proje oluştur' penceresinin ekran görüntüsü.](media/vs-2022/start-window-create-new-project.png)

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uyguladikten sonra Konsol Uygulaması **şablonunu ve** ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması (.NET Core) için C# şablonunun ekran görüntüsü.](media/vs-2022/quickstart-csharp-create-new-project.png)

   > [!NOTE]
   > .NET Core için Konsol **Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz:**
   > - **Arayabilirsiniz mi? iletisinde** Daha fazla araç  ve özellik yükle bağlantısını seçen kullanıcı Visual Studio Yükleyicisi.
   >
   >    !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısının ekran görüntüsü.](media/vs-2022/not-finding-what-looking-for.png)
   > 
   > - Visual Studio Yükleyicisi’nde:
   >   - **.NET masaüstü geliştirme iş yükünü** seçin.
   >
   >      ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünün ekran Visual Studio Yükleyicisi.](media/vs-2022/dot-net-core-desktop-dev-workload.png)
   >
   >   - Değiştir **düğmesini** seçin. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. 
   >   - İş **yükünü yüklemek** için Devam'ı seçin.
   > - Bu " Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *HelloWorld* yazın veya **Project** girin. Ardından, **Sonraki'yi seçin.**

   ![Visual Studio 2022'de proje adı 'HelloWorld' olarak ayarlanmış şekilde 'Yeni projenizi yapılandır' penceresinin ekran görüntüsü.](media/vs-2022/csharp-name-your-helloworld-project.png)

1. Ek bilgiler penceresinde **Çerçeve** açılan menüsünde  **.NET 6.0 (Önizleme)** öğesinin seçili olduğundan emin olun ve oluştur'a **tıklayın.**

   ![Visual Studio 2022'de Framework'te '.NET 6.0 (Önizleme)' olarak ayarlanmış 'Ek bilgiler' penceresinin ekran görüntüsü.](media/vs-2022/create-project-additional-info.png)

   Visual Studio projenizi açar.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

::: moniker range="vs-2017"

C# proje şablonlarınızı seçerek projenize bir ad verdikten sonra Visual Studio basit bir "Merhaba Dünya" uygulaması oluşturur.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio projenize varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio projenize varsayılan "Merhaba Dünya" kodunu içerir. Düzenleyicide görüntülemek için, Çözüm Gezgini penceresinde *program.cs* kod dosyasını seçin. Bu Visual Studio.

::: moniker-end

::: moniker range="<=vs-2019"

(Bunu yapmak için yöntemini <xref:System.Console.WriteLine%2A> çağırarak "Merhaba Dünya!" sabit dizesini görüntüler konsol penceresinde.)

   ![Şablondan varsayılan Merhaba Dünya kodunun ekran görüntüsü.](../ide/media/csharp-console-helloworld-template.png)

**F5 tuşuna basın,** programı Hata Ayıklama modunda çalıştırabilirsiniz. Ancak konsol penceresi kapanmadan önce yalnızca bir süre görünür.

(Bu davranış, `Main` yöntemin tek deyimi yürütülürken sonlandırılır ve bu nedenle uygulama sona erer.)

::: moniker-end

::: moniker range=">=vs-2022"

Tek kod deyimi, <xref:System.Console.WriteLine%2A> "Hello, World!" değişmez dizesini görüntülemek için yöntemini arar seçin.

   ![Şablondan varsayılan Merhaba Dünya kodunun ekran görüntüsü.](media/vs-2022/csharp-console-helloworld-template.png)

**F5 tuşuna basın,** programı Hata Ayıklama modunda çalıştırabilirsiniz. Uygulama hata ayıklayıcıda çalıştır edildikten sonra konsol penceresi açık kalır. Ancak, uygulama hata ayıklayıcısı dışında çalıştırıldı ise, konsol penceresi kapanmadan önce yalnızca bir dakika görünür. Bunun nedeni, `Main` yönteminin tek kod deyimi yürütülürken sonlandırılır ve bu nedenle uygulama sona erer. Hata ayıklayıcı dışında bir konsol uygulaması çalıştırma hakkında daha fazla bilgi için [bkz. .NET konsol uygulaması yayımlama.](/dotnet/core/tutorials/publishing-with-visual-studio)

> [!NOTE]
> Düzenleyicide tek kod satırı C# üst düzey [deyimidir](/dotnet/csharp/whats-new/csharp-9#top-level-statements)ve ortak [Main](/dotnet/csharp/fundamentals/program-structure/main-command-line) yönteminin basitleştirilmesidir.

::: moniker-end

### <a name="add-some-code"></a>Kod ekleme

::: moniker range="<=vs-2019"

Enter tuşuna basana kadar konsol penceresinin kapanması için uygulamayı duraklatmak için biraz kod ek **o zaman.**

1. yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu <xref:System.Console.WriteLine%2A> ekleyin:

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde aşağıdaki gibi göründüğünü doğrulayın:

   ![Uygulamayı duraklatmak için yeni eklenen kodun Merhaba Dünya görüntüsü.](../ide/media/csharp-console-helloworld-add-code.png)

::: moniker-end

::: moniker range=">=vs-2022"

Enter tuşuna basılana kadar yöntemin sonlandırılmamak için `main` uygulamayı duraklatmak için bazı kodlar **ekleriz.**

1. yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu <xref:System.Console.WriteLine%2A> ekleyin:

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde aşağıdaki gibi göründüğünü doğrulayın:

   ![Uygulamayı duraklatmak için yeni eklenen kodun Merhaba Dünya görüntüsü.](media/vs-2022/csharp-console-helloworld-add-code.png)

::: moniker-end

## <a name="run-the-application"></a>Uygulamayı çalıştırma

::: moniker range="<=vs-2019"

1. Uygulamayı Hata Ayıklama modunda çalıştırmak için araç çubuğunda **HelloWorld** düğmesini seçin. Veya F5 tuşuna **da basarak.**

   ![Araç çubuğundan Merhaba Dünya çalıştıran Uygulama Ekle düğmesinin ekran görüntüsü.](../ide/media/csharp-console-hello-world-button.png)

1. Konsol penceresinde uygulamalarınızı görüntüleme.

   !['Merhaba Dünya!' ifadesini gösteren Konsol penceresinin ekran görüntüsü iletisi döndürmektedir.](../ide/media/csharp-console-hello-world.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Uygulamayı Hata Ayıklama modunda çalıştırmak için araç çubuğunda **HelloWorld** düğmesini seçin. (Veya **F5** tuşuna basabilirsiniz.)

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
