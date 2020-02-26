---
title: '2\. Adım: Ilk ASP.NET Core Web uygulamanızı oluşturma'
description: Bu video öğreticisiyle ilk ASP.NET Core Web uygulamanızı oluşturun ve adım adım yönergeleri uygulayın.
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580080"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>2\. Adım: ilk ASP.NET Core Web uygulamanızı oluşturma

Bu video öğreticisiyle ilk ASP.NET Core Web uygulamanızı oluşturun ve adım adım yönergeleri uygulayın.

_İlk ASP.NET Core uygulamanızı oluşturmak için bu videoyu izleyin ve takip edin._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Visual Studio 2019 'yi başlatın ve yeni bir proje oluşturun

Visual Studio 2019 ' u başlatın ve **Yeni proje oluştur**' a tıklayın. **ASP.NET Core Web uygulaması**' nı seçin. **Web uygulaması** şablonunu seçin ve varsayılan proje adını ve konumunu tutun. ASP.NET Core sürümüyle açılan menüde, **ASP.NET Core 2,1** veya **ASP.NET Core 2,2**' i seçin. **Oluştur**’ tıklayın. Daha ayrıntılı yönergeler için [Bu öğretici serisinde önceki videoya](tutorial-aspnet-core-ef-step-01.md)bakın.

![Visual Studio 2019 ASP.NET Core projesi seçeneklerini belirleyin](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> ASP .NET Core 2,1 veya ASP.NET Core 2,2 ' i seçtiğinizden emin olun. Bu öğretici ASP.NET Core 3. x ile uyumlu değildir.

## <a name="explore-the-new-project"></a>Yeni projeyi keşfet

Sağ taraftaki Çözüm Gezgini penceresinde, yeni projenin içeriğini görebilirsiniz. Burada açıklanırlar.

![Visual Studio 2019 ASP.NET Core projesi](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>Wwwroot

*Wwwroot* klasörü, Web uygulamasından herkese açık olarak erişilebilen statik dosyaları barındırır. Genellikle stil sayfaları, istemci tarafı betik dosyaları ve görüntüleri barındırır.

### <a name="pages"></a>Sayfalar

*Sayfalar* klasörü, sitenin Razor Pages barındırır. Varsayılan şablon, uygulama giriş sayfası olan *Index. cshtml* sayfası ve hakkında, ilgili olarak, vb. dahil olmak üzere çeşitli sayfalar sağlar.

### <a name="appsettingsjson"></a>appSettings. JSON

Bu dosya, JSON biçiminde site için yapılandırma ayarlarını barındırır.

### <a name="programcs"></a>Program.cs

Bu dosya, uygulama için giriş noktası işlevi görür. Uygulama çalıştırıldığında, ana yöntemi çalıştırılan ilk yöntemdir ve uygulamayı içerecek olan Web konağını oluşturmaktan sorumludur.

### <a name="startupcs"></a>Startup.cs

*Program.cs* Içinde oluşturulan Web ana bilgisayarı başlangıç sınıfına başvurur ve uygulamayı yapılandırmak için yöntemlerini çağırır. ConfigureServices yöntemi, uygulamanın kullanacağı Hizmetleri ayarlamaktan sorumludur. `Configure` yöntemi, uygulamanın HTTP isteği ardışık düzenini ayarlar. Her istek bu işlem hattından geçerek her bir *Ara yazılım* ile etkileşime girer.

### <a name="indexcshtml"></a>Index.cshtml

Sitenin ana sayfası, bazı HTML biçimlendirmeleri ve bazı sunucu tarafı Razor kodlarını içerir. İlişkili *Index.cshtml.cs* dosyasında bulunan `IndexModel`sayfa modelini belirtmek için Razor kullanır. Ayrıca, ViewData içindeki bir değeri ayarlayarak sayfa başlığını ayarlar. Bu ViewData değeri, sayfalar klasörünün içindeki paylaşılan klasörde bulunan *\_Layout. cshtml* dosyasında okundu. Düzen dosyası pek çok Razor Pages paylaşılır ve uygulama için ortak görünüm sağlar. Her sayfanın içeriği, düzen dosyasının HTML 'si içinde işlenir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Şimdi uygulamayı çalıştırın ve tarayıcıda görüntüleyin. Uygulamayı **Ctrl**+**F5** kullanarak veya Visual Studio 'nun menüsünden hata ayıklama ** > ** **Başlat** ' a seçerek çalıştırabilirsiniz.

## <a name="customize-the-application"></a>Uygulamayı özelleştirme

*Index.cshtml.cs* dosyasına bir özellik ekleyin ve değerini `OnGet` işleyicisinde geçerli zamana ayarlayın:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

*Index. cshtml* 'deki `<div>` içeriğini bu biçimlendirme ile değiştirin:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Uygulamayı yeniden çalıştırın. Sayfanın şimdi geçerli saati görüntülediğini görmeniz gerekir, ancak her zaman gece yarısı! Bu doğru değildir.

![Visual Studio 2019 ASP.NET Core tarayıcıda proje](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Uygulamada hata ayıklama

`Time` bir değer atadığımızda `OnGet` yöntemine bir kesme noktası ekleyin ve bu kez uygulamada hata ayıklamayı başlatın.

Yürütme satırda duraklar ve `DateTime.Today` tarihi de içerdiğini görebilirsiniz, ancak saat verisi içermediğinden saat her zaman gece yarısı olur. 

![Visual Studio 2019 ASP.NET Core tarayıcıda proje](media/vs-2019/vs2019-breakpoint.png)

`DateTime.Now` kullanacak şekilde değiştirin ve yürütülmeye devam edin. `OnGet` için yeni kod şu olmalıdır:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Uygulamaya gittiğinizde, şimdi tarayıcıda gerçek sunucu saatini görmeniz gerekir.

> [!NOTE]
> ToShortDateTimeString 'in çıkış biçimi geçerli kültür ayarına bağlı olduğundan, çıktınızın görüntüsü farklılık gösterebilir. Bkz. <xref:System.DateTime.ToShortTimeString>.

![Visual Studio 2019 ASP.NET Core tarayıcıda proje](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Sonraki adımlar

Bir sonraki videoda, uygulamanıza veri desteği eklemeyi öğreneceksiniz.

[Öğretici: ASP.NET Core uygulamanızdaki verilerle çalışma](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: ASP.NET Core bir Razor Pages Web uygulaması oluşturma](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
