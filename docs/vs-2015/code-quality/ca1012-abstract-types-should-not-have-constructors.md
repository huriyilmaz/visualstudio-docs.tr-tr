---
title: 'CA1012: soyut türlerin oluşturucuları olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2c88144e788fb35a3c330aa28b4e9d8b91ff8003
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545463"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Soyut türlerin oluşturucuları olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|Soyut Cttypesshouldnothaveoluşturucular|
|CheckId|CA1012|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak bir tür soyut ve ortak bir oluşturucuya sahiptir.

## <a name="rule-description"></a>Kural Tanımı
 Soyut türler üzerindeki kurucular yalnızca türetilen türler tarafından çağrılabilir. Ortak yapıcılar türün bir örneğini yaptığından ve siz bir soyut türün örneğini yapamayacağınızdan, soyut sınıf hatalı biçimde dizayn edilmiş ortak yapıcıya sahip olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, oluşturucuyu korumalı yapın veya türü soyut olarak bildirmeyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Soyut türün ortak bir Oluşturucusu vardır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir soyut tür içerir.

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, oluşturucusunun erişilebilirliğini olarak değiştirerek önceki ihlalin düzeltir `public` `protected` .

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]
