---
title: Aylık Abonelikler için Yönetici Ayarlama | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: conceptual
description: Aylık Abonelikler için Yöneticiler Ayarlama
ms.openlocfilehash: c9a1303d4111f0ec4a0c1249a25e49fc40cf26de
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232651"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Visual Studio aylık abonelikleri için yöneticiler ayarlama

Visual Studio aylık abonelikleri yöneticiler tarafından yönetilir. Bu kişiler abonelikler atayabilir, atamaları düzenleyebilir, abonelik ekleyebilir veya silebilir ve diğer abonelik yönetimi görevlerini gerçekleştirebilir.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Azure abonelik sahibi ilk yöneticidir

Satın alma işlemlerinde kullanılan Azure aboneliğinin sahibi olarak Visual Studio aylık abonelikleri satın aldığınızda, otomatik olarak bu abonelikler için yönetici olarak ayarlanırsınız.

[Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions)üzerinden veya bir Bulut Çözüm Sağlayıcısı'na başvurarak aylık aboneliksatın alabilirsiniz. Visual Studio Marketplace üzerinden satın alırsanız, satın alma deneyiminin sonunda, kullanıcıları yönetmek için bir fırsat elde elabilirsiniz. Bu seçeneği n seçimi sizi Visual Studio Abonelikleri [https://manage.visualstudio.com](https://manage.visualstudio.com)Yönetim Portalı'na götürecektir.

Abonelik satın aldıktan sonra, istediğiniz zaman [Yönetim Portalı'nı](https://manage.visualstudio.com) ziyaret edebilirsiniz. Portalda oturum açmave sol üst köşedeki uygun Azure aboneliğini seçmeniz.

Aylık abonelikleri satın almak için kullanılan Azure aboneliğinin sahibi olarak ek yöneticiler de atayabilirsiniz.

## <a name="add-administrators"></a>Yönetici ekleme

Yönetici eklemek için:

1. azure portalına [portal.azure.com'dan](https://portal.azure.com)bağlanın.
2. Visual Studio aylık aboneliklerini satın almak için kullandığınız hesapla oturum açın.
3. **Azure hizmetleri**altında Maliyet Yönetimi **+ Faturalandırma'yı**seçin.
   > [!div class="mx-imgBorder"]
   > ![Azure hizmetleri altında Maliyet Yönetimi + Faturalandırma'yı seçin](_img/cloud-admin/azure-cost-billing.png)
4. **Aboneliklerim** listesinde, satın alma işlemi yapmak için kullandığınız Azure aboneliğini seçin.
   > [!div class="mx-imgBorder"]
   > ![Abonelik seçin](_img/cloud-admin/subscription-list.png)
5. Sol gezinti bölmesinde listenin en üstünde bulunan **Access denetimi'ni (IAM)** tıklatın.
6. Sayfanın üst kısmındaki **Ekle** sekmesini tıklatın.
7. **Rol Atama ekle'yi**tıklatın.
   > [!div class="mx-imgBorder"]
   > ![Access denetimini seçin, ekle, rol ataması ekle](_img/cloud-admin/access-control-add.png)
8. Sağdaki fly-out bölmesinde, bölmenin üst kısmındaki **Role** açılır bölümüne tıklayın, aşağı kaydırın ve **Kullanıcı Erişim Yöneticisi'ni**seçin.
9. Kullanıcı listesinde, yönetici yapmak istediğiniz kullanıcıya gidin ve bunları seçin. 
   > [!div class="mx-imgBorder"]
   > ![Rol, Kullanıcı erişim yöneticisi seçin](_img/cloud-admin/add-role-user-access-admin.png)
10. **Kaydet**'e tıklayın.
11. Seçtiğiniz kullanıcının kullanıcı erişim yöneticisi olarak görüntülediğini doğrulamak için **Rol atamaları** sekmesini tıklatın.

Yeni yönetici artık [Yönetim Portalı'nda](https://manage.visualstudio.com)oturum açabilir, sayfanın sol üst köşesindeki listeden aylık abonelikleri satın almak için kullanılan aynı Azure aboneliğini seçebilir ve bu abonelikleri yönetmeye başlayabilir.

> [!NOTE]
> Yönetici olarak oluşturmadığınız aylık aboneliklerinizi yönetme erişimi olan kullanıcıların temel Azure aboneliğinde abonelikleri yönetmelerine olanak tanıyan rolleri olabilir. Bu roller şunlardır: sahibi, katılımcı, hizmet yöneticisi veya co-admin. Daha fazla bilgi için [fatura yöneticileri ekle'yi](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts)ziyaret edin.

Visual Studio aylık abonelikleri hakkında daha fazla bilgi için Satın Alma abonelikleri altındaki [Genel Bakış'a](vscloud-overview.md) bakın. Visual Studio aylık abonelikleri satın almak için [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)Visual Studio Marketplace adresini ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Tek tek abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Maksimum kullanımı belirleme](maximum-usage.md)



