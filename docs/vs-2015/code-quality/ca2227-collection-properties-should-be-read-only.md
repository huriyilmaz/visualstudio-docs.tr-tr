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
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540536"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Koleksiyon özellikleri salt okunur olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görünebilir yazılabilir özellik, uygulayan bir türdür <xref:System.Collections.ICollection?displayProperty=fullName> . Diziler, Dizin oluşturucular (adı ' Item ' olan Özellikler) ve izin kümeleri kural tarafından yok sayılır.

## <a name="rule-description"></a>Kural Tanımı
 Yazılabilir bir koleksiyon özelliği, kullanıcının koleksiyonu tamamen farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir. Koleksiyonu değiştirmek bir hedeftir, tercih edilen tasarım alanı, koleksiyondaki tüm öğeleri kaldırmak için bir yöntem ve koleksiyonu yeniden doldurmak için bir yöntem dahil olmaktır. <xref:System.Collections.ArrayList.Clear%2A> <xref:System.Collections.ArrayList.AddRange%2A> <xref:System.Collections.ArrayList?displayProperty=fullName> Bu düzenin bir örneği için sınıfının ve yöntemlerine bakın.

 Hem ikili hem de XML serileştirme koleksiyonları olan salt yazılır özellikleri destekler. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>Sınıfı, <xref:System.Collections.ICollection> ve <xref:System.Collections.IEnumerable?displayProperty=fullName> seri hale getirilebilir olması için uygulayan türler için özel gereksinimlere sahiptir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, özelliği salt okunurdur ve tasarım gerektiriyorsa, koleksiyonu temizlemek ve yeniden doldurmak için yöntemler ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yazılabilir bir koleksiyon özelliğine sahip bir tür gösterir ve koleksiyonun nasıl doğrudan değiştirileceğini gösterir. Ayrıca, ve yöntemlerini kullanarak salt okunurdur bir koleksiyon özelliğinin değiştirilmesi için tercih edilen `Clear` yol `AddRange` gösterilmektedir.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819-properties-should-not-return-arrays.md)
