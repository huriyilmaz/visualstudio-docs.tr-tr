---
title: aylık Visual Studio abonelikleri için yöneticileri ayarlama | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/21/2021
ms.topic: how-to
description: Aylık abonelikler için yöneticileri ayarlama
ms.openlocfilehash: aaa847aab4b56591d2fdd070192d14c62c33d96c
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427578"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Visual Studio aylık abonelikler için yöneticileri ayarlama

Visual Studio aylık abonelikler yöneticiler tarafından yönetilir. Bu bireyler abonelik atayabilir, atamaları düzenleyebilir, abonelik ekleyebilir veya silebilir ve diğer abonelik yönetim görevlerini gerçekleştirebilir.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Azure abonelik sahibi ilk yöneticiydir

satın alma işlemleri yapmak için kullanılan Azure aboneliğinin sahibi olan Visual Studio aylık abonelikler satın aldığınızda, bu abonelikler için otomatik olarak yönetici olarak ayarlanır.

[Visual Studio marketi](https://marketplace.visualstudio.com/subscriptions)aracılığıyla veya bir Bulut Çözümü Sağlayıcısı arayarak aylık abonelikler satın alabilirsiniz. satın alma deneyiminin sonunda Visual Studio marketi üzerinden satın aldıysanız, kullanıcıları yönetmeye yönelik bir fırsat sunulur. bu seçeneğin belirlenmesi sizi Visual Studio abonelikleri yönetim portalına götürür [https://manage.visualstudio.com](https://manage.visualstudio.com) .

Abonelikleri satın aldıktan sonra istediğiniz zaman [yönetim portalını](https://manage.visualstudio.com) ziyaret edebilirsiniz. Portalda oturum açmanız yeterlidir ve sol üst köşedeki uygun Azure aboneliğini seçin.

Aylık abonelikleri satın almak için kullanılan Azure aboneliğinin sahibi olarak ek yöneticiler de atayabilirsiniz.

## <a name="add-admins"></a>Yönetici Ekle

Yönetici eklemek için:

1. [portal.azure.com](https://portal.azure.com)adresindeki Azure portal Bağlan.
2. Visual Studio aylık abonelikleri satın almak için kullandığınız hesapla oturum açın.
3. **Azure hizmetleri** altında **maliyet yönetimi + faturalandırma**' i seçin.
   > [!div class="mx-imgBorder"]
   > ![Maliyet yönetimi ve Azure Hizmetleri altında Faturalandırma ' i seçin](_img/cloud-admin/azure-cost-billing.png "Azure Hizmetleri grubundan maliyet yönetimi 'ni seçin")
4. **Aboneliklerim** listesinde, satın almayı yapmak Için kullandığınız Azure aboneliğini seçin.
   > [!div class="mx-imgBorder"]
   > ![Abonelik seçin](_img/cloud-admin/subscription-list.png "Satın alımınızın olmasını sağlamak için kullanmak istediğiniz Azure aboneliğini seçin.")
5. Sol gezinti bölmesindeki listenin üst kısmında yer alan **erişim denetimi (IAM)** seçeneğine tıklayın.
6. Sayfanın üst kısmındaki **Ekle** sekmesine tıklayın.
7. **Rol ataması Ekle**' ye tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Erişim denetimi, Ekle, rol ataması Ekle seçeneklerini belirleyin](_img/cloud-admin/access-control-add.png "Sol taraftaki listeden erişim denetimi ' ni seçin ve ardından Ekle ' yi seçin.")
8. Sağdaki giriş bölmesinde, bölmenin üst kısmındaki **rol** açılır listesine tıklayın, aşağı kaydırın ve **Kullanıcı erişimi Yöneticisi**' ni seçin.
9. Kullanıcı listesinde, yönetici yapmak istediğiniz kullanıcıya gidin ve bunları seçin. 
   > [!div class="mx-imgBorder"]
   > ![Rol, Kullanıcı erişimi Yöneticisi seçin](_img/cloud-admin/add-role-user-access-admin.png "Rol ' i seçin, Kullanıcı erişimi Yöneticisi ' ni seçin ve ardından yönetici yapmak için kullanıcının adını seçin.")
10. **Kaydet**’e tıklayın.
11. Seçtiğiniz kullanıcının bir Kullanıcı Erişim Yöneticisi olarak göründüğünü doğrulamak için **rol atamaları** sekmesine tıklayın.

Yeni yönetici artık [yönetim portalında](https://manage.visualstudio.com)oturum açabilir, sayfanın sol üst köşesindeki listeden aylık abonelikleri satın almak Için kullanılan Azure aboneliğini seçebilir ve bu abonelikleri yönetmeye başlayabilirsiniz.

> [!NOTE]
> Yönetici olarak kurmadığınız aylık aboneliklerinizi düzenlemek için kullanıcılara erişimi görürseniz, bu kullanıcıların, abonelikleri yönetmesine izin veren, temel alınan Azure aboneliğinde rolleri olabilir. Bu roller şunlardır: sahip, katkıda bulunan, hizmet yöneticisi veya ortak yönetici. Daha fazla bilgi için [faturalandırma yöneticileri Ekle](/azure/devops/organizations/billing/add-backup-billing-managers)' ye gidin.

aylık abonelikler Visual Studio hakkında daha fazla bilgi için bkz. satın alma abonelikleri altındaki [genel bakış](vscloud-overview.md) . Visual Studio aylık abonelikler satın almak için, adresindeki Visual Studio marketi ' ni ziyaret edin [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) .

## <a name="resources"></a>Kaynaklar
- [Abonelik desteği](https://aka.ms/vsadminhelp)

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
- [En fazla kullanımı belirleme](maximum-usage.md)