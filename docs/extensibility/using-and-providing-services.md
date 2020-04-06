---
title: Hizmet Kullanma ve Sağlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698733"
---
# <a name="using-and-providing-services"></a>Hizmetleri Kullanma ve Sağlama
Hizmet, iki VSPackages arasındaki bir sözleşmedir. Bir VSPackage, başka bir VSPackage'ın tüketilmesi için belirli bir arayüz kümesi sunar. Örneğin, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> hizmet, yüklenenen herhangi bir VSPackage'a sunar. Bu hizmet, <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılabilecek arabirimi sağlar. Daha fazla bilgi için [bkz: Etkinlik Günlüğü'nün kullanımı.](../extensibility/how-to-use-the-activity-log.md)

 VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> arayüzü kullanarak kendi hizmetleri sunabilir ...

 Visual Studio aşağıdaki gibi önemli hizmetler sunar:

|IDE hizmeti|Açıklama|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Temel işlevlerle, VSPackages'le ve kayıt defteriyle ilgili IDE hizmetlerine erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Araçlar ve belge pencereleri oluşturma olanağı gibi IDE'de temel pencere ve Kullanıcı Arabirimi ile ilgili işlevsellik sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Projeleri sayısalama, yeni projeler oluşturma ve proje değişikliklerini izleme gibi çözümle ilgili temel işlevleri sağlar.|

## <a name="in-this-section"></a>Bu Bölümde
- [Hizmet Esasları](../extensibility/internals/service-essentials.md) Visual Studio hizmetinin önemli unsurlarını sunar.

- [Nasıl Yapilir: Hizmet Alın](../extensibility/how-to-get-a-service.md) Bir hizmeti nasıl isteyeceğimi (tüketeceklerini) tartışır.

- [Nasıl yapilir: Hizmet Sağlama](../extensibility/how-to-provide-a-service.md) Bir hizmetin nasıl sağverilebildiğini tartışır.

- [Nasıl: Bir Asynchronous Visual Studio Service sağlayın](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Eşzamanlı bir hizmetin nasıl sağverilebildiğini tartışır.

- [Nasıl yapılsın: HizmetlerLe Sorun Giderme](../extensibility/how-to-troubleshoot-services.md) Ortak sorunları tartışır ve bunlara çözümler sunar.

## <a name="related-sections"></a>İlgili Bölümler
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
