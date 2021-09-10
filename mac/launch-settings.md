---
title: launchSettings.json desteği
description: Bu belge, launchSettings.js'de Mac için Visual Studio
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: df702b5d49e5204e65675c1c57d222e490a33824
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964810"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Bir ASP.NET Core geliştirme aşamasında, dosyada yer alan uygulamanın içeriğini özelleştirerek projenizin geliştirme senaryolarında nasıl launchSettings.jsyapılandırabilirsiniz. Bu Mac için Visual Studio, proje seçenekleri kullanıcı arabirimini kullanarak veya doğrudan düzenleyerek bu dosyayı güncelleştirebilirsiniz. Bu dosya, dosya üzerinde veya aracılığıyla komut Visual Studio Windows çalıştırarak kullanabileceğiniz yapılandırma `dotnet` dosyasıdır. Bu dosya, Projenizin Özellikler klasörü altında depolanır.

Daha ayrıntılı bilgi için [bkz. Birden çok ortam kullanma ASP.NET Core.](/aspnet/core/fundamentals/environments) Bu makalede, bu dosyanın nasıl güncelleştirilmektedir? makalesinde Mac için Visual Studio.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak başlangıç yapılandırmasını güncelleştirme

Dosyada yer alan launchSettings.jsdoğrudan düzenleyebilir Mac için Visual Studio proje seçeneklerini kullanarak düzenleyebilirsiniz. Proje seçeneklerine almak için projenize sağ tıklayın ve Seçenekler'i **seçin.**

![Project "Seçenekler" seçeneğinin seçili olduğu bir kısayol menüsü](media/vsmac-ctx-proj-options.png)

Yapılandırmaları **Çalıştır**  >  **Varsayılan'ı**  >  **seçin.**

![Proje seçeneklerinde "Çalıştır", "Yapılandırmalar" ve "Varsayılan"](media/vsmac-run-config-default.png)

Öncelikle burada iki şeyi yapılandırmış oluruz:

- Ortam değişkenleri
- Proje için uygulama URL'si

## <a name="configure-environment-variables"></a>Ortam değişkenlerini yapılandırma

Ortam değişkenlerinin değerlerini belirtmek için kılavuzu kullanabilirsiniz. Bu ortam değişkenleri, uygulamanıza yeni bir başlangıç Mac için Visual Studio. Uygulama geliştirme ASP.NET Core, özel ortam değişkeninin farkında `ASPNETCORE_ENVIRONMENT` olmak gerekir. Daha fazla bilgi edinmek için [bkz. Birden çok ortam kullanma ASP.NET Core.](/aspnet/core/fundamentals/environments)


## <a name="configure-the-start-url"></a>Başlangıç URL'sini yapılandırma

Uygulamanın başlatılamayacak URL'sini yapılandırmak için uygulamanın **ASP.NET Core** gidin.

![Proje seçeneklerinde uygulama URL'si](media/vsmac-run-config-default-aspnetcore.png)

Burada, uygulamanın başlatılana kadar dinleyecekleri URL'yi belirtebilirsiniz.
