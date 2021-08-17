---
title: İşlem Ekleme | Microsoft Docs
description: "\"İşleme Eklenemiyor\" ifadesinin anlamını, buna neden olan iki senaryoyu ve çözümleri öğrenin."
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1509e5a24bf1f61f164c9dae6864072ce415b57e14314dfdb0f16971d9315456
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435731"
---
# <a name="unable-to-attach-to-the-process"></a>İşleme İliştirilemiyor
İşleme eklenemiyor. Sunucusundaki hata ayıklayıcı bileşeni, bu makineye bağlanırken erişim reddedildi.

 Bu hataya neden olan iki yaygın senaryo vardır:

 **Senaryo 1:** A Makinesi XP'Windows çalışıyor. B Makinesi Windows Server 2003'te çalışıyor. Makine B'de kayıt defteri aşağıdaki DWORD değerini içerir:

 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`

 Kullanıcı 1, B makinesi üzerinde bir Terminal Sunucusu oturumu (oturum 1) başlatır ve bu oturumdan yönetilen bir uygulama başlatır.

 Her iki makinede de yönetici olan Kullanıcı 2, Makine A'da oturum açtı. Buradan, B Makinesi'nin 1. oturumunda çalışan bir uygulamaya ekleme yapmaya çalışır.

 **Senaryo 2:** İki makinede de aynı parolayı kullanarak bir kullanıcı aynı çalışma grubunda A ve B olmakta olan iki makinede oturum açtı. Hata ayıklayıcı A Makinesi üzerinde çalışıyor ve B Makinesi üzerinde çalışan bir yönetilen uygulamaya eklemeye çalışıyor. Makine A'da Ağ erişimi **var:** Yerel hesaplar için paylaşım ve güvenlik modeli Konuk olarak **ayarlanmış.**

### <a name="to-solve-scenario-1"></a>Senaryo 1'i çözmek için

- Hata ayıklayıcıyı ve yönetilen uygulamayı aynı kullanıcı hesabı adı ve parolası altında çalıştırın.

### <a name="to-solve-scenario-2"></a>Senaryo 2'de çözmek için

1. Başlat **menüsünden** Seç'i **Denetim Masası.**

2. Bu Denetim Masası Yönetimsel **araçlar'a çift tıklayın.**

3. Yönetim araçları penceresinde Yerel Güvenlik **İlkesi'ne çift tıklayın.**

4. Yerel Güvenlik İlkesi penceresinde Yerel **İlkeler'i seçin.**

5. **İlkeler sütununda** Ağ **erişimi: Yerel hesaplar için paylaşım ve güvenlik modeli'ne çift tıklayın.**

6. Ağ **erişimi: Yerel hesaplar için paylaşım** ve güvenlik modeli iletişim kutusunda yerel güvenlik ayarını Klasik olarak **değiştirin** ve Tamam'a **tıklayın.**

    > [!CAUTION]
    > Güvenlik modelinin Klasik olarak değiştirilmesi, paylaşılan dosyalara ve DCOM bileşenlerine beklenmedik erişime neden olabilir. Bu değişikliği yaptıysanız, uzak bir kullanıcı Konuk yerine yerel kullanıcı hesabınızla kimlik doğrulamasından olabilir. Uzak bir kullanıcı kullanıcı adınız ve parolanız ile eşılıyorsa, bu kullanıcı, paylaşılan herhangi bir klasöre veya DCOM nesnesine erişebilirsiniz. Bu güvenlik modelini kullanıyorsanız, makinede tüm kullanıcı hesaplarının güçlü parolalara sahip olduğundan emin olun veya yetkisiz erişimi önlemek için hata ayıklama ve hata ayıklanmış makineler için yalıtılmış bir ağ adası ayarlayın.

7. Tüm pencereleri kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarlar Hazırlama](../debugger/debugger-settings-and-preparation.md)