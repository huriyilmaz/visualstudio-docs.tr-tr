---
title: VSPackage'larda Güvenlik için En İyi | Microsoft Docs
description: Bir uygulamanın temel güvenlik ve dağıtım birimi olan VSPackage'da güvenlik için en iyi Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a49279c9a08c51c5dc81a80bbe0c6db30426b72e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159288"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage'larda güvenlik için en iyi yöntemler
'i [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bilgisayarınıza yüklemek için yönetici kimlik bilgileriyle bir bağlamda çalışıyor olması gerekir. Uygulamanın temel güvenlik ve dağıtım birimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [VSPackage'dır.](../../extensibility/internals/vspackages.md) Bir VSPackage, yönetim kimlik bilgileri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de gerektiren kullanılarak kayded gerekir.

 Yöneticiler kayıt defterine ve dosya sistemine yazma ve herhangi bir kodu çalıştırma için tam izinlere sahiptir. VSPackage geliştirmek, dağıtmak veya yüklemek için bu izinlere sahipsiniz.

 Yüklendikten hemen sonra VSPackage'a tam olarak güvenilir. BIR VSPackage ile ilişkili bu yüksek izin düzeyi nedeniyle, kötü amaçlı bir VSPackage'ı yanlışlıkla yüklemek mümkündür.

 Kullanıcıların VSPackage'ları yalnızca güvenilen kaynaklardan yüklemelerini sağlamak gerekir. VSPackage'lar geliştiren şirketlerin, kullanıcıya üzerinde oynamanın engelli olduğunu garanti etmek için bunları kesin bir şekilde adı ve imzaları gerekir. VSPackage'lar geliştiren şirketlerin güvenlik sorunlarını değerlendirmek ve düzeltmek için web hizmetleri ve uzaktan yükleme gibi dış bağımlılıklarını incelemeleri gerekir.

 Daha fazla bilgi için [bkz. Güvenli kodlama yönergeleri için .NET Framework.](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))

## <a name="see-also"></a>Ayrıca bkz.
- [Eklenti güvenliği](/previous-versions/1326zbk3(v=vs.140))
- [DDEX güvenliği](/previous-versions/bb163703(v=vs.140))