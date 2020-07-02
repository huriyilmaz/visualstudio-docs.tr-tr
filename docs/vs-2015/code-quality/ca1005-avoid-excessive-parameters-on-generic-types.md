---
title: 'CA1005: genel türlerde aşırı parametrelerden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56c69badf76a05351b37a7c8a41a9cacf54f9974
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539730"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Genel türlerde aşırı parametre kullanmaktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görülebilen genel tür, ikiden fazla tür parametresine sahiptir.

## <a name="rule-description"></a>Kural Tanımı
 Daha çok tip parametresi, genel tip içerir, bilmek daha zordur ve hangi tip parametrelerinin temsil ettiğini anımsamak zordur. Genellikle, içinde olduğu gibi tek bir tür parametresiyle `List<T>` ve içinde olduğu gibi iki tür parametresiyle bazı durumlarda belirgin bir şekilde açıktır `Dictionary<TKey, TValue>` . İkiden fazla tür parametresi varsa, zorluk çoğu kullanıcı için çok büyük hale gelir (örneğin, `TooManyTypeParameters<T, K, V>` C# veya `TooManyTypeParameters(Of T, K, V)` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için tasarımı, ikiden fazla tür parametresi kullanmak üzere değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tasarım kesinlikle ikiden fazla tür parametresi gerektirmedikçe bu kuraldan bir uyarıyı bastırmayın. Anlaşılması kolay ve kullanımı kolay bir sözdiziminde genel türler sağlamak, yeni kitaplıkların benimseme oranını öğrenmek ve artmak için gereken süreyi azaltır.

## <a name="related-rules"></a>İlgili kurallar
 [CA1010: Koleksiyonlar genel arabirimi uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Genel türlerde statik üyeler belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanma](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Genel olay işleyicisi örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Uygun yerlerde genel türleri kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
