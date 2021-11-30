---
title: Visual Studio abonelikte ön üretim stoku | Visual Studio marketi
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 10/08/2021
ms.topic: conceptual
description: Yöneticiler hakkında, ön üretim envanterleri yürütme sorumluluğunu öğrenin
ms.openlocfilehash: d4b5dcaa79376d792620b50b2eba744e41027209
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133257809"
---
# <a name="inventory-of-pre-production-environment"></a>Üretim öncesi ortam envanteri
Visual Studio abonelikler, cihazları yerine kullanıcıları sayarak varlık yönetimini basitleştirir.

Visual Studio yöneticileri **, adlandırılmış bireylere** Visual Studio abonelikleri atamalıdır. Dev1, Dev2 veya "FeatureTeam" gibi takım adlarının kullanımı gibi adlandırma kurallarına **izin verilmez**.

Üretim öncesi ortamınızın envanterini almayı kolaylaştırmak için bazı yollar şunlardır:
- Kullanıcı atamalarınızı gözden geçirin. Microsoft, Visual Studio abonelik atamalarını izlemenize yardımcı olması için [Visual Studio yönetim portalı](https://manage.visualstudio.com/) adlı bir web sitesi sağlar.
- Kullanıcıları listelemek için şirket içi veya bulut tabanlı Active Directory kullanın. Kullanıcı erişimini yönetmek için Active Directory kullanıyorsanız, geliştirme ve kullanıcıları Dizin üyeliğiyle test edebilirsiniz.
- Envanter sistemleri için otomatikleştirilmiş araçları kullanın. Ayrıca, yazılım varlıklarınızı yönetmenize ve üretim öncesi ortamlarını üretimden ayırt etmenize yardımcı olması için bir yazılım envanteri aracı da kullanmanız gerekebilir. Microsoft System Center birçok müşteri, envanter sürecinin bu bölümünü otomatik hale getirmeye yardımcı olmak için adlandırma kuralları oluşturur.
- El ile mutabakata yönelik yardım alın. Geliştirme ve test ortamlarınızla geliştirme ve test kullanıcılarınız için test etmenize yardımcı olmak üzere personelinizi listeleme.

> [!NOTE]
> Visual Studio abonelik yazılımı, son kullanıcılar tarafından kabul testi veya geri bildirim, bir üretim veritabanına bağlanan ortam, olağanüstü durum kurtarma veya üretim yedeklemesini destekleme veya en yüksek etkinlik dönemlerinde üretim için kullanılan ortamlar dahil olmak üzere üretim ortamları için lisanslanır. buna özel durumlar, [Visual Studio lisanslama teknik incelemesi](https://aka.ms/vslicensing)içinde özetlenen belirli abonelik düzeyleri için özel avantajlar içerir.  

## <a name="resources"></a>Kaynaklar
- [Visual Studio lisanslama teknik incelemesi](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Visual Studio abonelik desteği](https://aka.ms/vsadminhelp)
- [Toplu Lisanslama Koşulları](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yöneticiler için sorumluluklar hakkında daha fazla bilgi edinin:
- [Yönetici sorumlulukları](admin-responsibilities.md)
- [Büyük takımları ve dışarıdan yüklenicileri yönetme](manage-teams.md)
- [Kullanıcı atamalarını izleme ve siparişleri işleme](assignments-orders.md)
- Satın alma taahhütlerini izlemek için [maksimum kullanımı](maximum-usage.md) kullanın