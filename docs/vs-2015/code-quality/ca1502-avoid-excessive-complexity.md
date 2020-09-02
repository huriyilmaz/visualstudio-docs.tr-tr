---
title: 'CA1502: aşırı karmaşıklıktan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547842"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Aşırı karmaşıklıktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntemin aşırı döngüsel karmaşıklığı vardır.

## <a name="rule-description"></a>Kural Tanımı
 *Döngüsel karmaşıklığı* , koşullu dalların sayısı ve karmaşıklığı tarafından belirlenen yöntemi aracılığıyla, doğrusal olarak bağımsız yolların sayısını ölçer. Düşük bir döngüsel karmaşıklığı genellikle anlaşılması, test etmek ve sürdürmek kolay bir yöntemi gösterir. Döngüsel karmaşıklığı, yönteminin bir denetim akışı grafiğinden hesaplanır ve aşağıdaki gibi verilmiştir:

 Döngüsel karmaşıklığı = kenar sayısı-düğüm sayısı + 1

 bir düğüm bir mantık dal noktasını temsil ettiğinde ve bir kenar, düğümler arasındaki çizgiyi temsil eder.

 Kural, döngüsel karmaşıklığı 25 ' ten fazla olduğunda bir ihlalin bildirir.

 Kod ölçümleri hakkında daha fazla bilgi edinmek için [karmaşıklık ve yönetilen kodun bakımlarındaki](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, döngüsel karmaşıklığını azaltmak üzere yöntemi yeniden düzenleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Karmaşıklığın kolayca azaltılamamasının ve yöntemin anlaşılması, test edilmesi ve bakımının kolay olması durumunda bu kuraldan bir uyarının gösterilmesinin güvenli olması güvenlidir. Özellikle, büyük `switch` (ın) ifadesini içeren bir yöntem `Select` , [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dışlama için bir adaydır. Kod tabanını geliştirme döngüsündeki geç hale getirme veya daha önce sevk edilen koddaki çalışma zamanı davranışında beklenmedik bir değişikliği tanıtma riski, kodu yeniden düzenlemenin bakım avantajlarının ağır olduğunu ortadan kaldırır.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Döngüsel karmaşıklığı nasıl hesaplanır
 Döngüsel karmaşıklığı aşağıdaki 1 eklenerek hesaplanır:

- Dal sayısı ( `if` , `while` ve gibi `do` )

- `case`İçindeki deyim sayısı`switch`

  Aşağıdaki örneklerde, değişen döngüsel karmaşıklıkları olan Yöntemler gösterilmektedir.

## <a name="example"></a>Örnek
 **1 döngüsel karmaşıklığı**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Örnek
 **2 döngüsel karmaşıklığı**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Örnek
 **3 döngüsel karmaşıklığı**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Örnek
 **8 döngüsel karmaşıklığı**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
