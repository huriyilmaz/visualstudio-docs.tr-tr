---
title: GitHub Enterprise ile Visual Studio abonelikleri atama | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/03/2021
ms.topic: conceptual
description: GitHub Visual Studio aboneliklerinde abonelikleri yönetme Enterprise
ms.openlocfilehash: b01baba84b0c75b5986ff82221ee915cf7b3f6fc
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428101"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>GitHub Enterprise Visual Studio abonelikleri yönetme
Microsoft ile Enterprise sözleşmeleri (EA) olan müşteriler, standart abonelikler ve GitHub Enterprise Visual Studio bir araya getiren yeni bir abonelik teklifi satın almaya uygundur. Visual Studio abonelerin GitHub Enterprise edinmek için kolay ve ekonomik bir yoldur. 

kuruluşunuz GitHub Enterprise sahip Visual Studio abonelikleri satın aldığında, bunlar iki bölümden sağlanır ve yönetilir.

## <a name="manage-visual-studio-subscriptions"></a>Visual Studio aboneliklerini yönetme
kuruluşunuz GitHub Enterprise sahip Visual Studio abonelikleri satın aldığında, aboneliklerin Visual Studio kısmı hemen sağlanır ve abonelikler, Visual Studio [abonelikler yönetiminde](https://manage.visualstudio.com) atama ve yönetim için kullanılabilir. Portal. GitHub Enterprise sahip bir Visual Studio aboneliği atadıktan sonra, abone bu kişilerin Visual Studio aboneliğine erişebileceğini bildiren bir e-posta alır <https://my.visualstudio.com/subscriptions> .

Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi için şu konulara bakın:
- [Yönetici portalını kullanma](using-admin-portal.md)
- [Abonelik atama](assign-license.md)
- [Abonelikleri Düzenle](edit-license.md)
- [Abonelikleri Sil](delete-license.md)
- [Fazla Yüklemeler](handle-overclaimed-license.md)

> [!Important]
> GitHub Enterprise sahip Visual Studio abonelikler önce satın almadan Visual Studio abonelik yöneticileri tarafından atanırsa, GitHub GitHub bir hesap oluşturmak istediğinizi bildirmeyecektir.  abonelikler atanmadan önce GitHub Enterprise ile **en az bir** Visual Studio aboneliğinin satın alınması gerekir.

## <a name="moving-to-visual-studio-with-github-enterprise"></a>GitHub Enterprise Visual Studio taşıma
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWEAsv]

kuruluşunuz standart Visual Studio Enterprise ve Visual Studio Professional abonelikler atandıktan sonra GitHub Enterprise paketleriyle Visual Studio abonelikleri satın alıyorsa, yönetim portalı yardım için bir özellik içerir mevcut abonelerinizin GitHub Enterprise ve/veya Visual Studio Professional GitHub Enterprise abonelikleriyle ilgili Visual Studio Enterprise taşıyın.  örneğin, Visual Studio Professional aboneliklerine sahip aboneler GitHub Enterprise abonelikleriyle Visual Studio Professional geçer. Sol çubukta "genel bakış" panelinde aşağıdaki kutucuğu görürsünüz:

   > [!div class="mx-imgBorder"]
   > ![Şimdi Taşı düğmesi](_img/assign-github/move-now.png "abonelikleri GitHub Enterprise abonelikleriyle Visual Studio yükseltmek için ' şimdi taşı ' düğmesine tıklayın")

> [!IMPORTANT]
> Yukarıda belirtildiği gibi, mevcut abone verileri, geçmişi ve abonelik KIMLIĞI korunur ve etkinleştirildikleri avantajlar bu taşıma nedeniyle kesilmeyecektir.  


**şimdi taşı** düğmesine tıkladığınızda, Enterprise ve/veya Professional aboneliklerinizi taşımaya yönelik önerilerle bir anında çıkış paneli sunulacaktır:

   > [!div class="mx-imgBorder"]
   > ![Uçarak çıkış paneli](_img/assign-github/fly-out.png)

