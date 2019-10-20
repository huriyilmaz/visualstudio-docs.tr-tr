---
title: 'CA1819: Özellikler dizileri döndürmemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c85efc3e601eb9e0d887043c50b30587e51321e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668369"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Özellikler diziler döndürmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak bir türdeki ortak veya korumalı özellik bir dizi döndürür.

## <a name="rule-description"></a>Kural Tanımı
 Özellik salt okunurdur olsa bile, Özellikler tarafından döndürülen diziler yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Tipik olarak, kullanıcılar bu tür bir özellik aramanın performans üzerindeki olumsuz etkilerini anlamayacaktır. Özellikle, özelliği dizini oluşturulmuş bir özellik olarak kullanabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, özelliği bir yöntem yapın veya özelliği bir koleksiyon döndürecek şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Öznitelikler diziler döndüren özellikler içerebilir, ancak koleksiyonlar döndüren özellikleri içeremez. [System. Attribute] sınıfından türetilmiş bir özniteliğin özelliği için oluşturulan bir uyarının görüntülenmesini sağlayabilirsiniz (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->sınıfı. Aksi takdirde, bu kuraldan bir uyarıyı bastırmayın.

## <a name="example-violation"></a>Örnek Ihlali

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, bu kuralı ihlal eden bir özelliği gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Açıklamalar
 Bu kural ihlalini onarmak için, özelliği bir metodu yapın ya da özelliği bir dizi yerine bir koleksiyon döndürecek şekilde değiştirin.

## <a name="change-the-property-to-a-method-example"></a>Özelliği bir yöntem örneği olarak değiştirin

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, özelliğini bir yöntemi ile değiştirerek ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Bir koleksiyon örneği döndürün

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, özelliği bir

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Kullanıcıların bir özelliği değiştirmesine izin verme

### <a name="description"></a>Açıklama
 Sınıfın tüketicisi bir özelliği değiştirmesine izin vermek isteyebilirsiniz. Aşağıdaki örnek, bu kuralı ihlal eden bir okuma/yazma özelliği gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Açıklamalar
 Aşağıdaki örnek, özelliği bir <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName> döndürecek şekilde değiştirerek ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1024: Uygun yerlerde özellikler kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)
