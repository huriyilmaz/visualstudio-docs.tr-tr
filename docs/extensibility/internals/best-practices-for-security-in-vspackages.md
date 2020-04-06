---
title: VSPackages Güvenlik için En İyi Uygulamalar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709902"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackages'te güvenlik için en iyi uygulamalar
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Bilgisayarınıza yüklemek için, yönetim kimlik bilgileri içeren bir bağlamda çalışıyor olmalısınız. Bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulamanın temel güvenlik birimi ve dağıtımı [VSPackage'dır.](../../extensibility/internals/vspackages.md) Bir VSPackage, yönetim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kimlik bilgileri de gerektiren bir şekilde kaydedilmelidir.

 Yöneticilerin kayıt defterine ve dosya sistemine yazma ve herhangi bir kodu çalıştırmak için tam izinleri vardır. Bir VSPackage geliştirmek, dağıtmak veya yüklemek için bu izinlere sahip olmalısınız.

 Yüklenir yüklenmez, BIR VSPackage'a tamamen güvenilir. VsPackage ile ilişkili bu yüksek izin düzeyi nedeniyle, yanlışlıkla kötü amaçlı bir VSPackage yüklemek mümkündür.

 Kullanıcılar VSPackages'i yalnızca güvenilir kaynaklardan yüklediklerinden emin olmalıdır. VSPackages'ı geliştiren şirketler, kullanıcıya kurcalamanın önlendirilmelerini sağlamak için bunları güçlü bir şekilde isimlendirmeli ve imzalamalıdır. VSPackages'ı geliştiren şirketler, güvenlik sorunlarını değerlendirmek ve düzeltmek için web hizmetleri ve uzaktan yükleme gibi dış bağımlılıklarını incelemelidir.

 Daha fazla bilgi [için .NET Framework için Güvenli kodlama yönergelerine](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Eklenti güvenliği](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [DDEX güvenliği](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
