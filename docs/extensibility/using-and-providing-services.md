---
title: Hizmetleri kullanma ve sağlama | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698733"
---
# <a name="using-and-providing-services"></a>Hizmetleri Kullanma ve Sağlama
Hizmet iki VSPackages arasında bir sözleşmedir. Bir VSPackage, başka bir VSPackage kullanmak için belirli bir arabirim kümesi sunar. Örneğin, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> hizmeti her türlü VSPackage hizmetine sunar. Bu hizmet, <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> etkinlik günlüğüne yazmak için kullanılabilecek arabirimi sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: etkinlik günlüğünü kullanma](../extensibility/how-to-use-the-activity-log.md).

 VSPackages, arabirimini kullanarak kendi hizmetlerini sunabilir <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .

 Visual Studio aşağıdakiler gibi önemli hizmetler sunar:

|IDE hizmeti|Description|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Temel işlevlerle, VSPackages ve kayıt defteriyle ilgili IDE hizmetlerine erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|IDE 'de araçlar ve belge pencereleri oluşturma gibi temel bir Pencereleme ve Kullanıcı arabirimi ile ilgili işlevsellik sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Projeleri listeleme, yeni projeler oluşturma ve proje değişikliklerini izleme gibi çözümle ilgili temel işlevleri sağlar.|

## <a name="in-this-section"></a>Bu Bölümde
- [Service Essentials](../extensibility/internals/service-essentials.md) Bir Visual Studio hizmetinin önemli öğelerini gösterir.

- [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md) Bir hizmetin nasıl isteneceğini (kullanacağınızı) açıklar.

- [Nasıl yapılır: hizmet sağlama](../extensibility/how-to-provide-a-service.md) Hizmetini nasıl sağlayabileceğinizi açıklar.

- [Nasıl yapılır: zaman uyumsuz bir Visual Studio hizmeti sağlama](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Bir zaman uyumsuz hizmeti nasıl sağlayabileceğinizi açıklar.

- [Nasıl yapılır: hizmetler sorunlarını giderme](../extensibility/how-to-troubleshoot-services.md) Yaygın sorunları açıklar ve bunlara çözümler sunar.

## <a name="related-sections"></a>İlgili Bölümler
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
