---
title: Aylık abonelikler için yöneticileri ayarlama | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Aylık abonelikler için yöneticileri ayarlama
ms.openlocfilehash: d9ae6f8aac48b9d54b851d543a72fd98854c1131
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235218"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Visual Studio aylık abonelikleri için yöneticileri ayarlama

Visual Studio aylık abonelikleri yöneticiler tarafından yönetilir. Bu bireyler abonelik atayabilir, atamaları düzenleyebilir, abonelik ekleyebilir veya silebilir ve diğer abonelik yönetim görevlerini gerçekleştirebilir.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Azure abonelik sahibi ilk yöneticiydir

Satın alma işlemleri yapmak için kullanılan Azure aboneliğinin sahibi olarak Visual Studio aylık abonelikleri satın aldığınızda, bu abonelikler için otomatik olarak bir yönetici olarak ayarlanır.

Aylık abonelikleri [Visual Studio Market](https://marketplace.visualstudio.com/subscriptions)aracılığıyla veya bir bulut çözümü sağlayıcısına başvurarak satın alabilirsiniz. Satın alma deneyiminin sonunda Visual Studio Market aracılığıyla satın alırsanız, kullanıcıları yönetmeye yönelik bir fırsat sunulur. Bu seçeneğin belirlenmesi sizi Visual Studio abonelikleri yönetim portalı- [https://manage.visualstudio.com](https://manage.visualstudio.com)götürür.

Abonelikleri satın aldıktan sonra istediğiniz zaman [yönetim portalını](https://manage.visualstudio.com) ziyaret edebilirsiniz. Portalda oturum açmanız yeterlidir ve sol üst köşedeki uygun Azure aboneliğini seçin.

Aylık abonelikleri satın almak için kullanılan Azure aboneliğinin sahibi olarak, ek yöneticiler de atayabilirsiniz.

## <a name="add-administrators"></a>Yönetici Ekle

Yöneticiler eklemek için:

1. [Portal.Azure.com](https://portal.azure.com)adresinden Azure portalına bağlanın.
2. Visual Studio aylık aboneliklerini satın almak için kullandığınız hesapla oturum açın.
3. Sol gezinti bölmesinde, **maliyet yönetimi + faturalandırma**' e gidin.
4. **Aboneliklerim** listesinde, satın almayı yapmak Için kullandığınız Azure aboneliğini seçin.
5. Sol gezinti bölmesindeki listenin üst kısmına yakın bir konumda bulunan **erişim denetimi**' ne tıklayın.
6. Sayfanın üst kısmındaki **Ekle** sekmesine tıklayın.
7. **Rol ataması Ekle**' ye tıklayın.
8. Sağdaki giriş bölmesinde, bölmenin üst kısmındaki **rol** açılır listesine tıklayın, aşağı kaydırın ve **Kullanıcı erişimi Yöneticisi**' ni seçin.
9. Kullanıcı listesinde, yönetici yapmak istediğiniz kullanıcıya gidin ve bunları seçin. 
10. **Kaydet** düğmesine tıklayın.
11. Seçtiğiniz kullanıcının bir Kullanıcı Erişim Yöneticisi olarak göründüğünü doğrulamak için **rol atamaları** sekmesine tıklayın.

Yeni yönetici artık [yönetim portalında](https://manage.visualstudio.com)oturum açabilir, sayfanın sol üst köşesindeki listeden aylık abonelikleri satın almak Için kullanılan Azure aboneliğini seçebilir ve bu abonelikleri yönetmeye başlayabilirsiniz.

> [!NOTE]
> Yönetici olarak kurmadığınız aylık aboneliklerinizi düzenlemek için kullanıcılara erişimi görürseniz, bu kullanıcıların, abonelikleri yönetmesine izin veren, temel alınan Azure aboneliğinde rolleri olabilir. Bu roller şunlardır: sahip, katkıda bulunan, hizmet yöneticisi veya ortak yönetici. Daha fazla bilgi için [faturalandırma yöneticileri Ekle](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts)' ye gidin.

Visual Studio aylık abonelikleri hakkında daha fazla bilgi için, satın alma abonelikleri altındaki [genel bakış](vscloud-overview.md) bölümüne bakın. Visual Studio aylık abonelikleri satın almak için [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)Visual Studio Market ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)



