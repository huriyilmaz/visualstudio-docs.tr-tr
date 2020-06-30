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
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544410"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Uygun yerlerde sabitleri kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir alan `static` ve `readonly` ( `Shared` ve `ReadOnly` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) olarak tanımlanır ve derleme zamanında oluşturulabilir bir değer ile başlatılır.

## <a name="rule-description"></a>Kural Tanımı
 `static``readonly`Bildirim türü için statik Oluşturucu çağrıldığında bir alanın değeri çalışma zamanında hesaplanır. `static``readonly`Alan bildirildiği zaman başlatılır ve statik bir oluşturucu açıkça bildirilmemiş ise, derleyici alanı başlatmak için statik bir Oluşturucu yayar.

 Bir alanın değeri, `const` derleme zamanında hesaplanır ve meta verilerde depolanır, bu da bir alanla karşılaştırıldığında çalışma zamanı performansını artırır `static``readonly` .

 Hedeflenen alana atanan değer derleme zamanında oluşturulabilir olduğundan, `const` değeri çalışma zamanı yerine derleme zamanında hesaplanabilmesi için bildirimi bir alanla değiştirin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, `static` ve `readonly` değiştiricilerini `const` değiştiriciyle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek veya performans sorun değilse kuralı devre dışı bırakmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralını karşılayan bir türü ihlal eden bir türü gösterir `UseReadOnly` `UseConstant` .

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
