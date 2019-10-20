---
title: 'CA1709: tanımlayıcılar doğru şekilde yazılmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c8022a9dfba3012e8c81523b076b7bbfbb6ee8d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669195"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1709: tanımlayıcılar doğru şekilde olmalıdır](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Parçalara ayırma-derlemeler, ad alanları, türler, Üyeler ve parametreler üzerinde tetiklenir.<br /><br /> Genel tür parametrelerinde harekete geçirildiğinde, bölünmez.|

## <a name="cause"></a>Sebep
 Tanımlayıcının adı doğru değil.

 \- veya-

 Bir tanımlayıcının adı iki harfli bir kısaltma içerir ve ikinci harf küçük harftir.

 \- veya-

 Bir tanımlayıcının adı, üç veya daha fazla büyük harf kısaltması içerir.

## <a name="rule-description"></a>Kural Tanımı
 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

 Kural gereği, parametre adları ortası büyük harfleri kullanır; ad alanı, tür ve üye adları, Pascal büyük harfleri kullanır. Bir Camel adı, ilk harf küçük ve ad içindeki kalan sözcüklerin ilk harfi büyük harfle yazılır. Camel adı örnekleri "Packetalgılayıcı", "ioFile" ve "fatalErrorCode" olarak verilebilir. Bir Pascal-tused adında, ilk harf büyük harfli ve ad içindeki kalan sözcüklerin ilk harfi büyük harfle yazılır. "Packetalgılayıcı", "Iofve" ve "FatalErrorCode" gibi, Pascal biçimli adlara örnek olarak verilebilir.

 Bu kural büyük küçük harfe göre adı sözcüklere böler ve iki harfli sözcükleri, "ın" veya "My" gibi yaygın iki harfli sözcüklerin bir listesine karşı denetler. Bir eşleşme bulunmazsa sözcüğün bir kısaltma olduğu varsayılır. Buna ek olarak, bu kural bir satırda dört büyük harf veya adın sonundaki satırdaki üç büyük harften oluşan bir kısaltma bulduğu varsayılır.

 Kurala göre, iki harfli kısaltmalar tüm büyük harfleri, üç veya daha fazla karakterin kısaltmalardan birini kullanır. Aşağıdaki örnekler bu adlandırma kuralını kullanır: ' DB ', ' CR ', ' CPA ' ve ' ECMA '. Aşağıdaki örnekler kuralı ihlal ediyor: ' IO ', ' XML ' ve ' DoD ' ve parametre olmayan adlar için, ' XP ' ve ' cpl '.

 ' ID ', bu kuralın ihlaline neden olmak için özeldir. ' ID ' bir kısaltma değil, ancak ' Identification ' için bir kısaltmadır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Adı doğru bir şekilde olacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kendi adlandırma kurallarınız varsa veya tanımlayıcı uygun bir adı (örneğin, bir şirketin veya bir teknolojinin adı) temsil ediyorsa, bu uyarıyı bastırmak güvenlidir.

 Ayrıca, kod analizi özel sözlüğüne belirli hüküm, kısaltmalar ve kısaltmalar ekleyebilirsiniz. Özel sözlükte belirtilen terimler bu kuralın ihlallerine neden olmaz. Daha fazla bilgi için bkz. [nasıl yapılır: kod analizi sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>İlgili kurallar
 [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
