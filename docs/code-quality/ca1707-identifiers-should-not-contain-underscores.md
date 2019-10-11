---
title: 'CA1707: Tanımlayıcılar alt çizgi içermemelidir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252578"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Tanımlayıcılar alt çizgi içermemelidir

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft. Naming|
|Son değişiklik|Parçalara ayırma-derlemeler üzerinde ne zaman tetiklenir<br /><br /> Tür parametrelerine ne zaman kabarık olmayan|

## <a name="cause"></a>Nedeni

Bir tanımlayıcının adı alt çizgi (\_) karakterini içerir.

## <a name="rule-description"></a>Kural açıklaması

Kurala göre, tanımlayıcı adları alt çizgi (\_) karakterini içermez. Kural ad alanlarını, türleri, üyeleri ve parametreleri denetler.

Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Adın tüm alt çizgi karakterlerini kaldırır.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Üretim koduna yönelik uyarıları göstermez. Ancak, bu uyarının test kodu için görüntülenmesini güvenlidir. [Önem derecesini](use-roslyn-analyzers.md#rule-severity) **none**olarak ayarlayarak bu kuraldan gelen uyarıları gizleyebilirsiniz. 

## <a name="related-rules"></a>İlgili kurallar

- [CA1709: Tanımlayıcılar doğru olmalıdır @ no__t-0
- [CA1708: Tanımlayıcılar, büyük/küçük harf bakımından farklı olmalıdır @ no__t-0
