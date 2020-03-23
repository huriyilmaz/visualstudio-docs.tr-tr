---
title: launchSettings.json desteği
description: Bu belge Mac için Visual Studio launchSettings.json için destek kapsar
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715940"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Core projeleri ASP.NET geliştirirken, launchSettings.json dosyasının içeriğini özelleştirerek geliştirme senaryolarında projenizin nasıl başlatılması gerektiğini yapılandırabilirsiniz. Mac için Visual Studio'da, proje seçenekleri kullanıcı arabirimi'ni kullanarak veya doğrudan düzenleyerek bu dosyayı güncelleştirebilirsiniz. Bu dosya, Windows'ta Visual Studio'yu çalıştırırken veya komut satırından ' `dotnet`da kullanabileceğiniz yapılandırma dosyasıdır. Bu dosya, Projenizde Özellikler klasörü altında depolanır.

Daha ayrıntılı bilgi için bkz: [ASP.NET Core'da birden fazla ortam kullanın.](/aspnet/core/fundamentals/environments) Bu makalede, bu dosyanın Mac için Visual Studio'da nasıl güncelleştirilenini ele alacağız.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mac için Visual Studio'yu kullanarak başlangıç yapılandırmasını güncelleştirin

Mac için Visual Studio'da launchSettings.json dosyasını doğrudan düzenleyebilir veya düzenlemek için proje seçeneklerini kullanabilirsiniz. Proje seçeneklerine ulaşmak için projenize sağ tıklayın ve **Seçenekler'i**seçin.

!["Seçenekler" seçili proje kısayol menüsü](media/vsmac-ctx-proj-options.png)

 > **Yapılandırmaları** **Çalıştır** > **Varsayılan'ı**seçin.

![Proje seçeneklerinde "Çalıştır", "Yapılandırmalar" ve "Varsayılan"](media/vsmac-run-config-default.png)

Öncelikle, burada iki şeyi yapılandıracaksınız:

 - Ortam değişkenleri
 - Proje için uygulama URL'si

## <a name="configure-environment-variables"></a>Ortam değişkenlerini yapılandırma

Çevre değişkenleri için değerleri belirtmek için ızgarayı kullanabilirsiniz. Bu ortam değişkenleri, Mac için Visual Studio'da uygulamanızı başlattığınızda ayarlanır. Core uygulamaları ASP.NET geliştirirken, özel `ASPNETCORE_ENVIRONMENT` ortam değişkeninin farkında olmalısınız. Daha fazla bilgi için [ASP.NET](/aspnet/core/fundamentals/environments)bkz.


## <a name="configure-the-start-url"></a>Başlangıç URL'sini yapılandırma

Uygulamanın başlatılacak URL'yi yapılandırmak için **ASP.NET Core** sekmesine gidin.

![Proje seçeneklerinde uygulama URL'si](media/vsmac-run-config-default-aspnetcore.png)

Burada, uygulamanın başlatıldığında dinleyeceğiniz URL'yi belirtebilirsiniz.