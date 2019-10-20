---
title: 'CA1047: korumalı türlerde korunan üyeleri bildirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ebc6732e559b70e753a44b14cf45b7de9fc150d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668176"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Korumalı türlerde korunan üyeleri bildirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak tür `sealed` ' dır (Visual Basic 'te `NotInheritable`) ve korumalı bir üye veya korumalı iç içe geçmiş bir tür bildirir. Bu kural, bu düzene uymalıdır <xref:System.Object.Finalize%2A> yöntemler için ihlaller raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Türler, devralmasına erişebileceğiniz veya üyeyi geçersiz kılmak için korunan üyelerin türlerini bildirir. Tanım olarak, korumalı türler üzerinde korunan yöntemlerin çağrılabilmesi için korumalı bir türden devralma yapılamaz.

 C# Derleyici bu hata için bir uyarı verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için üyenin erişim düzeyini özel olarak değiştirin veya türü devralınabilir yapın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Türü geçerli durumunda bırakmak, bakım sorunlarına neden olabilir ve herhangi bir avantaj sağlamaz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
