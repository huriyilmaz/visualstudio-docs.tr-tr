---
title: 'CA1058: türler belirli temel türleri genişlememelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603060"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belli temel türleri genişletmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen tür belirli temel türleri genişletir. Şu anda, bu kural aşağıdaki türlerden türetilen türleri raporlar:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 sürüm 1 ' de, <xref:System.ApplicationException> yeni özel durumlar türetmeniz önerilir. Öneri değişmiştir ve yeni özel durumlar, <xref:System> ad alanındaki <xref:System.Exception?displayProperty=fullName> veya alt sınıflarından türetilmelidir.

 Temel alınan nesne modelinin veya veri kaynağının XML görünümünü oluşturmak istiyorsanız <xref:System.Xml.XmlDocument> alt sınıfını oluşturmayın.

### <a name="non-generic-collections"></a>Genel olmayan Koleksiyonlar
 Mümkün olan her durumda genel koleksiyonları kullanın ve/veya genişletin. Daha önce sevk etmediğiniz takdirde, kodunuzda genel olmayan koleksiyonları genişletmeyin.

 **Hatalı kullanım örnekleri**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Doğru kullanım örnekleri**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, türü farklı bir temel türden veya genel bir koleksiyondan türetebilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 @No__t_0 ilgili ihlaller için bu kuraldan bir uyarıyı bastırmayın. @No__t_0 ilgili ihlaller için bu kuraldan bir uyarıyı gizlemek güvenlidir. Kod daha önce yayınlanmışsa, genel olmayan bir koleksiyon hakkında uyarı bastırmak güvenlidir.
