---
title: 'CA1600: boşta işlem önceliği kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545684"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Boş işlem önceliğini kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategori|Microsoft. Mobility|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bu kural, işlem olarak ayarlandığında oluşur `ProcessPriorityClass.Idle` .

## <a name="rule-description"></a>Kural Tanımı
 İşlem önceliğini Boşta olarak ayarlamayın. Bu işlem, `System.Diagnostics.ProcessPriorityClass.Idle` Aksi durumda boşta kaldığında CPU 'yu kaplayacaktır ve bu nedenle beklemeyi engeller.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İşlem olarak ayarlayın `ProcessPriorityClass.BelowNormal` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural yalnızca boş işlem önceliği gerekli olduğunda ve hareketlilik konuları güvenli bir şekilde yoksayılarak bastırılır.
