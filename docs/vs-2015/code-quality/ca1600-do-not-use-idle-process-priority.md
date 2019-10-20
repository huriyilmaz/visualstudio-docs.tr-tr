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
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669291"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Boş işlem önceliğini kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategori|Microsoft. Mobility|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bu kural, işlem `ProcessPriorityClass.Idle` olarak ayarlandığında oluşur.

## <a name="rule-description"></a>Kural Tanımı
 İşlem önceliğini Boşta olarak ayarlamayın. @No__t_0 olan süreçler, aksi durumda boşta kalması durumunda CPU 'nun kaplamasına neden olur ve bu nedenle beklemeyi engeller.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İşlem `ProcessPriorityClass.BelowNormal` olarak ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural yalnızca boş işlem önceliği gerekli olduğunda ve hareketlilik konuları güvenli bir şekilde yoksayılarak bastırılır.
