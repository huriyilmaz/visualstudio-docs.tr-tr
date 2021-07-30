---
title: Azure Active Directory grupları kullanarak Visual Studio aboneliklerinizi otomatikleştirme
author: esteban-herrera
ms.author: esherrer
manager: shve
ms.date: 07/22/2021
ms.topic: how-to
description: yöneticilerin Azure Active Directory gruplarını kullanarak nasıl atayabileceği ve aboneliklerine nasıl abone olabileceğini öğrenin
ms.openlocfilehash: de485170185049270d4819a418ea7d027b1a9d4b
ms.sourcegitcommit: 2694ab246eb857a1c607738a67198c46f826f106
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2021
ms.locfileid: "114995415"
---
# <a name="how-to-automate-your-visual-studio-subscriptions-using-azure-active-directory-groups"></a>Azure Active Directory grupları kullanarak Visual Studio aboneliklerinizi otomatikleştirme

bu kılavuzda, Visual Studio aboneliklerinizi otomatik hale getirmek ve yönetmek için basit ve uygun bir işlem oluşturmak üzere Azure Active Directory (Azure AD) gruplarından nasıl yararlanabileceğiniz gösterilmektedir.
bir Azure Active Directory grubuna abonelik düzeyi atadıktan sonra, kullanıcılarınız ihtiyaç duydukları abonelik düzeyine bağlı olarak bir Azure Active Directory grubuna katılmayı talep edebilir. Gruba katılması onaylandıktan sonra otomatik olarak ilgili abonelik atanır. gruptan veya Azure Active Directory kaldırıldıklarında otomatik olarak aboneliğini kaldırılır.

## <a name="requirements"></a>Gereksinimler
- kuruluşunuzun kimlik yönetimi için bir Azure Active Directory kullanıyor olması gerekir.
- [Yönetim portalına](https://manage.visualstudio.com)yönetici haklarına sahip olmanız ve erişmeniz gerekir.
- [Azure Active Directory yönetim merkezinde](https://aad.portal.azure.com/)dizin için genel yönetici veya ayrıcalıklı rol yöneticisi rolüne sahip olmanız gerekir.

## <a name="how-to"></a>Nasıl Yapılır
1.  kullanmayı planladığınız her abonelik düzeyi için bir Azure Active Directory grubu oluşturun 
    > [!NOTE]
    > Azure Active Directory grubunuzu oluştururken bazı ipuçları:
    > - Gruba en az bir üye ekleyin.
    > - Üyelerin tümünün en üst düzeyde olması gerekir (diğer grupları iç içe kullanmayın).
    > - abonelik düzeyini Azure Active Directory grup adına ekleyin, bu nedenle grubun ne için kullanılacağını açıkça gösterdi. 
    > - tüm grup üyeleri, aynı dilde Visual Studio abonelikleri e-postasına hoş geldiniz. Abonelerin bu e-postayı tercih ettiği dilde aldığından emin olmak için her bölge için farklı bir grup kullanın.
    > - tüm üyelerin Azure Active Directory hesabıyla ilişkilendirilmiş bir e-posta adresi olmalıdır.

2.  Seçim Kullanıcıların bir gruba katılmayı istemesi için bir yol ayarlayın bu, bunun için birden çok seçenek vardır:
    1.  grup üyeliklerini yönetmek için [Azure Active Directory Graph API](https://docs.microsoft.com/graph/api/resources/groups-overview?view=graph-rest-1.0) yararlanan bir iç portal oluşturun.
    2.  Access panel üzerinden [kendi kendine yardım portalını](https://docs.microsoft.com/azure/active-directory/enterprise-users/groups-self-service-management) kullanma 
3.  [Yönetim portalına](https://manage.visualstudio.com)gidin.
4.  **ekle** ve **Azure Active Directory grubunu** seçin
    > [!div class="mx-imgBorder"]
    > ![Azure Active Directory grubu ekle düğmesinin ekran görüntüsü.](media/add-azure-ad-group.png "ekle düğmesine ve sonra Azure Active Directory grubu ' na tıklayın.")

5.  **grup ekle** slaydında, aboneliklerin atanmasını istediğiniz Azure Active Directory grubunu bulun. Abonelik düzeyinin doğru olduğundan emin olun ve ' Ekle ' düğmesine tıklamadan önce kalan alanları tamamlayın.
    a.  Azure Active Directory grubunun üyelerine zaten atanmış bir abonelik varsa, bunlar, ileri doğru hareket eden grup tarafından yönetilmek üzere güncelleştirilir.\*
    > [!div class="mx-imgBorder"]
    > ![Azure Active Directory grubu ayrıntıları bölmesinin ekran görüntüsü.](media/azure-ad-group-details.png "Grubu atamak için Grup ve abonelik düzeyini seçin")

6.  gerekirse her abonelik düzeyi için işlemi tekrarlayın, örneğin Visual Studio Professional kullanıcılar için bir Azure Active Directory ve bir Visual Studio Enterprise için bir tane oluşturun.
7.  İşiniz bitti! kullanıcılar Azure Active Directory gruplarına eklenip kaldırıldığında, otomatik olarak bir abonelik atanır veya atanmaz ve e-posta ile bildirim gönderilir.

\*Visual Studio aboneliklerini zaten yönetiyorsanız, Azure Active Directory grupları kullanmak üzere güncelleştirmek istediğiniz atamalarınız zaten var. Bu kadar kolay! zaten abonelikleri olan kişileri içeren bir Azure Active Directory grubu eklerseniz, ilk eşitleme tamamlandıktan sonra otomatik olarak yeni eklenen Azure Active Directory grubu altında gruplandırılır. Abone, abonelik KIMLIKLERINI korur ve bir şeyi değiştirmeyecektir. gelecekte Azure Active Directory grubundan kaldırılırsa, abonelikleri otomatik olarak kaldırılır. 

> [!NOTE]
>Tek tek abonelik farklı bir abonelik düzeyi için ise, yeni düzey için ek bir abonelik olarak verilirler. örnek: bir kullanıcı tek bir Visual Studio Professional aboneliğine sahipse ve Visual Studio Enterprise abonelikleri atadığınız bir grubun üyesiyse, artık her ikisine de sahip olur. 
