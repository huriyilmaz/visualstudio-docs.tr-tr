---
title: Sunulan hizmetler (kaynak denetimi VSPackage) | Microsoft Docs
description: Visual Studio ıde ve vspackages ile etkileşim de dahil olmak üzere vspackages 'ın hizmetler aracılığıyla nasıl paylaşılacağını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062764"
---
# <a name="services-provided-source-control-vspackage"></a>Sağlanan Hizmetler (Kaynak Denetimi VSPackage’ı)
hizmetler, işlevin vspackages ve Visual Studio tümleşik geliştirme ortamı (ıde) ve yüklü vspackages 'ler arasında paylaşıldığı birincil mekanizmadır. hizmetlerin ayrıntılı açıklaması ve Visual Studio ıde 'de önemini öğrenmek için bkz.[hizmetleri kullanma ve sağlama](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Kaynak denetim hizmeti
 Visual Studio, iki adet hizmet katmanı, ıde düzeyi hizmet ve paket düzeyi hizmet sunar. Visual Studio ıde yerel olarak ıde düzeyi hizmetler sağlar. Kaynak denetim paketi bu hizmetlerden bazılarını tüketir. Kaynak denetim paketi VSPackage, kendi kendine özel bir kaynak denetimi hizmeti sağlayarak kaynak denetimi işlevselliğini paylaşır. kaynak denetim paketi, Visual Studio ıde tarafından kullanılabilecek bir sözleşme biçiminde uygulanan kaynak denetimi ile ilgili arabirimlerin kümesini kapsüller.

## <a name="see-also"></a>Ayrıca bkz.
- [Tasarım Öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
