---
title: 'CA1702: Bileşik sözcüklerin doğru şekilde kullanılması gerekir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 76ce346430a249b562f00e17c3173e79128d1708
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669252"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1702: Bileşik sözcüklerin doğru şekilde kullanılması gerekir](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Parçalara ayırma-derlemeler üzerinde harekete geçirildi.<br /><br /> Tür parametrelerinde harekete geçirildiğinde, bozmasız değildir.|

## <a name="cause"></a>Sebep
 Bir tanımlayıcının adı birden çok sözcük içeriyor ve sözcüklerden en az biri, doğru şekilde desteklenmeyen bir bileşik sözcük gibi görünüyor.

## <a name="rule-description"></a>Kural Tanımı
 Tanımlayıcının adı, büyük/küçük harfe bağlı olan sözcüklere bölünür. Her bitişik iki sözcüklü birleşim, Microsoft yazım denetleyicisi kitaplığı tarafından denetlenir. Tanınırsa, tanımlayıcı kuralın ihlal edildiğini üretir. İhlalin oluşmasına neden olan Birleşik kelimelerin örnekleri, sırasıyla "Checksum" ve "multipart" olarak, "Checksum" ve "multipart" şeklinde olmalıdır. Önceki yaygın kullanım nedeniyle, birkaç özel durum kuralda yerleşik olarak bulunur ve "araç çubuğu" ve "dosya adı" gibi birçok tek sözcük işaretlenir, bu da iki ayrı sözcük olarak (Bu durumda "araç çubuğu" ve "dosya adı") kullanılır.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Adı doğru bir şekilde olacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bileşik sözcüğün her iki bölümü de yazım sözlüğü tarafından tanınıyorsa ve amaç iki sözcükten birini kullanıyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Adlandırma yönergeleri](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [büyük/küçük kuralları](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
