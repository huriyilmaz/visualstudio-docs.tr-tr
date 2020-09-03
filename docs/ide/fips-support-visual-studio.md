---
title: FIPS 140-2 tarafından onaylanan işlem modu için Visual Studio desteği
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d06204fd1ef6ee2deb5eadc514af1ede8ae9bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84180499"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>FIPS 140-2 tarafından onaylanan işlem modu için Visual Studio desteği

[Sürüm 16,4](/visualstudio/releases/2019/release-notes-v16.4/)' den başlayarak, Visual Studio 2019, Windows, Azure ve .net Için Federal bilgi işleme standardı (FIPS) yayını 140-2 onaylı işlem modunu destekler. Visual Studio, [sürüm 16,5](/visualstudio/releases/2019/release-notes-archive-v16.5)' de, [uzak bir Linux sistemini hedefleyen C++ UYGULAMALARı](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)geliştirirken artık FIPS 140-2 tarafından onaylanan işlem modunu desteklemektedir.

Visual Studio için FIPS 140-2 onaylı modunu yapılandırmak için [.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) ' yi yükleyip Grup İlkesi ayarını etkinleştirin ve **Sistem şifrelemesi: şifreleme, karma ve imzalama için FIPS Ile uyumlu algoritmalar kullanın**.

FIPS 140-2 onaylı işlem modu ve bunun nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [fıps 140-2 doğrulaması](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> İOS veya Android gibi Microsoft dışı platformlar için uygulama geliştirmek üzere kullandığınız araçlar FIPS ile uyumlu algoritmalar kullanmayabilir. Visual Studio 'da bulunan üçüncü taraf yazılımlar veya yüklediğiniz uzantılar FIPS uyumlu algoritmalar de kullanmayabilir. Ve, [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) çözümleri için GELIŞTIRME, FIPS 140-2 onaylı işlem modunu desteklemez.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio için FIPS 140-2 onaylı işlem modu ve diğer Microsoft ürünleri ve hizmetleri hakkında daha fazla bilgi edinmek için aşağıdaki bağlantılara bakın:

- [Visual Studio: C++ ile FIPS uyumlu güvenli uzak Linux geliştirme ayarlama](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Sistem şifrelemesi ve şifreleme, karma ve imzalama için FIPS ile uyumlu algoritmalar kullanma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: FIPS uyumluluğu](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Ayrıca bkz.

[Uygulamaları güvenli hale getirme](securing-applications.md)
