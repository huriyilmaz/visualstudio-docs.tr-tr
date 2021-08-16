---
title: Razor Web uygulamaları oluşturma
description: Mac için Visual Studio ASP.NET Core uygulamalarda Razor desteği hakkında bilgi sağlar.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 96be41d910fa70fd60199c188b785b8271f36424eb131017b6037559e6256a78
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381809"
---
# <a name="create-razor-web-apps"></a>Razor Web uygulamaları oluşturma

Bu kılavuzda, ilk Razor Web uygulamanızı oluşturmaya yönelik bir giriş sunulmaktadır. Daha ayrıntılı rehberlik için bkz. [ASP.NET Core Razor Pages giriş](/aspnet/core/razor-pages/index).

Mac için Visual Studio, ıntellisense ve *. cshtml* dosyalarında sözdizimi vurgulama dahil olmak üzere Razor düzenlemesi için destek sağlar. Mac 8.3 için Visual Studio 2019 ' deki yenilikler + bir Razor dosyası içinde içerik algılayan ıntellisense, bu sayede bir belge içinde düzenlemekte olduğunuz dille eşleşen ıntellisense elde edersiniz.

![Mac için Visual Studio 'de Razor düzenlemesi](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Yeni bir Razor projesi oluşturma

1. Yeni bir proje oluşturmak için hoş geldiniz ekranında **Yeni** ' yi seçin:

   ![yeni Mac için Visual Studio proje](media/razor-new.png)
1. **yeni Project** iletişim kutusunda **.net Core**  >  **uygulama**  >  **Web uygulaması** ' na gidin ve **ileri**' yi seçin:

   ![Razor proje şablonu](media/razor-new-project1.png)
1. .NET Core hedef çatısını seçin (sürüm 2,2 veya üzeri önerilir) ve ardından **İleri**' yi seçin. Projeniz için bir ad seçin ve gerekirse git desteği ekleyin. Projeyi oluşturmak için **Oluştur**'u seçin.

   ![Razor proje adı](media/razor-new-project2.png)

   Mac için Visual Studio, projenizi kod düzeni penceresinde açar.
1. **Komut + Option + F5** kullanarak projeyi hata ayıklama olmadan çalıştırın.

   Visual Studio, [Kestrel](/aspnet/core/fundamentals/servers/kestrel)başlatır, için bir tarayıcı açar `https://localhost:5001` ve ilk Razor web uygulamanızı görüntüler.

   ![Safari 'de Razor Web uygulaması](media/razor-webapp.png)

## <a name="project-anatomy"></a>Proje anatomisi

Razor Web uygulamaları aşağıdaki bileşenleri içerir.

### <a name="pages-folder"></a>Sayfalar klasörü

Bu klasör bir projenin Web sayfalarını, her biri için arka plan kodu içerir:
- HTML biçimlendirme ve Razor söz dizimi için bir *\* . cshtml* dosyası.
- Sayfa olaylarını işlemek için C# arka plan kodu için bir *\* . cshtml. cs* dosyası.

Destekleyici dosyalar bir alt çizgiyle başlayan adlara sahiptir. Örneğin, *\_ Layout. cshtml* dosyası tüm sayfalarda ortak kullanıcı arabirimi öğelerini yapılandırır. Bu dosya, sayfanın üst kısmındaki gezinti menüsünü ve en alttaki telif hakkı bildirimini ayarlar. Daha fazla bilgi için [ASP.NET Core düzen](/aspnet/core/mvc/views/layout)bölümüne bakın.

### <a name="launch-settings"></a>Başlatma ayarları

Dosyadaki *launchSettings.js* IIS ayarlarını, uygulama URL 'sini ve diğer ilgili ayarları içerir.

### <a name="app-settings"></a>Uygulama ayarları

Dosyadaki *appSettings.js* , bağlantı dizeleri gibi yapılandırma verilerini içerir.

yapılandırma hakkında daha fazla bilgi için [ASP.NET kılavuzundaki yapılandırma](/aspnet/core/fundamentals/configuration/index)bölümüne bakın.

### <a name="wwwroot-folder"></a>Wwwroot klasörü

Bu klasör HTML, JavaScript ve CSS dosyaları gibi statik dosyaları içerir. Daha fazla bilgi için [ASP.NET Core Içindeki statik dosyalar](/aspnet/core/fundamentals/static-files)bölümüne bakın.

### <a name="programcs"></a>Program.cs

Bu dosya, program için giriş noktasını içerir. daha fazla bilgi için bkz. [ASP.NET Core Web Host](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Bu dosya, uygulamanın tanımlama bilgileri için izin gerektirip gerektirmediğini belirtir gibi uygulama davranışını yapılandıran kodu içerir. Daha fazla bilgi için [ASP.NET Core uygulamasında uygulama başlatma](/aspnet/core/fundamentals/startup)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

Razor Web uygulamaları oluşturmaya yönelik daha kapsamlı bir kılavuz için bkz. [ASP.NET Core Razor Pages giriş](/aspnet/core/razor-pages/index).
