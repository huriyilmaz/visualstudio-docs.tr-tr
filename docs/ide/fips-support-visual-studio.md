---
title: FIPS 140-2 onaylı çalışma modu için Visual Studio desteği
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386451"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>FIPS 140-2 onaylı çalışma modu için Visual Studio desteği

Visual Studio 2019 [sürümü 16.4](/visualstudio/releases/2019/release-notes-v16.4/)ile başlayarak, Windows, Azure ve .NET için Federal Bilgi İşlem Standardı (FIPS) Yayını 140-2 onaylı çalışma modunu destekler. Ve, [sürüm 16.5](/visualstudio/releases/2019/release-notes-v16.5/)ile , Visual Studio şimdi fips 140-2 onaylı çalışma modunu destekler zaman [uzak bir Linux sistemi hedef C++ uygulamaları](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)geliştirmek .

Visual Studio için FIPS 140-2 onaylı çalışma modunu yapılandırmak için [.NET Framework 4.8'i yükleyin](https://dotnet.microsoft.com/download/dotnet-framework/net48) ve ardından Grup İlkesi ayarı, **Sistem şifrelemesi: Şifreleme, karma ve imzalama için FIPS uyumlu algoritmaları kullanın.**

FIPS 140-2 onaylı çalışma modu ve nasıl etkinleştirilir hakkında daha fazla bilgi için [FIPS 140-2 Doğrulama](/windows/security/threat-protection/fips-140-validation/)bölümüne bakın.

> [!NOTE]
> iOS veya Android gibi Microsoft'a uygun olmayan platformlar için uygulama geliştirmek için kullandığınız araçlar FIPS uyumlu algoritmalar kullanmayabilir. Visual Studio'ya veya yüklediğiniz uzantılara dahil olan üçüncü taraf yazılımları da FIPS uyumlu algoritmalar kullanmayabilir. Ayrıca, [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) çözümleri için geliştirme FIPS 140-2 onaylı çalışma modunu desteklemez.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ve diğer Microsoft ürün ve hizmetleri için FIPS 140-2 onaylı çalışma modu hakkında daha fazla bilgi edinmek için aşağıdaki bağlantılara bakın:

- [Visual Studio: C++ ile FIPS uyumlu güvenli uzak Linux geliştirmeyi ayarlama](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Sistem şifrelemesi ve şifreleme, karma ve imzalama için FIPS uyumlu algoritmalar kullanma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: FIPS uyumluluğu](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Ayrıca bkz.

[Uygulamaları güvenli hale getirme](securing-applications.md)