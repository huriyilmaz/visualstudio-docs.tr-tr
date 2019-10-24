---
title: 'Hata: çalışma grubu uzaktan oturum açma hatası | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d1ee0cfbd021eb7d6a03a791713d187d3c8877c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736268"
---
# <a name="error-workgroup-remote-logon-failure"></a>Hata: Çalışma Grubu Uzak Oturum Açma Başarısız
Bu hata şunu okur:

 Oturum açma hatası: Bilinmeyen Kullanıcı adı veya hatalı parola

 **Nedeni**

 Bu hata, çalışma grubundaki bir makineden hata ayıklarken ve uzak makineye bağlanmaya çalıştığınızda oluşabilir. Olası nedenler şunlardır:

- Uzak makinede eşleşen adı ve parolayı içeren bir hesap yok.

- Hem Visual Studio bilgisayarı hem de uzak makine çalışma gruplarında ise, bu hata uzak makinedeki varsayılan **yerel güvenlik ilkesi** ayarı nedeniyle oluşabilir. **Yerel güvenlik ilkesi** ayarı için varsayılan ayar **Yalnızca Konuk-yerel kullanıcılar konuk olarak kimlik doğrular**. Bu kurulumda hata ayıklamak için, uzak makinedeki ayarı **Klasik yerel kullanıcılar olarak kimlik doğrulaması yapacak**şekilde değiştirmeniz gerekir.

> [!NOTE]
> Aşağıdaki görevleri gerçekleştirmek için bir yönetici olmanız gerekir.

### <a name="to-open-the-local-security-policy-window"></a>Yerel Güvenlik Ilkesi penceresini açmak için

1. **Secpol. msc** Microsoft Yönetim Konsolu ek bileşenini başlatın. Windows Search 'te, Windows Run kutusunda veya bir komut isteminde secpol. msc yazın.

### <a name="to-add-user-rights-assignments"></a>Kullanıcı hakları ataması eklemek için

1. **Yerel güvenlik ilkesi** penceresini açın.

2. **Yerel ilkeler** klasörünü genişletin.

3. **Kullanıcı hakları ataması**' na tıklayın.

4. **İlke** sütununda, **yerel güvenlik ilkesi ayarı** iletişim kutusunda geçerli yerel Grup İlkesi atamalarını görüntülemek için **programlarda hata ayıkla** ' ya çift tıklayın.

     ![Yerel Güvenlik Ilkesi Kullanıcı hakları](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Yeni kullanıcılar eklemek için **Kullanıcı veya Grup Ekle** düğmesine tıklayın.

### <a name="to-change-the-sharing-and-security-model"></a>Paylaşım ve güvenlik modelini değiştirmek için

1. **Yerel güvenlik ilkesi** penceresini açın.

2. **Yerel ilkeler** klasörünü genişletin.

3. **Güvenlik seçenekleri**' ne tıklayın.

4. **İlke** sütununda, **ağ erişimi: yerel hesaplar için paylaşım ve güvenlik modeli**' ne çift tıklayın.

5. **Ağ erişimi: yerel hesaplar Için paylaşım ve güvenlik modeli** iletişim kutusunda, değeri **Klasik-yerel kullanıcılar olarak kimlik doğrulaması** yapın ve **Uygula** düğmesine tıklayın.

     ![Yerel Güvenlik Ilkesi güvenlik seçenekleri](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)