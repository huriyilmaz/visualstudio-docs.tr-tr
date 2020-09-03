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
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545398"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Türler belirli temel türleri aşmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
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
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Sürüm 1 ' de, ' den yeni özel durumlar türetmeniz önerilir <xref:System.ApplicationException> . Öneri değişmiştir ve yeni özel durumlar <xref:System.Exception?displayProperty=fullName> , ad alanındaki alt sınıflarından veya birini türetmelidir <xref:System> .

 <xref:System.Xml.XmlDocument>Temel alınan nesne modeli veya veri kaynağı için BIR xml görünümü oluşturmak istiyorsanız, alt sınıfını oluşturmayın.

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
 Bu kuraldan ilgili ihlalleri öğrenmek için bir uyarı göstermez <xref:System.ApplicationException> . Bu kuraldan ilgili ihlalleri öğrenmek için bir uyarı görüntülenmesini güvenlidir <xref:System.Xml.XmlDocument> . Kod daha önce yayınlanmışsa, genel olmayan bir koleksiyon hakkında uyarı bastırmak güvenlidir.
