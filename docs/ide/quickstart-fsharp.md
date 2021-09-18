---
title: "Hızlı Başlangıç: F'ASP.NET Core web hizmeti oluşturma #"
description: F# ile ASP.NET Core adım Visual Studio web hizmeti oluşturma hakkında bilgi edinin.
ms.date: 09/14/2021
ms.topic: quickstart
ms.custom: vs-acquisition
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 17d443c9dac7a37670c65c7fb9c8da8362aa4ab4
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920048"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Hızlı Başlangıç: F'Visual Studio web hizmetinizi oluşturmak ASP.NET Core hızlı başlangıç\#

Bu 5-10 dakika içinde Visual Studio F# uygulamasına giriş için bir F# ASP.NET Core oluşturabilirsiniz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir Web API'si ASP.NET Core oluşturabilirsiniz. Proje türü, siz herhangi bir şey eklemeden önce işlevsel bir web hizmeti oluşturan şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

1. Yeni uygulama **Project** iletişim kutusunda, sol bölmede Visual F#'yi **genişletin** ve **Web'i seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core ve ardından** Tamam'ı **seçin.**

   **.NET Core** proje şablonu kategorisini görmüyorsanız sol **bölmedeki** Visual Studio Yükleyicisi aç bağlantısını seçin. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**

   ![ASP.NET VS Yükleyicisi'ne iş yükü yükleme](../ide/media/quickstart-aspnet-workload.png)

1. Yeni **Web ASP.NET Core iletişim kutusunda,** üst **açılan menüden ASP.NET Core 2.1'i** seçin. (Listede ASP.NET Core **2.1'i** görmüyorsanız, iletişim kutusunun üst kısmında  sarı bir çubukta görünmesi gereken İndir bağlantısını takip edin.) **Tamam'ı seçin.**

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur sayfasında,** arama kutusuna **f# web** yazın ve ASP.NET Core **Web Uygulaması proje şablonunu** seçin. **İleri**’yi seçin.

1. Yeni **projenizi yapılandır sayfasında** bir ad girin ve Oluştur'a **tıklayın.**

1. Yeni bir **web uygulaması ASP.NET Core sayfasında,** **üst açılan menüden ASP.NET Core 2.1'i** seçin ve ardından Oluştur'a **tıklayın.**

## <a name="explore-the-ide"></a>IDE'ye keşfetme

1. Çözüm Gezgini **araç** çubuğunda **Denetleyiciler** klasörünü genişletin, ardından **ValuesController.fs'yi** seçarak düzenleyicide açın.

   ![Bir F# Web API Çözüm Gezgini Controllers klasörünün genişlet olduğu uygulamanın ekran görüntüsü.](../ide/media/hello-world-fs-sln-explorer.png)

1. Ardından, `Get()` üyeyi aşağıdaki gibi yapın:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. Bir F# değer dizisi, adına bağlı ve ardından bir olarak `values` ASP.NET Core MVC çerçevesine geçirildi. `ActionResult` ASP.NET Core sizin için diğer tüm işlerini sizin için yaptı.

Düzenleyicide aşağıdaki gibi olması gerekir:

![ValuesController.fs içinde Üye al için değiştirilen kodu gösteren ekran görüntüsü.](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak ve bir web tarayıcısında açmak için **Ctrl** + **F5'e** basın.

1. Sayfa yönlendirmeye `/api/values` gitse de, yönlendirene kadar gitse de `https://localhost:44396/api/values` tarayıcınıza girin.

Web tarayıcısı artık daha önce yazacakları ile eşleşen JSON'u görüntüler.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur penceresinde** arama kutusuna **f# web** yazın veya listeyi geliştirmek için dil, platform ve proje türü filtrelerini kullanın. Web **API ASP.NET Core şablonunu** ve ardından Sonraki'yi **seçin.**

1. Yeni **projenizi yapılandır penceresinde,** yeni bir Project **girin ve** ardından Sonraki'yi **seçin.**

1. Ek **bilgiler penceresinde Framework** alanında **.NET 6.0'ın** görüntülendiğinden **emin olup** Oluştur'a **tıklayın.**

## <a name="explore-the-ide"></a>IDE'ye keşfetme

1. Çözüm Gezgini **araç** çubuğunda Denetleyiciler klasörünü  genişletin, ardından **WeatherForecast.fs'yi** seçarak düzenleyicide açın.

   :::image type="content" source="media/vs-2022/hello-world-fs-sln-explorer.png" alt-text="F# Web API Çözüm Gezgini Controllers klasörünün genişletilirken gösterilen ekran görüntüsü.":::

1. Ardından, mevcut üye `Get()` örneğini aşağıdaki kodla eş olacak şekilde değiştirebilirsiniz:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. Bir F# değer dizisi, adına bağlı ve ardından bir olarak `values` ASP.NET Core MVC çerçevesine geçirildi. `ActionResult` ASP.NET Core sizin için diğer tüm işlerini sizin için yaptı.

Düzenleyicide aşağıdaki gibi olması gerekir:

:::image type="content" source="media/vs-2022//hello-world-fs-get-member.png" alt-text="WeatherForecast.fs'de Üye al için değiştirilen kodu gösteren ekran görüntüsü.":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak ve bir web tarayıcısında açmak için **Ctrl** + **F5'e** basın. 

> [!NOTE]
> IIS SSL Express sertifikasını kabul etmek istemenizi isteyen bir  ileti alırsanız, kodu bir web  tarayıcısında görüntülemek için Evet'i seçin ve ardından bir güvenlik uyarısı iletisi alırsanız Evet'i seçin.

Visual Studio daha önce eklemış olduğunuz "Merhaba Dünya" iletisiyle eşleşen JSON'u görüntüleyen bir tarayıcı penceresi açar.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! F#, ASP.NET Core ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. Genel sunucuda çalışan uygulamayı görmek için aşağıdaki düğmeyi seçin.

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service](../deployment/quickstart-deploy-to-azure.md)

F# hakkında daha fazla bilgi edinmek için resmi [F# Kılavuzuna göz atabilirsiniz.](/dotnet/fsharp/index)
