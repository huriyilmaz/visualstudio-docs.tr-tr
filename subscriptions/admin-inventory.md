---
title: Abonelik aboneliğinde üretim Visual Studio envanteri | Visual Studio Pazar
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/19/2021
ms.topic: conceptual
description: Yöneticilerin üretim öncesi envanterleri yürütme sorumluluğunu öğrenin
ms.openlocfilehash: f6b1e1ebc02a986be86fb48578a4be47ccc3dfaa
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123966319"
---
# <a name="inventory-of-pre-production-environment"></a>Üretim öncesi ortamın envanteri
Visual Studio abonelikleri, cihazları değil kullanıcıları sayarak varlık yönetimini basitleştirir.

Visual Studio yöneticilerinin belirli, adlandırılmış Visual Studio **abonelikleri ataması gerekir.** Dev1, Dev2 gibi adlandırma kurallarına veya "FeatureTeam" gibi takım adlarının kullanımına **izin verilmez.**

Üretim öncesi ortamınızı envantere alma işlemini basitleştirmenin bazı yolları:
- Kullanıcı atamalarınızı gözden geçirme. Microsoft, abonelik atamalarını takip [Visual Studio için](https://manage.visualstudio.com/) Visual Studio Yönetim Portalı adlı bir web sitesi sağlar.
- Şirket içi veya bulut tabanlı Active Directory'nizi kullanarak kullanıcıları listele. Kullanıcı erişimini yönetmek için Active Directory kullanıyorsanız, geliştirme ve test kullanıcılarını dizin üyeliklerine göre tanımlayabilirsiniz.
- Sistemlerin envanterini oluşturmak için otomatik araçları kullanın. Ayrıca yazılım varlıklarınızı yönetmeye ve üretim öncesi ortamları üretim ortamlarından ayırt etmeye yardımcı olmak için bir yazılım envanteri aracı da kullanabilirsiniz. Microsoft'a sahip System Center, envanter işleminin bu kısmını otomatikleştirmeye yardımcı olmak için adlandırma kuralları oluşturur.
- El ile mutabakat konusunda yardım almak. Geliştirme ve test kullanıcılarınızı geliştirme ve test ortamınıza uzlaştırmanıza yardımcı olmak için personelinizi listele.

> [!NOTE]
> Visual Studio abonelikleri yazılımı, kabul testi veya geri bildirim dışında son kullanıcılar tarafından erişilen herhangi bir ortam, üretim veritabanına bağlanan, olağanüstü durum kurtarmayı veya üretim yedeklemeyi destekleyen ya da yoğun etkinlik dönemleri sırasında üretim için kullanılan ortamlar da dahil olmak üzere üretim ortamları için lisanslanmaz. Buna yönelik özel durumlar, lisanslama teknik bilgisinde özetlenen belirli abonelik [düzeylerine Visual Studio avantajları içerir.](https://aka.ms/vslicensing)  

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