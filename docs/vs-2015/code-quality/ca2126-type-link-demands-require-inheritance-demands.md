---
title: 'CA2126: tür bağlantı talepleri devralma taleplerini gerektirir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051a041c245fae55e3d4759130c145c662734aa8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544280"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Tür bağlantı talepleri kalıtım taleplerini gerektirir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Genel korumasız bir tür, bağlantı talebi ile korunur, geçersiz kılınabilir bir yönteme sahiptir ve tür ya da yöntem bir devralma talebi ile korunmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir yöntemde veya bildirim türünde bir bağlantı talebi, yöntemin hemen çağırıcının belirtilen izne sahip olmasını gerektirir. Bir yöntemde devralma talebi, belirtilen izne sahip olması için geçersiz kılan bir yöntem gerektirir. Bir tür üzerindeki devralma talebi, belirtilen izne sahip olması için türetilen bir sınıf gerektirir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, tür ya da yöntemi, bağlantı isteği ile aynı izin için bir devralma talebi ile güvenli hale getirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Bağlantı talepleri olan metotları dolaylı olarak açığa çıkarmayın](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Geçersiz kılan bağlantı talepleri taban ile özdeş olmalıdır](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Devralma talepleri](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [bağlantı talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [talepleri](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)
