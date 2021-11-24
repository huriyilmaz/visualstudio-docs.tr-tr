---
title: Abone verilerini Visual Studio anonimleştirme | Microsoft Docs
author: evanwindom
ms.author: amast
manager: amast
ms.assetid: ce5fc8a4-484c-4df6-97c3-cb60174fb66b
ms.date: 03/11/2021
ms.topic: conceptual
description: Aboneliklere erişim kaybedilirken abone verileri nasıl anonimleştirildiğini öğrenin.
ms.openlocfilehash: 5787ef469c8ce0f075bf83a3d7e127f2e77647d4
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132995606"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>Abone bilgilerini Visual Studio anonimleştirme
Aboneliğin sona ermesi veya abonenin oturum açma hesabının silinmesi gibi abonenin abonelik kullanımını engelleyen bir olay oluştuğunda, kullanıcının ad ve oturum açma hesabı gibi kişisel bilgileri temelde bunları kullanılamaz hale getirecektir.  Bu, abonenin kişisel bilgilerini korumak için yapılır.

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>Anonimleştirme ne zaman gerçekleşir?
Aboneliği abone için kullanılamaz hale getiren olaylar anonimleştirmeyi tetikler.  Anonimleştirmenin ne kadar hızlı gerçekleşmesi, aboneliğin türüne ve tetikleyen olaya bağlıdır. Daha fazla bilgi için aşağıdaki tabloyu inceleyin.

| Subscription Type (Abonelik Türü)                                                                                                                       | Anonimleştirmeyi tetikleyen olay                                                                                                     | Anonimleştirme oluştuğunda |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | Abone programı iptal eder veya kullanım koşullarını kabul etmez                                    | 30 gün               |
| Visual Studio aracılığıyla satın alınan abonelikleri Microsoft Store (perakende)                                                                      | Aboneliğin süresi doldu veya etkinleştirilmedi                                                                   | 360 gün                  |
| Visual Studio Lisans, Visual Studio Market (bulut abonelikleri) veya MPN gibi programlar aracılığıyla alınan abonelikler | Aboneliğin süresi dolar veya kullanıcıya atanmamış                                                          | 180 gün                  |
| Tüm abonelikler                                                                                                                       | Abonelikte Azure Active Directory için kullanılan bir hesap veya Microsoft Hesabı (MSA) kapatıldı | Hemen               |
| Tüm abonelikler                                                                                                                       | Abone, kiracı hesabıyla ilişkili kiracıdan Azure Active Directory kaldırılır                                | Hemen               |

## <a name="faq"></a>SSS
### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>S: Abonenin kişisel bilgilerini anonimleştirme, aboneliğe erişimi kaybetmelerine neden oluyor mu?
A: Hayır.  Anonimleştirme, aboneliğe erişim kaybına neden olan ancak erişim eksikliğine neden olmayan bir olayla yanıt olur.

### <a name="q--im-an-admin-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>S: Kuruluşum abonelikleri için yöneticiyim.  Abonemin bilgilerinden biri anonimleştirilmişse bu abonelik başka bir kullanıcıya yeniden atanabilir mi?
A: Evet.  Bu ölçütler karşılandı ise abonelikler yeniden atanabilir:
- Aboneliğin süresi dolmadı
- Aboneliğin aboneye en son atandığı zamandan bu yana en az 90 gün geçti.  Örneğin, bir abonelik 1 Haziran'da aboneye atanmışsa, en az 30 Ağustos'a kadar abonelik yeniden atanamaz.

### <a name="q-how-can-i-prevent-anonymization-caused-by-deleting-a-sign-in-email-address"></a>S: Oturum açma e-posta adresini silmenin neden olduğu anonimleştirmeyi nasıl önlenebilirim?
A: Sorunu önlemenin iki yolu vardır:
- MSA veya AAD tek bir kimlik yönetimi sistemi dağıtın ancak her ikisini birden dağıtın.  
- Kiracı AAD MSA kimliklerini ilişkilendirme. 

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio Abonelikleri için satış, abonelikler, hesaplar ve faturalama ile ilgili yardım için bkz. Visual Studio [Abonelikler desteği.](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
MSA ve kimlikleri arasında [AAD öğrenin.](/azure/active-directory/b2b/add-users-administrator)