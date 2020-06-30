---
title: 'CA1409: com görünebilir türler oluşturulabilmelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547335"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: COM görünebilir türler oluşturulabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Özellikle bileşen nesne modeli (COM) tarafından görünür olarak işaretlenen bir başvuru türü ortak parametreli bir Oluşturucu içerir ancak ortak bir varsayılan (parametresiz) Oluşturucu içermez.

## <a name="rule-description"></a>Kural Tanımı
 Ortak varsayılan oluşturucusu olmayan bir tür COM istemcileri tarafından oluşturulamaz. Ancak, tür oluşturmak ve istemciye geçirmek (örneğin, bir yöntem çağrısının dönüş değeri aracılığıyla) için başka bir anlamı varsa, bu tür COM istemcileri tarafından yine de erişilebilir.

 Kural öğesinden türetilmiş türleri yoksayar <xref:System.Delegate?displayProperty=fullName> .

 Varsayılan olarak, aşağıdakiler COM 'a görünür: derlemeler, ortak türler, ortak türlerdeki ortak örnek üyeleri ve tüm ortak değer türleri üyeleri.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, genel bir varsayılan oluşturucu ekleyin veya <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> türünden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Nesneyi oluşturmak ve COM istemcisine geçirmek için başka yollar sağlanmışsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen kod ile birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Için .NET türlerini nitelendirme](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
