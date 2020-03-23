---
title: Blazor web uygulamaları oluşturma
description: Mac için Visual Studio'daki ASP.NET Core uygulamalarında Blazor desteği hakkında bilgi sağlar.
author: jongalloway
ms.author: jogallow
ms.date: 12/17/2019
ms.technology: vs-ide-general
ms.assetid: D2717D3A-9225-40A8-8155-7D0143B2CA60
ms.openlocfilehash: dbc49a0ea9b4e4fa7880b6226331d447339b6575
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75737588"
---
# <a name="create-blazor-web-apps"></a>Blazor web uygulamaları oluşturma

Bu kılavuz, ilk Blazor web uygulamanızı oluşturmak için bir giriş sunar. Daha ayrıntılı rehberlik için, [ASP.NET Giriş Blazor'a](/aspnet/core/blazor/index)bakın.

Visual Studio for Mac (sürüm 8.4 ile başlayarak) Core Blazor Server uygulamaları nın geliştirilmesi ve yayınlanması için ASP.NET desteği içerir. Blazor, web geliştiricileri için aşağıdaki avantajları sunan .NET ile etkileşimli istemci tarafı web ui oluşturmak için bir çerçevedir:

* JavaScript yerine C# kodu yazın.
* .NET kitaplıklarının mevcut .NET ekosisteminden yararlanın.
* Uygulama mantığını sunucu ve istemci arasında paylaşın.
* Yararlanın . NET'in performansı, güvenilirliği ve güvenliği.
* PC, Linux ve macOS'ta Visual Studio ile üretken kalın.
* Kararlı, zengin özelliklere sahip ve kullanımı kolay ortak bir dil, çerçeve ve araç kümesi oluşturun.

## <a name="creating-a-new-blazor-project"></a>Yeni bir Blazor projesi oluşturma

1. Başlat **Penceresinde,** yeni bir proje oluşturmak için **Yeni'yi** seçin:

   ![Yeni seçim vurgulanan Mac Başlangıç Penceresi için Visual Studio](media/blazor-new-project.png)
1. Yeni **Proje** iletişim kutusunda **,.NET Core** > **App** > **Blazor Server App'ı** seçin ve **Sonraki'ni**seçin : ![Seçilen Blazor Server App şablonuyla yeni proje iletişim iniz için bir şablon seçin](media/blazor-project-template.png)

1. Hedef çerçeve olarak .NET Core 3.1'i seçin ve **ardından İleri'yi**seçin. 
   ![.NET Core 3.1 olarak seçilen Hedef Çerçevesi ile görüntülenen yeni Blazor Server App iletişim günlüğünüze yapınızı](media/blazor-select-target-framework.png)

1. Projeniz için bir ad seçin ve istenirse Git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.
   ![BProje Adı girerken görüntülenen yeni Blazor Server App iletişim günlüğünü yapılandırma](media/blazor-name-project.png)

   Mac için Visual Studio, Kod düzeni penceresinde projenizi açar.
1. Uygulamayı çalıştırmak için > **Hata Ayıklama olmadan** **Çalıştır'ı**seçin.

   Visual Studio [Kerkenez](/aspnet/core/fundamentals/servers/kestrel)başlar , `https://localhost:5001`için bir tarayıcı açar , ve Blazor web uygulaması görüntüler.

   ![Safari Blazor web uygulaması](media/blazor-new-app-in-edge.png)

## <a name="blazor-support-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Blazor desteği

Mac için Visual Studio (sürüm 8.4 ile başlayan) yeni Blazor sunucu projeleri oluşturmanıza yardımcı olacak yeni özellikler içerir. Ayrıca, Blazor projelerini oluşturma, çalıştırma ve hata ayıklama gibi beklediğiniz standart desteği de sağlar. 

Yukarıdaki iz üzerinde, Blazor Server App proje şablonunun yeni bir Blazor Server App projesi oluşturmanıza nasıl yardımcı olduğunu gördük. Blazor sunucu proje geliştirmeyi desteklemek için Visual Studio for Mac'teki bazı ek özelliklere bir göz atalım.

### <a name="editor-support-for-razor-files"></a>*.razor* files için editör desteği
Mac için Visual Studio, Blazor uygulamalarını oluştururken kullanacağınız dosyaların çoğu olan .razor dosyalarını düzenleme desteğini içerir. IDE'nin Windows ve Mac sürümü ,jilet dosyaları için aynı düzenleyiciyi paylaşır. Projede beyan edilen Razor bileşenlerinin tamamlanması da dahil olmak üzere .razor dosyalarınız için tam renklendirme ve tamamlama desteği görürsünüz.

![Blazor için Intellisense gösteren Mac editörü penceresi için Visual Studio](media/blazor-intellisense.png)

### <a name="publishing-blazor-applications-to-azure-app-service"></a>Blazor uygulamalarını Azure Uygulama Hizmetinde Yayımlama
Blazor uygulamalarını doğrudan Azure Uygulama Hizmeti'nde de yayınlayabilirsiniz. Blazor uygulamanızı Azure'da çalıştıracak bir Azure hesabınız yoksa, [12](https://azure.microsoft.com/free) aylık ücretsiz popüler hizmetler, 200 ABD doları ücretsiz Azure kredisi ve 25'in üzerinde her zaman ücretsiz hizmet de içeren ücretsiz bir hesabınız alabilirsiniz.

![Azure yayımlama deneyimini gösteren Mac için Visual Studio](media/blazor-azure-publish.png)

## <a name="project-anatomy"></a>Proje anatomisi

Blazor web uygulamaları varsayılan olarak birkaç dizin ve dosya içerir. Başlarken, bilmeniz gereken başlıca başlıca kişiler şunlardır:

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör, *.razor* dosya uzantısı kullanan bir projenin web sayfalarını içerir.

### <a name="shared-folder"></a>Paylaşılan klasör

Bu klasör, *.razor* uzantısını da kullanarak paylaşılan bileşenleri içerir. Bunun, uygulama genelinde ortak düzeni tanımlamak için kullanılan *MainLayout.razor'u*içerdiğini görürsünüz. Ayrıca tüm sayfalarda kullanılan paylaşılan *NavMenu.razor* bileşeni içerir. Yeniden kullanılabilir bileşenler oluşturuyorsanız, bunlar **Paylaşılan** klasöre gider.

### <a name="app-settings"></a>Uygulama ayarları

*appSettings.json* dosyası bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [ASP.NET kılavuzundaki Yapılandırma'ya](/aspnet/core/fundamentals/configuration/index)bakın.

### <a name="wwwroot-folder"></a>wwwroot klasörü

Bu klasör, HTML, JavaScript ve CSS dosyaları gibi statik dosyalar içerir. Daha fazla bilgi için [ASP.NET Core'daki Statik dosyalara](/aspnet/core/fundamentals/static-files)bakın.

### <a name="programcs"></a>Program.cs

Bu dosya, programın giriş noktasını içerir. Daha fazla bilgi için [Core Web HostASP.NET](/aspnet/core/fundamentals/host/web-host)bakın.

### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın çerezler için onay gerektiremesi gibi uygulama davranışını yapılandıran kodlar içerir. Daha fazla bilgi için ASP.NET [Core'da Uygulama başlangıç bilgisine](/aspnet/core/fundamentals/startup)bakın.

## <a name="summary"></a>Özet
Bu eğitimde, Mac için Visual Studio'da yeni bir Blazor Server Uygulamasının nasıl oluşturulabileceğinizi gördünuz ve Mac için Visual Studio'nun Blazor uygulamalarını oluşturmanıza yardımcı olmak için sunduğu bazı özellikleri öğrendiniz.

## <a name="see-also"></a>Ayrıca bkz.

Blazor web uygulamaları oluşturmak için daha kapsamlı bir kılavuz için, [Core BlazorASP.NET giriş](/aspnet/core/blazor/index)bakın.
