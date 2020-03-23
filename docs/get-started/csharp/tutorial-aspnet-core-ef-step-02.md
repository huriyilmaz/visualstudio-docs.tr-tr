---
title: 'Adım 2: İlk ASP.NET Çekirdek Web Uygulaması Oluşturma'
description: Bu video eğitimi ve adım adım talimatlarla ilk ASP.NET Core Web Uygulamanızı oluşturun.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1d382e83aa9672cfdcbdca64b89be79d090f2aac
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580080"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Adım 2: İlk ASP.NET Core web uygulamanızı oluşturun

Bu video eğitimi ve adım adım talimatlarla ilk ASP.NET Core Web Uygulamanızı oluşturun.

_Bu videoyu izleyin ve ilk ASP.NET Core uygulamanızı oluşturmak için takip edin._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Visual Studio 2019'u başlatın ve yeni bir proje oluşturun

Visual Studio 2019'u başlatın ve **yeni proje oluştur'a**tıklayın. **Core Web Uygulaması ASP.NET**seçin. Web **Uygulaması** şablonu seçin ve varsayılan proje adını ve konumunu tutun. ASP.NET Core sürümü ile açılır, **Core 2.1** veya ASP.NET **Core 2.2**ASP.NET seçin. **Oluştur'u**tıklatın. Daha ayrıntılı talimatlar için, [bu öğretici serisiönceki video](tutorial-aspnet-core-ef-step-01.md)bakın.

![Visual Studio 2019 Temel Proje Seçenekleri ASP.NET seçin](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> ASP .NET Core 2.1 veya ASP.NET Core 2.2'yi seçtiğinizden emin olun. Bu öğretici core 3.x ile uyumlu ASP.NET.

## <a name="explore-the-new-project"></a>Yeni projeyi keşfedin

Sağdaki çözüm gezgini penceresinde, yeni projenin içeriğini görüntüleyebilirsiniz. Burada tarif edilebiliyorlar.

![Visual Studio 2019 ASP.NET Çekirdek Projesi](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

*wwwroot* klasörü, web uygulamasından genel olarak erişilebilen statik dosyaları tutar. Genellikle stil sayfaları, istemci tarafı komut dosyası dosyaları ve görüntüler tutar.

### <a name="pages"></a>Sayfalar

*Sayfalar* klasörü sitenin Jilet Sayfalarını tutar. Varsayılan şablon, uygulama giriş sayfası olan *Index.cshtml* sayfası nın yanı sıra About, Contact ve benzeri sayfalar da dahil olmak üzere çeşitli sayfalar sağlar.

### <a name="appsettingsjson"></a>appsettings.json

Bu dosya, JSON formatında site için yapılandırma ayarlarını tutar.

### <a name="programcs"></a>Program.cs

Bu dosya, uygulama için giriş noktası olarak hareket eder. Uygulama çalıştırıldığında, Ana yöntemi çalıştırılabilen ilk yöntemdir ve uygulamayı içerecek Web Barındıran Ağıt'ı oluşturmaktan sorumludur.

### <a name="startupcs"></a>Startup.cs

*Program.cs'da* oluşturulan Web Host, Başlangıç sınıfına başvurur ve uygulamayı yapılandırma yöntemlerini çağırır. ConfigureServices yöntemi, uygulamanın kullanacağı hizmetleri ayarlamakndan sorumludur. Yöntem, `Configure` uygulamanın HTTP istek ardışık hattını ayarlar. Her istek bu ardışık ardışık ardışık, bunu yaparken *ara yazılım* her parçası ile etkileşim geçer.

### <a name="indexcshtml"></a>Index.cshtml

Sitenin ana sayfasında bazı HTML biçimlendirmesi ve bazı sunucu tarafı Razor kodu bulunmaktadır. İlgili Index.cshtml.cs dosyasında bulunan `IndexModel`sayfa modelini belirtmek *Index.cshtml.cs* için Razor kullanır. Ayrıca ViewData'da bir değer ayarlayarak sayfa başlığını ayarlar. Bu Görünüm Verileri değeri, Pages klasöründeki Paylaşılan klasörde bulunan * \_Layout.cshtml* dosyasında okunur. Düzen dosyası birçok Razor Pages tarafından paylaşılır ve uygulama için ortak bir görünüm ve his sağlar. Her sayfanın içeriği Düzen dosyasının HTML'sinde işlenir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Şimdi uygulamayı çalıştırın ve tarayıcıda görüntüleyin. Uygulamayı **Ctrl**+**F5** kullanarak veya Visual Studio'nun menüsünden Hata Ayıklama olmadan **Hata Ayıklama** > **Başlat'ı** seçerek çalıştırabilirsiniz.

## <a name="customize-the-application"></a>Uygulamayı özelleştirme

*Index.cshtml.cs* dosyasına bir özellik ekleyin ve değerini `OnGet` işleyicideki geçerli saate ayarlayın:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

`<div>` *Index.cshtml'deki* içeriği şu biçimlendirmeyle değiştirin:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Uygulamayı yeniden çalıştırın. Sayfanın şu anda geçerli saati görüntülediğini görmeniz gerekir, ancak her zaman gece yarısıdır! Bu doğru değil.

![Visual Studio 2019 tarayıcıda ASP.NET Çekirdek Projesi](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

Değer atadığımız `OnGet` yönteme `Time` bir kesme noktası ekleyin ve bu kez uygulamayı hata ayıklamaya başlayın.

Yürütme satırda durur ve tarih `DateTime.Today` içerir görebilirsiniz ama zaman verileri içermez çünkü saat her zaman gece yarısı. 

![Visual Studio 2019 tarayıcıda ASP.NET Çekirdek Projesi](media/vs-2019/vs2019-breakpoint.png)

Kullanmak `DateTime.Now` için değiştirin ve yürütmeye devam edin. Yeni kod `OnGet` şu olmalıdır:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Şimdi uygulamaya gidince tarayıcıda gerçek sunucu süresini görmeniz gerekir.

> [!NOTE]
> ToShortDateTimeString'in çıktı biçimi geçerli kültür ayarına bağlı olduğundan çıktınız görüntüden farklı olabilir. Bkz. <xref:System.DateTime.ToShortTimeString>.

![Visual Studio 2019 tarayıcıda ASP.NET Çekirdek Projesi](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, uygulamanıza nasıl veri desteği ekleyeceğinizi öğreneceksiniz.

[Öğretici: ASP.NET Çekirdek Uygulamanızdaki Verilerle Çalışma](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: ASP.NET Core ile Bir Razor Pages web uygulaması oluşturun](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
