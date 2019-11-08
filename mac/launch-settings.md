---
title: launchSettings. JSON desteği
description: Bu belge Mac için Visual Studio 'de launchSettings. JSON desteğini içerir
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715940"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

ASP.NET Core projeleri geliştirirken, launchSettings. json dosyasının içeriğini özelleştirerek geliştirme senaryolarında projenizin nasıl başlatılacağını yapılandırabilirsiniz. Mac için Visual Studio, bu dosyayı proje seçenekleri Kullanıcı arabirimini kullanarak veya doğrudan düzenleyerek güncelleştirebilirsiniz. Bu dosya, Visual Studio 'Yu Windows üzerinde veya `dotnet`ile komut satırından çalıştırırken kullanabileceğiniz yapılandırma dosyası ile aynıdır. Bu dosya projenizde Özellikler klasörü altında depolanır.

Daha ayrıntılı bilgi için bkz. [ASP.NET Core birden çok ortam kullanma](/aspnet/core/fundamentals/environments). Bu makalede, Mac için Visual Studio ' de bu dosyayı nasıl güncelleştireceğiz.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak başlangıç yapılandırmasını güncelleştirme

Mac için Visual Studio ' de launchSettings. json dosyasını doğrudan düzenleyebilir veya proje seçeneklerini kullanarak düzenleyebilirsiniz. Proje seçeneklerine ulaşmak için projenize sağ tıklayın ve **Seçenekler**' i seçin.

!["Seçenekler" seçiliyken proje kısayol menüsü](media/vsmac-ctx-proj-options.png)

**Varsayılan** >  > **yapılandırmayı** **Çalıştır** ' ı seçin.

![Proje seçeneklerinde "Çalıştır," "Configurations" ve "default"](media/vsmac-run-config-default.png)

Öncelikle, burada iki şeyi yapılandıracaksınız:

 - Ortam değişkenleri
 - Projenin uygulama URL 'SI

## <a name="configure-environment-variables"></a>Ortam değişkenlerini yapılandırma

Ortam değişkenlerinin değerlerini belirtmek için kılavuzunu kullanabilirsiniz. Bu ortam değişkenleri, uygulamanızı Mac için Visual Studio ' de başlattığınızda ayarlanır. ASP.NET Core uygulamalar geliştirirken, özel `ASPNETCORE_ENVIRONMENT` ortam değişkenini bilmelisiniz. Daha fazla bilgi için bkz. [ASP.NET Core birden çok ortam kullanma](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Başlangıç URL 'sini yapılandırın

Uygulamanın başlatıldığı URL 'YI yapılandırmak için **ASP.NET Core** sekmesine gidin.

![Proje seçeneklerindeki uygulama URL 'SI](media/vsmac-run-config-default-aspnetcore.png)

Burada, uygulamanın başlatıldığında dinleyeceği URL 'YI belirtebilirsiniz.