---
title: 'CA1019: öznitelik bağımsız değişkenleri için erişimcileri tanımlayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ec9be9dae502ec48570a85576f483518ed0d75d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534959"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Öznitelik bağımsız değişkenleri için erişimciler tanımlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Yapıcısında bir öznitelik, karşılık gelen özellikleri olmayan bağımsız değişkenleri tanımlar.

## <a name="rule-description"></a>Kural Tanımı
 Öznitelikler özniteliği işaretlediğinizde özelleştirilen zorunlu bağımsız değişkenleri tanımlayabilir. Ayrıca bunlar konum parametreleri olarak öznitelik yapıcısına verildiğinden duruma bağlı bağımsız değişkenler olarak da bilinirler. Zorunlu her bağımsız değişken için bağımsız değişkenin değeri yürütme zamanından alınması gerektiğinden öznitelik ilgili salt okunur özelliği de sağlamalıdır. Bu kural, her Oluşturucu parametresi için ilgili özelliği tanımladınız olduğunu denetler.

 Öznitelikler adlandırılmış bağımsız değişkenler olarak bilinen duruma bağlı bağımsız değişkenler olarak da tanımlanabilir. Bu bağımsız öznitelik oluşturucular ad tarafından sağlanır ve karşılık gelen bir okuma/yazma özelliğine sahip olmalıdır.

 Zorunlu ve isteğe bağlı bağımsız değişkenler için, karşılık gelen özellikler ve Oluşturucu parametreleri aynı adı ancak büyük küçük harfleri kullanmalıdır. Özellikler, Pascal büyük harfleri kullanır ve parametreler ortası büyük harfleri kullanır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, bir tane olmayan her bir oluşturucu parametresi için salt okunurdur bir özellik ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Zorunlu bağımsız değişkenin değerinin alınabilir olmasını istemiyorsanız bu kuraldan bir uyarı gizleyin.

## <a name="custom-attributes-example"></a>Özel öznitelikler örneği

### <a name="description"></a>Description
 Aşağıdaki örnek, zorunlu (konumsal) bir parametre tanımlayan iki özniteliği gösterir. Özniteliğin ilk uygulanması yanlış tanımlanmış. İkinci uygulama doğru.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Konumsal ve adlandırılmış bağımsız değişkenler

### <a name="description"></a>Description
 Konumsal ve adlandırılmış bağımsız değişkenler, kitaplığınızın tüketicilerine açık hale gelir ve bu da bağımsız değişkenler öznitelik için zorunludur ve hangi bağımsız değişkenler isteğe bağlıdır.

 Aşağıdaki örnek, hem Konumsal hem de adlandırılmış bağımsız değişkenlere sahip bir özniteliğin bir uygulamasını gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Yorumlar
 Aşağıdaki örnek, özel özniteliğin iki özelliğe nasıl uygulanacağını gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1813: Mühürsüz özniteliklerden kaçının](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
