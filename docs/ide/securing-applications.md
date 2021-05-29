---
title: Güvenlik
description: Güvenli uygulamalar geliştirme konusunda etkili bir şekilde yardımcı olacak bazı güvenlik kavramları ve güvenlik özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3dcd034a76fbc371c95a2bbf386687830e3b63d
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687660"
---
# <a name="secure-applications"></a>Uygulamaları güvenli hale getirme

Uygulama geliştirme sürecinizde, tasarımdan geliştirmeye kadar her yönüyle güvenliği göz önünde bulundurmalısınız. Başlangıç olarak Visual Studio güvenli bir şekilde çalıştırarak. Bkz. [Kullanıcı izinleri.](../ide/user-permissions-and-visual-studio.md)

Etkin bir şekilde güvenli uygulamalar geliştirmenize yardımcı olması için, geliştirmekte olduğunuz platformların güvenlik kavramları ve güvenlik özellikleri hakkında temel bilgiye sahip olmanız gerekir. Güvenli kodlama tekniklerini de anlamanız gerekir.

## <a name="code-for-security"></a>Güvenlik kodu

Güvenlik açıklarına neden olan kodlama hatalarının çoğu, geliştiricilerin kullanıcı girişiyle çalışırken yanlış varsayımlarda bulunarak veya geliştirmekte olduğu platformu tam olarak anlamamalarından dolayı oluşur.

- [Güvenli kodlama yönergeleri,](/dotnet/standard/security/secure-coding-guidelines) .NET kodunun güvenlik sistemiyle çalışmak için farklı yollarını açıklar.
- [C++ için en iyi güvenlik uygulamaları, C++](/cpp/top/security-best-practices-for-cpp) geliştiricilerine yönelik güvenlik araçları ve uygulamaları hakkında bilgi içerir.

## <a name="build-for-security"></a>Güvenlik için derleme

Derleme sürecinde güvenlik de önemli bir konudur. Birkaç ek adım, dağıtılan bir uygulamanın güvenliğini geliştirebilir ve yetkisiz tersine mühendislik, spolama veya diğer saldırıları önlemeye yardımcı olabilir:

- [Dotfuscator](dotfuscator/index.md) ücretsizdir ve .NET derlemelerinin tersine mühendislik ve yetkisiz hata ayıklama gibi yetkisiz kullanıma karşı korunmasına yardımcı olur.
- [Güçlü ad imzalama,](managing-assembly-and-manifest-signing.md) yazılım bileşenlerini benzersiz olarak tanımlamak ve ad kimliklerini engellemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET içinde güvenlik](/dotnet/standard/security/index)
- [Azure güvenliği](/azure/security/)
- [Windows 10 Mobile güvenlik kılavuzu](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova platformu güvenlik özellikleri](/previous-versions/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017&preserve-view=true)
- [ASP.NET Core güvenliği](/aspnet/core/security/?view=aspnetcore-2.1&preserve-view=true)
- [Windows Forms güvenlik](/dotnet/framework/winforms/windows-forms-security)
