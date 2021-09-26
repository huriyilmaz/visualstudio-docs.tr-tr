---
title: Toplu karşıya yükleme sorunlarını çözme
description: Süper yönetici veya yönetici, kullanıcıları yeni sözleşmeye atadı ancak kullanıcıları yanlış sözleşmeye ekledi.
ms.topic: include
ms.assetid: 273f5f7a-739e-4de0-b7f7-d0bdd616e059
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: bulk, upload
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: a8338378828ad9297004d1bf41ea77346405c39f
ms.sourcegitcommit: 364e106fcbf4fb6af534e81d8b700901f79f4ec8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2021
ms.locfileid: "129013343"
---
## <a name="how-do-i-fix-a-bulk-upload-to-use-the-correct-agreement"></a>Nasıl yaparım? sözleşmeyi kullanmak için toplu karşıya yükleme sorunu mu düzeltildi?

Yanlış sözleşmeye yanlışlıkla toplu yükleme yapıyorsanız, sorunu çözmek için aşağıdaki adımları izleyin.

İlk olarak, aboneleri doğru sözleşmeye yüklediğinizden ve ardından diğer sözleşmeden aboneleri sildikten emin olun. Yönetici portalı aracılığıyla tek bir kullanıcı için sorunu toplu olarak silebilir veya düzeltebilirsiniz.

## <a name="individual-users"></a>Bireysel kullanıcılar

1. Yönetici [portalının Aboneler sayfasında,](https://manage.visualstudio.com/subscribers)sütun adına ve sıralamaya tıklayarak kaldırmanız gereken aboneleri bulun. Kullanıcıları daha kolay bulmak için filtre seçeneğini de kullanabilirsiniz.
2. Kaldır İhlal etmek istediğiniz aboneleri bu olduktan sonra kullanıcıların yanındaki onay kutusunu işaretleyin. Aynı anda seçebilirsiniz kullanıcı sayısıyla ilgili bir sınır yoktur. Ayrıca kaldırmak istediğiniz listede ilk kullanıcıyı, ardından Shift'i ve ardından listede son kullanıcıyı seçebilirsiniz. Bu adımlar, listede yer alan tüm kullanıcıları seçer. Ayrıca listenin en üstünde yer alan onay simgesini seçerek tüm kullanıcıları seçebilirsiniz. 
3. **Kılavuzun** üst kısmında Sil'i seçin ve silme işlemini onaylayın.

## <a name="azure-active-directory-azure-ad-group"></a>Azure Active Directory (Azure AD) grubu

Kullanıcılar bir Azure AD grubu aracılığıyla eklendiyse, kullanıcıları doğrudan Azure AD grubundan kaldırmanız gerekir. Kullanıcılar gruptan kaldırıldıktan sonra silme işleminin yönetici portalında görünür olması 24 saate kadar sürebilir. 

## <a name="impact-of-moving-subscriptions"></a>Abonelikleri taşımanın etkisi

Aboneler yeni bir sözleşmeye taşındığında yeni bir abonelik kimliği alırlar. Bu değişiklik, aylık Azure kredi avantajıyla ilişkili Azure aboneliği bağlantısını bozar. Bağlantı bozuk olduğunda, eski Azure aboneliği nihai devre dışı bırakılama durumuna tabi olur. Kesintiyi önlemek için abonelerin yeni Visual Studio aboneliği avantajını kullanarak yeni bir Azure aboneliği oluşturması ve ardından mevcut Azure varlıklarını eski [Azure](https://docs.microsoft.com/azure/azure-resource-manager/management/move-resource-group-and-subscription) aboneliğinden yeni aboneliğe aktarması gerekir.