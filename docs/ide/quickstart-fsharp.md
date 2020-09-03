---
title: "Hızlı başlangıç: F 'de ASP.NET Core Web hizmeti oluşturma #"
description: "F # ile Visual Studio 'da bir ASP.NET Core Web hizmeti oluşturmayı öğrenin, adım adım."
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70180317"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Hızlı başlangıç: Visual Studio 'Yu kullanarak ilk ASP.NET Core Web hizmetinizi F 'de oluşturun\#

Visual Studio 'da F # ' a giriş bu 5-10 dakikadır, bir F # ASP.NET Core Web uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir ASP.NET Core Web API projesi oluşturacaksınız. Proje türü, hatta herhangi bir şey eklemeden önce işlevsel bir Web hizmetini oluşturan şablon dosyaları ile birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, sol bölmede, **Visual F#**' ı genişletin ve ardından **Web**' i seçin. Orta bölmede **ASP.NET Core Web uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.

     **.NET Core** proje şablonu kategorisini görmüyorsanız sol bölmedeki **Visual Studio yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **ASP.net ve Web geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![VS yükleyicisinde ASP.NET iş yükü](../ide/media/quickstart-aspnet-workload.png)

**yeni ASP.NET Core Web uygulaması** iletişim kutusunu 4.ın üst açılan menüden **ASP.NET Core 2,1** ' i seçin. (Listede **ASP.NET Core 2,1** görmüyorsanız, iletişim kutusunun üst kısmına yakın bir sarı çubukta görünmesi gereken **indirme** bağlantısını izleyerek yükleyin.) **Tamam ' ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, ara kutusuna **f # Web** yazın ve ardından **ASP.NET Core Web uygulaması** proje şablonu ' nu seçin. **İleri**’yi seçin.

4. **Yeni projenizi yapılandırın** sayfasında, bir ad girin ve ardından **Oluştur**' u seçin.

5. **Yeni bir ASP.NET Core Web uygulaması oluştur** sayfasında, üst açılan menüden **ASP.NET Core 2,1** ' i seçin ve ardından **Oluştur**' u seçin.

::: moniker-end

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. **Çözüm Gezgini** araç çubuğunda, **denetleyiciler** klasörünü genişletin ve ardından, düzenleyicide açmak için **valuescontroller. FS** ' yi seçin.

   ![F # Web API projesinde genişletilmiş denetleyiciler klasörüyle Çözüm Gezgini](../ide/media/hello-world-fs-sln-explorer.png)

2. Sonra, `Get()` üyeyi aşağıdakiler olacak şekilde değiştirin:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. Bir F # değer dizisi `values` ada bağlanır ve sonra ASP.NET Core MVC çerçevesine bir olarak geçirilir `ActionResult` . ASP.NET Core, geri kalanını sizin yerinize gerçekleştirir.

Düzenleyicide şöyle görünmelidir:

![Değiştirilen üye Al](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Ctrl** + Uygulamayı çalıştırmak ve bir Web tarayıcısında açmak için CTRL**F5** tuşuna basın.

2. Sayfa yola gitmelidir `/api/values` , ancak yoksa `https://localhost:44396/api/values` tarayıcınıza girin.

Web tarayıcısı artık daha önce yazdıklarınız ile eşleşen JSON 'ı görüntüleyecek.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! F #, ASP.NET Core ve Visual Studio IDE hakkında biraz bilgi edindiniz. Uygulamayı ortak bir sunucuda çalıştırmayı görmek için aşağıdaki düğmeyi seçin.

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service dağıtma](../deployment/quickstart-deploy-to-azure.md)

F # hakkında daha fazla bilgi edinmek için resmi [f # kılavuzuna](/dotnet/fsharp/index)göz atın.