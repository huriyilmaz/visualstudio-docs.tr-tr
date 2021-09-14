---
title: 'ASP.NET Hata ayıklama: sistem gereksinimleri | Microsoft Docs'
description: Visual Studio ve web uygulamasının aynı bilgisayarda çalıştığı ve uzaktan hata ayıklamanın ASP.NET yerel hata ayıklama için yazılım ve güvenlik gereksinimlerini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 6de11302ea67e27e46348638701172abc5e0964b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630963"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Hata Ayıklama: Sistem Gereksinimleri
Bu konuda, hata ayıklama senaryolarında yazılım ve güvenlik gereksinimleri açıklanmaktadır [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :

- Yerel hata ayıklama, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve Web uygulaması aynı bilgisayarda çalışır. Bu senaryonun iki sürümü vardır:

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Kod dosya sisteminde bulunur.

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Kod BIR IIS Web sitesinde bulunur.

- İçindeki bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] istemci bilgisayarda çalışan ve bir uzak sunucu bilgisayarında çalışan bir Web uygulamasını hata ayıkladığında uzaktan hata ayıklama.

## <a name="security-requirements"></a>Güvenlik Gereksinimleri
 Uzaktan hata ayıklama için yerel ve uzak bilgisayarların bir etki alanı kurulumunda veya bir çalışma grubu kurulumunda olması gerekir.

 Çalışan işlemde hata ayıklamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (bir uygulama havuzu tarafından barındırılan), bu işlemde hata ayıklamak için izninizin olması gerekir. Varsayılan olarak, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ııs 6,0 ' den önceki uygulamalar **ASPNET** kullanıcısı olarak çalışır. IIS 6,0 ve IIS 7,0 ' de, **ağ hizmeti** hesabı varsayılandır. Çalışan işlemi **ASPNET** veya **ağ hizmeti** olarak çalışıyorsa, hata ayıklamak için yönetici ayrıcalıklarına sahip olmanız gerekir.

 > [!IMPORTANT]
 > Windows Server 2008 R2 'den başlayarak, her uygulama havuzu için kimlik olarak [applicationpokaydentity](/iis/manage/configuring-security/application-pool-identities) kullanılması önerilir.

 Çalışan işleminin adı, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hata ayıklama senaryosuna ve IIS sürümüne göre farklılık gösterir. daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET işlemin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]IIS çalıştıran sunucuda machine.config dosyasını düzenleyerek, çalışan işlemin altında çalıştığı kullanıcı hesabını değiştirebilirsiniz. bunu yapmanın en iyi yolu **Internet Information Services (ııs) yöneticisi**' ni kullanmaktır. Daha fazla bilgi için bkz. [nasıl yapılır: çalışan işlemini bir kullanıcı hesabı altında çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışan işlemini kendi Kullanıcı hesabınız altında çalışacak şekilde değiştirirseniz, IIS çalıştıran sunucuda yönetici olmanız gerekmez.

> [!CAUTION]
> [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışan işlemini farklı bir hesap altında çalışacak şekilde değiştirmeden önce, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlem bu hesap altında çalışırken bu olası sonuçları göz önünde bulundurun. ASPNET ve NETWORK SERVICE kullanıcı hesapları, en az izinlerle çalışır ve işlem hacimdiğinde olası hasarı azaltır. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışan işlemini daha fazla izne sahip bir hesap altında çalışacak şekilde değiştirmeniz gerekiyorsa, olası hasar büyük olur.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET uygulamalarda hata ayıkla](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Nasıl yapılır: bir kullanıcı hesabı altında çalışan Işlemini çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md)