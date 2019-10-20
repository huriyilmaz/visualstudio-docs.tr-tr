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
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662826"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Değişken bağımsız değişkenler için params kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir tür, `VarArgs` çağırma kuralını kullanan ortak veya korumalı bir yöntem içerir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 çağırma kuralı, değişken sayıda parametre alan belirli yöntem tanımlarıyla birlikte kullanılır. @No__t_0 çağırma kuralını kullanan bir yöntem ortak dil belirtimi (CLS) uyumlu değil ve programlama dilleri arasında erişilebilir olmayabilir.

 ' C#De, bir yöntemin parametre listesi `__arglist` anahtar sözcüğüyle sona erdiğinde `VarArgs` çağırma kuralı kullanılır. Visual Basic, `VarArgs` çağırma kuralını desteklemez ve Visual C++ , yalnızca elips `...` gösterimini kullanan yönetilmeyen kodda kullanılmasına izin verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İçindeki C#bu kuralın ihlalini onarmak için `__arglist` yerine [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) anahtar sözcüğünü kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, biri kuralı ve kuralı karşılayan birini ihlal eden iki yöntemi gösterir.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
