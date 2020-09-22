---
title: Bağlı Microsoft hesabı ve Azure Active Directory kimliklerini kullanma | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Bağlı Microsoft hesaplarıyla ve Azure Active Directory kimliklerle çalışmayı öğrenin
ms.openlocfilehash: 6d67576ab715f3ff8a49287155423a3dd6c20867
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005244"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde bağlı kimlikler kullanma
Çalışmanız veya okulunuz aracılığıyla bir Visual Studio aboneliği alırsanız ve oturum açmak için Microsoft hesabı (MSA) kullanıyorsanız, abonelik yöneticiniz, MSA 'yı kuruluşunuzun Azure Active Directory (Azure AD) olarak kimliğinize bağlayabilirsiniz.  Bu, aboneliğinize dahil olan avantajlardan bazılarına nasıl erişirsiniz. 

## <a name="overview-of-connected-ids"></a>Bağlı kimliklere genel bakış
Kuruluşlar, aboneliklerin otomatik yönetimi için geliştirilmiş güvenlik ve destek sunmak amacıyla Azure AD tabanlı kimliklere giderek daha fazla hareket ettirilir.  Aboneliğiniz @outlook.com ya da başka bir kişisel e-posta adresi gibi BIR MSA kullanıyorsa, yöneticiniz oturum açma e-postanızı Azure AD kimliğinize değiştirebilir.  Bu, abone portalında oturum açmayı değiştirecek, https://my.visualstudio.com ancak tüm avantajlarınıza nasıl erişrinizi değiştiremeyebilir.  

Yöneticiniz MSA ve Azure AD kimliklerinizi bağladığında, MSA yerine Azure AD Kimliğiniz ile Visual Studio aboneliğinize erişmeye başlamasını sağlayan bir e-posta alırsınız. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Azure AD kimlikleri kullanarak avantajlara erişme
Yöneticiniz, MSA 'ı Azure AD kimliğinize bağladıktan sonra Azure AD https://my.visualstudio.com kimlik bilgilerinizi kullanarak Azure AD 'yi kullanan avantajlara erişmeniz için abone portalında oturum açmanız gerekir.  Bu güncelleştirmeler şunlardır:
- Visual Studio IDE
- Azure DevOps
- Azure DevTest bireysel kredisi

## <a name="how-to-access-benefits-using-your-msa"></a>MSA kullanarak avantajlara erişme
Pluralgözetimi, LinkedIn, CloudPilot ve diğerleri gibi Visual Studio aboneliklerinde sunulan birçok avantaj için, iş ortaklarının Web sitelerinde Kullanıcı hesapları oluşturursunuz.  Bu hesaplar için, hesabı oluştururken kullandığınız kimliği kullanmaya devam etmelisiniz.  Örneğin, MSA kullanarak Pluralm avantajınızı etkinleştirdiyseniz, abone portalında oturum açmak için kullandığınız kimlikle bağımsız olarak, Pluralm eğitimi alırken MSA 'nizi kullanmaya devam etmelisiniz.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Aboneliğinize erişmek için alternatif bir kimlik kullanın
Visual Studio aboneliğinize alternatif hesap eklemek, aboneliğin atandığı kimlikten farklı bir kimlikle Azure DevOps ve Azure gibi abonelik avantajlarına erişebilmenizi sağlar. Geçmişte, bu işlev yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft hesabına (MSA) atanmışsa kullanılabilir. Azure Active Directory (Azure AD) içinde iş veya okul hesapları için bu işlevselliği genişlettik.  Alternatif hesapları kullanma hakkında daha fazla bilgi için [Alternatif kimlikler](vs-alternate-identity.md) makalemize göz atın. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-how-can-i-contact-my-admin-about-this"></a>S: yöneticime bunun hakkında nasıl iletişim kurabilirim?
A: yöneticinizle iletişim kurma hakkında bilgi edinmek için lütfen [abonelik yöneticinize başvurun](contact-my-admin.md) makalesine bakın.  

### <a name="q-im-an-admin--how-do-i-use-this"></a>S: yöneticiyim.  Nasıl yaparım? bunu kullanmak istiyor musunuz?
Y: bağlı kimlikleri uygulama basittir.  Daha fazla bilgi için [Bu makaleye](personal-email-sign-ins.md) göz atın. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yöneticiniz Azure AD ve MSA hesaplarınızı bağladıktan sonra, [abonelik portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs) başarıyla oturum açabilmeniz ve Azure DevOps, Visual Studio ve Azure DevTest bireysel krediniz gibi erişim avantajlarına sahip olmanız gerektiğini doğrulamanız önerilir.