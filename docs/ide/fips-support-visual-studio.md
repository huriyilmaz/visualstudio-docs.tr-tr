---
title: FIPS Visual Studio desteği
titleSuffix: ''
description: Visual Studio, Azure ve .NET için Federal Bilgi İşleme Standart Yayın 140-2 onaylı Windows modunu nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/01/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9e0e1200d01a7cec8524dacb0232b3f2fed44f3a
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431542"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Visual Studio FIPS 140-2 onaylı çalışma modu için destek

sürüm [16.4'den](/visualstudio/releases/2019/release-notes-v16.4/)başlayarak, Visual Studio 2019, Windows, Azure ve .NET için Federal Bilgi İşleme Standardı (FIPS) Yayın 140-2 onaylı işlem modunu destekler. Ayrıca sürüm [16.5](/visualstudio/releases/2019/release-notes-v16.5)ile Visual Studio, uzak bir Linux sistemini hedef alan C++ uygulamaları geliştirirken FIPS 140-2 onaylı [işlem modunu destekliyor.](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)

Visual Studio için FIPS 140-2 onaylı işlem modunu yapılandırmak için [.NET Framework 4.8'i](https://dotnet.microsoft.com/download/dotnet-framework/net48) yükleyin ve grup ilkesi sistem **şifrelemesi: Şifreleme,** karma ve imzalama için FIPS uyumlu algoritmalar kullanın.

FIPS 140-2 onaylı işlem modu ve nasıl etkinleştireceği hakkında daha fazla bilgi için bkz. [FIPS 140-2 Doğrulama](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> iOS veya Android gibi Microsoft dışı platformlar için uygulama geliştirmek için kullanılan araçlar FIPS uyumlu algoritmalar kullanmayabiliyor. Yükle birlikte Visual Studio veya uzantılara dahil olan üçüncü taraf yazılımlar da FIPS uyumlu algoritmalar kullanmayabilirsiniz. Ayrıca, [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) geliştirme FIPS 140-2 onaylı çalışma modunu desteklemez.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ve diğer Microsoft ürün ve hizmetleri için FIPS 140-2 onaylı işlem modu hakkında daha fazla bilgi edinmek için aşağıdaki bağlantılara bakın:

- [Visual Studio: C++ ile FIPS uyumlu güvenli uzak Linux geliştirmesi ayarlama](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Şifreleme, karma ve imzalama için sistem şifrelemesi ve FIPS uyumlu algoritmalar kullanma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: FIPS uyumluluğu](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Ayrıca bkz.

[Uygulamaları güvenli hale getirme](securing-applications.md)