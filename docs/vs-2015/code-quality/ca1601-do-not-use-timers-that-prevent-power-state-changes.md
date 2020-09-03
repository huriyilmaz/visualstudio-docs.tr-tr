---
title: 'CA1601: güç durumu değişikliklerini önleyen zamanlayıcılar kullanmayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7928b2fff8c12ca3f0cc3c58bee31fe5809517e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545645"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Güç durumu değişikliklerini önleyen zamanlayıcılar kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategori|Microsoft. Mobility|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir zamanlayıcının bir saniye başına birden fazla kez gerçekleşmesi için ayarlanmış bir aralığı vardır.

## <a name="rule-description"></a>Kural Tanımı
 Saniyede bir kez daha fazla yoklama yapın veya saniye başına bir kez daha sık gerçekleşen zamanlayıcılar kullanın. Yüksek frekanslı dönemsel faaliyet CPU'yu meşgul tutar ve sabit diski gösteren güç tasarruflu zamanlayıcılarla müdahale edilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Zamanlayıcı aralıklarını saniye başına bir kez gerçekleşmeyecek şekilde ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural, yalnızca süreölçeri bir saniyede birden fazla kez tetiklebilme gerekliyse ve hareketlilik konuları güvenle yoksayılırsa bastırılır.
