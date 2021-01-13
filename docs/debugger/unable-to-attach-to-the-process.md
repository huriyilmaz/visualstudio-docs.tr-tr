---
title: Işleme Iliştirilemiyor | Microsoft Docs
description: "\"Işleme Iliştirilemedi\", soruna neden olan iki senaryo ve çözümler hakkında bilgi edinin."
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e7a90d2e08d16ddfb7ac22baafe58cf76b4895d3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150853"
---
# <a name="unable-to-attach-to-the-process"></a>İşleme İliştirilemiyor
İşleme iliştirilemiyor. Sunucu üzerindeki hata ayıklayıcı bileşeni, bu makineye bağlanılırken erişim reddedildi.

 Bu hataya neden olan iki yaygın senaryo vardır:

 **Senaryo 1:** A makinesi Windows XP çalıştırıyor. B makinesi Windows Server 2003 çalıştırıyor. B makinesindeki kayıt defteri Şu DWORD değerini içerir:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 Kullanıcı 1 B makinesi üzerinde bir Terminal sunucusu oturumu (oturum 1) başlatır ve bu oturumdan yönetilen bir uygulama başlatır.

 Her iki makinede yönetici olan Kullanıcı 2, A makinesinde günlüğe kaydedilir. Buradan, B makinesi üzerinde oturum 1 ' de çalışan bir uygulamaya eklemeyi dener.

 **Senaryo 2:** Tek bir Kullanıcı, her iki makinede de aynı parolayı kullanarak, A ve B olmak üzere iki makinede aynı çalışma grubunda oturum açar. Hata ayıklayıcı A makinesinde çalışıyor ve B makinesinde çalışan yönetilen bir uygulamaya iliştirmeye çalışıyor. makine A 'nın **ağ erişimi vardır: yerel hesaplar Için paylaşım ve güvenlik modeli** , **Konuk** olarak ayarlanır.

### <a name="to-solve-scenario-1"></a>Senaryo 1 ' i çözümlemek için

- Hata ayıklayıcı ve yönetilen uygulamayı aynı kullanıcı hesabı adı ve parolası altında çalıştırın.

### <a name="to-solve-scenario-2"></a>Senaryoyu gidermek için 2

1. **Başlat** menüsünde, **Denetim Masası**' nı seçin.

2. Denetim Masası 'nda **Yönetimsel Araçlar**' a çift tıklayın.

3. Yönetimsel Araçlar penceresinde **yerel güvenlik ilkesi**' ne çift tıklayın.

4. Yerel Güvenlik Ilkesi penceresinde, **Yerel ilkeler**' i seçin.

5. **İlkeler** sütununda, **ağ erişimi: yerel hesaplar için paylaşım ve güvenlik modeli**' ne çift tıklayın.

6. **Ağ erişimi: yerel hesaplar Için paylaşım ve güvenlik modeli** iletişim kutusunda yerel güvenlik ayarını **Klasik** olarak değiştirin ve **Tamam**' a tıklayın.

    > [!CAUTION]
    > Güvenlik modelinin klasik olarak değiştirilmesi, paylaşılan dosyalara ve DCOM bileşenlerine beklenmeyen erişimle sonuçlanabilir. Bu değişikliği yaparsanız, uzak bir Kullanıcı Konuk yerine yerel kullanıcı hesabınızla kimlik doğrulaması yapabilir. Bir uzak Kullanıcı Kullanıcı adı ve parolanızla eşleşiyorsa, bu kullanıcı paylaştığınız herhangi bir klasöre veya DCOM nesnesine erişebilir. Bu güvenlik modelini kullanırsanız, makinedeki tüm Kullanıcı hesaplarının güçlü parolalara sahip olduğundan emin olun veya hata ayıklama için yalıtılmış bir ağ Adası ve yetkisiz erişimi engellemek için hata ayıklama makineleri ayarlayın.

7. Tüm pencereleri kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)