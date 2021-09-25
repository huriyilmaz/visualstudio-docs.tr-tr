---
title: "hızlı başlangıç: F 'de ASP.NET Core web hizmeti oluşturma #"
description: 'F # ile Visual Studio bir ASP.NET Core web hizmeti oluşturmayı öğrenin, adım adım.'
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
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427765"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>hızlı başlangıç: ilk ASP.NET Core web hizmetinizi F 'de oluşturmak için Visual Studio kullanma\#

bu 5-10 dakika içinde f # ' a giriş Visual Studio, bir f # ASP.NET Core web uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

ilk olarak, bir ASP.NET Core Web apı projesi oluşturacaksınız. Proje türü, hatta herhangi bir şey eklemeden önce işlevsel bir Web hizmetini oluşturan şablon dosyaları ile birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. **yeni Project** iletişim kutusunda, sol bölmede, **Visual F#**' i genişletin ve **Web**' i seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin ve ardından **tamam**' ı seçin.

   **.net Core** proje şablonu kategorisini görmüyorsanız sol bölmedeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

   ![VS yükleyicisinde iş yükünü ASP.NET](../ide/media/quickstart-aspnet-workload.png)

1. **yeni ASP.NET Core Web uygulaması** iletişim kutusunda üst açılan menüden **ASP.NET Core 2,1** ' ı seçin. (listede **ASP.NET Core 2,1** görmüyorsanız, iletişim kutusunun üst kısmına yakın bir sarı çubukta görünmesi gereken **indirme** bağlantısını izleyerek yükleyin.) **Tamam ' ı** seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **yeni proje oluştur** sayfasında, ara kutusuna **f # web** yazın ve ardından **ASP.NET Core web uygulaması** proje şablonu ' nu seçin. **İleri**’yi seçin.

1. **Yeni projenizi yapılandırın** sayfasında, bir ad girin ve ardından **Oluştur**' u seçin.

1. **yeni bir ASP.NET Core Web uygulaması oluştur** sayfasında, üst açılan menüden **ASP.NET Core 2,1** ' i seçin ve ardından **oluştur**' u seçin.

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. **Çözüm Gezgini** araç çubuğunda, **denetleyiciler** klasörünü genişletin ve ardından, düzenleyicide açmak için **valuescontroller. FS** ' yi seçin.

   ![Bir F # Web API projesinde genişletilmiş denetleyiciler klasörüyle Çözüm Gezgini ekran görüntüsü.](../ide/media/hello-world-fs-sln-explorer.png)

1. Sonra, `Get()` üyeyi aşağıdakiler olacak şekilde değiştirin:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. bir F # değer dizisi `values` ada bağlanır ve sonra ASP.NET Core MVC çerçevesine bir olarak geçirilir `ActionResult` . ASP.NET Core, geri kalanını sizin yerinize gerçekleştirir.

Düzenleyicide şöyle görünmelidir:

![ValuesController. FS içindeki Get üyesine yönelik değiştirilen kodu gösteren ekran görüntüsü.](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1.  + Uygulamayı çalıştırmak ve bir Web tarayıcısında açmak için CTRL **F5** tuşuna basın.

1. Sayfa yola gitmelidir `/api/values` , ancak yoksa `https://localhost:44396/api/values` tarayıcınıza girin.

Web tarayıcısı artık daha önce yazdıklarınız ile eşleşen JSON 'ı görüntüleyecek.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** penceresinde, arama kutusuna **f # Web** yazın ya da listeyi daraltmak için dil, platform ve proje türü filtrelerini kullanın. **ASP.NET Core Web apı 'si** proje şablonunu seçin ve ardından **ileri**' yi seçin.

1. **yeni projenizi yapılandırın** penceresinde bir **Project adı** girin ve ardından **ileri**' yi seçin.

1. **Ek bilgi** penceresinde, **Framework** alanında **.net 6,0** ' ın göründüğünü doğrulayın ve ardından **Oluştur**' u seçin.

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. **Çözüm Gezgini** araç çubuğunda, **denetleyiciler** klasörünü genişletin ve ardından, düzenleyicide açmak için **dalgalı tahmin. FS** ' yi seçin.

   :::image type="content" source="media/vs-2022/hello-world-fs-sln-explorer.png" alt-text="Bir F # Web API projesinde genişletilmiş denetleyiciler klasörüyle Çözüm Gezgini gösteren ekran görüntüsü.":::

1. Sonra, varolan `Get()` üye örneğini aşağıdaki kodla eşleşecek şekilde değiştirin:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kod basittir. bir F # değer dizisi `values` ada bağlanır ve sonra ASP.NET Core MVC çerçevesine bir olarak geçirilir `ActionResult` . ASP.NET Core, geri kalanını sizin yerinize gerçekleştirir.

Düzenleyicide şöyle görünmelidir:

:::image type="content" source="media/vs-2022//hello-world-fs-get-member.png" alt-text="Dalgalı tahmin. FS 'de Get üyesinin değiştirilme kodunu gösteren ekran görüntüsü.":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

 + Uygulamayı çalıştırmak ve bir Web tarayıcısında açmak için CTRL **F5** tuşuna basın. 

> [!NOTE]
> IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti alırsanız, kodu bir Web tarayıcısında görüntülemek için **Evet** ' i seçin ve ardından bir izleme güvenlik uyarısı Iletisi alırsanız **Evet** ' i seçin.

Visual Studio, daha önce eklediğiniz "Merhaba Dünya" iletisiyle eşleşen JSON 'yi görüntüleyen bir tarayıcı penceresi başlatır.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! F #, ASP.NET Core ve Visual Studio ıde hakkında bir şey öğrendiklerinizi umuyoruz. Uygulamayı ortak bir sunucuda çalıştırmayı görmek için aşağıdaki düğmeyi seçin.

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service dağıtma](../deployment/quickstart-deploy-to-azure.md)

F # hakkında daha fazla bilgi edinmek için resmi [f # kılavuzuna](/dotnet/fsharp/index)göz atın.
