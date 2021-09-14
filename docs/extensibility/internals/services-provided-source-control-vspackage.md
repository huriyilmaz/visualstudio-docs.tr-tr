---
title: Sağlanan Hizmetler (Kaynak Denetimi VSPackage) | Microsoft Docs
description: VSPackage'ların IDE ve VSPackage'ları ile etkileşim Visual Studio hizmetler aracılığıyla işlevselliği nasıl paylaştığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 34ef5c26184f06b0a9bec3307f4c6af155f51586
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627327"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan Hizmetler (Kaynak Denetimi VSPackage’ı)
Hizmetler, işlevlerin VSPackage'lar arasında ve Visual Studio tümleşik geliştirme ortamı (IDE) ile yüklü VSPackage'ları arasında paylaştırılır. Hizmetlerin ayrıntılı açıklaması ve IDE'de Visual Studio için bkz. Hizmetleri Kullanma[ve Sağlama.](../../extensibility/using-and-providing-services.md)

## <a name="the-source-control-service"></a>Kaynak Denetimi Hizmeti
 Visual Studio iki hizmet katmanı sağlar: IDE düzeyi hizmetler ve paket düzeyi hizmetler. IDE Visual Studio yerel olarak IDE düzeyinde hizmetler sağlar. Kaynak denetim paketi bu hizmetlerden bazılarını tüketir. VSPackage olarak kaynak denetim paketi, kendi özel bir kaynak denetimi hizmeti sağlayarak kaynak denetimi işlevselliğini paylaştırır. Kaynak denetim paketi, kaynak denetimiyle ilgili arabirimler kümesi tarafından IDE tarafından kullanılmaktadır bir sözleşme şeklinde Visual Studio içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
