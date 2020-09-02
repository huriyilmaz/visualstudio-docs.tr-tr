---
title: 'CA1501: aşırı devralmadan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cf797ad67b7df2eb1f3ba1246e965ed6ebbd586d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547868"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Aşırı devralmadan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür.

## <a name="rule-description"></a>Kural Tanımı
 İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. Bu kural, Analizi aynı modüldeki Hiyerarşilerle sınırlandırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlal edildiğini gidermek için, türü devralma hiyerarşisinde daha az derin olan temel bir türden türeten veya bazı ara taban türlerinden birini ortadan kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir. Ancak, kod bakımı daha zor olabilir. Temel türlerin görünürlüğüne bağlı olarak, bu kuralın ihlallerinin çözümlenmesi, son değişiklikler oluşturabilir. Örneğin, ortak temel türleri kaldırmak bir son değişiklik.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]
