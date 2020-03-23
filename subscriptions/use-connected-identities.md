---
title: Bağlı Microsoft hesabı ve Azure Active Directory kimlikleri nasıl kullanılır | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Bağlı Microsoft hesapları ve Azure Etkin Dizin kimlikleri ile nasıl çalışacağınızı öğrenin
ms.openlocfilehash: 3dcb41a26f27e5135962edf7ff933de40ccefe5e
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508985"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde bağlı kimlikler nasıl kullanılır?
İşinizden veya okulunuzun aracılığıyla bir Visual Studio aboneliği alırsanız ve oturum açmak için Microsoft hesabınızı (MSA) kullanırsanız, abonelik yöneticiniz MSA'nızı kuruluşunuzun Azure Etkin Dizini'nde (Azure AD) kimliğinize bağlayabilir.  Bu, aboneliğinizde yer alan bazı avantajlara nasıl erişeceğiniz değişir. 

## <a name="overview-of-connected-ids"></a>Bağlı t.c.'lere genel bakış
Kuruluşlar, aboneliklerin otomatik yönetimi için gelişmiş güvenlik ve destek sağlamak için Azure AD tabanlı kimliklere giderek daha fazla geçiyor.  Aboneliğiniz veya başka bir kişisel @outlook.com e-posta adresi gibi bir MSA kullanıyorsa, yöneticiniz oturum açma e-postanızı Azure AD kimliğinizle değiştirebilir.  Bu, abone portalında oturum açma şeklinizi değiştirir, https://my.visualstudio.com ancak tüm avantajlarınıza nasıl erişeceğiniz değiştirilemez.  

Yöneticiniz MSA ve Azure AD kimliklerinizi bağlarsa, Visual Studio aboneliğinize MSA'nız yerine Azure AD kimliğinizle erişmeye başlamanızı sağlayan bir e-posta alırsınız. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Azure AD kimliklerini kullanarak avantajlara nasıl erişilir?
Yöneticiniz MSA'nızı Azure AD kimliğinize bağladıktan sonra, Azure AD kimliğinize https://my.visualstudio.com dayanan avantajlara erişmek için Azure AD kimliğinizle abone portalında oturum açmanız gerekir.  Bunlar:
- Visual Studio IDE
- Azure DevOps
- Azure DevTest bireysel kredisi

## <a name="how-to-access-benefits-using-your-msa"></a>MSA'nızı kullanarak avantajlara nasıl erişilir?
Pluralsight, LinkedIn, CloudPilot ve diğerleri gibi Visual Studio aboneliklerinde sunulan avantajların çoğu için, aslında ortakların web sitelerinde kullanıcı hesapları oluşturursunuz.  Bu hesaplar için, hesabı oluşturduğunuzda kullandığınız kimliği kullanmaya devam etmelisiniz.  Örneğin, MSA'nızı kullanarak Pluralsight avantajınızı etkinleştirdilerseniz, abone portalında oturum açtığınızda kullandığınız kimlikten bağımsız olarak Çoğul görüş eğitimini alırken MSA'nızı kullanmaya devam etmelisiniz.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Aboneliğinize erişmek için alternatif bir kimlik kullanma
Visual Studio aboneliğinize alternatif bir hesap eklemek, Azure DevOps ve Azure gibi abonelik avantajlarına aboneliğin atandığı hesaptan farklı bir kimliğe sahip olarak erişmenizi sağlar. Geçmişte bu işlev, yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft Hesabına (MSA) atanmışsa kullanılabilirdi. Bu işlevselliği Azure Etkin Dizini'ndeki (Azure AD) iş veya okul hesapları için genişlettik.  Alternatif hesap kullanma hakkında daha fazla bilgi için [Alternatif Kimlikler](vs-alternate-identity.md) makalemize göz atın. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-how-can-i-contact-my-admin-about-this"></a>S: Bu konuda yöneticime nasıl başvurabilirim?
C: [Yöneticinizle](contact-my-admin.md) iletişim kurma hakkında bilgi için lütfen abonelik yöneticiniz ile iletişime geçin.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yöneticiniz Azure AD ve MSA hesaplarınızı bağladıktan sonra, [abonelik portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs) başarılı bir şekilde oturum açabileceğinizi ve Azure DevOps, Visual Studio ve Azure DevTest bireysel krediniz gibi avantajlara erişebileceğinizi doğrulamanızı öneririz. 