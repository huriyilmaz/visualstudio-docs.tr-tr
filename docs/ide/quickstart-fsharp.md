---
title: "Hızlı Başlangıç: F'ASP.NET Core web hizmeti oluşturma #"
description: F# ile ASP.NET Core adım Visual Studio web hizmeti oluşturma hakkında bilgi edinin.
ms.date: 08/24/2018
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
ms.openlocfilehash: df1ea3b5cb57180c8f9fd8402b892594888d3bae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635974"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Hızlı Başlangıç: F'Visual Studio web hizmetinizi oluşturmak ASP.NET Core hızlı başlangıç\#

bu 5-10 dakika içinde Visual Studio'da F# ASP.NET Core web uygulaması oluşturabilirsiniz.

::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2019"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio [2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) yüklemelerini henüz yüklememişsinizdir.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir Web API'si ASP.NET Core oluşturabilirsiniz. Proje türü, siz herhangi bir şey eklemeden önce işlevsel bir web hizmeti oluşturan şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

3. Yeni uygulama **Project** iletişim kutusunda, sol bölmede Visual F#'yi **genişletin** ve **Web'i seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core ve ardından** Tamam'ı **seçin.**

     **.NET Core** proje şablonu kategorisini görmüyorsanız sol **bölmedeki** Visual Studio Yükleyicisi aç bağlantısını seçin. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**

     ![ASP.NET Yükleyicisi'ne iş yükü yükleme](../ide/media/quickstart-aspnet-workload.png)

4.In Web **ASP.NET Core iletişim** kutusunda, üst açılan **menüden ASP.NET Core 2.1'i** seçin. (Listede ASP.NET Core **2.1'i** görmüyorsanız, iletişim kutusunun üst kısmında  sarı bir çubukta görünmesi gereken İndir bağlantısını takip edin.) **Tamam'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında,** arama kutusuna **f# web** yazın ve web uygulaması **proje ASP.NET Core** seçin. **İleri**’yi seçin.

4. Yeni **projenizi yapılandır sayfasında** bir ad girin ve Oluştur'a **tıklayın.**

5. Yeni bir **web uygulaması ASP.NET Core sayfasında,** üst **açılan menüden ASP.NET Core 2.1'i** seçin ve ardından Oluştur'a **tıklayın.**

::: moniker-end

## <a name="explore-the-ide"></a>IDE'ye keşfetme

1. Çözüm Gezgini **araç** çubuğunda Denetleyiciler klasörünü **genişletin** ve ardından **ValuesController.fs'yi** seçarak düzenleyicide açın.

   ![Çözüm Gezgini F# Web API projesinde genişletilmiş Denetleyiciler klasörüyle birlikte kullanma](../ide/media/hello-world-fs-sln-explorer.png)

2. Ardından, `Get()` üyeyi aşağıdaki gibi yapın:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. Bir F# değer dizisi, adına bağlı ve ardından `values` MVC çerçevesine ASP.NET Core olarak `ActionResult` geçirildi. ASP.NET Core sizin için diğer tüm işlerini sizin için yaptı.

Düzenleyicide aşağıdaki gibi olması gerekir:

![Değiştirilen Üye al](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak ve bir web tarayıcısında açmak için **Ctrl** + **F5'e** basın.

2. Sayfa yönlendirmeye `/api/values` gitse de, yönlendirene kadar gitse de `https://localhost:44396/api/values` tarayıcınıza girin.

Web tarayıcısı artık daha önce yazacakları ile eşleşen JSON'u görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! F#, ASP.NET Core ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. Genel sunucuda çalışan uygulamayı görmek için aşağıdaki düğmeyi seçin.

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service](../deployment/quickstart-deploy-to-azure.md)

F# hakkında daha fazla bilgi edinmek için resmi [F# Kılavuzuna göz atabilirsiniz.](/dotnet/fsharp/index)
