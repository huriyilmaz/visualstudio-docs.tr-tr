---
title: Web Blazor uygulamaları oluşturma
description: BlazorASP.NET Core'daki ASP.NET Core hakkında bilgi Mac için Visual Studio.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 30e9a62e8bf0364a76cbd43995cbb77c1a5bd0c4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725993"
---
# <a name="create-blazor-web-apps"></a>Web Blazor uygulamaları oluşturma

Bu kılavuz, ilk web uygulamanızı oluşturmaya giriş Blazor sunar. Daha ayrıntılı rehberlik için bkz. [ASP.NET Core. Blazor ](/aspnet/core/blazor/index)

BlazorASP.NET Core iki farklı barındırma seçeneği destekler; Blazor WebAssembly(WASM) veya Blazor Sunucu. Mac için Visual Studio iki barındırma modeli de destekler. Mac için Visual Studio 8.4+ Blazor Sunucu'Mac için Visual Studio 8.6+ her ikisini de destekler. Barındırma modelleri hakkında daha Blazor fazla bilgi için [bkz. ASP.NET Core barındırma Blazor modelleri. ](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1&preserve-view=true) Mac için Visual Studio projelerinde hata ayıklama Blazor WebAssembly desteği, v8.8'in Önizleme yayınlarında kullanılabilir (Güncelleştirmeleri **Denetleme... menüsündeki Önizleme güncelleştirme kanalı** üzerinden Visual Studio > kullanılabilir).

Nedir? Blazor Blazor , .NET ile etkileşimli istemci tarafı web kullanıcı arabirimi oluşturmak için bir çerçevedir ve web geliştiricilerine aşağıdaki avantajları sunar:

* JavaScript yerine C# ile kod yazın.
* .NET kitaplıklarının mevcut .NET ekosistemini kullanabilirsiniz.
* Uygulama mantığını sunucu ve istemci arasında paylaşın.
* avantajından faydalanma. NET'in performansı, güvenilirliği ve güvenliği.
* PC, Linux ve macOS Visual Studio daha verimli bir şekilde çalışma.
* Kararlı, özellik bakımından zengin ve kullanımı kolay ortak bir dil, çerçeve ve araç kümesi üzerinde derleme.

## <a name="create-a-new-blazor-webassembly-project"></a>Yeni proje Blazor WebAssembly oluşturma
1. Başlangıç Penceresinde **Yeni'yi** **seçerek** yeni bir proje oluşturun:

   ![Mac için Visual Studio Yeni seçim vurgulanmış Başlangıç Penceresi](media/blazor-new-project.png)

1. Yeni **Project** iletişim kutusunda **.NET Core** Uygulama Uygulaması'ni seçin ve Sonraki: Yeni Project iletişim kutusunun ekran >  > **Blazor WebAssembly**  ![ görüntüsü: Blazor WebAssembly Uygulama, ASP.NET Core altında Uygulama bölmesinde vurgulanmış ve Sonraki düğmesi seçilmiş.](media/blazor-wasm-project-template.png)

