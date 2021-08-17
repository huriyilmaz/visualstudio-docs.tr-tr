---
title: Visual Studio aboneleri için kimlikler
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 86f2856c-8adf-4085-9962-f4136679e5ed
ms.date: 02/19/2021
ms.topic: conceptual
description: Azure DevOps ve Azure için kullanmak üzere Visual Studio aboneliğiniz için alternatif bir kimlik ekleme
ms.openlocfilehash: ef182fa299f79be7883f8d369cc717c96dcb36ce2cfb601b992fdb8fe919567c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121392895"
---
# <a name="identities-for-visual-studio-subscribers"></a>Visual Studio aboneleri için kimlikler
Visual Studio aboneliğinizi etkinleştirdiğinizde, etkinleştirme sırasında kullandığınız kimliği (veya oturum açma) Visual Studio abonelikle bağlantılandırtık. bu şekilde, sizi [Visual Studio abone portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs), Azure DevOps ve Azure 'da tanıyabiliriz.

Azure DevOps, her oturum açışınızda Visual Studio abonelik durumunuzu denetliyoruz ve bir üye olduğunuz her kuruluş içinde size otomatik olarak özellikler verirsiniz.
bu özellikler bir abone avantajı olarak eklendiğinden, Visual Studio aboneliğinize bağlı bir kimlik kullandığınızda sizi herhangi bir Azure DevOps kuruluşunda üye olarak eklemek ücretsizdir.

azure 'da, abone avantajı olan [aylık Azure devtest kredilerinizi](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) etkinleştirdiğinizde Visual Studio abonelik durumunuzu denetliyoruz.

[Visual Studio abone portalı](https://my.visualstudio.com?wt.mc_id=o~msft~docs)içinde, etkinleştirme sırasında kullandığınız kimliğe ek olarak alternatif bir **kimlik** ekleyebilirsiniz. Aboneliğinizi etkinleştirmek için bir Microsoft hesabı kullandıysanız alternatif bir kimlik eklemenize izin veriyoruz. bu şekilde, hem kişisel hesabınızı hem de iş veya okul hesabınızı kullanarak Azure DevOps erişmenize izin veren bir iş veya okul hesabı (Visual Studio, Microsoft 365 veya şirket veya okul ağınıza oturum açarken kullandığınız) ekleyebilirsiniz.

## <a name="add-an-alternate-account-to-your-subscription"></a>Aboneliğinize alternatif bir hesap ekleyin
Visual Studio aboneliğinize alternatif bir hesap eklemek, Azure DevOps ve Azure gibi belirli abonelik avantajlarına erişmenize veya Visual Studio ıde 'de aboneliğin atandığı farklı bir kimlikle oturum açmanıza olanak tanır. geçmişte, bu işlev yalnızca Visual Studio (VS) aboneliğiniz bir Microsoft hesabına (MSA) atanmışsa kullanılabilir. Azure Active Directory (Azure AD) içinde iş veya okul hesapları için bu işlevselliği genişlettik.

> [!NOTE]
> alternatif kimlik yalnızca Azure kredilerini etkinleştirmek ve Azure DevOps ve Visual Studio ıde 'de oturum açmak için bu ikinci kimliği kullanmanıza izin verir.  Bu, konumundaki abonelik portalında oturum açmak için kullanılamaz <https://my.visualstudio.com> .  Hala portalda oturum açmak için aboneliğin atandığı KIMLIĞI kullanmanız gerekir. 

tüm abonelikler için bir "iş veya okul hesabı" ekleyebilirsiniz. bu sayede, bu hesabı oturum açma gerektiren avantajlarınızla (VS ıde, Azure DevOps ve Azure) kullanabilirsiniz.

### <a name="add-the-alternate-account"></a>Alternatif hesabı ekleyin
1. Visual Studio abone portalında Microsoft hesabı ile oturum açın ( https://my.visualstudio.com) .
2. **Abonelikler** sekmesini seçin.
3. **Alternatif hesap ekle**' yi seçin.
4. İş veya okul hesabınızı ekleyin.
    > [!div class="mx-imgBorder"]
    > ![İş veya okul hesabı ekle](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png "Aboneliğinize alternatif bir hesap olarak iş veya okul hesabı ekleme.")

5. Azure DevOps oturum açmak için iş veya okul hesabınızı kullanın (https://{youraccount}. visualstudio. com).

alternatif hesabınız Visual Studio aboneliğine eklenerek, her iki kimliğin da diğer hesap (ıde, Azure DevOps ve Azure) ile oturum açmanızı gerektiren aboneliğin avantajlarından yararlanmasına olanak tanır.

## <a name="faq"></a>SSS

### <a name="q--why-doesnt-azure-devops-recognize-me-as-a-visual-studio-subscriber"></a>s: neden Azure DevOps beni Visual Studio abonesi olarak tanımıyor?

y: birincil veya alternatif kimliğinizi kullanarak oturum açtığınızda Azure DevOps aboneliğinizi otomatik olarak tanıyabilmelidir. Tanımıyorsa birkaç şey deneyebilirsiniz:

* avantaj olarak [Azure DevOps](vs-azure-devops.md#eligibility) içeren etkin bir Visual Studio aboneliğine sahip olup olmadığınızı kontrol edin.

* Visual Studio aboneliğiniz için birincil ya da alternatif kimlik olan bir oturum açma/kimlik kullandığınızı onaylayın.

* Azure DevOps oturum açmadan önce [Visual Studio abone portalını](https://my.visualstudio.com?wt.mc_id=o~msft~docs) en az bir kez ziyaret edin.

aboneliğinizi hala tanımıyorsa, [Azure DevOps desteğe](https://azure.microsoft.com/support/devops/)başvurun. Azure DevOps

## <a name="resources"></a>Kaynaklar
[Visual Studio abonelik desteği](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar 
Azure 'u Azure DevOps veya Visual Studio ıde 'yi kullanma hakkında daha fazla bilgi için şu kaynaklara göz atın:
- [Azure](vs-azure.md)
- [Azure DevOps](vs-azure-devops.md)
- [Visual Studio](vs-ide-benefit.md)