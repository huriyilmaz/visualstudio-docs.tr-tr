---
title: 'CA1725: Parametre adları taban yöntem ile eşleşmelidir'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 417e03f5d682ad448372d74fa8c9a5c31b798ccc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72438921"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Parametre adları taban yöntem ile eşleşmelidir

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir yöntem geçersiz kılma içindeki bir parametrenin adı, metodun temel bildirimindeki parametrenin adı veya metodun arabirim bildiriminde parametresinin adı ile eşleşmiyor.

Bu kural varsayılan olarak yalnızca dışarıdan görünen yöntemlere bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için parametreyi temel bildirimle eşleşecek şekilde yeniden adlandırın. Bu çözüm, COM görünebilir yöntemlerine yönelik bir son değişiklik.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Daha önce sevk edilen kitaplıklarda COM görünebilir Yöntemler hariç, bu kuraldan bir uyarıyı bastırmayın.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1725.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (adlandırma) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).
