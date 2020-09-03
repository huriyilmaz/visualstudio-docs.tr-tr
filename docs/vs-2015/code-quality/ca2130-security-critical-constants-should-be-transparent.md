---
title: 'CA2130: güvenlik kritik sabitleri saydam olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4439e7b520232b71c16d3f3c6b4afb3a4ba35f21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534608"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Güvenlik kritik sabitleri saydam olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Sabit bir alan veya numaralandırma üyesi ile işaretlenir <xref:System.Security.SecurityCriticalAttribute> .

## <a name="rule-description"></a>Kural Tanımı
 Saydamlık zorlaması, sabit değerler için zorlanmaz çünkü derleyiciler sabit değerleri satır içi hale getirir bu nedenle arama, çalışma zamanında gerekli değildir. Sabit alanlar saydam güvenlikli olmalıdır; böylece kodu gözden geçirenler saydam kodun sabitlere erişemediğini varsaymaz.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, SecurityCritical özniteliğini alandan veya değerden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örneklerde, Enum değeri `EnumWithCriticalValues.CriticalEnumValue` ve sabiti `CriticalConstant` Bu uyarıyı yükseltir. Sorunları gidermek için [ `SecurityCritical` ] özniteliğini kaldırarak güvenliği saydam hale getirin.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
