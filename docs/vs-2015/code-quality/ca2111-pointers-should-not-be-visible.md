---
title: 'CA2111: Işaretçiler görünür olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7429251a66ce2fe22a825a153cb90248faabb9fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544371"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: İşaretçiler görünür olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı <xref:System.IntPtr?displayProperty=fullName> veya <xref:System.UIntPtr?displayProperty=fullName> alan salt okunurdur.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.IntPtr> ve <xref:System.UIntPtr> yönetilmeyen belleğe erişmek için kullanılan işaretçi türleridir. Bir işaretçi özel, iç veya salt okunurdur değilse, kötü amaçlı kod işaretçinin değerini değiştirebilir, bu da, bellekteki rastgele konumlara erişime izin verebilir veya uygulama ya da sistem arızalarına neden olabilir.

 İşaretçi alanını içeren türe erişimi güvenli hale getirmek istiyorsanız, bkz. [CA2112: güvenli türler alanları kullanıma sunmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İşaretçiyi salt okunurdur, iç veya özel yaparak güvenli hale getirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İşaretçinin değerine bağlı değilseniz bu kuraldan bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod, kuralı ihlal eden ve karşılayan işaretçileri gösterir. Özel olmayan işaretçilerin CA1051 kuralını da ihlal ettiğini unutmayın [: görünür örnek alanlarını bildirme](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
