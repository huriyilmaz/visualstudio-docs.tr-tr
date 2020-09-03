---
title: 'CA2230: değişken bağımsız değişkenler için params kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540367"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Değişken bağımsız değişkenler için params kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür, çağırma kuralını kullanan ortak veya korumalı bir yöntem içerir `VarArgs` .

## <a name="rule-description"></a>Kural Tanımı
 `VarArgs`Çağırma kuralı, değişken sayıda parametre alan belirli yöntem tanımlarıyla birlikte kullanılır. Çağırma kuralını kullanan bir yöntem `VarArgs` ortak dil belirtimi (CLS) uyumlu değil ve programlama dilleri arasında erişilebilir olmayabilir.

 C# ' de, `VarArgs` yöntemin parametre listesi anahtar sözcüğüyle sona erdiğinde çağırma kuralı kullanılır `__arglist` . Visual Basic `VarArgs` , çağırma kuralını desteklemez ve Visual C++ yalnızca elips gösterimini kullanan yönetilmeyen kodda kullanılmasına izin verir `...` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 C# dilinde bu kuralın ihlalini onarmak için yerine [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) anahtar sözcüğünü kullanın `__arglist` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, biri kuralı ve kuralı karşılayan birini ihlal eden iki yöntemi gösterir.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
