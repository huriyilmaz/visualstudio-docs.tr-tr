---
title: 'ASP.NET hata ayıklama: sistem gereksinimleri | Microsoft Docs'
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
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa8951be6da4d77ffb51b6bc8f09a796b373a944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826257"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Hata Ayıklama: Sistem Gereksinimleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, hata ayıklama senaryolarında yazılım ve güvenlik gereksinimleri açıklanmaktadır [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
- Yerel hata ayıklama, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve Web uygulaması aynı bilgisayarda çalışır. Bu senaryonun iki sürümü vardır:  
  
  - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Kod dosya sisteminde bulunur.  

  - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Kod BIR IIS Web sitesinde bulunur.  
  
- İçindeki bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] istemci bilgisayarda çalışan ve bir uzak sunucu bilgisayarında çalışan bir Web uygulamasını hata ayıkladığında uzaktan hata ayıklama.  
  
## <a name="security-requirements"></a>Güvenlik Gereksinimleri  
 Uzaktan hata ayıklama için yerel ve uzak bilgisayarların bir etki alanı kurulumunda veya bir çalışma grubu kurulumunda olması gerekir.  
  
 Çalışan işlemde hata ayıklamak için, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Bu işlemde hata ayıklamak için izninizin olması gerekir. Uygulamalar, varsayılan olarak [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **ASPNET** kullanıcısı olarak çalışır. Çalışan işlemi **ASPNET**veya **ağ hizmeti**olarak çalışıyorsa, hata ayıklamak için yönetici ayrıcalıklarına sahip olmanız gerekir.  
  
 Çalışan işleminin adı, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hata ayıklama senaryosuna ve IIS sürümüne göre farklılık gösterir. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.net Işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]IIS çalıştıran sunucuda machine.config dosyasını düzenleyerek, çalışan işlemin altında çalıştığı kullanıcı hesabını değiştirebilirsiniz. Bunu yapmanın en iyi yolu **Internet Information Services (IIS) Yöneticisi**' ni kullanmaktır. Daha fazla bilgi için bkz. [nasıl yapılır: çalışan işlemini bir kullanıcı hesabı altında çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Çalışan işlemini kendi Kullanıcı hesabınız altında çalışacak şekilde değiştirirseniz, IIS çalıştıran sunucuda yönetici olmanız gerekmez.  
  
> [!CAUTION]
> [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Çalışan işlemini farklı bir hesap altında çalışacak şekilde değiştirmeden önce, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] çalışan işlem bu hesap altında çalışırken bu olası sonuçları göz önünde bulundurun. ASPNET ve NETWORK SERVICE kullanıcı hesapları, en az izinlerle çalışır ve işlem hacimdiğinde olası hasarı azaltır. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Çalışan işlemini daha fazla izne sahip bir hesap altında çalışacak şekilde değiştirmeniz gerekiyorsa, olası hasar büyük olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Nasıl yapılır: bir kullanıcı hesabı altında çalışan Işlemini çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
