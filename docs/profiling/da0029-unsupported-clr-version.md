---
title: 'DA0029: Desteklenmeyen CLR Sürümü | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbc0bfcdb49557e56711b60dca11977a3504d907
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777521"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Desteklenmeyen CLR sürümü

|||
|-|-|
|Kural Id|DA0029|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Komut satırından profil oluşturma|
|İleti|Toplama sırasında desteklenmeyen bir CLR sürümü algılandı. Yönetilen semboller doğru çözülmeyebilir.|
|Kural türü|Bilgi.|

## <a name="cause"></a>Nedeni
 Profil Oluşturma Araçları tarafından desteklenmeyen [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] bir uygulamanın profilini çıkarmaya çalışıyorsunuz.

## <a name="rule-description"></a>Kural açıklaması
 Profil oluşturma araçları uygulamada çalışan yönetilen kod için sembolleri çözümleyemeyeceğinden bu uyarı oluşur. Profil oluşturma araçları, [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]'yi çalıştıran uygulamalar için yönetilen kod sembollerini çözemez.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Yok.
