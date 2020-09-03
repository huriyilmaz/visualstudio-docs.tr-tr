---
title: 'CA1703: kaynak dizeleri doğru yazılmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544059"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Kaynak dizeleri doğru yazılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Kaynak dizesi, Microsoft Yazım kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, kaynak dizesini kelimelere ayrıştırır (Birleşik kelimeleri simgeleştiriler) ve her bir sözcüğün/belirtecin yazımını denetler. Ayrıştırma algoritması hakkında daha fazla bilgi için bkz. [CA1704: tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Varsayılan olarak, yazım denetleyicisinin Ingilizce (en) sürümü kullanılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için doğru yazılmış olan tüm sözcükleri kullanın veya sözcükleri özel bir sözlüğe ekleyin. Özel sözlükleri kullanma hakkında daha fazla bilgi için bkz. [CA1704: tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Doğru yazılmış sözcükler, yeni yazılım kitaplıklarını öğrenmek için gereken süreyi azaltır.

## <a name="related-rules"></a>İlgili kurallar
 [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Harfler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
