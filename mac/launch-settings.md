---
title: launchSettings.json desteği
description: bu belge Mac için Visual Studio 'de launchsettings. json desteğini içerir
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 09/18/2019
ms.topic: how-to
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: 2cdb8a6f28b10dc7c5a899d57c2bd9c084b10b32
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806423"
---
# <a name="launchsettingsjson"></a>launchSettings.json

ASP.NET Core projeleri geliştirirken, launchsettings. json dosyasının içeriğini özelleştirerek geliştirme senaryolarında projenizin nasıl başlatılacağını yapılandırabilirsiniz. Mac için Visual Studio, bu dosyayı proje seçenekleri kullanıcı arabirimini kullanarak veya doğrudan düzenleyerek güncelleştirebilirsiniz. bu dosya, Windows Visual Studio ya da ile komut satırından çalıştırırken kullanabileceğiniz yapılandırma dosyasıdır `dotnet` . Bu dosya projenizde Özellikler klasörü altında depolanır.

Daha ayrıntılı bilgi için bkz. [ASP.NET Core birden çok ortam kullanma](/aspnet/core/fundamentals/environments). bu makalede, Mac için Visual Studio ' de bu dosyayı nasıl güncelleştireceğiz.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak başlangıç yapılandırmasını güncelleştirme

Mac için Visual Studio ' de launchsettings. json dosyasını doğrudan düzenleyebilir veya proje seçeneklerini kullanarak düzenleyebilirsiniz. Proje seçeneklerine ulaşmak için projenize sağ tıklayın ve **Seçenekler**' i seçin.

!["seçenekler" seçiliyken kısayol menüsü Project](media/vsmac-ctx-proj-options.png)

Varsayılan **çalıştırma**  >  **yapılandırması**' nı seçin  >  .

![Proje seçeneklerinde "Çalıştır," "Configurations" ve "default"](media/vsmac-run-config-default.png)

Öncelikle, burada iki şeyi yapılandıracaksınız:

- Ortam değişkenleri
- Projenin uygulama URL 'SI

## <a name="configure-environment-variables"></a>Ortam değişkenlerini yapılandırma

Ortam değişkenlerinin değerlerini belirtmek için kılavuzunu kullanabilirsiniz. bu ortam değişkenleri, uygulamanızı Mac için Visual Studio ' de başlattığınızda ayarlanır. ASP.NET Core uygulamalar geliştirirken, özel `ASPNETCORE_ENVIRONMENT` ortam değişkenini bilmelisiniz. Daha fazla bilgi için bkz. [ASP.NET Core birden çok ortam kullanma](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Başlangıç URL 'sini yapılandırın

uygulamanın başlatıldığı URL 'yi yapılandırmak için **ASP.NET Core** sekmesine gidin.

![Proje seçeneklerindeki uygulama URL 'SI](media/vsmac-run-config-default-aspnetcore.png)

Burada, uygulamanın başlatıldığında dinleyeceği URL 'YI belirtebilirsiniz.
