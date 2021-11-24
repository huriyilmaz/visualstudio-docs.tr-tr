---
title: Abonelik aboneliğinde üretim Visual Studio envanteri | Visual Studio Market
author: evanwindom
ms.author: amast
manager: amast
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 10/08/2021
ms.topic: conceptual
description: Yöneticilerin üretim öncesi envanterleri yürütme sorumluluğunu öğrenin
ms.openlocfilehash: 1d38c9e3f06c560df54b1a6af7592f5334603923
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132994880"
---
# <a name="inventory-of-pre-production-environment"></a>Üretim öncesi ortamın envanteri
Visual Studio abonelikleri, cihazları değil kullanıcıları sayarak varlık yönetimini basitleştirir.

Visual Studio yöneticilerinin belirli, Visual Studio kişilere **Abonelikler ataması gerekir.** Dev1, Dev2 gibi adlandırma kurallarına veya "FeatureTeam" gibi takım adlarının kullanımına **izin verilmez.**

Üretim öncesi ortamınızı envantere alma işlemini basitleştirmenin bazı yolları:
- Kullanıcı atamalarınızı gözden geçirme. Microsoft, abonelik atamalarını takip [Visual Studio için](https://manage.visualstudio.com/) Visual Studio Yönetim Portalı adlı bir web sitesi sağlar.
- Şirket içi veya bulut tabanlı Active Directory'nizi kullanarak kullanıcıları listele. Kullanıcı erişimini yönetmek için Active Directory kullanıyorsanız, geliştirme ve test kullanıcılarını dizin üyeliklerine göre tanımlayabilirsiniz.
- Sistemlerin envanterini oluşturmak için otomatik araçları kullanın. Ayrıca yazılım varlıklarınızı yönetmeye ve üretim öncesi ortamları üretim ortamlarından ayırt etmeye yardımcı olmak için bir yazılım envanteri aracı da kullanabilirsiniz. Microsoft'a sahip System Center, envanter işleminin bu kısmını otomatikleştirmeye yardımcı olmak için adlandırma kuralları oluşturabilir.
- El ile mutabakat konusunda yardım almak. Geliştirme ve test kullanıcılarınızı geliştirme ve test ortamınıza uzlaştırmanıza yardımcı olmak için personelinizi listele.

> [!NOTE]
> Visual Studio abonelikleri yazılımı, kabul testi veya geri bildirim dışında son kullanıcılar tarafından erişilen herhangi bir ortam, üretim veritabanına bağlanan, olağanüstü durum kurtarma veya üretim yedeklemeyi destekleyen ya da yoğun etkinlik dönemleri sırasında üretim için kullanılan ortamlar da dahil olmak üzere üretim ortamları için lisanslanmaz. Buna yönelik özel durumlar, lisanslama teknik bilgisinde özetlenen belirli abonelik [düzeylerine Visual Studio avantajları içerir.](https://aka.ms/vslicensing)  

## <a name="resources"></a>Kaynaklar
- [Visual Studio lisanslama teknik incelemesi](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Visual Studio abonelik desteği](https://aka.ms/vsadminhelp)
- [Toplu Lisanslama koşulları](https://www.microsoft.com/licensing/product-licensing/products.aspx)

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
- Satın [alma taahhütlerini](maximum-usage.md) izlemek için Maksimum Kullanım kullanma