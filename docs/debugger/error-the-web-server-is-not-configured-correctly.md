---
description: Sorunu çözmek için buradaki adımları ayrıntılandırdıktan sonra ve hata ayıklamayı yeniden denemeden önce, IIS 'yi de sıfırlamanız gerekebilir.
title: Web sunucusu doğru yapılandırılmamış | Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 288210ac250be0dd92ec409a4b1d45075c0baf2e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134070"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Hata: Web sunucusu doğru yapılandırılmamış

Sorunu çözmek için buradaki adımları ayrıntılandırdıktan sonra ve hata ayıklamayı yeniden denemeden önce, IIS 'yi de sıfırlamanız gerekebilir. Bunu, bir yönetici komut istemi açıp yazarak yapabilirsiniz `iisreset` .

Bu sorunu çözmek için şu adımları uygulayın:

1. Sunucuda barındırılan Web uygulaması bir yayın derlemesi olarak yapılandırılmışsa, hata ayıklama derlemesi olarak yeniden yayımlayın ve web.config dosyasının `debug=true` derleme öğesinde içerdiğini doğrulayın. IIS 'i sıfırlayın ve yeniden deneyin.

    Örneğin, bir yayın derlemesi için bir yayımlama profili kullanıyorsanız, bunu hata ayıklama ve yeniden yayımlama için değiştirin. Aksi takdirde, hata ayıklama özniteliği yayımladığınızda olarak ayarlanır `false` .

2. ISS Fiziksel yolun doğru olduğundan emin olun. ııs 'de, bu ayarı **temel Ayarlar > fiziksel yol** (veya daha eski ııs sürümlerinde **gelişmiş Ayarlar** ) içinde bulabilirsiniz.

    Web uygulaması farklı bir makineye kopyalanmışsa, el ile yeniden adlandırılırsa veya taşındığında fiziksel yol yanlış olabilir. IIS 'i sıfırlayın ve yeniden deneyin.

3. Visual Studio yerel olarak hata ayıklaması yapıyorsanız, özelliklerde doğru sunucunun seçildiğini doğrulayın. (Proje türüne bağlı olarak **hata ayıklama >** **Web > sunucuları veya özellikleri > Özellikler** açın. Web Forms bir proje için, özellik sayfaları ' nı açın **> başlat seçenekler > sunucu**).

    IIS gibi bir dış (özel) sunucu kullanıyorsanız, URL 'nin doğru olması gerekir. aksi takdirde IIS Express seçin ve yeniden deneyin.

4. ISS sunucuda doğru ASP.NET sürümünün yüklü olduğundan emin olun.

    ııs ve Visual Studio projenizde ASP.NET eşleşmeyen sürümleri bu soruna neden olabilir. Çerçeve sürümünü web.config ayarlamanız gerekebilir. ııs 'de ASP.NET yüklemek için [Web platformu yükleyicisi (webpı)](https://www.microsoft.com/web/downloads/platform.aspx)kullanın. ayrıca bkz. [ııs 8,0 ASP.NET 3,5 ve ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) veya ASP.NET Core, [Windows üzerinde ııs ile barındırma](https://docs.asp.net/en/latest/publishing/iis.html).

4. `maxConnection`IIS 'deki sınır çok düşükse ve çok fazla bağlantınız varsa, [bağlantı sınırını artırmanız](/iis/configuration/system.applicationhost/sites/sitedefaults/limits)gerekebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
