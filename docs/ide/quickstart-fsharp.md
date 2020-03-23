---
title: "Quickstart: F'de ASP.NET Core web hizmeti oluşturun #"
description: Visual Studio'da adım adım F# ile ASP.NET Core web hizmeti oluşturmayı öğrenin.
ms.date: 08/24/2018
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 990106f7f3ca97ae38a20170ca6ed2e1d699d4e4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180317"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Quickstart: F'deki ilk ASP.NET Core web hizmetinizi oluşturmak için Visual Studio'yı kullanın\#

Visual Studio'da F# ile 5-10 dakikalık bu girişte, Bir F# ASP.NET Core web uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir ASP.NET Core Web API projesi oluşturursunuz. Proje türü, daha bir şey eklemeden önce işlevsel bir web hizmeti oluşturan şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

3. Yeni **Proje** iletişim kutusunda, sol bölmede, **Visual F#** genişletmek, sonra **Web**seçin. Orta bölmede, **Çekirdek Web Uygulaması ASP.NET**seçin, sonra **Tamam'ı**seçin.

     **.NET Core** proje şablonu kategorisini görmüyorsanız, sol bölmedeki **Açık Visual Studio Yükleyici** bağlantısını seçin. Visual Studio Installer başlattı. ASP.NET **ve web geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

     ![VS Yükleyici'de ASP.NET iş yükü](../ide/media/quickstart-aspnet-workload.png)

Yeni **ASP.NET Çekirdek Web Uygulaması** iletişim kutusunu 4.In, üst açılır menüden **Core 2.1ASP.NET** seçin. (Listede **Core 2.1 ASP.NET** görmüyorsanız, iletişim kutusunun üst kısmındaki sarı çubukta görünmesi gereken **İndir** bağlantısını izleyerek yükleyin.) **Tamam'ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

3. Yeni **bir proje oluştur** sayfasında, arama kutusuna **f# web** yazın ve ardından ASP.NET Çekirdek Web **Uygulaması** proje şablonunu seçin. **İleri**’yi seçin.

4. Yeni **proje sayfanızı Yapılandır'da** bir ad girin ve ardından **Oluştur'u**seçin.

5. Yeni **bir ASP.NET Core Web Application** oluştur sayfasında, üst açılır menüden ASP.NET Core **2.1'i** seçin ve ardından **Oluştur'u**seçin.

::: moniker-end

## <a name="explore-the-ide"></a>IDE'yi keşfedin

1. Solution **Explorer** araç çubuğunda, **Denetleyiciler** klasörünü genişletin ve düzenleyicide açmak için **ValuesController.fs'yi** seçin.

   ![F# Web API projesinde Denetleyiciler klasörüne sahip Çözüm Gezgini genişletildi](../ide/media/hello-world-fs-sln-explorer.png)

2. Ardından, üyeaşağıdaki gibi değiştirin: `Get()`

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. F# değerleri dizisi `values` ada bağlıdır ve daha sonra ASP.NET Core MVC `ActionResult`çerçevesine '. ASP.NET Core gerisini senin için halleder.

Editörde şöyle görünmelidir:

![Modifiye Üye Ol](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak ve bir web tarayıcısında açmak için **Ctrl**+**F5** tuşuna basın.

2. Sayfa `/api/values` rotaya gitmeli, ancak göndermiyorsa `https://localhost:44396/api/values` tarayıcınıza girin.

Web tarayıcısı artık Daha önce yazdığınız ile eşleşen JSON görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Bu Quickstart'ı tamamladığınız için tebrikler! Umarız F#, ASP.NET Core ve Visual Studio IDE hakkında biraz bilgi edinebilirsiniz. Uygulamanın ortak bir sunucuda çalıştığını görmek için aşağıdaki düğmeyi seçin.

> [!div class="nextstepaction"]
> [Uygulamayı Azure Uygulama Hizmetine dağıtma](../deployment/quickstart-deploy-to-azure.md)

F# hakkında daha fazla bilgi edinmek için resmi [F# Kılavuzu'na](/dotnet/fsharp/index)göz atın.