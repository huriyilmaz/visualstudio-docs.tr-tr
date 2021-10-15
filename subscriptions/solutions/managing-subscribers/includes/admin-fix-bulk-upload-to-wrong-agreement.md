---
title: Toplu karşıya yükleme Nasıl yaparım? düzeltilsin mi?
description: Süper yönetici veya yönetici, kullanıcıları yeni sözleşmeye atamış olduğunu düşündüler, ancak kullanıcıları yanlış sözleşmeye ekledi.
ms.topic: include
ms.assetid: 273f5f7a-739e-4de0-b7f7-d0bdd616e059
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: bulk, upload
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: 451629c284ae4e6630e461dc67e74c28b0c2ddfb
ms.sourcegitcommit: 485f0f6f578568ee31b2ac093e32a6d01dc9c1c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130019340"
---
## <a name="how-do-i-fix-a-bulk-upload-to-use-the-correct-agreement"></a>Toplu karşıya yükleme işleminin doğru anlaşmayı Nasıl yaparım? düzeltilsin mi?

Yanlış sözleşmeye yanlışlıkla toplu yükleme yaparsanız, sorunu gidermeye yönelik bu adımları izleyin.

İlk olarak, aboneleri doğru sözleşmeye yüklediğinizden emin olun ve ardından diğer anlaşmadan aboneleri silin. Toplu olarak silebilir veya yönetim portalı aracılığıyla tek bir kullanıcı için sorunu çözebilirsiniz.

## <a name="individual-users"></a>Bireysel kullanıcılar

1. [Yönetici portalının aboneler sayfasında](https://manage.visualstudio.com/subscribers), sütun adı ve sıralama ' ya tıklayarak kaldırmanız gereken aboneleri bulun. Kullanıcıları daha kolay bulmak için filtre seçeneğini de kullanabilirsiniz.
2. Kaldırılacak aboneleri bulduktan sonra, kullanıcılar ' ın yanındaki onay kutusunu işaretleyin. Tek seferde seçebileceğiniz Kullanıcı sayısı için bir sınır yoktur. Ayrıca, kaldırmak istediğiniz bir listedeki ilk kullanıcıyı seçip SHIFT ' i seçip listeden son kullanıcıyı seçebilirsiniz. Bu adımlar listedeki tüm kullanıcıları seçer. Ayrıca, tüm kullanıcılar ' ı seçmek için listenin en üstündeki onay simgesini de seçebilirsiniz. 
3. Kılavuzun en üstünde bulunan **Sil** ' i seçin ve sonra silmeyi onaylayın.

## <a name="azure-active-directory-azure-ad-group"></a>Azure Active Directory (Azure AD) grubu

Kullanıcılar bir Azure AD grubu üzerinden eklendiyse, kullanıcıları doğrudan Azure AD grubundan kaldırmanız gerekir. Kullanıcılar gruptan kaldırıldıktan sonra, silmenin yönetici portalında görünmesini 24 saate kadar sürebilir. 

## <a name="impact-of-moving-subscriptions"></a>Aboneliklerin taşınmasının etkileri

Aboneler yeni bir sözleşmeye taşındığında yeni bir abonelik KIMLIĞI alırlar. Bu değişiklik, aylık Azure kredisi avantajlarıyla ilişkili Azure aboneliklerinden bağlantıyı keser. Bağlantı kesildiğinde, eski Azure aboneliği son devre dışı bırakmaya tabidir. kesintiden kaçınmak için, abonelerin yeni Visual Studio aboneliğindeki avantajı kullanarak yeni bir azure aboneliği oluşturması ve ardından [mevcut azure varlıklarını](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription) eski azure aboneliğinden yeni bir azure aboneliği ile aktarması gerekir.