---
title: Razor web uygulamaları oluşturma
description: Mac için Visual Studio'daki ASP.NET Core uygulamalarında Razor desteği hakkında bilgi sağlar.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715882"
---
# <a name="create-razor-web-apps"></a>Razor web uygulamaları oluşturma

Bu kılavuz, ilk Razor web uygulamanızı oluşturmaya giriş sunar. Daha ayrıntılı kılavuz için, [ASP.NET Core'daki Razor Sayfalarına Giriş'e](/aspnet/core/razor-pages/index)bakın.

Mac için Visual Studio, IntelliSense ve *.cshtml* dosyalarında sözdizimi vurgulama dahil olmak üzere Razor düzenlemesi için destek sağlar. Visual Studio 2019'da Mac 8.3+ için yeni bir intelliSense'in bir Razor dosyası içinde bağlam bilgisine sahip olması, böylece bir belgede şu anda düzenlemekte olduğunuz dile uyan IntelliSense'i alma olanağıdır.

![Mac için Visual Studio'da jilet düzenleme](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Yeni bir Razor projesi oluşturma

1. Karşılama ekranında, yeni bir proje oluşturmak için **Yeni'yi** seçin:

   ![Mac için Visual Studio yeni proje](media/razor-new.png)
1. Yeni **Proje** iletişim kutusunda **,.NET Core** > **App** > **Web Application** adresine gidin ve **Sonraki'ni**seçin:

   ![Jilet proje şablonu](media/razor-new-project1.png)
1. .NET Core hedef çerçevenizi seçin (sürüm 2.2 veya sonraki sürüm öneririz) ve sonra **İleri'yi**seçin. Projeniz için bir ad seçin ve gerekirse Git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.

   ![Jilet proje adı](media/razor-new-project2.png)

   Mac için Visual Studio, Kod düzeni penceresinde projenizi açar.
1. **Komut+Seçenek+F5**kullanarak projeyi hata ayıklamadan çalıştırın.

   Visual Studio [Kerkenez](/aspnet/core/fundamentals/servers/kestrel)başlar , `https://localhost:5001`için bir tarayıcı açar , ve ilk Razor web uygulaması görüntüler.

   ![Safari'de Jilet web uygulaması](media/razor-webapp.png)

## <a name="project-anatomy"></a>Proje anatomisi

Razor web uygulamaları aşağıdaki bileşenleri içerir.

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör, her biri için kod arkası ile birlikte bir projenin web sayfalarını içerir:
   - HTML biçimlendirmesi ve Razor sözdizimi için * \*bir .cshtml* dosyası.
   - Sayfa olaylarını işlemek için C# kod arkanız için * \*bir .cshtml.cs* dosyası.

Destekleyen dosyaların alt altı yla başlayan adları vardır. Örneğin, _Layout.cshtml dosyası tüm sayfalarda yaygın olan UI öğelerini yapılandırır. Bu dosya, sayfanın üst kısmındaki gezinti menüsünü ve alttaki telif hakkı bildirimini ayarlar. Daha fazla bilgi için ASP.NET [Core'daki Düzen'e](/aspnet/core/mvc/views/layout)bakın.

### <a name="launch-settings"></a>Başlatma ayarları

*LaunchSettings.json* dosyası IIS ayarlarını, uygulama URL'sini ve diğer ilgili ayarları içerir.

### <a name="app-settings"></a>Uygulama ayarları

*appSettings.json* dosyası bağlantı dizeleri gibi yapılandırma verilerini içerir.

Yapılandırma hakkında daha fazla bilgi için [ASP.NET kılavuzundaki Yapılandırma'ya](/aspnet/core/fundamentals/configuration/index)bakın.

### <a name="wwwroot-folder"></a>wwwroot klasörü

Bu klasör, HTML, JavaScript ve CSS dosyaları gibi statik dosyalar içerir. Daha fazla bilgi için [ASP.NET Core'daki Statik dosyalara](/aspnet/core/fundamentals/static-files)bakın.

### <a name="programcs"></a>Program.cs

Bu dosya, programın giriş noktasını içerir. Daha fazla bilgi için [Core Web HostASP.NET](/aspnet/core/fundamentals/host/web-host)bakın.

### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın çerezler için onay gerektiremesi gibi uygulama davranışını yapılandıran kodlar içerir. Daha fazla bilgi için ASP.NET [Core'da Uygulama başlangıç bilgisine](/aspnet/core/fundamentals/startup)bakın.

## <a name="see-also"></a>Ayrıca bkz.

Razor web uygulamaları oluşturmak için daha kapsamlı bir kılavuz için, [ASP.NET Core'da Razor Sayfalarına Giriş'e](/aspnet/core/razor-pages/index)bakın.
