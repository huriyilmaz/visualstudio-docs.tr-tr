---
title: Visual Studio aboneleri için kimlikler
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Azure DevOps ve Azure için kullanmak üzere Visual Studio aboneliğiniz için alternatif bir kimlik ekleme
ms.openlocfilehash: e19774f2314280b2e5a995a7d83336f1403682a4
ms.sourcegitcommit: bcdab788085bd9931d73883fe70cd5831317dca2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72816551"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio aboneleri için kimlikler
Visual Studio aboneliğinizi etkinleştirdiğinizde, Visual Studio aboneliğiyle etkinleştirme sırasında kullandığınız kimliği (veya oturum açma) bağlayacağız. Bu şekilde, sizi [Visual Studio abone portalı](https://my.visualstudio.com?wt.mc_id=o~msft~docs), Azure DevOps ve Azure 'da tanıyabiliriz.

Azure DevOps 'da, her oturum açışınızda Visual Studio abonelik durumunuzu denetliyoruz ve bir üye olduğunuz her kuruluş içinde size otomatik olarak Özellikler verirsiniz.
Bu özellikler bir abone avantajı olarak eklendiğinden, Visual Studio aboneliğinize bağlı bir kimlik kullanırken sizi herhangi bir Azure DevOps kuruluşunda üye olarak eklemek ücretsizdir.

Azure 'da, abonelik avantajı olan [aylık Azure DevTest kredilerinizi](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) etkinleştirdiğinizde Visual Studio abonelik durumunuzu denetliyoruz.

[Visual Studio abone portalı](https://my.visualstudio.com?wt.mc_id=o~msft~docs)içinde, etkinleştirme sırasında kullandığınız kimliğe ek olarak alternatif bir **kimlik** ekleyebilirsiniz. Aboneliğinizi etkinleştirmek için bir Microsoft hesabı kullandıysanız alternatif bir kimlik eklemenize izin veriyoruz. Bu şekilde, hem kişisel hesabınızı hem de iş ya da okul hesabınızı kullanarak Azure DevOps 'a erişmenize olanak tanıyan bir iş veya okul hesabı (Visual Studio, Office 365 veya şirket veya okul ağınız için oturum açarken kullandığınız) da ekleyebilirsiniz.

## <a name="add-an-alternate-account-to-your-subscription"></a>Aboneliğinize alternatif bir hesap ekleyin
Visual Studio aboneliğinize alternatif bir hesap eklemek, aboneliğin atandığı farklı bir kimlikle Azure DevOps ve Azure gibi abonelik avantajlarına erişmenizi sağlar. Geçmişte, bu işlev yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft hesabına (MSA) atanmışsa kullanılabilir. Azure Active Directory (Azure AD) içinde iş veya okul hesapları için bu işlevselliği genişlettik.

Bu, aboneliğin bir kopyasını diğer hesaba vermez; yalnızca alternatif hesap ile iki avantaja erişme olanağı sağlar.

Tüm abonelikler için bir "iş veya okul hesabı" ekleyebilirsiniz. bu sayede, oturum açma (VS IDE, Azure DevOps ve Azure) gerektiren avantajlarınızla bu hesabı kullanabilirsiniz.

### <a name="add-the-alternate-account"></a>Alternatif hesabı ekleyin
1. Microsoft hesabı (https://my.visualstudio.com) ile Visual Studio abone portalında oturum açın.
2. **Abonelikler** sekmesine tıklayın.
3. **Alternatif hesap ekle**' yi seçin.
4. İş veya okul hesabınızı ekleyin.
    > [!div class="mx-imgBorder"]
    > ![iş veya okul hesabı ekle](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Azure DevOps 'da oturum açmak için iş veya okul hesabınızı kullanın (https://{youraccount}. VisualStudio. com).
    > [!div class="mx-imgBorder"]
    > ![iş veya okul hesabınızı kullanın](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Alternatif hesabınız, Visual Studio aboneliğine eklenir ve her iki kimliğin de Alternatif hesap (IDE, Azure DevOps ve Azure) ile oturum açmanızı gerektiren aboneliğin avantajlarından yararlanmasına olanak tanır.

## <a name="faq"></a>SSS

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>S: Azure DevOps neden bir Visual Studio abonesi olarak beni tanımıyor?

Y: birincil veya alternatif kimliğinizi kullanarak oturum açtığınızda Azure DevOps aboneliğinizi otomatik olarak tanıyabilmelidir. Aksi takdirde, birkaç şeyi deneyebilirsiniz:

* Avantaj olarak [Azure DevOps](vs-azure-devops.md#eligibility) içeren etkin bir Visual Studio aboneliğine sahip olup olmadığınızı kontrol edin.

* Visual Studio aboneliğiniz için birincil ya da alternatif kimlik olan bir oturum açma/kimlik kullandığınızı onaylayın.

* Azure DevOps 'da oturum açmadan önce, [Visual Studio abone portalını](https://my.visualstudio.com?wt.mc_id=o~msft~docs) en az bir kez ziyaret edin.

Azure DevOps hala aboneliğinizi tanımıyorsa [Azure DevOps desteğine](https://azure.microsoft.com/support/devops/)başvurun.
