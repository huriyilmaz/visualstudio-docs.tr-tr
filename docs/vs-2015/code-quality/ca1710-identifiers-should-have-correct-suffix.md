---
title: 'CA1710: tanımlayıcıda doğru sonek olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7dc0ed72ddab39bda5f3de9b978f4d55dc2358ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669163"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Tanımlayıcıların sonekleri doğru olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Tanımlayıcı, doğru sonekine sahip değil.

## <a name="rule-description"></a>Kural Tanımı
 Kural gereği, belirli temel türleri genişleten veya belirli arabirimleri ya da bu türlerden türetilmiş türleri uygulayan türlerin adları, temel tür veya arabirimle ilişkili bir soneke sahiptir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

 Aşağıdaki tabloda, ilişkili sonekleri olan temel türler ve arabirimler listelenmektedir.

|Temel tür/arabirim|Önekini|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Öznitelik|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Özel Durum|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Koleksiyon|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Sözlüğünü|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Koleksiyon|
|<xref:System.Collections.Queue?displayProperty=fullName>|Koleksiyon veya kuyruk|
|<xref:System.Collections.Stack?displayProperty=fullName>|Koleksiyon veya yığın|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Koleksiyon|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Sözlüğünü|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Koleksiyon veya DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Akış|
|<xref:System.Security.IPermission?displayProperty=fullName>|İzin|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Koşul|
|Bir olay işleyicisi temsilcisi.|Çalışılıyor|

 @No__t_0 uygulayan ve sözlük, yığın veya kuyruk gibi Genelleştirilmiş bir veri yapısı türü olan türler, türün amaçlanan kullanımı hakkında anlamlı bilgiler sağlayan adlara izin verilir.

 @No__t_0 uygulayan ve belirli öğelerin bir koleksiyonu olan türler, ' Collection ' sözcüğüyle biten adlara sahiptir. Örneğin, <xref:System.Collections.Queue> nesnelerinin bir koleksiyonu ' QueueCollection ' adına sahip olabilir. ' Collection ' soneki, koleksiyon üyelerinin `foreach` (`For Each` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ifadesinde numaralandırılacağını belirtir.

 @No__t_0 uygulayan türler, tür <xref:System.Collections.IEnumerable> veya <xref:System.Collections.ICollection> de uygulayan ' sözlük ' kelimesiyle biten adlara sahiptir. ' Collection ' ve ' Dictionary ' sonek adlandırma kuralları, kullanıcıların aşağıdaki iki numaralandırma deseni arasında ayrım kurmasını sağlar.

 ' Collection ' sonekine sahip türler bu numaralandırma düzenlerini izler.

```
foreach(SomeType x in SomeCollection) { }
```

 ' Dictionary ' sonekine sahip türler bu numaralandırma düzenlerini izler.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 @No__t_0 nesnesi, <xref:System.Data.DataColumn?displayProperty=fullName> ve <xref:System.Data.DataRow?displayProperty=fullName> nesneleri koleksiyonlarından oluşan <xref:System.Data.DataTable> nesneleri koleksiyonundan oluşur. Bu koleksiyonlar, temel <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> sınıfı aracılığıyla <xref:System.Collections.ICollection> uygular.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Doğru terimle soncak olması için türü yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür genişletilebilen veya rastgele bir dizi farklı öğeyi tutan genelleştirilmiş bir veri yapısı ise, ' koleksiyon ' sonekini kullanmak için bir uyarının görüntülenmesini güvenlidir. Bu durumda, uygulama, performans veya veri yapısının diğer özellikleri hakkında anlamlı bilgiler sağlayan bir ad (örneğin, BinaryTree) oluşabilir. Türün belirli bir türün (örneğin, StringCollection) bir koleksiyonunu temsil ettiği durumlarda, sonek türün bir `foreach` ifadesiyle numaralandırılacağını gösterdiği için bu kuraldan bir uyarıyı bastırmayın.

 Diğer sonekler için, bu kuraldan bir uyarıyı bastırmayın. Son ek, hedeflenen kullanımın tür adından önlenebilir olmasını sağlar.

## <a name="related-rules"></a>İlgili kurallar
 [CA1711: Tanımlayıcıların sonekleri yanlış olmamalıdır](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [nib: olaylar ve temsilciler](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
