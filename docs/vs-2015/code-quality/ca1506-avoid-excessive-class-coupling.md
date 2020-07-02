---
title: 'CA1506: aşırı sınıf bağlantısından kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545710"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Aşırı sınıf bağlantısından kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir tür ya da yöntem diğer birçok türle birlikte bağlanmış.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer.

 Yüksek ölçüde sınıf bağlantısı olan türler ve Yöntemler devam etmek zor olabilir. Düşük ve yüksek bir cohede gösteren türler ve yöntemlere sahip olmak iyi bir uygulamadır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu ihlalin giderilmesi için, türü veya yöntemi, bağlandığı türlerin sayısını azaltmak için yeniden tasarlayadeneyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür veya yöntem hala bakım yapılabilir olarak kabul edildiğinde bu uyarıyı hariç tutun.

## <a name="see-also"></a>Ayrıca Bkz.
 [Maintainability Warnings](../code-quality/maintainability-warnings.md) [Yönetilen kodun karmaşıklık ve bakım durumunu ölçen](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) bakım uyarıları
