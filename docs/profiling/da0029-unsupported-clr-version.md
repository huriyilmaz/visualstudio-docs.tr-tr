---
title: DA0029 - Desteklenmeyen CLR Sürüm | Microsoft Docs
description: Uygulama tarafından desteklenen .NET Framework 1.1 kullanan bir uygulamanın profilini Profil Oluşturma Araçları.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 608135e6600dd64e7edd14eeccfe279962e412b9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626937"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Desteklenmeyen CLR sürümü

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0029|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Komut satırdan profil oluşturma|
|İleti|Koleksiyon sırasında desteklenmeyen bir CLR sürümü algılandı. Yönetilen semboller doğru çözümleyene kadar devam ediyor olabilir.|
|Kural türü|Bilgi.|

## <a name="cause"></a>Nedeni
 Uygulama tarafından destek almayan kullanan [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] bir uygulamanın profilini Profil Oluşturma Araçları.

## <a name="rule-description"></a>Kural açıklaması
 Profil oluşturma araçları uygulamada çalışan yönetilen kod için sembolleri çözümleyemezse bu uyarı oluşur. Profil oluşturma araçları, çalıştıran uygulamalar için yönetilen kod sembollerini çözümleyemezse. [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Yok.
