---
title: Razor web uygulamaları oluşturma
description: Bir uygulamanın içinde yer alan ASP.NET Core Razor desteği hakkında Mac için Visual Studio.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 3a99b02009b940f6d51405ff81901763bce92816
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805526"
---
# <a name="create-razor-web-apps"></a>Razor web uygulamaları oluşturma

Bu kılavuz, ilk Razor web uygulamanızı oluşturmaya giriş sunar. Daha ayrıntılı rehberlik için [bkz. ASP.NET Core'de Razor Pages' ASP.NET Core.](/aspnet/core/razor-pages/index)

Mac için Visual Studio. *.cshtml* dosyalarında IntelliSense ve söz dizimi vurgulama da dahil olmak üzere Razor düzenleme desteği sağlar. Mac için Visual Studio 2019 8.3+ sürümü, bir Razor dosyasında bağlam algısı olan IntelliSense'e sahip olmaktır. Böylece, bir belge içinde düzenlemekte olduğu dille eşleşen IntelliSense'i alırsınız.

![Mac için Visual Studio'da Razor düzenleme](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Yeni Razor projesi oluşturma

1. Hoş geldiniz ekranında **Yeni'yi seçerek** yeni bir proje oluşturun:

   ![Mac için Visual Studio proje](media/razor-new.png)
1. Yeni Uygulama **Project** iletişim kutusunda **.NET Core** Uygulaması Web  >    >  **Uygulaması'ne** gidin ve Sonraki'yi **seçin:**

   ![Razor proje şablonu](media/razor-new-project1.png)
1. .NET Core hedef çerçevenizi seçin (sürüm 2.2 veya sonraki bir sürümü öneririz) ve ardından Sonraki'yi **seçin.** Projeniz için bir ad seçin ve gerekirse Git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.

   ![Razor proje adı](media/razor-new-project2.png)

   Mac için Visual Studio kod düzeni penceresinde projenizi açar.
1. **Command+Option+F5 komutunu kullanarak projeyi hata ayıklamadan çalıştırın.**

   Visual Studio [Kestrel'i](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı `https://localhost:5001` açar ve ilk Razor web uygulamanızı görüntüler.

   ![Safari'de Razor web uygulaması](media/razor-webapp.png)

## <a name="project-anatomy"></a>Proje anatomisi

Razor web uygulamaları aşağıdaki bileşenleri içerir.

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör, bir projenin web sayfalarını ve her biri için arkadeki kodu içerir:
- HTML *\* işaretlemesi ve biçimlendirmesi için bir .cshtml* Razor söz dizimi.
- Sayfa olaylarını işlemeye yardımcı olmak için C# arka arkasındaki kodunuz için bir *\* .cshtml.cs* dosyası.

Destekleyen dosyaların adları alt çizgiyle başlar. Örneğin, *\_ Layout.cshtml dosyası* tüm sayfalarda ortak olan kullanıcı arabirimi öğelerini yapılandırır. Bu dosya, sayfanın üst kısmında gezinti menüsünü ve alttaki telif hakkı bildirimini ayarlar. Daha fazla bilgi için [bkz. ASP.NET Core.](/aspnet/core/mvc/views/layout)

### <a name="launch-settings"></a>Başlatma ayarları

*launchSettings.json dosyası* IIS ayarlarını, uygulama URL'sini ve diğer ilgili ayarları içerir.

### <a name="app-settings"></a>Uygulama ayarları

*appSettings.json dosyası* bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [bkz. yapılandırma ASP.NET.](/aspnet/core/fundamentals/configuration/index)

### <a name="wwwroot-folder"></a>wwwroot klasörü

Bu klasör HTML, JavaScript ve CSS dosyaları gibi statik dosyaları içerir. Daha fazla bilgi için [bkz. ASP.NET Core.](/aspnet/core/fundamentals/static-files)

### <a name="programcs"></a>Program.cs

Bu dosya, programın giriş noktasını içerir. Daha fazla bilgi için [bkz. ASP.NET Core Web Ana Bilgisayarı.](/aspnet/core/fundamentals/host/web-host)

### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın tanımlama bilgileri için onay isteyip istemesi gibi uygulama davranışını yapılandıran kodu içerir. Daha fazla bilgi için [bkz. ASP.NET Core.](/aspnet/core/fundamentals/startup)

## <a name="see-also"></a>Ayrıca bkz.

Razor web uygulamaları oluşturma hakkında daha kapsamlı bir kılavuz için [bkz. Razor Pages'ASP.NET Core.](/aspnet/core/razor-pages/index)
