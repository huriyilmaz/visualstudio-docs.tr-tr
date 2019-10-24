---
title: Işleme Iliştirilemiyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22d798d30d09cb509f53d093ae61bb1a02b414ec
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728885"
---
# <a name="unable-to-attach-to-the-process"></a>İşleme İliştirilemiyor
İşleme iliştirilemiyor. Sunucu üzerindeki hata ayıklayıcı bileşeni, bu makineye bağlanılırken erişim reddedildi.

 Bu hataya neden olan iki yaygın senaryo vardır:

 **Senaryo 1:** A makinesi Windows XP çalıştırıyor. B makinesi Windows Server 2003 çalıştırıyor. B makinesindeki kayıt defteri Şu DWORD değerini içerir:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 Kullanıcı 1 B makinesi üzerinde bir Terminal sunucusu oturumu (oturum 1) başlatır ve bu oturumdan yönetilen bir uygulama başlatır.

 Her iki makinede yönetici olan Kullanıcı 2, A makinesinde günlüğe kaydedilir. Buradan, B makinesi üzerinde oturum 1 ' de çalışan bir uygulamaya eklemeyi dener.

 **Senaryo 2:** Tek bir Kullanıcı, her iki makinede de aynı parolayı kullanarak, A ve B olmak üzere iki makinede aynı çalışma grubunda oturum açar. Hata ayıklayıcı A makinesinde çalışıyor ve B makinesinde çalışan yönetilen bir uygulamaya iliştirmeye çalışıyor. makine A 'nın **ağ erişimi vardır: yerel hesaplar Için paylaşım ve güvenlik modeli** , **Konuk**olarak ayarlanır.

### <a name="to-solve-scenario-1"></a>Senaryo 1 ' i çözümlemek için

- Hata ayıklayıcı ve yönetilen uygulamayı aynı kullanıcı hesabı adı ve parolası altında çalıştırın.

### <a name="to-solve-scenario-2"></a>Senaryoyu gidermek için 2

1. **Başlat** menüsünde, **Denetim Masası**' nı seçin.

2. Denetim Masası 'nda **Yönetimsel Araçlar**' a çift tıklayın.

3. Yönetimsel Araçlar penceresinde **yerel güvenlik ilkesi**' ne çift tıklayın.

4. Yerel Güvenlik Ilkesi penceresinde, **Yerel ilkeler**' i seçin.

5. **İlkeler** sütununda, **ağ erişimi: yerel hesaplar için paylaşım ve güvenlik modeli**' ne çift tıklayın.

6. **Ağ erişimi: yerel hesaplar Için paylaşım ve güvenlik modeli** iletişim kutusunda yerel güvenlik ayarını **Klasik**olarak değiştirin ve **Tamam**' a tıklayın.

    > [!CAUTION]
    > Güvenlik modelinin klasik olarak değiştirilmesi, paylaşılan dosyalara ve DCOM bileşenlerine beklenmeyen erişimle sonuçlanabilir. Bu değişikliği yaparsanız, uzak bir Kullanıcı Konuk yerine yerel kullanıcı hesabınızla kimlik doğrulaması yapabilir. Bir uzak Kullanıcı Kullanıcı adı ve parolanızla eşleşiyorsa, bu kullanıcı paylaştığınız herhangi bir klasöre veya DCOM nesnesine erişebilir. Bu güvenlik modelini kullanırsanız, makinedeki tüm Kullanıcı hesaplarının güçlü parolalara sahip olduğundan emin olun veya hata ayıklama için yalıtılmış bir ağ Adası ve yetkisiz erişimi engellemek için hata ayıklama makineleri ayarlayın.

7. Tüm pencereleri kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)