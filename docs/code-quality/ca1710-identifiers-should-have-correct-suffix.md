---
title: 'CA1710: Tanımlayıcıların sonekleri doğru olmalıdır'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d52b9dd3eaf6312ece4939d3bdf1b64574bc21da
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72439833"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Tanımlayıcıların sonekleri doğru olmalıdır

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Tanımlayıcı, doğru sonekine sahip değil.

Bu kural varsayılan olarak yalnızca dışarıdan görünen tanımlayıcılara bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

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

@No__t-0 uygulayan ve sözlük, yığın veya kuyruk gibi Genelleştirilmiş bir veri yapısı türü olan türler, türün amaçlanan kullanımı hakkında anlamlı bilgiler sağlayan adlara sahiptir.

@No__t-0 uygulayan ve belirli öğelerin bir koleksiyonu olan türler, ' Collection ' sözcüğüyle biten adlara sahip. Örneğin, <xref:System.Collections.Queue> nesnelerinin bir koleksiyonu ' QueueCollection ' adına sahip olabilir. ' Collection ' soneki, koleksiyonun üyelerinin `foreach` ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ifadesinde @no__t kullanılarak numaralandırılacağını belirtir.

@No__t ' i uygulayan türler, <xref:System.Collections.IEnumerable> ' i veya <xref:System.Collections.ICollection> ' i de uygular, "Sözlük" kelimesiyle biten adlara sahiptir. ' Collection ' ve ' Dictionary ' sonek adlandırma kuralları, kullanıcıların aşağıdaki iki numaralandırma deseni arasında ayrım kurmasını sağlar.

' Collection ' sonekine sahip türler bu numaralandırma düzenlerini izler.

```
foreach(SomeType x in SomeCollection) { }
```

' Dictionary ' sonekine sahip türler bu numaralandırma düzenlerini izler.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

@No__t-0 nesnesi, diğerleri arasında <xref:System.Data.DataColumn?displayProperty=fullName> ve <xref:System.Data.DataRow?displayProperty=fullName> nesnelerinden oluşan koleksiyonlardan oluşan bir <xref:System.Data.DataTable> nesneleri koleksiyonundan oluşur. Bu koleksiyonlar, temel <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> sınıfı aracılığıyla <xref:System.Collections.ICollection> uygular.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Doğru terimle soncak olması için türü yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Tür genişletilebilen veya rastgele bir dizi farklı öğeyi tutan genelleştirilmiş bir veri yapısı ise, ' koleksiyon ' sonekini kullanmak için bir uyarının görüntülenmesini güvenlidir. Bu durumda, uygulama, performans veya veri yapısının diğer özellikleri hakkında anlamlı bilgiler sağlayan bir ad (örneğin, BinaryTree) oluşabilir. Türün belirli bir türün (örneğin, StringCollection) bir koleksiyonunu temsil ettiği durumlarda, sonek türün bir `foreach` ifadesiyle numaralandırılacağını gösterdiği için bu kuraldan bir uyarıyı bastırmayın.

Diğer sonekler için, bu kuraldan bir uyarıyı bastırmayın. Son ek, hedeflenen kullanımın tür adından önlenebilir olmasını sağlar.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1710.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (adlandırma) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>İlgili kurallar

[CA1711: Tanımlayıcıların sonekleri yanlış olmamalıdır](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](/dotnet/standard/design-guidelines/attributes)
- [Olayları işleme ve oluşturma](/dotnet/standard/events/index)