1. Hedef çerçeve olarak .NET Core 3.1'i ve ardından Sonraki'yi **seçin.** 
   ![Yeni Blazor WebAssembly Hedef Çerçeve 'nin .NET Core 3.1 olarak seçili olduğu uygulama iletişim kutusunu yapılandırma](media/blazor-wasm-select-target-framework.png)

1. Projeniz için bir ad seçin ve istenirse Git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.
    ![Yeni Blazor WebAssembly Uygulama iletişim kutusu, Ad alanına Project yapılandırma](media/blazor-wasm-name-project.png)

   Mac için Visual Studio kod düzeni penceresinde projenizi açar.

1. Uygulamayı **çalıştırmak için** Hata Ayıklama Olmadan  >  **Başlat'ı** seçin.

   Visual Studio [Kestrel'i](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı açar `https://localhost:5001` ve web Blazor uygulamanızı görüntüler.

   ![Blazor Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-blazor-server-project"></a>Yeni sunucu Blazor projesi oluşturma

1. Başlangıç Penceresinde **Yeni'yi** **seçerek** yeni bir proje oluşturun:

   ![Mac için Visual Studio Yeni seçim vurgulanmış Başlangıç Penceresi](media/blazor-new-project.png)
1. Yeni **Project** iletişim kutusunda **.NET Core** Uygulama Sunucusu Uygulaması'ni seçin ve Sonraki: Yeni Project iletişim kutusunun ekran >  > **Blazor**  ![ görüntüsü: Blazor ASP.NET Core altındaki Uygulama bölmesinde Sunucu Uygulaması vurgulanmış ve Sonraki düğmesi seçilmiş.](media/blazor-project-template.png)

1. Hedef çerçeve olarak .NET Core 3.1'i ve ardından Sonraki'yi **seçin.** 
   ![Yeni Blazor Hedef Çerçeve 'nin .NET Core 3.1 olarak seçili olduğu Sunucu Uygulaması iletişim kutusunu yapılandırma](media/blazor-select-target-framework.png)

1. Projeniz için bir ad seçin ve istenirse Git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.
   ![Yeni Blazor Sunucu Uygulaması iletişim kutusu, Ad alanına Project yapılandırma](media/blazor-name-project.png)

   Mac için Visual Studio kod düzeni penceresinde projenizi açar.
1. Uygulamayı **çalıştırmak için** Hata Ayıklama Olmadan  >  **Başlat'ı** seçin.

   Visual Studio [Kestrel'i](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı açar `https://localhost:5001` ve web Blazor uygulamanızı görüntüler.

   ![Blazor Microsoft Edge](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>BlazorMac için Visual Studio'de destek

Mac için Visual Studio (sürüm 8.4'den başlayarak) yeni sunucu projeleri oluşturmanıza yardımcı olacak yeni Blazor özellikler içerir. Ayrıca, projelerin inşası, çalıştırması ve hata ayıklaması gibi beklediğiniz standart desteği Blazor de sağlar. Bu Mac için Visual Studio oluşturma, oluşturma ve çalıştırma için 8.6 Blazor WebAssembly desteği eklendi.

Yukarıdaki kılavuzda, Sunucu Uygulaması proje şablonunun yeni bir Sunucu Uygulaması veya Uygulama projesi oluşturmanıza nasıl Blazor Blazor yardımcı olduğunu Blazor WebAssembly gördük. Şimdi proje geliştirmeyi desteklemek için Mac için Visual Studio bazı ek özelliklere Blazor göz at bakalım.

### <a name="editor-support-for-razor-files"></a>*.razor* dosyaları için düzenleyici desteği
Mac için Visual Studio . razor dosyalarını düzenleme desteği içerir. Bu, uygulama oluştururken kullanmakta olacağınız dosyaların Blazor çoğunluğunu içerir. Mac için Visual Studio, projede bildirilen Razor bileşenleri için tamamlamalar da dahil olmak üzere .razor dosyalarınız için tam renklendirme ve tamamlama desteği sağlar.

![Mac için Visual Studio için IntelliSense'i gösteren bir düzenleyici penceresi: ::no-loc(Blazor):::](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Uygulamaları Blazor Azure App Service
Ayrıca uygulamaları doğrudan Blazor Azure App Service. Azure'da çalıştırılacak bir Azure hesabınız yoksa, burada her zaman 12 ay boyunca ücretsiz popüler hizmetler, 200 ABD doları ücretsiz Azure kredisi ve her zaman ücretsiz 25'in üzerinde hizmetle birlikte gelen ücretsiz bir hesap için Blazor kaydolabilirsiniz. [](https://azure.microsoft.com/free)

![Mac için Visual Studio Azure yayımlama deneyimini gösteren uygulama](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Proje anatomisi

Blazor web uygulamaları varsayılan olarak birkaç dizin ve dosya içerir. Başlarken şu ana bilgi sahibi olmak için ihtiyacınız olan temeller:

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör, projenin *.razor* dosya uzantısını kullanan web sayfalarını içerir.

### <a name="shared-folder"></a>Paylaşılan klasör

Bu klasör paylaşılan bileşenleri içerir ve *.razor uzantısını da* kullanır. Bunun, uygulama genelinde ortak düzeni tanımlamak için kullanılan *MainLayout.razor'ı* da içerir. Ayrıca tüm sayfalarda *kullanılan paylaşılan NavMenu.razor* bileşenini de içerir. Yeniden kullanılabilir bileşenler oluşturuyorsanız, bunlar Paylaşılan **klasörüne** gider.

### <a name="app-settings"></a>Uygulama ayarları

*appSettings.json dosyası* bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [bkz. yapılandırma ASP.NET.](/aspnet/core/fundamentals/configuration/index)

### <a name="wwwroot-folder"></a>wwwroot klasörü

Bu klasör HTML, JavaScript ve CSS dosyaları gibi statik dosyaları içerir. Daha fazla bilgi için [bkz. ASP.NET Core.](/aspnet/core/fundamentals/static-files)

### <a name="programcs"></a>Program.cs

Bu dosya, programın giriş noktasını içerir. Daha fazla bilgi için [bkz. ASP.NET Core Web Ana Bilgisayarı.](/aspnet/core/fundamentals/host/web-host)

### <a name="blazor-server-app-specific-files"></a>Blazor Sunucu Uygulamasına özgü dosyalar
#### <a name="app-settings"></a>Uygulama ayarları

*appSettings.json dosyası* bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [bkz. yapılandırma ASP.NET.](/aspnet/core/fundamentals/configuration/index)

#### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın tanımlama bilgileri için onay isteyip istemesi gibi uygulama davranışını yapılandıran kodu içerir. Daha fazla bilgi için [bkz. ASP.NET Core.](/aspnet/core/fundamentals/startup)

## <a name="summary"></a>Özet
Bu öğreticide, Mac için Visual Studio'de yeni bir Sunucu Uygulaması veya Uygulama oluşturma hakkında bilgi edindi ve uygulama oluşturmanıza yardımcı olmak için Mac için Visual Studio özellikler hakkında Blazor Blazor WebAssembly bilgi Blazor edindi.

## <a name="see-also"></a>Ayrıca bkz.

Web uygulaması oluşturma hakkında daha kapsamlı bir Blazor kılavuz için [bkz. ASP.NET Core. Blazor ](/aspnet/core/blazor/index)