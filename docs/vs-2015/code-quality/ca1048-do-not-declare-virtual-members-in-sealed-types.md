---
title: 'CA1048: korumalı türlerde sanal üyeleri bildirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19ae3a4fdc620343f18aa0845c33e1d73529adfe
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546802"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Sealed türlerde virtual üyeler bildirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak bir tür Sealed olur ve her ikisi de `virtual` ( `Overridable` Visual Basic) ve son olmayan bir yöntem bildirir. Bu kural, bu düzene uymalıdır olması gereken temsilci türleri için ihlalleri raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Türler yöntemi sanal olarak bildirir, böylece devralan türler sanal yöntemin uygulanmasını geçersiz kılabilir. Tanım olarak, korumalı bir türden bir sanal yöntem anlamsız bir şekilde bir korumalı türden devralma yapılamaz.

 Visual Basic .NET ve C# derleyicileri, türlerin bu kuralı ihlal edeceğini izin vermez.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, yöntemi sanal değil veya türü devralınabilir yapın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Türü geçerli durumunda bırakmak, bakım sorunlarına neden olabilir ve herhangi bir avantaj sağlamaz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
