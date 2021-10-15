---
title: Visual Studio aboneliklerde bağlı kimlikleri | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 10/14/2021
ms.topic: conceptual
robots: noindex, nofollow
description: Bağlı Microsoft hesapları ve farklı kimliklerle Azure Active Directory öğrenin
ms.openlocfilehash: 2e6c0ffc4c2173f9f80b30c6ab0e8deffd19afe9
ms.sourcegitcommit: a8e6a8c6ca36dc76cdc44d1db934eae43470b5fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2021
ms.locfileid: "130030238"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Aboneliklerde bağlı kimlikleri Visual Studio kullanma
İş veya okul Visual Studio bir Visual Studio aboneliği alırsanız ve oturum açma için Microsoft hesabı (MSA) kullanıyorsanız, abonelik yöneticiniz MSA'nızı kuruluşun Azure Active Directory (Azure AD) kimliğinize bağ kullanabilir.  Bu, aboneliğinize dahil edilen bazı avantajlara erişmenizi değiştirir. 

## <a name="overview-of-connected-ids"></a>Bağlı kimliklere genel bakış
Kuruluşlar, aboneliklerin otomatik yönetimi için gelişmiş güvenlik ve destek sağlamak için giderek daha fazla Azure AD tabanlı kimliklere taşınıyor.  Aboneliğiniz veya başka bir kişisel e-posta adresi gibi bir MSA kullanıyorsa yöneticiniz oturum açma @outlook.com e-postanızı Azure AD kimliğiyle değiştirebilir.  Bu, üzerinden abone portalında oturum açmanızı https://my.visualstudio.com değiştirir, ancak tüm avantajlarınıza erişmenizi değiştirmez.  

Yöneticiniz MSA ve Azure AD kimliklerinizi bağlarsa, MSA'nız yerine Azure AD kimliğiyle Visual Studio aboneliğinize erişmeye başlayacağınızı size haber alan bir e-posta alırsınız. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Azure AD kimliklerini kullanarak avantajlara erişme
Yöneticiniz MSA'nızı Azure AD kimliğinize bağladıktan sonra, Azure AD'ye bağlı avantajlara erişmek için Azure AD kimliğiyle abone portalında https://my.visualstudio.com oturum açmanız gerekir.  Bu modüller şunlardır:
- Visual Studio IDE
- Azure DevOps
- Azure DevTest bireysel kredisi

## <a name="how-to-access-benefits-using-your-msa"></a>MSA'nızı kullanarak avantajlara erişme
Pluralsight, LinkedIn, CloudPilot Visual Studio aboneliklerde sunulan avantajların çoğu için iş ortaklarının web sitelerinde kullanıcı hesapları oluşturabilirsiniz.  Bu hesaplar için, hesabı oluşturulduğunda kullanılan kimliği kullanmaya devam edersiniz.  Örneğin, MSA'nızı kullanarak Pluralsight avantajınızı etkinleştirdiyseniz, abone portalında oturum a0 için hangi kimliği kullanırsanız kullanın Pluralsight eğitimi kullanırken MSA'nızı kullanmaya devam edin.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Aboneliğinize erişmek için alternatif kimlik kullanma
Visual Studio aboneliğinize alternatif bir hesap eklemek, Azure DevOps ve Azure gibi abonelik avantajlarına, aboneliğin atandığı kimlikten farklı bir kimlikle erişmenizi sağlar. Geçmişte bu işlev yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft Hesabına (MSA) atanmışsa kullanılabilirdi. Bu işlevi Azure AD'de iş veya okul hesapları için genişletildik.  Alternatif hesapları kullanma hakkında daha fazla bilgi için Alternatif kimlikler [makalemize göz](vs-alternate-identity.md) atabilirsiniz. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-how-can-i-contact-my-admin-about-this"></a>S: Bu konuda yöneticime nasıl başvurum?
A: Abone portalının sağ üst kısmında "Yöneticime başvur" düğmesini seçin. Yöneticinizle [iletişim kurma hakkında daha fazla](contact-my-admin.md) bilgi için Abonelik yöneticinize ulaşın makalemize bakın.  

### <a name="q-im-an-admin--how-do-i-use-this"></a>S: Yöneticiyim.  Nasıl yaparım? kullanıyor musunuz?
A: Bağlı kimlikleri uygulamak kolaydır.  Daha fazla [bilgi için bu](personal-email-sign-ins.md) makaleye göz atabilirsiniz. 

## <a name="resources"></a>Kaynaklar
- Visual Studio Abonelikleri için satış, abonelikler, hesaplar ve faturalama ile ilgili yardım için bkz. Visual Studio [Abonelikler desteği.](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yöneticiniz Azure AD ve MSA hesaplarınıza bağlanıyorsa abonelik [portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs) başarıyla oturum açmanızı ve Azure DevOps, Visual Studio ve Azure DevTest bireysel krediniz gibi avantajlara erişebilirsiniz.