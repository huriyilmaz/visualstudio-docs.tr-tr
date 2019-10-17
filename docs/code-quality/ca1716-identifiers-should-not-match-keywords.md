---
title: 'CA1716: Tanımlayıcılar anahtar sözcüklerle eşleşmemelidir'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b52fb16d2cf5e56ded5cf8f4ed9e8e25c942d7c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72438981"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Tanımlayıcılar anahtar sözcüklerle eşleşmemelidir

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir ad alanı, tür veya sanal ya da arabirim üyesinin adı, bir programlama dilinde ayrılmış bir anahtar sözcükle eşleşir.

Bu kural varsayılan olarak yalnızca dışarıdan görünen ad alanları, türler ve Üyeler ' e bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

Ad alanları, türler ve sanal ve arabirim üyelerinin tanımlayıcıları, ortak dil çalışma zamanını hedefleyen diller tarafından tanımlanan anahtar sözcüklerle eşleşmemelidir. Kullanılan dile ve anahtar sözcüğüne bağlı olarak, derleyici hataları ve belirsizlikleri, kitaplığı kullanmayı zorlaştırır.

Bu kural aşağıdaki dillerdeki anahtar sözcüklere karşı denetler:

- Visual Basic
- C#
- C++/CLI

Büyük/küçük harfe duyarsız karşılaştırma, Visual Basic anahtar kelimeleri için kullanılır ve diğer diller için büyük/küçük harfe duyarlı karşılaştırma kullanılır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Anahtar sözcük listesinde görünmeyen bir ad seçin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Tanımlayıcının API kullanıcılarını karıştırmadığına ve kitaplığın .NET 'teki tüm kullanılabilir dillerde kullanılabilir olduğunu ikna ediyorsanız, bu kuraldan bir uyarıyı gizleyebilirsiniz.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (adlandırma) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).
