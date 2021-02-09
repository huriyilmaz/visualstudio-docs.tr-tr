---
title: Sunulan hizmetler (kaynak denetimi VSPackage) | Microsoft Docs
description: VSPackages 'ın, Visual Studio IDE ve VSPackages ile etkileşme dahil olmak üzere Hizmetler aracılığıyla nasıl paylaşılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 515422266ce3d719319c4ba9717106af16e84f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910994"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan Hizmetler (Kaynak Denetimi VSPackage’ı)
Hizmetler, işlevin VSPackages arasında ve Visual Studio tümleşik geliştirme ortamı (IDE) ile yüklü VSPackages 'ler arasında paylaşıldığı birincil mekanizmadır. Hizmetlerin ayrıntılı açıklaması ve Visual Studio IDE 'deki önem derecesi için bkz.[Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Kaynak denetim hizmeti
 Visual Studio, iki katmanlı hizmet, IDE düzeyi hizmet ve paket düzeyi hizmet sunar. Visual Studio IDE yerel olarak IDE düzeyi hizmetler sağlar. Kaynak denetim paketi bu hizmetlerden bazılarını tüketir. Kaynak denetim paketi VSPackage, kendi kendine özel bir kaynak denetimi hizmeti sağlayarak kaynak denetimi işlevselliğini paylaşır. Kaynak denetim paketi, Visual Studio IDE tarafından kullanılabilecek bir sözleşme biçiminde uygulanan kaynak denetimi ile ilgili arabirimlerin kümesini kapsüller.

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
