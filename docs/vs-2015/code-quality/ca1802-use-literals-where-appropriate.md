---
title: 'CA1802: uygun yerlerde harfler kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671523"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Uygun Yerlerde Sabitleri Kullan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir alan `static` ve `readonly` (`Shared` ve `ReadOnly` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) olarak tanımlanır ve derleme zamanında oluşturulabilir bir değer ile başlatılır.

## <a name="rule-description"></a>Kural Tanımı
 Bildirim türü için statik Oluşturucu çağrıldığında, bir `static``readonly` alanının değeri çalışma zamanında hesaplanır. @No__t_0 alan bildirildiği zaman başlatılır ve statik bir oluşturucu açıkça bildirilmemiş ise, derleyici alanı başlatmak için statik bir Oluşturucu yayar.

 Bir `const` alanının değeri, derleme zamanında hesaplanır ve meta verilerde depolanır, bu da bir `static``readonly` alanla karşılaştırıldığında çalışma zamanı performansını artırır.

 Hedeflenen alana atanan değer derleme zamanında oluşturulabilir olduğundan, değerin çalışma zamanı yerine derleme zamanında hesaplanabilmesi için bildirimi `const` bir alana değiştirin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için `static` ve `readonly` değiştiricilerini `const` değiştiricisiyle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek veya performans sorun değilse kuralı devre dışı bırakmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve `UseConstant` ' i ihlal eden `UseReadOnly` bir türü gösterir.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
