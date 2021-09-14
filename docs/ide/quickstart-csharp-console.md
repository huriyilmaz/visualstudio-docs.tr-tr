---
title: 'Öğretici: Visual Studio ile C# konsol uygulaması oluşturma'
titleSuffix: ''
description: C# ile Merhaba Dünya adım Visual Studio basit bir konsol uygulaması oluşturma hakkında bilgi edinin.
ms.custom: vs-acquisition
ms.date: 03/23/2019
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
ms.openlocfilehash: 6711ae64261e3ca11de07bdbc72e86f604e11c5f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635977"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Hızlı Başlangıç: İlk Visual Studio C# konsol uygulamasını oluşturmak için Visual Studio'yi kullanma

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte, konsolunda çalışan basit bir C# uygulaması oluşturabilirsiniz.

::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2019"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir C# uygulama projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda **C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Konsol Uygulaması **(.NET Core) 'ı seçin.** Ardından projeye *HelloWorld adını girin.*

   ![Visual Studio IDE'de Yeni Project iletişim kutusundaki Konsol Uygulaması (.NET Core) Visual Studio şablonu](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız,  Yeni Visual Studio Yükleyicisi iletişim kutusunun sol bölmesindeki Açık Project **bağlantısını** seçin.

   ![Yeni Dosya iletişim Visual Studio Yükleyicisi Aç bağlantısını Project seçin](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

     ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresi](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde** arama kutusuna *konsol yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin. 

   Dil ve platform filtrelerini uyguladikten sonra Konsol Uygulaması **(.NET Core)** şablonunu ve ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması için C# şablonunu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Konsol Uygulaması **(.NET Core)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ardından, Visual Studio Yükleyicisi **.NET Core** platformlar arası geliştirme iş yükünü seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından **Oluştur'a seçin.**

   !['Yeni projenizi yapılandırma' penceresinde projenize 'HelloWorld' adını girin](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio projenizi açar.
   
::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

::: moniker range="vs-2017"

C# proje şablonlarınızı seçerek projenize bir ad verdikten Visual Studio basit bir "Merhaba Dünya" uygulaması oluşturur.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio projenize varsayılan "Merhaba Dünya" kodunu içerir.

::: moniker-end

(Bunu yapmak için yöntemini <xref:System.Console.WriteLine%2A> çağırarak "Merhaba Dünya!" sabit dizesini görüntüler konsol penceresinde.)

   ![Şablondan varsayılan Merhaba Dünya kodunu görüntüleme](../ide/media/csharp-console-helloworld-template.png)

**F5 tuşuna basın,** programı Hata Ayıklama modunda çalıştırabilirsiniz. Ancak konsol penceresi kapanmadan önce yalnızca bir süre görünür.

(Bu davranış, `Main` yöntemin tek deyimi yürütülürken sonlandırılır ve bu nedenle uygulama sona erer.)

### <a name="add-some-code"></a>Kod ekleme

Enter tuşuna basana kadar konsol penceresinin kapanması için uygulamayı duraklatmak için biraz kod ek **o zaman.**

1. yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu <xref:System.Console.WriteLine%2A> ekleyin:

   ```csharp
   Console.ReadLine();
   ```

1. Kod düzenleyicisinde aşağıdaki gibi göründüğünü doğrulayın:

   ![Uygulamayı duraklatmak için Merhaba Dünya ekleme](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı Hata Ayıklama modunda çalıştırmak için araç çubuğunda **HelloWorld** düğmesini seçin. (Veya **F5 tuşuna basarak**.)

   ![Uygulamayı Merhaba Dünya araç çubuğundan çalıştırmak için Aşağıdaki düğmeyi seçin](../ide/media/csharp-console-hello-world-button.png)

1. Konsol penceresinde uygulamalarınızı görüntüleme.

   ![Konsol penceresi, Merhaba Dünya!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Uygulamayı kapatma

1. Konsol penceresini kapatmak için **ENTER** tuşuna basın.

1. Bölmede  Çıkış bölmesini Visual Studio.

   ![Bölmede Çıkış bölmesini Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Visual Studio’yu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! C# ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Kullanmaya başlayın C# konsol uygulamasıyla Visual Studio](../get-started/csharp/tutorial-console.md)
