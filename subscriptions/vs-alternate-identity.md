---
title: Aboneler için Visual Studio kimlikler
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 10/14/2021
ms.topic: conceptual
description: Visual Studio ve Azure için Azure DevOps aboneliğinize alternatif kimlik ekleme
ms.openlocfilehash: 6964c5c2b6e1c63e067958bbeb1c05ce5ca7573d
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133256145"
---
# <a name="identities-for-visual-studio-subscribers"></a>Aboneler için Visual Studio kimlikler
Visual Studio aboneliğinizi Visual Studio etkinleştirme sırasında kullanılan kimliği (veya oturum açma bilgilerini) Visual Studio sağlarız. Bu şekilde, sizi Visual Studio [portalında,](https://my.visualstudio.com?wt.mc_id=o~msft~docs)Azure DevOps Azure'da tanıyabilirsiniz.

Bu Azure DevOps her oturum Visual Studio aboneliğinizin durumunu kontrol eder ve size üye olduğunuz her kuruluşta otomatik olarak özellikler sağlarsınız.
Bu özellikler abone avantajı olarak dahil olduğundan, Visual Studio aboneliğinize bağlı bir kimlik kullanırken sizi herhangi bir Azure DevOps kuruluşunda üye olarak eklemek ücretsizdir.

Azure'da, abone Visual Studio olan aylık Azure [DevTest](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) bireysel kredinizi etkinleştirebilirsiniz.

Bu [Visual Studio portalında,](https://my.visualstudio.com?wt.mc_id=o~msft~docs)etkinleştirme sırasında kullanılan kimliğe  ek olarak alternatif bir kimlik de ekleyebilirsiniz. Aboneliğinizi etkinleştirmek için bir Microsoft hesabı kimlik eklemenize olanak sağlar. Bu şekilde bir iş veya okul hesabı (Visual Studio, Microsoft 365 veya şirket ya da okul ağınız ile oturum asanız) kullanarak hem kişisel hesabınızla hem de iş ya da okul hesabınızla Azure DevOps'a erişmenize olanak sağlar.

## <a name="add-an-alternate-account-to-your-subscription"></a>Aboneliğinize alternatif bir hesap ekleme
Visual Studio aboneliğinize alternatif bir hesap eklemek, Azure DevOps ve Azure gibi belirli abonelik avantajlarına erişmenizi veya Visual Studio IDE'de aboneliğin atandığı kimlikten farklı bir kimlikle oturum açmanızı sağlar. Geçmişte bu işlev yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft Hesabına (MSA) atanmışsa kullanılabilirdi. Azure AD'de iş veya okul hesapları için bu Azure Active Directory genişletildi.

> [!NOTE]
> Alternatif kimlik yalnızca bu ikinci kimliği kullanarak Azure kredilerini ve Azure DevOps etkinleştirmenizi ve Visual Studio IDE'de oturum açmasını sağlar.  üzerinden abonelik portalında oturum açma için <https://my.visualstudio.com> kullanılamaz.  Yine de aboneliğin atandığı kimliği kullanarak portalda oturum açmanız gerekir. 

Tüm abonelikler için bir "iş veya okul hesabı" ekleyebilir, böylece bu hesabı oturum açma gerektiren avantajlarınız (VS IDE, Azure DevOps ve Azure) ile kullanabilirsiniz.

### <a name="add-the-alternate-account"></a>Alternatif hesabı ekleme
1. Microsoft hesabı () ile Visual Studio portalında oturum https://my.visualstudio.com) açın.
2. Abonelikler **sekmesini** seçin.
3. Alternatif **hesap ekle'yi seçin.**
4. İş veya okul hesabı ekleyin.
    > [!div class="mx-imgBorder"]
    > ![İş veya okul hesabı ekleme](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png "Aboneliğinize alternatif bir hesap olarak iş veya okul hesabı ekleme.")

5. Azure DevOps'de (https://{hesabınız}.visualstudio.com) oturum açması için iş veya okul visualstudio.com.

Alternatif hesabınız Visual Studio aboneliğine eklenir ve her iki kimliğin de alternatif hesapla (IDE, Azure DevOps ve Azure) oturum açmanızı gerektiren aboneliğin avantajlarından yararlanmasına olanak sağlar.

## <a name="faq"></a>SSS

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>S: Neden Azure DevOps abone olarak Visual Studio tanımıyor?

A: Azure DevOps veya alternatif kimliğinizi kullanarak oturum asanız aboneliğinizi otomatik olarak tanımanız gerekir. Tanımıyorsa birkaç şey deneyebilirsiniz:

* Avantaj olarak Visual Studio aboneliğinizin [olup](vs-azure-devops.md#eligibility) Azure DevOps olun.

* Abonelik aboneliğiniz için birincil veya alternatif kimlik olan bir oturum açma/kimlik Visual Studio onaylayın.  Örneğin birçok kişinin farklı bir oturum açma kimliğiyle Visual Studio Dev Essentials bir oturum açma üyeliği de vardır.  Bu abonelikler bu e-posta adresiyle ilişkili olmadığı sürece bu kimlikle diğer aboneliklerde oturum açma denemesi başarısız olur.

* Portalda [Visual Studio oturum açmadan](https://my.visualstudio.com?wt.mc_id=o~msft~docs) önce en az bir kez Azure DevOps.

Aboneliğinizi Azure DevOps tanımazsanız destek için Azure DevOps [başvurun.](https://azure.microsoft.com/support/devops/)

## <a name="resources"></a>Kaynaklar
[Visual Studio abonelik desteği](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar 
Azure, IDE veya IDE Azure DevOps Visual Studio daha fazla bilgi için şu kaynaklara göz atabilirsiniz:
- [Azure DevTest teklifi/kredileri](/azure/devtest/offer/)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)