---
title: Visual Studio abone verilerinin anonimleştirme | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 03/11/2021
ms.topic: conceptual
description: Aboneliklerde erişim kesildiğinde abone verilerinin nasıl anonimleştirilmemiş olduğunu öğrenin.
ms.openlocfilehash: 6e7f775213b158765448dc306d676ffc2a86e4ea
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133254403"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Visual Studio abone bilgilerinin anonimleştirme
Bir aboneliğin kullanım süresi veya bir abonenin oturum açma hesabı silme gibi bir abonelik kullanımını engelleyen bir olay meydana geldiğinde, kullanıcının ad ve oturum açma hesabı gibi kişisel bilgileri, bunları kullanılamaz hale getirecek şekilde karmaşıklamaz.  Bu, abonenin kişisel bilgilerini korumak için yapılır.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Anonimleştirme ne zaman oluşur?
Abone için kullanılamayan bir aboneliği işleyen olaylar, anonimleştirme tetikleyecektir.  Anonimleştirme ne kadar hızlı olursa, abonelik türüne ve tetikleme olayına bağlıdır. Daha fazla bilgi için aşağıdaki tabloyu inceleyin.

| Subscription Type (Abonelik Türü)                                                                                                                       | Anonim seçme tetikleme olayı                                                                                                     | Anonimleştirme oluştuğunda |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Abone programın dışına çıkarır veya kullanım koşullarını kabul etmez                                    | 30 gün               |
| Microsoft Store üzerinden satın alınan Visual Studio abonelikler (perakende)                                                                      | Aboneliğin süresi doluyor veya etkin değil                                                                   | 360 gün                  |
| toplu lisans, Visual Studio market (bulut abonelikleri) veya mpn gibi programlar aracılığıyla alınan abonelikler Visual Studio | Aboneliğin süresi doluyor veya bir kullanıcıya atanmamış                                                          | 180 gün                  |
| Tüm abonelikler                                                                                                                       | abonelikte oturum açmak için kullanılan bir Azure Active Directory hesabı veya Microsoft hesabı (MSA) kapatıldı | Hemen               |
| Tüm abonelikler                                                                                                                       | abone, Azure Active Directory hesabıyla ilişkili kiracıdan kaldırılır                                | Hemen               |

## <a name="faq"></a>SSS
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>S: abonenin kişisel bilgilerinin anonimleştirmesi, aboneliğe erişimi kaybetmesine neden olur mu?
Y: Hayır.  Anonimleştirme, aboneliğe erişim kaybına neden olan bir olaya yanıt olarak, ancak erişim eksikliğine neden olmaz.

### <a name="q--im-an-admin-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>S: Kuruluşumun abonelikleri için yöneticiyim.  Abonimin bilgilerden biri anonimleştirilmiştir, bu abonelik başka bir kullanıcıya yeniden atanabilir mi?
Y: Evet.  Bu ölçütler karşılanıyorsa abonelikler yeniden atanabilir:
- Aboneliğin süresi dolmadı
- Aboneliğin bir aboneye en son atanmasından bu yana en az 90 gün geçti.  Örneğin, abonelik 1 Haziran tarihinde abone olmak üzere atandıysa, en az 30 Ağustos 'a kadar yeniden atanamaz.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>S: bir oturum açma e-posta adresinin silinmesinden kaynaklanan anonim seçimi nasıl önleyebilirim?
Y: Bu sorunu önlemenin iki yolu vardır:
- tek bir kimlik yönetimi sistemi dağıtın--ya MSA ya da AAD--her ikisi birden değil.  
- AAD ve MSA kimliklerini kiracı aracılığıyla ilişkilendirin. 

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio abonelikleriyle ilgili satış, abonelik, hesap ve faturalandırma konusunda yardım için bkz. Visual Studio [abonelikleri desteği](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
[MSA ve AAD kimliklerini ilişkilendirerek](/azure/active-directory/b2b/add-users-administrator)anonimleştirme yapmayı nasıl önleyeceğinizi öğrenin.