---
title: Visual Studio + GitHub kurumsal teklifi | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: f271d623-dcde-442a-865c-4dca5ad8a9c5
ms.date: 03/17/2020
ms.topic: conceptual
description: Visual Studio + GitHub kurumsal teklifinde abonelikleri yönetme
ms.openlocfilehash: 01b043698aaeb23151357595d5c39cd117fd47c7
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249832"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>GitHub Enterprise ile Visual Studio aboneliklerini yönetme
Microsoft ile kurumsal anlaşma (EA) olan müşteriler, Visual Studio Standard abonelikleri ve GitHub Enterprise 'ı birlikte getiren yeni bir abonelik teklifi satın almaya uygundur. Visual Studio abonelerinin GitHub Enterprise 'ı edinmenin kolay ve ekonomik bir yoludur. 

Kuruluşunuz GitHub Enterprise ile Visual Studio abonelikleri satın aldığında, bunlar iki bölümden sağlanır ve yönetilir.

## <a name="manage-visual-studio-subscriptions"></a>Visual Studio aboneliklerini yönetme
Kuruluşunuz GitHub Enterprise ile Visual Studio abonelikleri satın aldığında, aboneliklerin Visual Studio bölümü hemen sağlanır ve abonelikler Visual Studio [abonelikleri yönetim](https://manage.visualstudio.com) portalı 'nda atama ve yönetim için kullanılabilir. 

Abonelikleri yönetme hakkında daha fazla bilgi için şu konulara bakın:
- [Yönetici portalını kullanma](using-admin-portal.md)
- [Abonelik atama](assign-license.md)
- [Abonelikleri Düzenle](edit-license.md)
- [Abonelikleri Sil](delete-license.md)
- [Fazla Yüklemeler](handle-overclaimed-license.md)

> [!Important]
> GitHub Enterprise ile Visual Studio abonelikleri, Visual Studio abonelik yöneticileri tarafından atanmışsa ve bu aboneliklerin hiç satın alınmadıysa, bu abonelikler kuruluş içindeki GitHub Enterprise Admins 'e görünür olmayacaktır. GitHub Enterprise aboneliklerinin görünür olmasını sağlamak için, aboneliklerin ilk kez atandığı GitHub Enterprise veya Visual Studio Enterprise ile **en az bir** Visual Studio Professional içeren bir satın alma yapılmalıdır.  
>
> Bu abonelik için lisans gereksinimleriyle uyumlu kalmak için, atanan her GitHub aboneliği için, Visual Studio abonelikleri yönetim portalında bir GitHub aboneliğinin atandığı karşılık gelen bir Visual Studio olduğundan emin olunması müşterinin sorumluluğundadır.

## <a name="manage-github-enterprise-subscriptions"></a>GitHub Enterprise aboneliklerini yönetme
GitHub Enterprise abonelikleri satın alındığında, GitHub 'a erişecek ve yöneticileri tanımlayan kuruluşları oluşturmaya ve yapılandırmaya yardımcı olmak üzere müşteriler ile GitHub iş ortakları yapılır.  Bu Yöneticiler daha sonra yöneticiler olarak ayarlandıklarından bir bildirim alır.  

Bu işlem daha karmaşık olduğundan, kuruluşların ve yöneticilerin tam olarak ayarlanması için abonelikler satın alındıktan sonra birkaç gün sürebilir.

GitHub, bulut tabanlı GitHub.com ya da şirket içi GitHub Enterprise Server olarak kullanılabilir.  İki sürümü yönetmek için süreçler farklılık gösterir.  GitHub, GitHub Enterprise aboneliklerini yönetmenize yardımcı olmak için çeşitli yardım konuları ve yönetici kılavuzlarını sağlar.  Aşağıdaki seçili konulara bağlantılar sağladık.  

### <a name="githubcom"></a>GitHub.com 
GitHub.com yönetimi hakkında daha fazla bilgi için lütfen [GitHub yardımı](https://help.github.com/en)'nda aşağıdaki konulara göz atın.
+ [Yardım konularının tam listesi](https://help.github.com/en)
+ [Kuruluşunuzdaki üyelikleri yönetme](https://help.github.com/en/articles/managing-membership-in-your-organization)
+ [Kullanıcıları kuruluşunuza katmak üzere davet etme](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
  - [Kullanıcıları ekiplerden/kuruluşlardan kaldırma](https://help.github.com/en/articles/removing-a-member-from-your-organization)
  - [Kuruluşunuzun eski bir üyesini yeniden belirten](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
+ [Rolleri kullanarak erişimi yönetme](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
+ [Kullanıcıları ekiplere düzenleme](https://help.github.com/en/articles/organizing-members-into-teams)
+ [Kuruluşunuzun depolarına erişimi yönetme](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories)

### <a name="github-enterprise-server"></a>GitHub Enterprise Server
GitHub yardımı, soruları yanıtlamak ve kuruluşunuzun GitHub Enterprise Server uygulamasının yönetimine ilişkin ipuçları vermek için çeşitli yönetici kılavuzlarını sağlar.

+ [Tüm yönetici kılavuzlarını görüntüle](https://help.github.com/en/enterprise/2.16/admin)
+ [Kullanıcı Yönetimi](https://help.github.com/en/enterprise/2.16/admin/user-management)
  - [Kuruluşlar ve takımlar](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
    - [Kuruluşlar oluşturma](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
    - [Takımlar oluşturma](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
    - [Takımlara kişi ekleme](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
    - [Ekiplerden ve kuruluşlardan kişileri kaldırma](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
  - [Kullanıcı güvenliği](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
+ [GitHub Enterprise Server 'ı yükleme ve yapılandırma](https://help.github.com/en/enterprise/2.16/admin/installation)

## <a name="support-resources"></a>Destek kaynakları

- [GitHub yardımı](https://help.github.com/en)'nda çok çeşitli GitHub konuları dizisiyle soruların yanıtlarını bulabilirsiniz.
- [GitHub topluluk forumundaki](https://github.community/)diğer GitHub kullanıcılarından yardım alın.
- Visual Studio abonelikleri için Sales, abonelikler, hesaplar ve faturalandırma konusunda yardım için Visual Studio [abonelikleri desteğiyle](https://visualstudio.microsoft.com/subscriptions/support/)görüşün.
- Visual Studio IDE, Azure DevOps Services veya diğer Visual Studio ürünleri veya hizmetleri hakkında sorularınız mı var?  [Visual Studio desteği](https://visualstudio.microsoft.com/support/)' ni ziyaret edin.
- GitHub Enterprise için [Teknik destek](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) alın.   

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)

Visual Studio aboneliklerini GitHub Enterprise ile yönetme hakkında daha fazla bilgi için Visual Studio [abonelikleri Yönetici portalı](https://visualstudio.microsoft.com/subscriptions-administration/)' na göz atın.
