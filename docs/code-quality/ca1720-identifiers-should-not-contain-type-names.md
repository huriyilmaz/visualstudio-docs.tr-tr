---
title: 'CA1720: Tanımlayıcılar tür adları içermemelidir'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64fd1aee2a778c72a81f82a0d435ce37d408c9a5
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443794"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Tanımlayıcılar tür adları içermemelidir

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir üye içindeki bir parametrenin adı bir veri türü adı içerir.

veya

Üyenin adı dile özgü bir veri türü adı içerir.

Bu kural varsayılan olarak yalnızca dışarıdan görünür üyelere bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

Parametrelerin ve üyelerin adları, geliştirme araçları tarafından sağlanması beklenen, kendi türlerini tanımlamaya kıyasla anlamını iletmek için daha iyi kullanılır. Üye adları için, bir veri türü adı kullanılması gerekiyorsa dile özgü bir ad kullanın. Örneğin `int` C# tür adı yerine, dilden bağımsız veri türü adı `Int32` ' yi kullanın.

Parametre veya üyenin adındaki her bir ayrık belirteç, büyük/küçük harfe duyarsız bir şekilde aşağıdaki dile özgü veri türü adlarına göre denetlenir:

- Bool
- WChar
- Int8
- UInt8
- Kısadır
- UShort
- int
- U
- Tamsayı
- UInteger
- Kalacağını
- 'Tur
- İşaretlenmemiş
- İmza
- Float
- Float32
- Float64

Ayrıca, bir parametrenin adları, büyük/küçük harf duyarsız bir şekilde aşağıdaki dilden bağımsız veri türü adlarına karşı de denetlenir:

- Nesne
- Nesnesi
- Boole değeri
- Char
- Dize
- SByte
- Bayt
- Ubde
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- Serisi
- Kaydetmeye
- Çağrısı
- Uıınptr
- UPtr
- UPointer
- Tek
- Çift
- Ondalık
- Guid

## <a name="how-to-fix-violations"></a>İhlalleri çözme

**Bir parametreye göre tetiklendiğinde:**

Parametresinin adı içindeki veri türü tanımlayıcısını, anlamını daha iyi açıklayan bir terim veya ' Value ' gibi daha genel bir terim ile değiştirin.

**Bir üyeye karşı harekete geçirildiğinde:**

Üyenin adında dile özgü veri türü tanımlayıcısını, anlamını daha iyi açıklayan bir terim, dilden bağımsız bir eşdeğer veya ' Value ' gibi daha genel bir terim ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Tür tabanlı parametre ve üye adlarının zaman zaman kullanımı uygun olabilir. Bununla birlikte, yeni geliştirme için, bu kuraldan bir uyarıyı bastırdığınızda bilinen senaryolar oluşmaz. Daha önce sevk edilen kitaplıklar için, bu kuraldan bir uyarıyı bastırdığınızda kalabilirsiniz.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (adlandırma) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>İlgili kurallar

- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719: Parametre adları üye adlarıyla eşleşmemelidir](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
