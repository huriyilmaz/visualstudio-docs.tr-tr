---
title: 'öğretici: F ''de ASP.NET Core web hizmeti oluşturma #'
description: 'bu öğreticide, F # ile Visual Studio bir ASP.NET Core web hizmeti oluşturmayı öğrenin.'
author: anandmeg
ms.author: meghaanand
ms.topic: tutorial
ms.date: 01/28/2022
ms.custom: vs-acquisition
ms.technology: vs-ide-general
dev_langs:
  - FSharp
ms.workload:
  - aspnet
  - dotnetcore
---

# <a name="tutorial-create-an-aspnet-core-web-service-in-f"></a>öğretici: F 'de ASP.NET Core web hizmeti oluşturma #

Visual Studio tümleşik geliştirme ortamı (ıde), çeşitli ürün türleri için F # destekler.
Tam bir Web Hizmetleri uygulamasını kolayca oluşturabilirsiniz.

F # ' da kodlama hakkında daha fazla bilgi için bkz. [f # nedir](/dotnet/fsharp/what-is-fsharp).
Merhaba Dünya konsol uygulaması oluşturmak için, bkz. [Visual Studio F # ile çalışmaya başlama](/dotnet/fsharp/get-started/get-started-visual-studio).

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
> - ASP.NET Core web hizmeti oluşturun.
> - F # içindeki **HttpGet** üyesine içerik ekleyin.
> - Programınızı derleyin ve çalıştırın.

## <a name="prerequisites"></a>Ön koşullar

::: moniker range="vs-2017"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ziyaret edin.
::: moniker-end
::: moniker range="vs-2019"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/) ziyaret edin.
::: moniker-end
::: moniker range=">=vs-2022"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/downloads) ziyaret edin.
::: moniker-end

Gerekli bileşenlerin yüklü olduğundan emin olun:

1. Windows **başlat** simgesini seçin ve *Visual Studio Yükleyicisi* yazın.
1. Yüklü iş yüklerinizi görmek için **Değiştir** ' i seçin.
1. **ASP.NET ve web geliştirme** 'nin seçildiğinden emin olun veya ekleyin.

   ![ekran görüntüsünde Visual Studio Yükleyicisi bir iş yükünü değiştirme gösterilmektedir.](./media/tutorial-fsharp-web-app/modify-visual-studio-workload.png)

1. Herhangi bir değişiklik yaptıysanız, bileşenleri yüklemek için **Değiştir** ' i seçin.

## <a name="create-an-aspnet-core-web-service"></a>ASP.NET Core web hizmeti oluşturma

bu bölümde bir ASP.NET Core Web apı projesi oluşturacaksınız.
Proje türü, herhangi bir şey eklemeden önce işlevsel bir Web hizmetini oluşturan şablon dosyaları ile birlikte gelir.

::: moniker range="vs-2017"
1. Visual Studio 2017'yi başlatın. üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin.

1. **yeni Project** iletişim kutusunda, sol bölmede, **Visual F#**' i genişletin ve **Web**' i seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin.

1. **Ad** Için, *fsharpöğreticisi* yazın ve ardından **Tamam**' ı seçin.

1. **yeni ASP.NET Core Web uygulaması** iletişim kutusunda varsayılan sürümü seçin.

   > [!NOTE]
   > ASP.NET Core 2,1 artık desteklenmiyor.
   > Üretim ortamları için desteklenmeyen seçenekler kullanılması önerilmez.

1. **Çözüm Gezgini**' de, **denetleyiciler** klasörünü genişletin ve ardından, düzenleyicide açmak için **valuescontroller. FS** ' yi seçin.

   ![Bir F # Web API projesinde genişletilmiş değerler denetleyicisiyle Çözüm Gezgini gösteren ekran görüntüsü.](./media/tutorial-fsharp-web-app/values-controller-fsharp-solution-explorer.png)

1. Sonra, varolan `Get()` üye örneğini aşağıdaki kodla eşleşecek şekilde değiştirin:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

   Bu kod, `values` ada bağlanan bir F # değer dizisi içerir.
   değerleri, ASP.NET Core model-view-controller çerçevesine bir `ActionResult` olarak geçirir.
   ASP.NET Core, geri kalanını sizin yerinize gerçekleştirir.

1. Projenizi çalıştırmak için **F5** tuşunu seçin.
   Merhaba Dünya iletinizi göstermek için bir tarayıcı penceresi açılır.

::: moniker-end
::: moniker range=">=vs-2019"
1. Visual Studio’yu çalıştırın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** sayfasında, ara kutusuna **F # Web** yazın. **ASP.NET Core Web apı 'si** proje şablonunu seçin ve ardından **ileri**' yi seçin.

1. **yeni projenizi yapılandırın** iletişim kutusunda **Project adı** için, *fsharpöğreticisi* girin.

1. **Ek bilgi** Iletişim kutusunda **Framework** için varsayılan sürümü kabul edin.

   **oluştur**' u seçtiğinizde, Visual Studio yeni F # projesi oluşturur. Proje bileşenlerini Çözüm Gezgini penceresinde görebilirsiniz.
   Visual Studio bir **genel bakış** sayfası sunar.

1. **Çözüm Gezgini** araç çubuğunda, **denetleyiciler** klasörünü genişletin ve ardından kod dosyasını düzenleyicide açmak için **dalgalı olarak denetleyici. FS** denetleyicisi ' ni seçin.

   ![Bir F # Web API projesinde genişletilmiş hava durumu tahmin denetleyicisiyle Çözüm Gezgini gösteren ekran görüntüsü.](./media/tutorial-fsharp-web-app/forecast-controller-fsharp-solution-explorer.png)

1. Sonra, üyeyi aşağıdaki kod olacak şekilde değiştirin `Get()` :

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

   Bu kod, `values` ada bağlanan bir F # değer dizisi içerir.
   değerleri, ASP.NET Core model-view-controller çerçevesine bir `ActionResult` olarak geçirir.
   ASP.NET Core, geri kalanını sizin yerinize gerçekleştirir.

1. Projenizi çalıştırmak için **F5** tuşunu seçin.
   Merhaba Dünya iletinizi göstermek için bir tarayıcı penceresi açılır.

::: moniker-end

> [!NOTE]
> IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti alırsanız, kodu bir Web tarayıcısında görüntülemek için **Evet** ' i seçin ve ardından bir izleme güvenlik uyarısı Iletisi alırsanız **Evet** ' i seçin.

## <a name="next-steps"></a>Sonraki adımlar

Henüz yapmadıysanız, [F # turuna](/dotnet/fsharp/tour)göz atın.
Bu tur, F # dilinin temel özelliklerini açıklar.
Bu, F # ' ın ve çalıştırabileceğiniz kod örneklerinin bazı özelliklerine genel bir bakış sağlar.

> [!div class="nextstepaction"]
> [F# Turu](/dotnet/fsharp/tour)

## <a name="see-also"></a>Ayrıca bkz.

- [F# dil başvurusu](/dotnet/fsharp/language-reference/index)
- [Tür çıkarımı](/dotnet/fsharp/language-reference/type-inference)
- [Sembol ve işleç başvurusu](/dotnet/fsharp/language-reference/symbol-and-operator-reference/index)
