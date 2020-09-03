---
title: 'CA1813: Korumasız özniteliklerden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543955"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Mühürsüz özniteliklerden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak bir tür öğesinden devralınır <xref:System.Attribute?displayProperty=fullName> , soyut değildir ve korumalı değildir ( `NotInheritable` Visual Basic).

## <a name="rule-description"></a>Kural Tanımı
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Sınıf Kitaplığı özel özniteliklerin alınması için yöntemler sağlar. Varsayılan olarak, bu yöntemler öznitelik devralma hiyerarşisinde arama yapın; Örneğin <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> , belirtilen öznitelik türünü veya belirtilen öznitelik türünü genişleten öznitelik türlerini arar. Özniteliği mühürde devralma hiyerarşisinde arama kaldırılır ve performans iyileştirebilirler.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için öznitelik türünü mühürleyin veya soyut hale getirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir. Bunu yalnızca bir öznitelik hiyerarşisi tanımlıyorsanız ve özniteliği mühürleyip soyut hale getirilemez yapmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı karşılayan özel bir özniteliği gösterir.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1019: Öznitelik bağımsız değişkenleri için erişimciler tanımlayın](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Öznitelikleri AttributeUsageAttribute ile işaretle](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
