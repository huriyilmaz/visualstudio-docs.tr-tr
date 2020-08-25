---
title: Visual Studio aboneleri için kimlikler
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 07/19/2019
ms.topic: conceptual
description: Azure DevOps ve Azure için kullanmak üzere Visual Studio aboneliğiniz için alternatif bir kimlik ekleme
ms.openlocfilehash: 0e19bff8885810e505dbe6481340e7a112160af0
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800781"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio aboneleri için kimlikler
Visual Studio aboneliğinizi etkinleştirdiğinizde, Visual Studio aboneliğiyle etkinleştirme sırasında kullandığınız kimliği (veya oturum açma) bağlayacağız. Bu şekilde, sizi [Visual Studio abone portalı](https://my.visualstudio.com?wt.mc_id=o~msft~docs), Azure DevOps ve Azure 'da tanıyabiliriz.

Azure DevOps 'da, her oturum açışınızda Visual Studio abonelik durumunuzu denetliyoruz ve bir üye olduğunuz her kuruluş içinde size otomatik olarak Özellikler verirsiniz.
Bu özellikler bir abone avantajı olarak eklendiğinden, Visual Studio aboneliğinize bağlı bir kimlik kullanırken sizi herhangi bir Azure DevOps kuruluşunda üye olarak eklemek ücretsizdir.

Azure 'da, abonelik avantajı olan [aylık Azure DevTest kredilerinizi](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) etkinleştirdiğinizde Visual Studio abonelik durumunuzu denetliyoruz.

[Visual Studio abone portalı](https://my.visualstudio.com?wt.mc_id=o~msft~docs)içinde, etkinleştirme sırasında kullandığınız kimliğe ek olarak alternatif bir **kimlik** ekleyebilirsiniz. Aboneliğinizi etkinleştirmek için bir Microsoft hesabı kullandıysanız alternatif bir kimlik eklemenize izin veriyoruz. Bu şekilde, hem kişisel hesabınızı hem de iş veya okul hesabınızı kullanarak Azure DevOps 'a erişmenizi sağlayan bir iş veya okul hesabı (Visual Studio 'da, Microsoft 365 veya şirket veya okul ağınız için oturum açarken kullanabilirsiniz) ekleyebilirsiniz.

## <a name="add-an-alternate-account-to-your-subscription"></a>Aboneliğinize alternatif bir hesap ekleyin
Visual Studio aboneliğinize alternatif hesap eklemek, aboneliğin atandığı kimlikten farklı bir kimlikle Azure DevOps ve Azure gibi abonelik avantajlarına erişebilmenizi sağlar. Geçmişte, bu işlev yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft hesabına (MSA) atanmışsa kullanılabilir. Azure Active Directory (Azure AD) içinde iş veya okul hesapları için bu işlevselliği genişlettik.

Bu yolla diğer hesaba aboneliğin bir kopyası sağlanmaz; yalnızca alternatif hesapla iki avantaja erişim olanağı sağlar.

Tüm abonelikler için bir "iş veya okul hesabı" ekleyebilirsiniz. bu sayede, oturum açma (VS IDE, Azure DevOps ve Azure) gerektiren avantajlarınızla bu hesabı kullanabilirsiniz.

### <a name="add-the-alternate-account"></a>Alternatif hesabı ekleyin
1. Visual Studio abone portalında Microsoft hesabı ile oturum açın ( https://my.visualstudio.com) .
2. **Abonelikler** sekmesini seçin.
3. **Alternatif hesap ekle**' yi seçin.
4. İş veya okul hesabınızı ekleyin.
    > [!div class="mx-imgBorder"]
    > ![İş veya okul hesabı ekle](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Azure DevOps 'da oturum açmak için iş veya okul hesabınızı kullanın (https://{youraccount}. VisualStudio. com).

Alternatif hesabınız, Visual Studio aboneliğine eklenir ve her iki kimliğin de Alternatif hesap (IDE, Azure DevOps ve Azure) ile oturum açmanızı gerektiren aboneliğin avantajlarından yararlanmasına olanak tanır.

## <a name="faq"></a>SSS

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>S: Azure DevOps neden bir Visual Studio abonesi olarak beni tanımıyor?

Y: birincil veya alternatif kimliğinizi kullanarak oturum açtığınızda Azure DevOps aboneliğinizi otomatik olarak tanıyabilmelidir. Aksi takdirde, birkaç şeyi deneyebilirsiniz:

* Avantaj olarak [Azure DevOps](vs-azure-devops.md#eligibility) içeren etkin bir Visual Studio aboneliğine sahip olup olmadığınızı kontrol edin.

* Visual Studio aboneliğiniz için birincil ya da alternatif kimlik olan bir oturum açma/kimlik kullandığınızı onaylayın.

* Azure DevOps 'da oturum açmadan önce, [Visual Studio abone portalını](https://my.visualstudio.com?wt.mc_id=o~msft~docs) en az bir kez ziyaret edin.

Azure DevOps hala aboneliğinizi tanımıyorsa [Azure DevOps desteğine](https://azure.microsoft.com/support/devops/)başvurun.

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