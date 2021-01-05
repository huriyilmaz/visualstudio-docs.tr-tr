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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a97ed69d37330132196f0334f5684c0704c5fd2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876083"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan Hizmetler (Kaynak Denetimi VSPackage’ı)
Hizmetler, işlevin VSPackages arasında ve Visual Studio tümleşik geliştirme ortamı (IDE) ile yüklü VSPackages 'ler arasında paylaşıldığı birincil mekanizmadır. Hizmetlerin ayrıntılı açıklaması ve Visual Studio IDE 'deki önem derecesi için bkz.[Hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Kaynak denetim hizmeti
 Visual Studio, iki katmanlı hizmet, IDE düzeyi hizmet ve paket düzeyi hizmet sunar. Visual Studio IDE yerel olarak IDE düzeyi hizmetler sağlar. Kaynak denetim paketi bu hizmetlerden bazılarını tüketir. Kaynak denetim paketi VSPackage, kendi kendine özel bir kaynak denetimi hizmeti sağlayarak kaynak denetimi işlevselliğini paylaşır. Kaynak denetim paketi, Visual Studio IDE tarafından kullanılabilecek bir sözleşme biçiminde uygulanan kaynak denetimi ile ilgili arabirimlerin kümesini kapsüller.

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
