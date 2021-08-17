---
title: "hızlı başlangıç: F 'de ASP.NET Core web hizmeti oluşturma #"
description: 'F # ile Visual Studio bir ASP.NET Core web hizmeti oluşturmayı öğrenin, adım adım.'
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: vs-acquisition
author: cartermp
ms.author: phcart
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ad45a9cefa183919f164e8e9f48667fdacfd3e2fe5721863dbfd0b444d3dc467
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372925"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>hızlı başlangıç: ilk ASP.NET Core web hizmetinizi F 'de oluşturmak için Visual Studio kullanma\#

bu 5-10 dakika içinde f # ' a giriş Visual Studio, bir f # ASP.NET Core web uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

ilk olarak, bir ASP.NET Core Web apı projesi oluşturacaksınız. Proje türü, hatta herhangi bir şey eklemeden önce işlevsel bir Web hizmetini oluşturan şablon dosyaları ile birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

3. **yeni Project** iletişim kutusunda, sol bölmede, **Visual F#**' i genişletin ve **Web**' i seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin ve ardından **tamam**' ı seçin.

     **.net Core** proje şablonu kategorisini görmüyorsanız sol bölmedeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

     ![VS yükleyicisinde iş yükünü ASP.NET](../ide/media/quickstart-aspnet-workload.png)

**yeni ASP.NET Core Web uygulaması** iletişim kutusunu 4.In üst açılan menüden **ASP.NET Core 2,1** ' i seçin. (listede **ASP.NET Core 2,1** görmüyorsanız, iletişim kutusunun üst kısmına yakın bir sarı çubukta görünmesi gereken **indirme** bağlantısını izleyerek yükleyin.) **Tamam ' ı** seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **yeni proje oluştur** sayfasında, ara kutusuna **f # web** yazın ve ardından **ASP.NET Core web uygulaması** proje şablonu ' nu seçin. **İleri**’yi seçin.

4. **Yeni projenizi yapılandırın** sayfasında, bir ad girin ve ardından **Oluştur**' u seçin.

5. **yeni bir ASP.NET Core Web uygulaması oluştur** sayfasında, üst açılan menüden **ASP.NET Core 2,1** ' i seçin ve ardından **oluştur**' u seçin.

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

Kod basittir. bir F # değer dizisi `values` ada bağlanır ve sonra ASP.NET Core MVC çerçevesine bir olarak geçirilir `ActionResult` . ASP.NET Core, geri kalanını sizin yerinize gerçekleştirir.

Düzenleyicide şöyle görünmelidir:

![Değiştirilen üye Al](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1.  + Uygulamayı çalıştırmak ve bir Web tarayıcısında açmak için CTRL **F5** tuşuna basın.

2. Sayfa yola gitmelidir `/api/values` , ancak yoksa `https://localhost:44396/api/values` tarayıcınıza girin.

Web tarayıcısı artık daha önce yazdıklarınız ile eşleşen JSON 'ı görüntüleyecek.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! F #, ASP.NET Core ve Visual Studio ıde hakkında biraz bilgi edindiniz. Uygulamayı ortak bir sunucuda çalıştırmayı görmek için aşağıdaki düğmeyi seçin.

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service dağıtma](../deployment/quickstart-deploy-to-azure.md)

F # hakkında daha fazla bilgi edinmek için resmi [f # kılavuzuna](/dotnet/fsharp/index)göz atın.
