---
title: Nasıl yaparım? aboneler toplu olarak atansın mı?
description: Süper yönetici veya yönetici, toplu özelliği kullanma hakkında daha fazla ayrıntı sağlar.
ms.topic: include
ms.assetid: 3b450a79-47d2-4434-899d-bea29a0271e1
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: ''
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: 6b7b5ae726588d19930c267fdd1b31656d5ce5e0de983706cf3d2d49d1b63eb1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "127892578"
---
## <a name="how-do-i-assign-subscribers-in-bulk"></a>Nasıl yaparım? aboneler toplu olarak atansın mı?

Aboneler toplu olarak atamak için iki seçeneğiniz vardır.
- [Excel şablonu kullanarak toplu karşıya yükleme](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-bulk-add-to-assign-subscriptions)yapabilirsiniz.
- kuruluşunuzun abonelik ata 'dan fazla bir anlaşma türü varsa, [Azure Active Directory (Azure AD) grup atamasını](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions)kullanabilirsiniz.

## <a name="use-bulk-upload"></a>Toplu karşıya yükleme kullan
1. Güncelleştirilmesi gereken sözleşmenin anlaşma açılan menüsünde seçili olduğundan emin olun.
2. **Ekle** ' yi seçin ve açılan menüden **Toplu Düzenle** ' yi seçin. Açılır penceredeki yönergeleri izleyin.
3. Excel sayfasını dışarı aktardıktan sonra dosyada gerekli düzenlemeleri yapın, sonra dosyayı kaydedip karşıya yükleyin. Düzenlemeleri yaptığınızda, GUID 'lerin değiştirilemeyeceğini aklınızda bulundurun.
4. Toplu düzenlemeye başlamak için **Tamam ' ı** seçin.

Şablonda hata varsa, yükleme başarısız olur. Hataları göstermekte olduğunuzdan, şablonu düzeltip yeniden deneyebilirsiniz.

## <a name="use-azure-ad-groups"></a>Azure AD gruplarını kullanma
Azure AD 'nin toplu karşıya yükleme işlemi şu anda yalnızca fazla talep veren anlaşmalar içeren kuruluşlarda sunulmaktadır.
1. Sözleşme açılan menüsünde, güncelleştirilmesi gereken sözleşmenin seçili olduğundan emin olun.
2. **ekle**' yi seçin ve açılan menüden **Azure Active Directory grubu** ' nu seçin.
3. Form alanına eklemek istediğiniz Azure AD grubunun adını girin. Adı yazarken, arama, kuruluşunuzda kullanılabilir Azure AD gruplarını göstermek için güncelleştirilir.
4. Grubu seçtiğinizde, alanı otomatik olarak grup adıyla doldurulur. Değişiklik yapmadan önce bu gruptaki kullanıcıları görüntüleyebilirsiniz.
5. **Ekle**' yi ve ardından **Onayla**' yı seçin.
6. Azure AD grubuna eklenen gelecekteki kullanıcılara otomatik olarak bir abonelik verilir. Gruptan kaldırılan herkesin aboneliği kaldırılmıştır.
