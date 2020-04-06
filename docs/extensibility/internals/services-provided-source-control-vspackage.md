---
title: Sağlanan Hizmetler (Kaynak Kontrol VSPackage) | Microsoft Dokümanlar
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
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705404"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan Hizmetler (Kaynak Denetimi VSPackage’ı)
Hizmetler, işlevselliğin VSPackages arasında ve Visual Studio tümleşik geliştirme ortamı (IDE) ve yüklü VSPackages'i arasında paylaşıldığı birincil mekanizmadır. Visual Studio IDE'deki hizmetlerin ayrıntılı açıklaması[ve](../../extensibility/using-and-providing-services.md)önemi için bkz.

## <a name="the-source-control-service"></a>Kaynak Kontrol Hizmeti
 Visual Studio iki hizmet katmanı, IDE düzeyinde hizmetler ve paket düzeyinde hizmetler sunmaktadır. Visual Studio IDE yerel olarak IDE düzeyinde hizmetler sunar. Kaynak denetim paketi bu hizmetlerden bazılarını tüketir. VSPackage olarak kaynak kontrol paketi, kendi özel kaynak kontrol hizmeti sunarak kaynak kontrol işlevini paylaşır. Kaynak denetim paketi, Visual Studio IDE tarafından kullanılabilecek bir sözleşme şeklinde uygulanan kaynak denetimi ile ilgili arabirimler kümesini kapsüller.

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
