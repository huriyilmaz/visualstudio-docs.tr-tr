---
title: 'Hata: çalışma grubu uzaktan oturum açma hatası | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09f018982b81535ae23eafe7158aa88c0b6b08a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64798709"
---
# <a name="error-workgroup-remote-logon-failure"></a>Hata: Çalışma Grubu Uzak Oturum Açma Başarısız
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata şunu okur:  
  
 Oturum açma hatası: Bilinmeyen Kullanıcı adı veya hatalı parola  
  
 **Neden**  
  
 Bu hata, çalışma grubundaki bir makineden hata ayıklarken ve uzak makineye bağlanmaya çalıştığınızda oluşabilir. Olası nedenler şunlardır:  
  
- Uzak makinede eşleşen adı ve parolayı içeren bir hesap yok.  
  
- Hem Visual Studio bilgisayarı hem de uzak makine çalışma gruplarında ise, bu hata uzak makinedeki varsayılan **yerel güvenlik ilkesi** ayarı nedeniyle oluşabilir. **Yerel güvenlik ilkesi** ayarı için varsayılan ayar **Yalnızca Konuk-yerel kullanıcılar konuk olarak kimlik doğrular**. Bu kurulumda hata ayıklamak için, uzak makinedeki ayarı **Klasik yerel kullanıcılar olarak kimlik doğrulaması yapacak**şekilde değiştirmeniz gerekir.  
  
> [!NOTE]
> Aşağıdaki görevleri gerçekleştirmek için bir yönetici olmanız gerekir.  
  
### <a name="to-open-the-local-security-policy-window"></a>Yerel Güvenlik Ilkesi penceresini açmak için  
  
1. **Secpol. msc** Microsoft Yönetim Konsolu ek bileşenini başlatın. Windows Search 'te, Windows Run kutusunda veya bir komut isteminde secpol. msc yazın.  
  
### <a name="to-add-user-rights-assignments"></a>Kullanıcı hakları ataması eklemek için  
  
1. Loca 'Yı açma  
  
2. **Yerel güvenlik ilkesi** penceresini açın.  
  
3. **Yerel ilkeler** klasörünü genişletin.  
  
4. **Kullanıcı hakları ataması**' na tıklayın.  
  
5. **İlke** sütununda, **yerel güvenlik ilkesi ayarı** iletişim kutusunda geçerli yerel Grup İlkesi atamalarını görüntülemek için **programlarda hata ayıkla** ' ya çift tıklayın.  
  
     ![Yerel Güvenlik Ilkesi Kullanıcı hakları](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6. Yeni kullanıcılar eklemek için **Kullanıcı veya Grup Ekle** düğmesine tıklayın.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Paylaşım ve güvenlik modelini değiştirmek için  
  
1. **Yerel güvenlik ilkesi** penceresini açın.  
  
2. **Yerel ilkeler** klasörünü genişletin.  
  
3. **Güvenlik seçenekleri**' ne tıklayın.  
  
4. **İlke** sütununda, **ağ erişimi: yerel hesaplar için paylaşım ve güvenlik modeli**' ne çift tıklayın.  
  
5. **Ağ erişimi: yerel hesaplar Için paylaşım ve güvenlik modeli** iletişim kutusunda, değeri **Klasik-yerel kullanıcılar olarak kimlik doğrulaması** yapın ve **Uygula** düğmesine tıklayın.  
  
     ![Yerel Güvenlik Ilkesi güvenlik seçenekleri](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
