---
title: 'CA1701: kaynak dizesi bileşik sözcüklerin doğru şekilde kullanılması gerekir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7c1c3b0fd6cf3a25d5db9e3039d4dc5d8364a18e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544111"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Kaynak dizesi, doğru şekilde görünmeyen bir bileşik sözcük içerir.

## <a name="rule-description"></a>Kural Tanımı
 Kaynak dizesindeki her sözcük büyük küçük harfe dayalı belirteçlere bölünür. Her bir bitişik ikili-işaret kombinasyonu Microsoft yazım kitaplığı tarafından denetlenir. Tanınırsa, kelime kural ihlali üretir. İhlalin oluşmasına neden olan Birleşik kelimelerin örnekleri, sırasıyla "Checksum" ve "multipart" olarak, "Checksum" ve "multipart" şeklinde olmalıdır. Önceki yaygın kullanım nedeniyle, birkaç özel durum kuralda yerleşik olarak bulunur ve "araç çubuğu" ve "dosya adı" gibi birkaç tek sözcük işaretlenir, bu da iki ayrı sözcük olarak kullanılabilir. Bu örnekte, "araç çubuğu" ve "dosya adı" işaretlenir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Kelimeyi doğru bir şekilde olacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bileşik sözcüğün her iki bölümü de yazım sözlüğü tarafından tanınıyorsa ve amaç iki sözcükten birini kullanıyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir.

 Ayrıca, yazım denetleyicisi için özel bir sözlüğe bileşik sözcükler ekleyebilirsiniz. Özel Sözlükteki sözcükler ihlallere neden olmaz. Daha fazla bilgi için bkz. [nasıl yapılır: kod analizi sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>İlgili kurallar
 [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Büyük harfe çevirme kuralları](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [Adlandırma yönergeleri](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
