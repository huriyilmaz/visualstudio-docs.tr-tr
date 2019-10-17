---
title: 'CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbc066709fc5f90944b91130c1ef57a5120b1844
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443946"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategori|Microsoft. Naming|
|Son değişiklik|Parçalara ayırma-derlemeler, ad alanları, türler, Üyeler ve parametreler üzerinde tetiklenir.<br /><br /> Genel tür parametrelerinde harekete geçirildiğinde, bölünmez.|

## <a name="cause"></a>Sebep

Tanımlayıcının adı doğru değil.

\- veya-

Bir tanımlayıcının adı iki harfli bir kısaltma içerir ve ikinci harf küçük harftir.

\- veya-

Bir tanımlayıcının adı, üç veya daha fazla büyük harf kısaltması içerir.

## <a name="rule-description"></a>Kural açıklaması

Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu tutarlılık, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve bu, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiği müşterinin güvenini artırır.

Kural gereği, parametre adları ortası büyük harfleri, ad alanı, tür ve üye adları, Pascal büyük harfleri kullanır. Bir Camel adı, ilk harf küçük ve ad içindeki kalan sözcüklerin ilk harfi büyük olur. Camel-cased adı örnekleri `packetSniffer`, `ioFile` ve `fatalErrorCode` ' dir. Bir Pascal-Kased adında, ilk harf büyük harfli ve ad içindeki kalan sözcüklerin ilk harfi büyük harfle yazılır. @No__t-0, `IOFile` ve `FatalErrorCode` ' nin örnek adlarına örnek olarak verilebilir.

Bu kural büyük küçük harfe göre adı sözcüklere böler ve iki harfli sözcükleri, "ın" veya "My" gibi yaygın iki harfli sözcüklerin bir listesine karşı denetler. Bir eşleşme bulunmazsa sözcüğün bir kısaltma olduğu varsayılır. Buna ek olarak, bu kural bir satırda dört büyük harf veya adın sonundaki satırdaki üç büyük harften oluşan bir kısaltma bulduğu varsayılır.

Kurala göre, iki harfli kısaltmalar tüm büyük harfleri, üç veya daha fazla karakterin kısaltmalardan birini kullanır. Aşağıdaki örnekler bu adlandırma kuralını kullanır: ' DB ', ' CR ', ' CPA ' ve ' ECMA '. Aşağıdaki örnekler, ' IO ', ' XML ' ve ' DoD ' ve parametre olmayan adlar için ' XP ' ve ' cpl ' kuralını ihlal ediyor.

' ID ', bu kuralın ihlaline neden olmak için özeldir. ' ID ' bir kısaltma değil, ancak ' Identification ' için bir kısaltmadır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Adı doğru bir şekilde olacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Kendi adlandırma kurallarınız varsa veya tanımlayıcı uygun bir adı (örneğin, bir şirketin veya bir teknolojinin adı) temsil ediyorsa, bu uyarıyı bastırmak güvenlidir.

Ayrıca, kod analizi özel sözlüğüne belirli hüküm, kısaltmalar ve kısaltmalar ekleyebilirsiniz. Özel sözlükte belirtilen terimler bu kuralın ihlallerine neden olmaz. Daha fazla bilgi için bkz. [nasıl yapılır: kod analizi sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>İlgili kurallar

[CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
