---
title: 'CA1504: Yanlış alan adlarını gözden geçirin'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa997ad5afb77df126cd0824d574884bef828ab6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443998"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Yanlış alan adlarını gözden geçirin

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategori|Microsoft. Bakımolmaması|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
Bir örnek alanının adı "s_" ile başlar veya @no__t adı-0 @no__t ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) alanında "m_" ile başlar.

## <a name="rule-description"></a>Kural açıklaması
"S_" ile başlayan alan adları, birçok kullanıcı tarafından statik verilerle ilişkilendirilir. Benzer şekilde, "m_" ile başlayan alan adları, örnek (üye) verilerle ilişkilendirilir. Daha kolay yönetilebilir kod için adlar genellikle kullanılan kurallara uymalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, uygun öneki kullanarak alanı yeniden adlandırın. Alternatif olarak, `static` değiştiricisini ekleyerek veya kaldırarak alanı geçerli soneke kabul edin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.
