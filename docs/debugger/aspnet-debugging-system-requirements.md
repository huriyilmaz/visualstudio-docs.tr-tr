---
title: 'ASP.NET hata ayıklama: sistem gereksinimleri | Microsoft Docs'
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 78f947c7ab9fcc1031d457526240ecdd7e9119a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745803"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Hata Ayıklama: Sistem Gereksinimleri
Bu konuda [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hata ayıklama senaryoları için yazılım ve güvenlik gereksinimleri açıklanmaktadır:

- @No__t_0 ve Web uygulamasının aynı bilgisayarda çalıştığı yerel hata ayıklama. Bu senaryonun iki sürümü vardır:

  - @No__t_0 kodu dosya sisteminde bulunur.

  - @No__t_0 kodu bir IIS Web sitesinde bulunur.

- @No__t_0 istemci bilgisayarda çalıştığı ve uzak sunucu bilgisayarında çalışan bir Web uygulamasını hata ayıklamanın uzaktan hata ayıklaması.

## <a name="security-requirements"></a>Güvenlik Gereksinimleri
 Uzaktan hata ayıklama için yerel ve uzak bilgisayarların bir etki alanı kurulumunda veya bir çalışma grubu kurulumunda olması gerekir.

 @No__t_0 çalışan işleminde hata ayıklamak için (bir uygulama havuzu tarafından barındırılan), bu işlemde hata ayıklamak için izninizin olması gerekir. Varsayılan olarak, IIS 6,0 ' den önceki uygulamalar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **ASPNET** kullanıcısı olarak çalışır. IIS 6,0 ve IIS 7,0 ' de, **ağ hizmeti** hesabı varsayılandır. Çalışan işlemi **ASPNET**veya **ağ hizmeti**olarak çalışıyorsa, hata ayıklamak için yönetici ayrıcalıklarına sahip olmanız gerekir.

 > [!IMPORTANT]
 > Windows Server 2008 R2 'den başlayarak, her uygulama havuzu için kimlik olarak [Applicationpokaydentity](/iis/manage/configuring-security/application-pool-identities) kullanılması önerilir.

 @No__t_0 çalışan işleminin adı, hata ayıklama senaryosuna ve IIS sürümüne göre farklılık gösterir. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.net Işleminin adını bulma](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 IIS çalıştıran sunucuda Machine. config dosyasını düzenleyerek [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işleminin altında çalıştığı kullanıcı hesabını değiştirebilirsiniz. Bunu yapmanın en iyi yolu **Internet Information Services (IIS) Yöneticisi**' ni kullanmaktır. Daha fazla bilgi için bkz. [nasıl yapılır: çalışan işlemini bir kullanıcı hesabı altında çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 @No__t_0 çalışan işlemini kendi Kullanıcı hesabınız altında çalışacak şekilde değiştirirseniz, IIS çalıştıran sunucuda yönetici olmanız gerekmez.

> [!CAUTION]
> @No__t_0 çalışan işlemini farklı bir hesap altında çalışacak şekilde değiştirmeden önce, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işleminin söz konusu hesap altında çalışırken korsan olması gerekiyorsa olası sonuçları göz önünde bulundurun. ASPNET ve NETWORK SERVICE kullanıcı hesapları, en az izinlerle çalışır ve işlem hacimdiğinde olası hasarı azaltır. @No__t_0 çalışan işlemini daha fazla izne sahip bir hesap altında çalışacak şekilde değiştirmeniz gerekiyorsa, olası hasar büyük olur.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Nasıl Yapılır: Bir Kullanıcı Hesabı Altında Çalışan İşlemini Çalıştırma](../debugger/how-to-run-the-worker-process-under-a-user-account.md)