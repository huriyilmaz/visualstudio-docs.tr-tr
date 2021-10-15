---
title: Nasıl yaparım? abonenin oturum açma e-posta adresi güncelleştirilsin mi?
description: Süper yönetici veya yönetici, aboneler etki alanını toplu olarak güncelleştirmek istiyor.
ms.topic: include
ms.assetid: c1220a33-26b0-4bf9-be97-ab2b3055e351
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: email
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: 56ba89a2546c384835addb05574c3280fed500e6
ms.sourcegitcommit: 485f0f6f578568ee31b2ac093e32a6d01dc9c1c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130019319"
---
## <a name="update-subscribers-sign-in-email-address"></a>Abonenin oturum açma e-posta adresini Güncelleştir

Abonenin oturum açma e-posta adresini ayrı ayrı veya toplu düzenleme kullanarak güncelleştirebilirsiniz. 

##  <a name="bulk-edit"></a>Toplu düzenleme
1. **Aboneleri Yönet** sayfasında, güncelleştirilmesi gereken anlaşmada olduğunuzdan emin olun.
2. **toplu düzenleme**' yi seçin, Excel dosyasını dışarı aktarın ve açılır penceredeki yönergeleri izleyin.
3. Dosyada gerekli düzenlemeleri yapın, sonra dosyayı kaydedip karşıya yükleyin. Düzenlemeleri yaptığınızda, GUID 'lerin değiştirilemeyeceğini aklınızda bulundurun.
4. Toplu düzenlemeye başlamak için **Tamam ' ı** seçin.
5. Abonelere, değişikliği bildiren bir e-posta gönderilir.

## <a name="individual-edit"></a>Bireysel düzenleme 
1. **Aboneleri Yönet** sayfasında, güncelleştirilmesi gereken anlaşmada olduğunuzdan emin olun.
2. Güncelleştirilecek abone ' i seçin ve ardından abone adının yanındaki üç nokta (...) simgesini seçin.
3. **Düzenle**'yi seçin.
4. Kullanıma hazır panelinde, gerekli düzenlemeleri yapın ve ardından **Kaydet**' i seçin.
5. Abonelere, değişikliği bildiren bir e-posta gönderilir.

## <a name="azure-active-directory-azure-ad"></a>Azure Active Directory (Azure AD) 
Azure AD gruplarını kullanarak abonelik atarsanız, tüm e-posta adresi veya ad güncelleştirmeleri otomatik olarak [Manage.VisualStudio.com](https://manage.visualstudio.com)' e yansıtılır. Değişiklikleri kaydettikten sonra, yönetim portalı 'nda yansıtılan güncelleştirmeleri 24 saat içinde görmeniz gerekir. 
1. [Azure portal](https://portal.azure.com) oturum açın.
2. Gerekli güncelleştirmeleri yapın.

## <a name="impact-of-sign-in-email-updates"></a>Oturum açma e-posta güncelleştirmelerinin etkisi
Oturum açma e-postasını değiştirmek, aboneler için aşağıdakiler de dahil olmak üzere olumsuz etkileri olabilir:
- Visual Studio ıde ile oturum açma sorunları.
- Azure DevOps ile oturum açma sorunları.
- Aylık Azure geliştirme ve test tek kredisi ile ilgili sorunlar.

[Oturum açma e-postasını değiştirme konusunda daha fazla bilgi için abonenin ilişkili avantajlarından nasıl etkilenirsiniz](https://docs.microsoft.com/visualstudio/subscriptions/subscription-level-changes) .