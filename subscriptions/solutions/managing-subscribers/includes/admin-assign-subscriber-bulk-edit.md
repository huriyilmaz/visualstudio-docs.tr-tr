---
title: Nasıl yaparım? toplu olarak atamak mı?
description: Süper yönetici veya yönetici toplu özelliği kullanma hakkında daha fazla ayrıntı istiyor.
ms.topic: include
ms.assetid: 3b450a79-47d2-4434-899d-bea29a0271e1
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: bulk
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: d837b52d57a212f7519adfbc027eadbcf5f45dab
ms.sourcegitcommit: 364e106fcbf4fb6af534e81d8b700901f79f4ec8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2021
ms.locfileid: "129013225"
---
## <a name="how-do-i-assign-subscribers-in-bulk"></a>Nasıl yaparım? toplu olarak atamak mı?

Aboneleri toplu olarak atamak için iki seçeneğiniz vardır.
- Bir şablon [kullanarak toplu Excel.](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-bulk-add-to-assign-subscriptions)
- Kuruluşta abonelikleri fazla atayamayacak bir sözleşme türü varsa, Azure Active Directory [(Azure AD) grup ataması kullanabilirsiniz.](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions)

## <a name="use-bulk-upload"></a>Toplu karşıya yükleme kullanma
1. Güncelleştirilecek sözleşmenin sözleşme açılan menüsünde seçildiğinden emin olun.
2. **Ekle'yi** ve ardından **açılan menüde Toplu** düzenleme'yi seçin. Açılır pencere yönergelerini izleyin.
3. Sayfayı dışarı Excel, dosyada gerekli düzenlemeleri yaptıktan sonra dosyayı kaydedecek ve karşıya yükleyebilirsiniz. Düzenlemeleri yapmak için GUID'lerin değiştirilenediğini unutmayın.
4. Toplu **düzenlemeye** başlamak için Tamam'ı seçin.

Şablon herhangi bir hata içeriyorsa karşıya yükleme başarısız olur. Hataların gösterildiği için şablonu düzeltin ve yeniden deneyin.

## <a name="use-azure-ad-groups"></a>Azure AD gruplarını kullanma
Azure AD'nin toplu karşıya yükleme için kullanımı şu anda yalnızca fazla yüklenilen sözleşmelere sahip kuruluşlar tarafından kullanılabilir.
1. Güncelleştirilmiş olması gereken sözleşmenin sözleşme açılan menüsünde seçildiğinden emin olun.
2. **Ekle'yi** seçin ve **Azure Active Directory menüden** Grup ekle'yi seçin.
3. Form alanına eklemek istediğiniz Azure AD grubunun adını girin. Siz adı yazarak arama, kuruluş içindeki kullanılabilir Azure AD gruplarını gösterecek şekilde ler.
4. Grubu seçerek alan otomatik olarak grup adıyla doldurmaktır. Değişiklik yapmadan önce bu gruptaki kullanıcıları görüntüebilirsiniz.
5. **Ekle'yi** ve ardından Onayla'ya **tıklayın.**
6. Gelecekte Azure AD grubuna eklenen tüm kullanıcılara otomatik olarak bir abonelik verilir. Gruptan kaldırılan herkesin aboneliği kaldırılır.