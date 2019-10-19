---
title: Web uygulamalarında uzaktan hata ayıklama önkoşulları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8cbf0ae920be00980d270aae16d5e7d1f7a5313
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574621"
---
# <a name="prerequisites-for-remote-debugging-web-applications"></a>Uzaktan hata ayıklama Web uygulamalarının önkoşulları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 hata ayıklayıcı ile, bir Web uygulamasında yerel bilgisayar veya uzak bir sunucu üzerinde saydam bir şekilde hata ayıklayabilirsiniz. Diğer bir deyişle, hata ayıklayıcı aynı şekilde çalışır ve her iki bilgisayarda aynı özellikleri kullanmanıza olanak sağlar. Uzaktan hata ayıklama 'nin düzgün çalışması için bazı Önkoşullar vardır.  
  
- hata ayıklamak istediğiniz sunucuda uzaktan hata ayıklama bileşenlerinin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklü olması gerekir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklamayı ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Varsayılan olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi bir ASPNET Kullanıcı işlemi olarak çalışır. Sonuç olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hata ayıklaması için çalıştığı bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir. @No__t_0 çalışan işleminin adı, IIS 'nin hata ayıklama senaryosuna ve sürümüne göre farklılık gösterir. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.net Işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.net ve Ajax uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)    
 [Sistem Gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
