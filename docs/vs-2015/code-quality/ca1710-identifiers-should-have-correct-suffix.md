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
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543994"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Tanımlayıcılar doğru soneke sahip olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Tanımlayıcı, doğru sonekine sahip değil.

## <a name="rule-description"></a>Kural Tanımı
 Kural gereği, belirli temel türleri genişleten veya belirli arabirimleri ya da bu türlerden türetilmiş türleri uygulayan türlerin adları, temel tür veya arabirimle ilişkili bir soneke sahiptir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

 Aşağıdaki tabloda, ilişkili sonekleri olan temel türler ve arabirimler listelenmektedir.

|Temel tür/arabirim|Önekini|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Öznitelik|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Özel durum|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Koleksiyon|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Sözlük|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Koleksiyon|
|<xref:System.Collections.Queue?displayProperty=fullName>|Koleksiyon veya kuyruk|
|<xref:System.Collections.Stack?displayProperty=fullName>|Koleksiyon veya yığın|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Koleksiyon|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Sözlük|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Koleksiyon veya DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Akış|
|<xref:System.Security.IPermission?displayProperty=fullName>|İzin|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Koşul|
|Bir olay işleyicisi temsilcisi.|Çalışılıyor|

 <xref:System.Collections.ICollection>Bir sözlük, yığın veya kuyruk gibi Genelleştirilmiş bir veri yapısı türü ve olan türler, türün amaçlanan kullanımı hakkında anlamlı bilgiler sağlayan adlara izin verilir.

 <xref:System.Collections.ICollection>Ve belirli öğelerin bir koleksiyonunu uygulayan türler, ' Collection ' kelimesiyle biten adlara sahiptir. Örneğin, bir <xref:System.Collections.Queue> nesne koleksiyonu ' QueueCollection ' adına sahip olur. ' Collection ' soneki, koleksiyon üyelerinin `foreach` ( `For Each` ın) ifadesinde numaralandırılacağını belirtir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

 Uygulayan türler <xref:System.Collections.IDictionary> , türü de veya uyguluyor olsa da, ' Dictionary ' kelimesiyle biten adlara sahiptir <xref:System.Collections.IEnumerable> <xref:System.Collections.ICollection> . ' Collection ' ve ' Dictionary ' sonek adlandırma kuralları, kullanıcıların aşağıdaki iki numaralandırma deseni arasında ayrım kurmasını sağlar.

 ' Collection ' sonekine sahip türler bu numaralandırma düzenlerini izler.

```
foreach(SomeType x in SomeCollection) { }
```

 ' Dictionary ' sonekine sahip türler bu numaralandırma düzenlerini izler.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Bir <xref:System.Data.DataSet> nesnesi, <xref:System.Data.DataTable> <xref:System.Data.DataColumn?displayProperty=fullName> ve nesneleri koleksiyonlarından oluşan nesneler koleksiyonundan oluşur <xref:System.Data.DataRow?displayProperty=fullName> . Bu koleksiyonlar <xref:System.Collections.ICollection> , temel sınıf aracılığıyla uygulanır <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Doğru terimle soncak olması için türü yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür genişletilebilen veya rastgele bir dizi farklı öğeyi tutan genelleştirilmiş bir veri yapısı ise, ' koleksiyon ' sonekini kullanmak için bir uyarının görüntülenmesini güvenlidir. Bu durumda, uygulama, performans veya veri yapısının diğer özellikleri hakkında anlamlı bilgiler sağlayan bir ad (örneğin, BinaryTree) oluşabilir. Türün belirli bir türün (örneğin, StringCollection) bir koleksiyonunu temsil ettiği durumlarda, sonek türün bir bildirim kullanılarak numaralandırılacağını gösterdiği için bu kuraldan bir uyarıyı bastırmayın `foreach` .

 Diğer sonekler için, bu kuraldan bir uyarıyı bastırmayın. Son ek, hedeflenen kullanımın tür adından önlenebilir olmasını sağlar.

## <a name="related-rules"></a>İlgili kurallar
 [CA1711: Tanımlayıcılar yanlış sonek içermemelidir](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [nib: olaylar ve temsilciler](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
