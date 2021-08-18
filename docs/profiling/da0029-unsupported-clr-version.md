---
title: DA0029-desteklenmeyen CLR sürümü | Microsoft Docs
description: Profil Oluşturma Araçları tarafından desteklenmeyen 1,1 .NET Framework kullanan bir uygulamayı profile çalışıyorsunuz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084330"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: desteklenmeyen CLR sürümü

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0029|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemi|Komut satırından profil oluşturma|
|İleti|Koleksiyon sırasında desteklenmeyen bir CLR sürümü algılandı. Yönetilen semboller doğru şekilde çözümlenmeyebilir.|
|Kural türü|Bilgi.|

## <a name="cause"></a>Nedeni
 Profil Oluşturma Araçları tarafından desteklenmeyen öğesini kullanan bir uygulamayı profile çalışıyorsunuz [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] .

## <a name="rule-description"></a>Kural açıklaması
 Bu uyarı, profil oluşturma araçlarının uygulamada çalışan yönetilen kodun sembollerini çözemediği için oluşur. Profil oluşturma araçları, çalıştıran uygulamalar için yönetilen kod sembollerini çözemez [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] .

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Yok.
