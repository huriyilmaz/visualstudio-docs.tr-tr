---
title: 'CA1600: Boş işlem önceliğini kullanmayın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2075918672452e222ba4becae915712ba20ff0d0
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440021"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Boş işlem önceliğini kullanmayın

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategori|Microsoft. Mobility|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Bu kural, işlem `ProcessPriorityClass.Idle` olarak ayarlandığında oluşur.

## <a name="rule-description"></a>Kural açıklaması
İşlem önceliğini Boşta olarak ayarlamayın. @No__t-0 olan süreçler, aksi durumda boşta kalması durumunda CPU 'nun kaplamasına neden olur ve bu nedenle beklemeyi engeller.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
İşlem `ProcessPriorityClass.BelowNormal` olarak ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kural yalnızca boş işlem önceliği gerekli olduğunda ve hareketlilik konuları güvenli bir şekilde yoksayılarak bastırılır.
