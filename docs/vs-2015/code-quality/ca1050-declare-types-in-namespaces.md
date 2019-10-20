---
title: 'CA1050: ad alanlarında tür bildirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c56de70daeabd05215f68024339d5855686d529b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653828"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Ad alanlarında türleri bildirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir tür, adlandırılmış bir ad alanının kapsamı dışında tanımlanır.

## <a name="rule-description"></a>Kural Tanımı
 Türler ad çakışmalarını engellemek için ad alanlarında ve bir nesne hiyerarşisinde ilgili türleri düzenlemenin bir yolu olarak belirtilir. Adlandırılmış ad alanı dışında olan türler, kodda başvurulmayacak genel bir ad alanında bulunur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, türü bir ad alanına yerleştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı bastırmanız gerekmese de, derleme diğer derlemelerle birlikte hiçbir zaman kullanılmaz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir ad alanı dışında yanlış bir şekilde bildirilmeli bir kitaplık ve bir ad alanında bildirildiği aynı ada sahip bir tür gösterir.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama daha önce tanımlanan kitaplığı kullanır. Ad alanı dışında belirtilen türün `Test` adı bir ad alanı tarafından nitelendirilmediği zaman oluşturulduğunu unutmayın. Ayrıca, `Goodspace` ' deki `Test` türüne erişmek için ad alanı adının gerekli olduğunu unutmayın.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
