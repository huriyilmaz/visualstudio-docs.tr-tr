---
title: 'CA1050: Ad alanlarında türleri bildirin'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4d7b132a2840afcc581dda8d341f0193c27f0ef2
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449190"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Ad alanlarında türleri bildirin

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Ortak veya korumalı bir tür, adlandırılmış bir ad alanının kapsamı dışında tanımlanır.

## <a name="rule-description"></a>Kural açıklaması
Türler ad çakışmalarını engellemek için ad alanlarında ve bir nesne hiyerarşisinde ilgili türleri düzenlemenin bir yolu olarak belirtilir. Adlandırılmış ad alanı dışında olan türler, kodda başvurulmayacak genel bir ad alanında bulunur.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, türü bir ad alanına yerleştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan bir uyarıyı bastırmanız gerekmese de, derleme diğer derlemelerle birlikte hiçbir zaman kullanılmaz.

## <a name="example"></a>Örnek
Aşağıdaki örnek, bir ad alanı dışında yanlış bir şekilde bildirilmeli bir kitaplık ve bir ad alanında bildirildiği aynı ada sahip bir tür gösterir.

[!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
[!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Örnek
Aşağıdaki uygulama daha önce tanımlanan kitaplığı kullanır. Ad alanı dışında belirtilen türün `Test` adı bir ad alanı tarafından nitelendirilmediği zaman oluşturulduğunu unutmayın. Ayrıca, `Goodspace` ' deki `Test` türüne erişmek için ad alanı adının gerekli olduğunu unutmayın.

[!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
[!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]
