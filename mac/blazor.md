---
title: Blazor Web uygulamaları oluşturma
description: Mac için Visual Studio ASP.NET Core uygulamalarda Blazor desteği hakkında bilgi sağlar.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.topic: how-to
ms.openlocfilehash: ac7fcd9044aa6367f140ac4aa96e6aaf4a9f5885
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939144"
---
# <a name="create-blazor-web-apps"></a>Blazor Web uygulamaları oluşturma

Bu kılavuzda, ilk Blazor Web uygulamanızı oluşturmaya yönelik bir giriş sunulmaktadır. Daha ayrıntılı bilgi için bkz. [giriş ASP.NET Core Blazor](/aspnet/core/blazor/index).

ASP.NET Core Blazor iki farklı barındırma seçeneğini destekler; Blazor Server ve Blazor WebAssembly. Mac için Visual Studio hem barındırma modellerini destekler. Mac için Visual Studio 8.4 + Blazor sunucusunu destekler ve Mac için Visual Studio 8.6 + destekler. Blazor barındırma modelleriyle ilgili daha fazla bilgi için bkz. [ASP.NET Core Blazor barındırma modelleri ](https://docs.microsoft.com/aspnet/core/blazor/hosting-models?view=aspnetcore-3.1). Mac için Visual Studio 'de Blazor WebAssembly projelerinde hata ayıklama desteği 8,6 sonrasında bir yayında yer alacak.

Blazor nedir? Blazor, Web geliştiricilerine aşağıdaki avantajları sunan, .NET ile etkileşimli istemci tarafı Web Kullanıcı arabirimi oluşturmaya yönelik bir çerçevedir:

* JavaScript yerine C# dilinde kod yazın.
* .NET kitaplıklarının mevcut .NET ekosisteminden yararlanın.
* Sunucu ve istemci arasında uygulama mantığını paylaşma.
* Avantajı. NET ' in performans, güvenilirlik ve güvenlik.
* PC, Linux ve macOS 'ta Visual Studio ile üretken olun.
* Kararlı, özellik açısından zengin ve kullanımı kolay olan ortak diller, çerçeveler ve araçlar kümesi oluşturun.

## <a name="creating-a-new-blazor-server-project"></a>Yeni bir Blazor Server projesi oluşturma

1. Yeni bir proje oluşturmak için **Başlangıç penceresinde** **Yeni** ' yi seçin:

   ![Yeni seçim vurgulanmış şekilde başlangıç penceresi Mac için Visual Studio](media/blazor-new-project.png)
1. **Yeni proje** iletişim kutusunda, **.NET Core** > **App** > **Blazor Server uygulaması** ' nı seçin ve **İleri ' yi**seçin: ![ Blazor Server uygulama şablonu seçiliyken yeni proje iletişim kutusu için bir şablon seçin](media/blazor-project-template.png)

1. Hedef çerçeve olarak .NET Core 3,1 ' i seçin ve ardından **İleri**' yi seçin. 
   ![Yeni Blazor Server uygulamanızı, .NET Core 3,1 ' de seçili hedef Framework ile birlikte yapılandırın](media/blazor-select-target-framework.png)

1. Projeniz için bir ad seçin ve isterseniz git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.
   ![BYeni Blazor Server uygulamanızı yapılandırma iletişim kutusunu proje adı girerken görüntülendi](media/blazor-name-project.png)

   Mac için Visual Studio, projenizi kod düzeni penceresinde açar.
1. **Run**  >  Uygulamayı çalıştırmak için**hata ayıklama olmadan başlatmayı** Çalıştır ' ı seçin.

   Visual Studio, [Kestrel](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı açar `https://localhost:5001` ve Blazor Web uygulamanızı görüntüler.

   ![Safari 'de Blazor Web App](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Mac için Visual Studio desteği Blazor

Mac için Visual Studio (sürüm 8,4 ' den itibaren), yeni Blazor Server projeleri oluşturmanıza yardımcı olacak yeni özellikler içerir. Ayrıca, Blazor projelerini oluşturma, çalıştırma ve hata ayıklama gibi bekleeceğiniz standart desteği sunar. Mac için Visual Studio 8,6 ' de, Blazor WebAssembly projelerini oluşturma, oluşturma ve çalıştırma desteği eklenmiştir.

Yukarıdaki izlenecek yolda, Blazor Server App Project şablonunun yeni bir Blazor Server uygulama projesi oluşturmanıza nasıl yardımcı olduğunu gördük. Blazor proje geliştirmeyi desteklemek için Mac için Visual Studio bazı ek özelliklere göz atalım.

### <a name="editor-support-for-razor-files"></a>*. Razor* dosyaları için düzenleyici desteği
Mac için Visual Studio, Blazor uygulamaları oluştururken kullanacağınız dosyaların büyük çoğunluğu olan. Razor dosyalarını düzenlemeyle ilgili destek içerir. IDE 'nin Windows ve Mac sürümü. Razor dosyaları için aynı düzenleyiciyi paylaşır. Projede belirtilen Razor bileşenleri için tamamlama dahil olmak üzere. Razor dosyalarınız için tam renklendirme ve tamamlama desteği görürsünüz.

![Blazor için IntelliSense 'i gösteren Mac için Visual Studio Düzenleyicisi penceresi](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Azure App Service Blazor uygulamalarını yayımlama
Ayrıca, Blazor uygulamalarını doğrudan Azure App Service yayınlayabilirsiniz. Blazor uygulamanızı Azure 'da çalıştırmak için bir Azure hesabınız yoksa, burada 12 ay ücretsiz popüler hizmetler, $200 ücretsiz Azure kredisi ve 25 her zaman ücretsiz hizmet için de sunulan [ücretsiz bir oturum için kaydolabilirsiniz](https://azure.microsoft.com/free) .

![Azure yayımlama deneyimini gösteren Mac için Visual Studio](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Proje anatomumu

Blazor Web Apps, varsayılan olarak birkaç dizin ve dosya içerir. Başlarken şu ana kadar tanıdık yapmanız gerekenler şunlardır:

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

### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın tanımlama bilgileri için izin gerektirip gerektirmediğini belirtir gibi uygulama davranışını yapılandıran kodu içerir. Daha fazla bilgi için [ASP.NET Core uygulamasında uygulama başlatma](/aspnet/core/fundamentals/startup)bölümüne bakın.

## <a name="summary"></a>Özet
Bu öğreticide, Mac için Visual Studio yeni bir Blazor Server uygulaması oluşturmayı ve Mac için Visual Studio tarafından Blazor uygulamaları oluşturmanıza yardımcı olacak bazı özelliklerden öğrenirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

Blazor Web uygulamaları oluşturmaya yönelik daha kapsamlı bir kılavuz için bkz. [ASP.NET Core Blazor 'ye giriş](/aspnet/core/blazor/index).
