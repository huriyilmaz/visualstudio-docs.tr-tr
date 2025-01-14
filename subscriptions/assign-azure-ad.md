---
title: Azure Active Directory gruplarını kullanarak Visual Studio Aboneliklerinizi otomatikleştirme
author: esteban-herrera
ms.author: amast
manager: shve
ms.date: 07/22/2021
ms.topic: how-to
description: Yöneticilerin Azure Active Directory gruplarını kullanarak nasıl abonelik Azure Active Directory öğrenin
ms.openlocfilehash: 0bcf6957ee2ab1c199a25858058e524bf76fa253
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132995725"
---
# <a name="how-to-automate-your-visual-studio-subscriptions-using-azure-active-directory-groups"></a>Azure Active Directory gruplarını kullanarak Visual Studio Aboneliklerinizi otomatikleştirme

Bu kılavuzda, Azure Active Directory (Azure AD) gruplarınızı otomatikleştirmek ve yönetmek için basit ve kullanışlı bir işlem oluşturmak için Visual Studio göstereceğiz.
Bir Azure Active Directory grubuna abonelik düzeyi atadıktan sonra kullanıcılarınız ihtiyaç Azure Active Directory grup katılmasını talep edebilirsiniz. Gruba katılmaları onaylandıktan sonra ilgili aboneliğe otomatik olarak atanır. Gruptan veya abonelikten kaldırılırsa Azure Active Directory abonelikleri otomatik olarak kaldırılır.

## <a name="requirements"></a>Gereksinimler
- Kimlik yönetimi için, Azure Active Directory bir kullanıcı kullanıyor olması gerekir.
- Yönetim Portalı'nın yönetici haklarına ve [erişimine sahipsiniz.](https://manage.visualstudio.com)
- yönetim merkezinde dizin için Genel Yönetici veya Ayrıcalıklı Rol Yöneticisi Azure Active Directory [gerekir.](https://aad.portal.azure.com/)

## <a name="how-to"></a>Nasıl Yapılır
1.  Kullanmayı Azure Active Directory abonelik düzeyi için bir grup oluşturun 
    > [!NOTE]
    > Azure Active Directory grubu oluşturmayla ilgili bazı ipuçları:
    > - Gruba en az bir üye ekleyin.
    > - Üyelerin hepsi en üst düzeyde olmalı (diğer grupları iç içe yerleştirme).
    > - Abonelik düzeyini grup Azure Active Directory dahil edin, böylece grubun ne için kullanıcazı açıkça belirtebilirsiniz. 
    > - Tüm grup üyelerine Aynı dilde Visual Studio Abonelikler e-postası gönderilir. Abonelerin tercih ettiği dilde bu e-postayı almalarını sağlamak için her bölge için farklı bir grup kullanın.
    > - Tüm üyelerin kendi hesap hesaplarıyla ilişkilendirilmiş bir e-Azure Active Directory olması gerekir.

2.  (İsteğe bağlı) Kullanıcıların gruba katılma isteği için bir yol ayarlama Bunun için birden çok seçenek vardır:
    1.  Grup üyeliklerini yönetmek için Azure Active Directory Graph [API'sini](https://docs.microsoft.com/graph/api/resources/groups-overview?view=graph-rest-1.0) kullanan bir iç portal oluşturun.
    2.  Kendi Kendine [Yardım portalını Erişim Paneli](https://docs.microsoft.com/azure/active-directory/enterprise-users/groups-self-service-management) 
3.  Yönetim [Portalı'ne gidin.](https://manage.visualstudio.com)
4.  Grup **ekle** ve **Azure Active Directory seçin**
    > [!div class="mx-imgBorder"]
    > ![Grup ekle Azure Active Directory ekran görüntüsü.](media/add-azure-ad-group.png "Ekle düğmesine tıklayın ve ardından Azure Active Directory seçin")

5.  Grup **ekle slayt** gösterisinde aboneliklerin Azure Active Directory istediğiniz grup grubunu bulun. Abonelik düzeyinin doğru olduğundan emin olun ve 'Ekle' düğmesine tıklamadan önce kalan alanları doldurun.
    a.  Grup üyelerinin Azure Active Directory zaten atanmış bir aboneliği varsa, bu üyeler ileriye doğru grup tarafından yönetilecek şekilde güncelleştirilir.\*
    > [!div class="mx-imgBorder"]
    > ![Grup ayrıntıları Azure Active Directory bölmesinin ekran görüntüsü.](media/azure-ad-group-details.png "Bu grubu atamak için grubu ve abonelik düzeyini seçin")

6.  Gerekirse her abonelik düzeyi için işlemi tekrarlayın; örneğin, Azure Active Directory kullanıcılar için bir Visual Studio Professional ve Visual Studio Enterprise.
7.  Bitti! Kullanıcılar kendi abonelik gruplarına eklendi Azure Active Directory kaldırıldıklarında, otomatik olarak bir abonelik atanır veya atanmamış olur ve e-posta ile bilgi gönderilir.

\*Visual Studio Aboneliklerini bir süredir yönetiyorsanız, büyük olasılıkla bu abonelik gruplarını kullanmak için güncelleştirmek Azure Active Directory vardır. Bunu kolaylaştırıldı! Zaten abonelikleri olan Azure Active Directory bir grup eklersiniz, ilk eşitleme tamamlandıktan sonra yeni eklenen Azure Active Directory grup altında otomatik olarak gruplanır. Abone abonelik kimliğini korur ve hiçbir şeyin değişmediğini fark etmez. Gelecekte Azure Active Directory gruptan kaldırılırsa abonelikleri otomatik olarak kaldırılır. 

> [!NOTE]
>Bireysel abonelik farklı bir abonelik düzeyinde ise, yeni düzey için bu aboneliklere ek bir abonelik verilir. Örnek: Bir kullanıcının tek bir Visual Studio Professional aboneliği varsa ve bu abonelikler için atadığınız bir grubun üyesi Visual Studio Enterprise şimdi her ikisine de sahip olur. 
