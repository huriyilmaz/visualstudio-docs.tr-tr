---
title: GitHub Enterprise ile Visual Studio abonelikleri atama | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: GitHub Enterprise ile Visual Studio aboneliklerinde abonelikleri yönetme
ms.openlocfilehash: d1734e3f416815b9c63f7237eca4e7df26e34331
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159581"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>GitHub Enterprise ile Visual Studio aboneliklerini yönetme
Microsoft ile kurumsal anlaşma (EA) olan müşteriler, Visual Studio Standard abonelikleri ve GitHub Enterprise 'ı birlikte getiren yeni bir abonelik teklifi satın almaya uygundur. Visual Studio abonelerinin GitHub Enterprise 'ı edinmenin kolay ve ekonomik bir yoludur. 

Kuruluşunuz GitHub Enterprise ile Visual Studio abonelikleri satın aldığında, bunlar iki bölümden sağlanır ve yönetilir.

## <a name="manage-visual-studio-subscriptions"></a>Visual Studio aboneliklerini yönetme
Kuruluşunuz GitHub Enterprise ile Visual Studio abonelikleri satın aldığında, aboneliklerin Visual Studio bölümü hemen sağlanır ve abonelikler Visual Studio [abonelikleri yönetim](https://manage.visualstudio.com) portalı 'nda atama ve yönetim için kullanılabilir. GitHub Enterprise ile bir Visual Studio aboneliği atadıktan sonra, abone tarafından Visual Studio aboneliğine erişebilecek bir e-posta gönderilir <https://my.visualstudio.com/subscriptions> .

Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi için şu konulara bakın:
- [Yönetici portalını kullanma](using-admin-portal.md)
- [Abonelik atama](assign-license.md)
- [Abonelikleri Düzenle](edit-license.md)
- [Abonelikleri Sil](delete-license.md)
- [Fazla Yüklemeler](handle-overclaimed-license.md)

> [!Important]
> GitHub Enterprise ile Visual Studio abonelikleri, ilk satın almadan Visual Studio abonelik yöneticileri tarafından atanırsa, GitHub kurumsal hesabı oluşturmak istediğinizi hiçbir uyarı verilmez.  **En az bir satın alma** GitHub Enterprise ile Visual Studio aboneliği, abonelikler atanmadan önce yapılmalıdır.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>GitHub Enterprise ile Visual Studio 'ya geçme
Kuruluşunuz standart Visual Studio Enterprise sonrasında GitHub kurumsal paketleri ile Visual Studio abonelikleri satın alıyorsa ve Visual Studio Professional abonelikler atandıktan sonra, Yönetici portalı mevcut abonelerinizin GitHub Enterprise ve/veya GitHub Enterprise abonelikleriyle Visual Studio Professional ilgili Visual Studio Enterprise taşımanıza yardımcı olacak bir özellik içerir.  Örneğin, Visual Studio Professional abonelikleri olan aboneler, GitHub Enterprise abonelikleri ile Visual Studio Professional ' ye taşınır. Sol çubukta "genel bakış" panelinde aşağıdaki kutucuğu görürsünüz:

   > [!div class="mx-imgBorder"]
   > ![Şimdi Taşı düğmesi](_img/assign-github/move-now.png "GitHub Enterprise abonelikleriyle abonelikleri Visual Studio 'ya yükseltmek için ' Şimdi taşı ' düğmesine tıklayın")

> [!IMPORTANT]
> Yukarıda belirtildiği gibi, mevcut abone verileri, geçmişi ve abonelik KIMLIĞI korunur ve etkinleştirildikleri avantajlar bu taşıma nedeniyle kesilmeyecektir.  
>
> Bu özellik evreler halinde dağıtılıyor ve sözleşmenizde hemen kullanılamayabilir.

**Şimdi taşı** düğmesine tıkladığınızda, kurumsal ve/veya profesyonel aboneliklerinizi taşımaya yönelik önerilerle birlikte bir anında çalışma paneli görüntülenir:

   > [!div class="mx-imgBorder"]
   > ![Uçarak çıkış paneli](_img/assign-github/fly-out.png)

Bu kutucukta etkilenen aboneleri gözden geçirebilir ve taşıma tamamlandıktan sonra onlara bir e-posta bildirimi almasını isteyip istemediğinizi belirtebilirsiniz.  Bu e-posta, abonelere avantajları olduğunu bildirir ve bu kişilerin GitHub 'da bir varlık ayarlamaya başlamasını önerir.  

**Tüm aboneleri taşı** düğmesine tıkladıktan sonra, seçimlerinizi onaylanır ve abonelik taşıması tamamlanana kadar birkaç saniye beklemeniz gerekir.  Uygulanabiliyorsa, bu adımları profesyonel ve kurumsal için ayrı olarak gerçekleştirmeniz gerekecektir.  


## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>GitHub Enterprise ile Visual Studio kurulum işlemi nasıldır?
GitHub Enterprise, Visual Studio aboneliklerinden ayrı olarak kurulur ve yönetilir. GitHub Kurumsal satın alma ile bir Visual Studio aboneliğini takip eden bir GitHub kurumsal hesap kurulum işlemi, [Manage.VisualStudio.com](https://manage.visualstudio.com)içinde bir sözleşme oluşturma ile paralel olarak başlatılır (ancak birbirinden farklıdır). Bu GitHub Enterprise hesabının oluşturulması biraz zaman alabilir. 

Şirketiniz GitHub Enterprise hesabını ayarladıktan sonra, kendilerine GitHub Enterprise ile Visual Studio abonelikleri atanan aboneler GitHub'dan Visual Studio aboneliklerinin bağlandığını bildiren bir e-posta alır. Aboneler bu e-postayı aldıktan sonra, uygun kuruluşa davetiye almak için GitHub kuruluş yöneticilerine ulaşabilirler.

GitHub Enterprise kurulumuna ilişkin ayrıntılar için lütfen [abone belgelerine](access-github.md)başvurun.   

## <a name="manage-github-enterprise-subscriptions"></a>GitHub Enterprise aboneliklerini yönetme
GitHub Enterprise abonelikleri satın alındığında, GitHub 'a erişecek ve yöneticileri tanımlayan kuruluşları oluşturmaya ve yapılandırmaya yardımcı olacak şekilde GitHub iş ortakları.  Bu Yöneticiler daha sonra yöneticiler olarak ayarlandıklarından bir bildirim alır.  

Bu işlem daha karmaşık olduğundan, kuruluşların ve yöneticilerin tam olarak ayarlanması için abonelikler satın alındıktan sonra birkaç gün sürebilir.

GitHub, bulut tabanlı GitHub.com ya da şirket içi GitHub Enterprise Server olarak kullanılabilir.  İki sürümü yönetmek için süreçler farklılık gösterir.  GitHub, GitHub Enterprise aboneliklerini yönetmenize yardımcı olmak için çeşitli yardım konuları ve yönetici kılavuzlarını sağlar.  Aşağıdaki seçili konulara bağlantılar sağladık.  

## <a name="support-resources"></a>Destek kaynakları

- [GitHub belgelerinden](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle) GitHub ataması hakkında daha fazla bilgi edinin
- [GitHub yardımı](https://help.github.com/en)'nda çok çeşitli GitHub konuları dizisiyle ilgili soruların yanıtlarını bulun.
- [GitHub topluluk forumundaki](https://github.community/)diğer GitHub kullanıcılarından yardım alın.
- Visual Studio abonelikleri için Sales, abonelikler, hesaplar ve faturalandırma konusunda yardım için [Visual Studio yönetim ve abonelik desteğiyle](https://my.visualstudio.com/gethelp)görüşün.
- Visual Studio IDE, Azure DevOps Services veya diğer Visual Studio ürünleri veya hizmetleri hakkında sorularınız mı var?  [Visual Studio desteği](https://visualstudio.microsoft.com/support/)' ni ziyaret edin.
- GitHub Enterprise için [Teknik destek](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) alın.   

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)

Visual Studio aboneliklerini GitHub Enterprise ile yönetme hakkında daha fazla bilgi için Visual Studio [abonelikleri Yönetici portalı](https://visualstudio.microsoft.com/subscriptions-administration/)' na göz atın.