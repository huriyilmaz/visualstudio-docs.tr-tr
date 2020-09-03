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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72574621"
---
# <a name="prerequisites-for-remote-debugging-web-applications"></a>Uzaktan Hata Ayıklama Web Uygulamaları Önkoşulları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hata ayıklayıcı ile, bir Web uygulamasının hatalarını saydam bir şekilde yerel bilgisayarda veya uzak bir sunucuda ayıklayabilirsiniz. Diğer bir deyişle, hata ayıklayıcı aynı şekilde çalışır ve her iki bilgisayarda aynı özellikleri kullanmanıza olanak sağlar. Uzaktan hata ayıklama 'nin düzgün çalışması için bazı Önkoşullar vardır.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Uzaktan hata ayıklama bileşenleri, hata ayıklamak istediğiniz sunucuda yüklü olmalıdır. Daha fazla bilgi için bkz. [Uzaktan hata ayıklamayı ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Varsayılan olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlemi BIR ASPNET Kullanıcı işlemi olarak çalışır. Sonuç olarak, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hata ayıklamak için çalıştırılan bilgisayarda yönetici ayrıcalıklarına sahip olmanız gerekir. Çalışan işleminin adı, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] IIS 'nin hata ayıklama senaryosuna ve sürümüne göre farklılık gösterir. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.net Işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Sistem Gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
