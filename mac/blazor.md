---
title: BlazorWeb uygulamaları oluşturma
description: BlazorMac için Visual Studio ASP.NET Core uygulamalarda destek hakkında bilgi sağlar.
author: jongalloway
ms.author: jogallow
ms.date: 08/31/2020
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 3280e63ae92a99cfa076b79e499a7b18952285c4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584041"
---
# <a name="create-no-locblazor-web-apps"></a>BlazorWeb uygulamaları oluşturma

Bu kılavuzda, ilk Web uygulamanızı oluşturmaya yönelik bir giriş sunulmaktadır Blazor . Daha ayrıntılı bilgi için bkz. [tanıtım ASP.NET Core Blazor ](/aspnet/core/blazor/index).

ASP.NET Core Blazor iki farklı barındırma seçeneğini destekler; Blazor WebAssembly (IStream) veya Blazor Server. Mac için Visual Studio hem barındırma modellerini destekler. Mac için Visual Studio 8.4 + Blazor sunucuyu destekler ve Mac için Visual Studio 8.6 + destekler. Barındırma modelleriyle ilgili daha fazla bilgi için Blazor bkz. [ASP.NET Core Blazor barındırma modelleri ](/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). Mac için Visual Studio 'deki projelerin hata ayıklama desteği, Blazor WebAssembly v 8.8 'In önizleme sürümünde (Visual Studio 'Da önizleme güncelleştirme kanalı aracılığıyla kullanılabilir **> güncelleştirmeleri denetle...** menüsünü kullanarak kullanılabilir).

Nedir Blazor ? Blazor , Web geliştiricilerine aşağıdaki avantajları sunan, .NET ile etkileşimli istemci tarafı Web Kullanıcı arabirimi oluşturmaya yönelik bir çerçevedir:

* JavaScript yerine C# dilinde kod yazın.
* .NET kitaplıklarının mevcut .NET ekosisteminden yararlanın.
* Sunucu ve istemci arasında uygulama mantığını paylaşma.
* Avantajı. NET ' in performans, güvenilirlik ve güvenlik.
* PC, Linux ve macOS 'ta Visual Studio ile üretken olun.
* Kararlı, özellik açısından zengin ve kullanımı kolay olan ortak diller, çerçeveler ve araçlar kümesi oluşturun.

## <a name="create-a-new-no-locblazor-webassembly-project"></a>Yeni bir Blazor WebAssembly proje oluştur
1. Yeni bir proje oluşturmak için **Başlangıç penceresinde** **Yeni** ' yi seçin:

   ![Yeni seçim vurgulanmış şekilde başlangıç penceresi Mac için Visual Studio](media/blazor-new-project.png)

1. **Yeni proje** iletişim kutusunda **.NET Core** > **uygulama** > ** Blazor WebAssembly uygulaması** ' nı seçin ve ileri ' **yi**seçin: ![ Yeni proje iletişim kutusu için bir şablon seçin::: No-Loc (Blazor)::: sunucu uygulama şablonu seçildi](media/blazor-wasm-project-template.png)

1. Hedef çerçeve olarak .NET Core 3,1 ' i seçin ve ardından **İleri**' yi seçin. 
   ![New::: No-Loc (Blazor WebAssembly)::: Target Framework ile birlikte .NET Core 3,1 için seçili olan uygulama iletişim kutusunu yapılandırın](media/blazor-wasm-select-target-framework.png)

1. Projeniz için bir ad seçin ve isterseniz git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.
    ![Yeni::: No-Loc (Blazor WebAssembly)::: proje adı girerken görünen uygulama iletişim kutusunu yapılandırın](media/blazor-wasm-name-project.png)

   Mac için Visual Studio, projenizi kod düzeni penceresinde açar.

1. **Run**  >  Uygulamayı çalıştırmak için**hata ayıklama olmadan başlatmayı** Çalıştır ' ı seçin.

   Visual Studio, [Kestrel](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı açar `https://localhost:5001` ve Blazor Web uygulamanızı görüntüler.

   ![::: No-Loc (Blazor)::: Microsoft Edge 'de Web uygulaması](media/blazor-new-app-in-edge.png)

## <a name="creating-a-new-no-locblazor-server-project"></a>Yeni bir Blazor sunucu projesi oluşturma

1. Yeni bir proje oluşturmak için **Başlangıç penceresinde** **Yeni** ' yi seçin:

   ![Yeni seçim vurgulanmış şekilde başlangıç penceresi Mac için Visual Studio](media/blazor-new-project.png)
1. **Yeni proje** iletişim kutusunda, **.NET Core** > **App** > ** Blazor Server uygulaması** ' nı seçin ve **İleri ' yi**seçin: ![ Yeni proje iletişim kutusu için bir şablon seçin::: No-Loc (Blazor)::: sunucu uygulama şablonu seçildi](media/blazor-project-template.png)

1. Hedef çerçeve olarak .NET Core 3,1 ' i seçin ve ardından **İleri**' yi seçin. 
   ![New::: No-Loc (Blazor)::: .NET Core 3,1 ' a seçili hedef Framework ile birlikte görüntülenecek sunucu uygulaması iletişim kutusunu yapılandırın](media/blazor-select-target-framework.png)

1. Projeniz için bir ad seçin ve isterseniz git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.
   ![Yeni::: No-Loc (Blazor)::: sunucu uygulaması iletişim kutusunun Proje adı girilirken görüntülendiğini yapılandırın](media/blazor-name-project.png)

   Mac için Visual Studio, projenizi kod düzeni penceresinde açar.
1. **Run**  >  Uygulamayı çalıştırmak için**hata ayıklama olmadan başlatmayı** Çalıştır ' ı seçin.

   Visual Studio, [Kestrel](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı açar `https://localhost:5001` ve Blazor Web uygulamanızı görüntüler.

   ![::: No-Loc (Blazor)::: Microsoft Edge 'de Web uygulaması](media/blazor-new-app-in-edge.png)

## <a name="no-locblazor-support-in-visual-studio-for-mac"></a>Blazor Mac için Visual Studio desteği

Mac için Visual Studio (sürüm 8,4 ' den başlayarak) yeni sunucu projeleri oluşturmanıza yardımcı olacak yeni özellikler içerir Blazor . Ayrıca, proje oluşturma, çalıştırma ve hata ayıklama gibi bir standart destek sağlar Blazor . Oluşturma, oluşturma ve çalıştırma için Mac için Visual Studio 8,6 desteği Blazor WebAssembly eklenmiştir.

Yukarıdaki izlenecek yolda, Blazor sunucu uygulaması proje şablonunun yeni bir Blazor sunucu uygulaması veya uygulama projesi oluşturmanıza nasıl yardımcı olduğunu gördük Blazor WebAssembly . Mac için Visual Studio, proje geliştirmeyi desteklemek için bazı ek özelliklere göz atalım Blazor .

### <a name="editor-support-for-razor-files"></a>*. Razor* dosyaları için düzenleyici desteği
Mac için Visual Studio,. Razor dosyalarının düzenlenmesine yönelik destek içerir. uygulamalar oluştururken kullanacağınız dosyaların çoğunluğu Blazor . Mac için Visual Studio, projede belirtilen Razor bileşenleri için tamamlama dahil olmak üzere. Razor dosyalarınız için tam renklendirme ve tamamlama desteği sağlar.

![IntelliSense 'i gösteren Mac için Visual Studio Düzenleyicisi penceresi::: No-Loc (Blazor):::](media/blazor-intellisense.png)

### <a name="publishing-no-locblazor-applications-to-azure-app-service"></a>BlazorUygulamaları Azure App Service yayımlama
Ayrıca, Blazor uygulamaları doğrudan Azure App Service için de yayımlayabilirsiniz. Uygulamanızı Azure 'da çalıştırmak için bir Azure hesabınız yoksa Blazor , burada 12 aylık ücretsiz hizmetler $200, ücretsiz Azure kredileri ve 25 ' ten fazla ücretsiz hizmet ile birlikte gelen ücretsiz [bir ücretsiz hizmet için](https://azure.microsoft.com/free) de her zaman ücretsiz kaydolabilirsiniz.

![Azure yayımlama deneyimini gösteren Mac için Visual Studio](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Proje anatomisi

Blazor Web uygulamaları, varsayılan olarak birkaç dizin ve dosya içerir. Başlarken şu ana kadar tanıdık yapmanız gerekenler şunlardır:

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör, bir projenin *. Razor* dosya uzantısını kullanan Web sayfalarını içerir.

### <a name="shared-folder"></a>Paylaşılan klasör

Bu klasör, *. Razor* uzantısını kullanarak da paylaşılan bileşenleri içerir. Bunun, uygulama genelinde ortak düzeni tanımlamak için kullanılan *mainlayout. Razor*içerdiğini görürsünüz. Ayrıca, tüm sayfalarda kullanılan paylaşılan *Navmenu. Razor* bileşenini de içerir. Yeniden kullanılabilir bileşenler oluşturuyorsanız, **paylaşılan** klasöre gider.

### <a name="app-settings"></a>Uygulama ayarları

Dosyadaki *appSettings.js* , bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [ASP.net Kılavuzu 'Ndaki yapılandırmaya](/aspnet/core/fundamentals/configuration/index)bakın.

### <a name="wwwroot-folder"></a>Wwwroot klasörü

Bu klasör HTML, JavaScript ve CSS dosyaları gibi statik dosyaları içerir. Daha fazla bilgi için [ASP.NET Core Içindeki statik dosyalar](/aspnet/core/fundamentals/static-files)bölümüne bakın.

### <a name="programcs"></a>Program.cs

Bu dosya, program için giriş noktasını içerir. Daha fazla bilgi için bkz. [ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="no-locblazor-server-app-specific-files"></a>Blazor Sunucu uygulamaya özgü dosyalar
#### <a name="app-settings"></a>Uygulama ayarları

Dosyadaki *appSettings.js* , bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [ASP.net Kılavuzu 'Ndaki yapılandırmaya](/aspnet/core/fundamentals/configuration/index)bakın.

#### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın tanımlama bilgileri için izin gerektirip gerektirmediğini belirtir gibi uygulama davranışını yapılandıran kodu içerir. Daha fazla bilgi için [ASP.NET Core uygulamasında uygulama başlatma](/aspnet/core/fundamentals/startup)bölümüne bakın.

## <a name="summary"></a>Özet
Bu öğreticide, Mac için Visual Studio yeni bir Blazor sunucu uygulaması veya Blazor WebAssembly uygulaması oluşturmayı ve Mac için Visual Studio sunduğu ve uygulamalar oluşturmanıza yardımcı olan özelliklerden bazıları hakkında bilgi edindiniz Blazor .

## <a name="see-also"></a>Ayrıca bkz.

Web uygulamaları oluşturmaya yönelik daha kapsamlı bir kılavuz için Blazor bkz. [tanıtım ASP.NET Core Blazor ](/aspnet/core/blazor/index).