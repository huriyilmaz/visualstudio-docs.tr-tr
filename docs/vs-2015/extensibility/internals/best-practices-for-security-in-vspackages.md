---
title: VSPackages 'ta güvenlik için en iyi uygulamalar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697277"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage’larda Güvenlik için En İyi Yöntemler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bilgisayarınıza yüklemek için [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] yönetici kimlik bilgilerine sahip bir bağlamda çalıştırıyor olmanız gerekir. Temel güvenlik birimi ve uygulamanın dağıtımı, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [VSPackages](../../extensibility/internals/vspackages.md)'dir. Bir VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , yönetim kimlik bilgileri gerektiren kullanılarak kaydedilmelidir.  
  
 Yöneticiler kayıt defteri ve dosya sistemine yazmak ve herhangi bir kodu çalıştırmak için tam izinlere sahiptir. VSPackage geliştirmek, dağıtmak veya yüklemek için bu izinlere sahip olmanız gerekir.  
  
 Yüklendikten hemen sonra VSPackage tamamen güvenilirdir. VSPackage ile ilişkili bu üst düzey izin nedeniyle, kötü amaçlı bir amaç içeren bir VSPackage 'ı yanlışlıkla yüklemek mümkündür.  
  
 Kullanıcılar, VSPackages 'ı yalnızca güvenilir kaynaklardan yüklediklerinden emin olmalıdır. VSPackages geliştiren şirketlerin, kullanıcının izinsiz değişiklik yapmasını güvence altına almak için, onları kesin olarak adı ve imzalayabilmelidir. VSPackages geliştiren şirketler, herhangi bir güvenlik sorununu değerlendirmek ve düzeltmek üzere Web Hizmetleri ve uzaktan yükleme gibi dış bağımlılıklarını incelemelidir.  
  
 Daha fazla bilgi için bkz. .NET Framework () için güvenli kodlama yönergeleri [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eklenti Güvenliği](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX güvenliği](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
