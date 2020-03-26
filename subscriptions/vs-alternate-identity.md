---
title: Visual Studio aboneleri için kimlikler
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 07/19/2019
ms.topic: conceptual
description: Visual Studio aboneliğiniz için azure devops ve Azure için kullanmak üzere alternatif bir kimlik ekleme
ms.openlocfilehash: ff5166da3cb782c0750b0ce61fdafec375811ff4
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232006"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio aboneleri için kimlikler
Visual Studio aboneliğinizi etkinleştirdiğinizde, etkinleştirme sırasında kullandığınız kimliği (veya girişi) Visual Studio aboneliğiyle birbirine bayıltır. Bu şekilde, sizi Visual [Studio abone portalında,](https://my.visualstudio.com?wt.mc_id=o~msft~docs)Azure DevOps'lerde ve Azure'da tanıyabiliriz.

Azure DevOps'te, her oturum açtığınızda Visual Studio abonelik durumunuzu kontrol ediyoruz ve üye olduğunuz her kuruluşta size otomatik olarak özellikler veririz.
Bu özellikler bir abone avantajı olarak dahil edildiğinden, Visual Studio aboneliğinize bağlı bir kimlik kullanırken sizi herhangi bir Azure DevOps kuruluşuna üye olarak eklemek ücretsizdir.

Azure'da, abone avantajı olan [aylık Azure DevTest bireysel kredinizi](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) etkinleştirdiğinizde Visual Studio abonelik durumunuzu kontrol ediyoruz.

Visual [Studio abone portalında,](https://my.visualstudio.com?wt.mc_id=o~msft~docs)etkinleştirme sırasında kullandığınız kimliğe ek olarak alternatif bir **kimlik** ekleyebilirsiniz. Aboneliğinizi etkinleştirmek için bir Microsoft hesabı kullandıysanız, alternatif bir kimlik eklemenize izin veririz. Bu şekilde, hem kişisel hesabınızı hem de iş veya okul hesabınızı kullanarak Azure DevOps'lere erişmenize olanak tanıyan bir iş veya okul hesabı (Visual Studio, Office 365 veya şirket veya okul ağınızda oturum açarken kullandığınız) ekleyebilirsiniz.

## <a name="add-an-alternate-account-to-your-subscription"></a>Aboneliğinize alternatif bir hesap ekleme
Visual Studio aboneliğinize alternatif bir hesap eklemek, Azure DevOps ve Azure gibi abonelik avantajlarına aboneliğin atandığı hesaptan farklı bir kimliğe sahip olarak erişmenizi sağlar. Geçmişte bu işlev, yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft Hesabına (MSA) atanmışsa kullanılabilirdi. Bu işlevselliği Azure Etkin Dizini'ndeki (Azure AD) iş veya okul hesapları için genişlettik.

Bu, diğer hesaba abonelik bir kopyasını sağlamaz; yalnızca alternatif hesapla iki avantaja erişebilme olanağı sağlar.

Tüm abonelikler için bir "iş veya okul hesabı" ekleyebilirsiniz, böylece bu hesabı giriş gerektiren avantajlarınızla (VS IDE, Azure DevOps ve Azure) kullanabilirsiniz.

### <a name="add-the-alternate-account"></a>Alternatif hesap ekleme
1. Microsoft hesabınızla Visual Studio abone portalındahttps://my.visualstudio.com)oturum açın ( .
2. **Abonelikler** sekmesine tıklayın.
3. **Alternatif hesap ekle'yi**seçin.
4. İş inizi veya okul hesabınızı ekleyin.
    > [!div class="mx-imgBorder"]
    > ![İş veya okul hesabı ekleme](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Azure DevOps'te oturum açabilmek için iş veya okul hesabınızı kullanın (https://{youraccount}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![İş veya okul hesabınızı kullanma](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Alternatif hesabınız Visual Studio aboneliğine eklenir ve her iki kimliğin de alternatif hesapla (IDE, Azure DevOps ve Azure) oturum açmanızı gerektiren aboneliğin avantajlarından yararlanmasını sağlar.

## <a name="faq"></a>SSS

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>S: Azure DevOps beni neden Visual Studio abonesi olarak tanımıyor?

C: Azure DevOps, birincil veya alternatif kimliğinizi kullanarak oturum açtığınızda aboneliğinizi otomatik olarak tanımalıdır. Değilse, birkaç şey deneyebilirsiniz:

* Avantaj olarak [Azure DevOps'leri](vs-azure-devops.md#eligibility) içeren etkin bir Visual Studio aboneliğiniz olup olmadığını kontrol edin.

* Visual Studio aboneliğiniz için birincil veya alternatif kimlik olan bir giriş/kimlik kullandığınızı doğrulayın.

* Azure DevOps'te oturum açmadan önce en az bir kez [Visual Studio abone portalını](https://my.visualstudio.com?wt.mc_id=o~msft~docs) ziyaret edin.

Azure DevOps aboneliğinizi hala tanımıyorsa, [Azure DevOps desteğine](https://azure.microsoft.com/support/devops/)başvurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar 
Azure, Azure DevOps veya Visual Studio IDE kullanma hakkında daha fazla bilgi için şu kaynaklara göz atın:
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)