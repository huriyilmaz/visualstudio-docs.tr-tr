---
title: Visual Studio abone verilerinin anonymizasyonu | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/20/2020
ms.topic: conceptual
description: Aboneliklere erişim kaybolduğunda abone verilerinin nasıl anonim hale edildiğini öğrenin.
ms.openlocfilehash: 439e53b1c67fde0fbda0666652e29bf396abfee2
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78894412"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Visual Studio abone bilgilerinin anonymizasyonu
Abonenin aboneliğin sona ermesi veya abonenin oturum açma hesabının silinmesi gibi aboneliği kullanmasını engelleyen bir olay meydana geldiğinde, kullanıcının ad ve oturum açma hesabı gibi kişisel bilgileri, kullanılamaz hale getirilebilir.  Bu, abonenin kişisel bilgilerini korumak için yapılır.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Anonymizasyon ne zaman gerçekleşir?
Bir abone için aboneliği kullanılamaz hale getiren olaylar, anonymizasyonu tetikler.  Ne kadar hızlı anonymization oluşur abonelik türüne ve tetikleyici olay bağlıdır. Daha fazla bilgi için aşağıdaki tabloyu inceleyin.

| Subscription Type (Abonelik Türü)                                                                                                                       | Anonymizasyonu tetikleyen olay                                                                                                     | Ne zaman anonymization oluşur |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Abone programdan çıkar veya kullanım koşullarını kabul etmez                                    | 30 gün               |
| Microsoft Mağazası (perakende) üzerinden satın alınan Visual Studio abonelikleri                                                                      | Abonelik süresi doluyor veya etkinleştirilmedi                                                                   | 360 gün                  |
| Toplu Lisans, Visual Studio Marketplace (bulut abonelikleri) veya MPN gibi programlar aracılığıyla edinilen Visual Studio abonelikleri | Aboneliğin süresi doluyor veya kullanıcıya atanmıyor                                                          | 180 gün                  |
| Tüm abonelikler                                                                                                                       | Abonelikte oturum açmak için kullanılan bir Azure Active Directory hesabı veya Microsoft Hesabı (MSA) kapatılır | Hemen               |
| Tüm abonelikler                                                                                                                       | Bir abone, Azure Etkin Dizin hesabıyla ilişkili kiracıdan kaldırılır                                | Hemen               |

## <a name="faq"></a>SSS
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>S: Abonenin kişisel bilgilerinin anonymizasyonu aboneye erişimini kaybetmelerine neden oluyor mu?
Y: Hayır.  Anonymization, aboneye erişim kaybına neden olan, ancak erişim eksikliğine neden olmayan bir olaya yanıt olarak verilir.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>S: Kuruluşumun abonelikleri için yöneticiyim.  Abonemin bilgilerinden biri anonimleştirilmişse, bu abonelik başka bir kullanıcıya yeniden atanabilir mi?
C: Evet -- Aboneliğin süresi dolmadığı sürece, başka bir aboneye yeniden atanabilir.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>S: Oturum açma e-posta adresinin silmesinedeniyle anonymizasyonu nasıl önleyebilirim?
C: Sorunu önlemenin iki yolu vardır:
- MSA veya AAD gibi tek bir kimlik yönetim sistemi konuşlandırın, ancak her ikisini birden devreye sayılmayın.  
- AAD ve MSA kimliklerini kiracı aracılığıyla ilişkilendirin. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
[MSA ve AAD kimliklerini ilişkilendirerek](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)anonyization'ı nasıl önleyeceğinizi öğrenin.


