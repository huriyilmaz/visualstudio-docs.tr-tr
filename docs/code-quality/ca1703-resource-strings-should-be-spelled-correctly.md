---
title: 'CA1703: Kaynak dizeler doğru yazılmalıdır'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7143b1e5550d7dbc24b3364b9a3a1e855d52e632
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443905"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Kaynak dizeler doğru yazılmalıdır

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategori|Microsoft. Naming|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Kaynak dizesi, Microsoft Yazım kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.

## <a name="rule-description"></a>Kural açıklaması

Bu kural, kaynak dizesini kelimelere ayrıştırır (Birleşik kelimeleri simgeleştiriler) ve her bir sözcüğün/belirtecin yazımını denetler. Ayrıştırma algoritması hakkında daha fazla bilgi için bkz. [CA1704: tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için doğru yazılmış olan tüm sözcükleri kullanın veya sözcükleri özel bir sözlüğe ekleyin. Özel sözlükleri kullanma hakkında daha fazla bilgi için bkz. [CA1704: tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Sözlük dilini değiştirme

Varsayılan olarak, yazım denetleyicisinin Ingilizce (en) sürümü kullanılır. Yazım denetleyicisinin dilini değiştirmek istiyorsanız, *AssemblyInfo.cs* veya *AssemblyInfo. vb* dosyanıza aşağıdaki özniteliklerden birini ekleyerek bunu yapabilirsiniz:

- Kaynaklarınızın uydu derlemesinde olması durumunda kültürü belirtmek için <xref:System.Reflection.AssemblyCultureAttribute> kullanın.
- Kaynaklarınızın kodunuzla aynı derlemede olması halinde, derlemelerinizin *bağımsız kültürünü* belirtmek için <xref:System.Resources.NeutralResourcesLanguageAttribute> kullanın.

> [!IMPORTANT]
> Kültürü, Ingilizce tabanlı kültür dışında bir şeye ayarlarsanız, bu kod analizi kuralı sessizce devre dışıdır.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Bu kuraldan uyarıyı bastırmayın. Doğru yazılmış sözcükler, yeni yazılım kitaplıklarını öğrenmek için gereken süreyi azaltır.

## <a name="related-rules"></a>İlgili kurallar

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204.md)
