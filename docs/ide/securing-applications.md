---
title: Güvenlik
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87f06746901baaaf14f91032f8968a0d99fc20c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595455"
---
# <a name="secure-applications"></a>Uygulamaları güvenli hale getirme

Uygulama geliştirme sürecinizde, tasarımdan geliştirmeye kadar her yönüyle güvenliği göz önünde bulundurmalısınız. Visual Studio'u mümkün olduğunca güvenli bir şekilde çalıştırarak başlayın. [Bkz. Kullanıcı izinleri.](../ide/user-permissions-and-visual-studio.md)

Etkin bir şekilde güvenli uygulamalar geliştirmenize yardımcı olması için, geliştirmekte olduğunuz platformların güvenlik kavramları ve güvenlik özellikleri hakkında temel bilgiye sahip olmanız gerekir. Güvenli kodlama tekniklerini de anlamanız gerekir.

## <a name="code-for-security"></a>Güvenlik kodu

Güvenlik açıklarıyla sonuçlanan çoğu kodlama hatası, geliştiricilerin kullanıcı girişiyle çalışırken yanlış varsayımlarda bulunmaları veya geliştirdikleri platformu tam olarak anlamadıkları için oluşur.

- [Güvenli kodlama yönergeleri,](/dotnet/standard/security/secure-coding-guidelines) .NET kodunun güvenlik sistemiyle çalışacak şekilde tasarlanabileceği farklı yolları açıklar.
- [C++ için güvenlik en iyi uygulamaları, C++](/cpp/top/security-best-practices-for-cpp) geliştiricileri için güvenlik araçları ve uygulamaları hakkında bilgi içerir.

## <a name="build-for-security"></a>Güvenlik için yapı

Güvenlik de yapı sürecinde önemli bir husustur. Birkaç ek adım, dağıtılan bir uygulamanın güvenliğini artırabilir ve yetkisiz ters mühendislik, sahteciliği veya diğer saldırıları önlemeye yardımcı olabilir:

- [Dotfuscator](dotfuscator/index.md) ücretsizdir ve .NET derlemelerinin yanlış mühendislik ve yetkisiz hata ayıklama gibi yetkisiz kullanımdan korunmasına yardımcı olur.
- [Güçlü ad imzalama,](managing-assembly-and-manifest-signing.md) yazılım bileşenlerini benzersiz olarak tanımlamak ve ad sızdırmasını önlemek için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET içinde güvenlik](/dotnet/standard/security/index)
- [Azure güvenliği](/azure/security/)
- [Windows 10 Mobil güvenlik kılavuzu](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova platformu güvenlik özellikleri](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET Çekirdek güvenlik](/aspnet/core/security/?view=aspnetcore-2.1)
- [Windows Forms güvenlik](/dotnet/framework/winforms/windows-forms-security)
