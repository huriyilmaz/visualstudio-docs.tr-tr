---
title: Aylık abonelikler ve abonelikler Visual Studio yöneticileri | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/21/2021
ms.topic: how-to
description: Aylık Abonelikler için yöneticileri ayarlama
ms.openlocfilehash: cce8753392e52523f7125d6a4943b757adf94e57
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133256327"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Aylık abonelikler için Visual Studio ayarlama

Visual Studio abonelikler yöneticiler tarafından yönetilir. Bu kişiler abonelik atayabilirsiniz, atamaları düzenleyebilir, abonelik ekleyebilir veya silebilir ve diğer abonelik yönetim görevlerini gerçekleştirebilir.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>Azure aboneliği sahibi ilk yöneticidir

Aylık Visual Studio satın aldığınız zaman, satın almaları yapmak için kullanılan Azure aboneliğinin sahibi olarak otomatik olarak bu abonelikler için yönetici olarak ayarlanırsınız.

Visual Studio Market üzerinden veya [bir Bulut Çözümü Sağlayıcısı](https://marketplace.visualstudio.com/subscriptions)ile iletişim kurarak aylık abonelik satın alabilirsiniz. Visual Studio Market üzerinden satın aldıysanız, satın alma deneyiminin sonunda size kullanıcıları yönetme fırsatı sağlanır. Bu seçeneğin belirlenirken, Visual Studio Abonelikler Yönetim Portalı [https://manage.visualstudio.com](https://manage.visualstudio.com) - .

Abonelik satın aldıktan sonra, yönetim portalını [herhangi bir zamanda](https://manage.visualstudio.com) ziyaret edebilirsiniz. Portalda oturum açın ve sol üst köşeden uygun Azure aboneliğini seçin.

Aylık abonelikleri satın almak için kullanılan Azure aboneliğinin sahibi olarak ek yöneticiler de atabilirsiniz.

## <a name="add-admins"></a>Yönetici ekleme

Yönetici eklemek için:

1. Bağlan Azure portal [portal.azure.com.](https://portal.azure.com)
2. Aylık abonelikleri satın almak için Visual Studio oturum açın.
3. **Azure hizmetleri'nin** altında Maliyet **Yönetimi + Faturalama'ya seçin.**
   > [!div class="mx-imgBorder"]
   > ![Azure hizmetleri'nin altında Maliyet Yönetimi + Faturalama'yi seçin](_img/cloud-admin/azure-cost-billing.png "Azure hizmetleri grubundan Maliyet Yönetimi'ne seçin")
4. **Aboneliklerim listesinde,** satın alma için kullanılan Azure aboneliğini seçin.
   > [!div class="mx-imgBorder"]
   > ![Abonelik seçme](_img/cloud-admin/subscription-list.png "Satın alma için kullanmak istediğiniz Azure aboneliğini seçin.")
5. Sol gezinti bölmesinde listenin üst kısmında bulunan Erişim denetimi **(IAM)**'a tıklayın.
6. Sayfanın **üst** kısmında Ekle sekmesine tıklayın.
7. Rol **ataması ekle'ye tıklayın.**
   > [!div class="mx-imgBorder"]
   > ![Erişim denetimi, Ekle, Rol ataması ekle'yi seçin](_img/cloud-admin/access-control-add.png "Sol tarafta yer alan listeden Erişim denetimi'ne ve ardından Ekle'ye tıklayın.")
8. Sağ bölmede açılır bölmede, bölmenin  üst kısmında Rol açılan bölmesine tıklayın, aşağı kaydırın ve Kullanıcı Erişimi **Yöneticisi'ni seçin.**
9. Kullanıcı listesinde ekranı aşağı kaydırarak yönetici yapmak istediğiniz kullanıcıya gidin ve seçin. 
   > [!div class="mx-imgBorder"]
   > ![Rol, Kullanıcı erişimi yöneticisi'ni seçin](_img/cloud-admin/add-role-user-access-admin.png "Rol'leri seçin, Kullanıcı Erişimi Yöneticisi'ni seçin ve ardından kullanıcı adını seçerek yönetici olarak seçin.")
10. **Kaydet**’e tıklayın.
11. Seçtiğiniz kullanıcının **Kullanıcı Erişimi Yöneticisi** olarak görüntülendiğinden emin olmak için Rol atamaları sekmesine tıklayın.

Yeni yönetici artık Yönetim [Portalı'da](https://manage.visualstudio.com)oturum açın, sayfanın sol üst köşesindeki listeden aylık abonelikleri satın almak için kullanılan Azure aboneliğini seçin ve bu abonelikleri yönetmeye başlayabilir.

> [!NOTE]
> Yönetici olarak oluşturmadınız aylık aboneliklerinizi düzenleme erişimine sahip kullanıcılar görüyorsanız, abonelikleri yönetmelerine olanak sağlayan temel Azure aboneliğinde rolleri olabilir. Bu roller şunlardır: sahip, katkıda bulunan, hizmet yöneticisi veya ortak yönetici. Daha fazla bilgi için Faturalama [yöneticileri ekleme'yi ziyaret edin.](/azure/devops/organizations/billing/add-backup-billing-managers)

Aylık abonelikler hakkında Visual Studio için Abonelik satın alma altındaki [Genel](vscloud-overview.md) Bakış'a bakın. Aylık Visual Studio satın almak için sayfasındaki Visual Studio Market'i ziyaret [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription) edin.

## <a name="resources"></a>Kaynaklar
- [Abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikleri yönetme hakkında daha fazla Visual Studio edinin.
- [Bireysel abonelik atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)