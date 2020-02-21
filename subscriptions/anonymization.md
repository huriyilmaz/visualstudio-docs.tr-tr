---
title: Visual Studio abone verilerini anonimleştirme | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/20/2020
ms.topic: conceptual
description: Aboneliklerde erişim kesildiğinde abone verilerinin nasıl anonimleştirilmemiş olduğunu öğrenin.
ms.openlocfilehash: f3a35448dd0befbbb91f1657dd62b2b99ff37a2a
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77520845"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Visual Studio abone bilgilerini anonimleştirme
Bir aboneliğin kullanım süresi veya bir abonenin oturum açma hesabı silme gibi bir abonelik kullanımını engelleyen bir olay meydana geldiğinde, kullanıcının ad ve oturum açma hesabı gibi kişisel bilgileri, işlemek için aslında karıştırıdur Bunlar kullanılamaz.  Bu, abonenin kişisel bilgilerini korumak için yapılır.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Anonimleştirme ne zaman oluşur?
Abone için kullanılamayan bir aboneliği işleyen olaylar, anonimleştirme tetikleyecektir.  Anonimleştirme ne kadar hızlı olursa, abonelik türüne ve tetikleme olayına bağlıdır. Daha fazla bilgi için aşağıdaki tabloyu inceleyin.

| Abonelik türü                                                                                                                       | Anonim seçme tetikleme olayı                                                                                                     | Anonimleştirme oluştuğunda |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Abone programın dışına çıkarır veya kullanım koşullarını kabul etmez                                    | 30 gün               |
| Microsoft Store aracılığıyla satın alınan Visual Studio abonelikleri (perakende)                                                                      | Aboneliğin süresi doluyor veya etkin değil                                                                   | 360 gün                  |
| Toplu Lisans, Visual Studio Market (bulut abonelikleri) veya MPN gibi programlar aracılığıyla alınan Visual Studio abonelikleri | Aboneliğin süresi doluyor veya bir kullanıcıya atanmamış                                                          | 180 gün                  |
| Tüm abonelikler                                                                                                                       | Abonelikte oturum açmak için kullanılan bir Azure Active Directory hesabı veya Microsoft hesabı (MSA) kapatıldı | Başlayacaktır               |
| Tüm abonelikler                                                                                                                       | Abone, Azure Active Directory hesabıyla ilişkili kiracıdan kaldırılır                                | Başlayacaktır               |

## <a name="faq"></a>SSS
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>S: abonenin kişisel bilgilerinin anonimleştirmesi, aboneliğe erişimi kaybetmesine neden olur mu?
Y: Hayır.  Anonimleştirme, aboneliğe erişim kaybına neden olan bir olaya yanıt olarak, ancak erişim eksikliğine neden olmaz.

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>S: Kuruluşumun abonelikleri için yöneticiyim.  Abonimin bilgilerden biri anonimleştirilmiştir, bu abonelik başka bir kullanıcıya yeniden atanabilir mi?
Y: Evet--aboneliğin süresi dolmadığından, başka bir aboneye yeniden atanabilir.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>S: bir oturum açma e-posta adresinin silinmesinden kaynaklanan anonim seçimi nasıl önleyebilirim?
Y: Bu sorunu önlemenin iki yolu vardır:
- Tek bir kimlik yönetimi sistemi (MSA veya AAD) dağıtın, ancak her ikisini birden kullanmayın.  
- AAD ve MSA kimliklerini kiracı aracılığıyla ilişkilendirin. 

## <a name="next-steps"></a>Sonraki adımlar
[MSA ve AAD kimliklerini ilişkilendirerek](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)anonimleştirme yapmayı nasıl önleyeceğinizi öğrenin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)