Bu kutucukta etkilenen aboneleri gözden geçirebilir ve taşıma tamamlandıktan sonra onlara bir e-posta bildirimi almasını isteyip istemediğinizi belirtebilirsiniz.  Bu e-posta, abonelere avantajları olduğunu bildirir ve GitHub bir varlığı ayarlamaya başlamalarını teşvik eder.  

 **Abone taşı**   düğmesine tıklamak, önerilen tüm aboneleri taşımanızı veya bir listeden bireyler seçmenizi sağlayacak.  Seçimlerinizi onayladıktan sonra, aboneliğin tamamlanması birkaç saniye sürer. uygulanabiliyorsa, bu adımları Professional ve Enterprise ayrı olarak gerçekleştirmeniz gerekir.  

## <a name="what-is-the-visual-studio-with-github-enterprise-setup-process"></a>GitHub Enterprise ile Visual Studio kurulum işlemi nasıldır?
GitHub Enterprise, Visual Studio aboneliklerinden ayrı olarak kurulur ve yönetilir. GitHub Enterprise satın alma ile Visual Studio aboneliğini takip eden bir GitHub Enterprise hesabı kurulum işlemi, [manage.visualstudio.com](https://manage.visualstudio.com)içinde bir sözleşme oluşturma ile paralel olarak başlatılır. Bu GitHub Enterprise hesabının oluşturulması biraz zaman alabilir. 

Şirketiniz GitHub Enterprise hesabını ayarladıktan sonra, kendilerine GitHub Enterprise ile Visual Studio abonelikleri atanan aboneler GitHub'dan Visual Studio aboneliklerinin bağlandığını bildiren bir e-posta alır. aboneler bu e-postayı aldıktan sonra, uygun kuruluşa davet almak için GitHub kuruluş yöneticilerine ulaşabilirler.

GitHub Enterprise kurulum hakkında ayrıntılar için lütfen [abone belgelerine](access-github.md)başvurun.   

## <a name="manage-github-enterprise-subscriptions"></a>GitHub Enterprise abonelikleri yönetme
GitHub Enterprise abonelikleri satın alındığında, GitHub erişen ve yöneticileri tanımlayan kuruluşları oluşturmaya ve yapılandırmaya yardımcı olacak iş ortakları GitHub.  Bu Yöneticiler daha sonra yöneticiler olarak ayarlandıklarından bir bildirim alır.  

Bu işlem daha karmaşık olduğundan, kuruluşların ve yöneticilerin tam olarak ayarlanması için abonelikler satın alındıktan sonra birkaç gün sürebilir.

GitHub, bulut tabanlı GitHub. com veya şirket içi GitHub Enterprise sunucu olarak kullanılabilir.  İki sürümü yönetmek için süreçler farklılık gösterir.  GitHub, GitHub Enterprise abonelikleri yönetmenize yardımcı olmak için çeşitli yardım konuları ve yönetici kılavuzlarını sağlar.  Aşağıdaki seçili konulara bağlantılar sağladık.  

## <a name="support-resources"></a>Destek kaynakları
- [GitHub Docs](https://docs.github.com/en/github/setting-up-and-managing-your-enterprise-account/managing-licenses-for-the-github-enterprise-and-visual-studio-bundle) 'ta GitHub atama hakkında daha fazla bilgi edinin
- [GitHub yardım](https://help.github.com/en)'da çok çeşitli GitHub konularda soruların yanıtlarını bulun.
- [GitHub Community forumundaki](https://github.community/)diğer GitHub kullanıcılardan yardım alın.
- Visual Studio aboneliklerinin yönetimi hakkında yardım için, [Visual Studio abonelik desteğiyle](https://aka.ms/vsadminhelp)iletişim kurun.
- Visual Studio ıde, Azure DevOps Services veya diğer Visual Studio ürünleri veya hizmetleri hakkında sorularınız mı var?  [Visual Studio desteği](https://visualstudio.microsoft.com/support/)' ni ziyaret edin.
- GitHub Enterprise için [teknik destek](https://support.microsoft.com/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) alın.   

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

GitHub Enterprise ile Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi için Visual Studio [abonelikleri yönetici portalına](https://visualstudio.microsoft.com/subscriptions-administration/)göz atın.