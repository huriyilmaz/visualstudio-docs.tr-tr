---
title: Çalışma grubu uzaktan oturum açma hatası | Microsoft Docs
description: Bu hata, çalışma grubundaki bir makineden hata ayıklarken ve uzak makineye bağlanmaya çalıştığınızda oluşabilir.
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c3784317df0b3fa46607f2055e29c7a9ccd62928
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080890"
---
# <a name="error-workgroup-remote-logon-failure"></a>Hata: Çalışma Grubu Uzak Oturum Açma Başarısız
Bu hata şunu okur:

 Oturum açma hatası: Bilinmeyen Kullanıcı adı veya hatalı parola

 **Neden**

 Bu hata, çalışma grubundaki bir makineden hata ayıklarken ve uzak makineye bağlanmaya çalıştığınızda oluşabilir. Olası nedenler şunlardır:

- Uzak makinede eşleşen adı ve parolayı içeren bir hesap yok.

- hem Visual Studio bilgisayar hem de uzak makine çalışma gruplarında ise, bu hata uzak makinedeki varsayılan **yerel güvenlik ilkesi** ayarı nedeniyle oluşabilir. **Yerel güvenlik ilkesi** ayarı için varsayılan ayar **Yalnızca Konuk-yerel kullanıcılar konuk olarak kimlik doğrular**. Bu kurulumda hata ayıklamak için, uzak makinedeki ayarı **Klasik yerel kullanıcılar olarak kimlik doğrulaması yapacak** şekilde değiştirmeniz gerekir.

> [!NOTE]
> Aşağıdaki görevleri gerçekleştirmek için bir yönetici olmanız gerekir.

### <a name="to-open-the-local-security-policy-window"></a>Yerel Güvenlik Ilkesi penceresini açmak için

1. **Secpol. msc** Microsoft Yönetim Konsolu ek bileşenini başlatın. Windows aramada, Windows çalıştır kutusunda veya bir komut isteminde secpol. msc yazın.

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
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
