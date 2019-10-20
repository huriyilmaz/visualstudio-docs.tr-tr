---
title: 'CA2227: koleksiyon özellikleri salt okunurdur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658864"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Koleksiyon özellikleri salt okunur olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünebilir yazılabilir Özellik <xref:System.Collections.ICollection?displayProperty=fullName> uygulayan bir türdür. Diziler, Dizin oluşturucular (adı ' Item ' olan Özellikler) ve izin kümeleri kural tarafından yok sayılır.

## <a name="rule-description"></a>Kural Tanımı
 Yazılabilir bir koleksiyon özelliği, kullanıcının koleksiyonu tamamen farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir. Koleksiyonu değiştirmek bir hedeftir, tercih edilen tasarım alanı, koleksiyondaki tüm öğeleri kaldırmak için bir yöntem ve koleksiyonu yeniden doldurmak için bir yöntem dahil olmaktır. Bu düzenin bir örneği için <xref:System.Collections.ArrayList?displayProperty=fullName> sınıfının <xref:System.Collections.ArrayList.Clear%2A> ve <xref:System.Collections.ArrayList.AddRange%2A> yöntemlerine bakın.

 Hem ikili hem de XML serileştirme koleksiyonları olan salt yazılır özellikleri destekler. @No__t_0 sınıfı, seri hale getirilebilir olması için <xref:System.Collections.ICollection> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> uygulayan türler için özel gereksinimlere sahiptir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, özelliği salt okunurdur ve tasarım gerektiriyorsa, koleksiyonu temizlemek ve yeniden doldurmak için yöntemler ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yazılabilir bir koleksiyon özelliğine sahip bir tür gösterir ve koleksiyonun nasıl doğrudan değiştirileceğini gösterir. Ayrıca, `Clear` ve `AddRange` yöntemleri kullanarak salt okunurdur bir koleksiyon özelliğinin değiştirilmesi için tercih edilen yol gösterilmektedir.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819-properties-should-not-return-arrays.md)
