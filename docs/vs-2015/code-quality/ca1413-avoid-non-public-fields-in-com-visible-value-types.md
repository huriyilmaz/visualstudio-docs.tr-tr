---
title: 'CA1413: COM görünebilir değer türlerinde genel olmayan alanlardan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548466"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Özellikle bileşen nesne modeli (COM) tarafından görünür olarak işaretlenen bir değer türü, ortak bir örnek alanı bildirir.

## <a name="rule-description"></a>Kural Tanımı
 COM-görünür değer türlerinin ortak olmayan örnek alanları COM istemcilerine görünürdür. Açığa çıkmamalıdır veya istenmeyen bir tasarım ya da güvenlik etkisine sahip olacak bilgiler için alanın içeriğini gözden geçirin.

 Varsayılan olarak, tüm ortak değer türleri COM olarak görünür. Ancak, hatalı pozitif sonuçları azaltmak için bu kural, türün COM görünürlüğünü açık bir şekilde ifade etmek için gereklidir. Kapsayan bütünleştirilmiş kod, olarak ayarlanmış olarak işaretlenmelidir <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` ve türü <xref:System.Runtime.InteropServices.ComVisibleAttribute> olarak kümesiyle işaretlenmelidir `true` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak ve alanı gizli tutmaya devam etmek için, değer türünü bir başvuru türü olarak değiştirin ya da <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği türden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Alanın genel pozlaması kabul edilebilir ise, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Birlikte çalışabilirlik Için yönetilmeyen kod niteleyen .net türleriyle](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
