---
title: 'CA1720: tanımlayıcılar tür adları içermemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f6d228b0fbf5507ba135f9ddc35d6d8b161f0011
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534855"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Tanımlayıcılar tür adları içermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir üyenin bir parametresinin adı bir veri türü adı içerir.

 -veya-

 Dışarıdan görünen bir üyenin adı dile özgü bir veri türü adı içerir.

## <a name="rule-description"></a>Kural Tanımı
 Parametrelerin ve üyelerin adları, geliştirme araçları tarafından sağlanması beklenen, kendi türlerini tanımlamaya kıyasla anlamını iletmek için daha iyi kullanılır. Üye adları için, bir veri türü adı kullanılması gerekiyorsa dile özgü bir ad kullanın. Örneğin, C# tür adı ' int ' yerine, dilden bağımsız veri türü adı olan Int32 kullanın.

 Parametre veya üyenin adındaki her bir ayrık belirteç, büyük/küçük harfe duyarsız bir şekilde aşağıdaki dile özgü veri türü adlarına karşı denetlenir:

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

  Ayrıca, bir parametrenin adları, büyük/küçük harfe duyarsız bir şekilde aşağıdaki dilden bağımsız veri türü adlarına karşı de denetlenir:

- Nesne

- Nesnesi

- Boole

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

- İşaretçi

- Uıınptr

- UPtr

- UPointer

- Tek

- Çift

- Ondalık

- Guid

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 **Bir parametreye göre tetiklendiğinde:**

 Parametresinin adı içindeki veri türü tanımlayıcısını, anlamını daha iyi açıklayan bir terim veya ' Value ' gibi daha genel bir terim ile değiştirin.

 **Bir üyeye karşı harekete geçirildiğinde:**

 Üyenin adında dile özgü veri türü tanımlayıcısını, anlamını daha iyi açıklayan bir terim, dilden bağımsız bir eşdeğer veya ' Value ' gibi daha genel bir terim ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür tabanlı parametre ve üye adlarının zaman zaman kullanımı uygun olabilir. Bununla birlikte, yeni geliştirme için, bu kuraldan bir uyarıyı bastırdığınızda bilinen senaryolar oluşmaz. Daha önce sevk edilen kitaplıklarda, bu kuraldan bir uyarıyı bastırdığınızda kalabilirsiniz.

## <a name="related-rules"></a>İlgili kurallar
 [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Parametre adları üye adları ile eşleşmemelidir](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
