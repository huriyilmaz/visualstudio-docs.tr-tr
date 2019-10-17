---
title: 'CA1724: Tür Adları Ad Alanlarıyla Eşleşmemelidir'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5ab83a73da6035df985b93294f850b5a49248f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443454"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: tür adları ad alanlarıyla eşleşmemelidir

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir tür adı, bir veya daha fazla dışarıdan görünür türe sahip Başvurulmuş bir ad alanı adıyla eşleşir. Ad karşılaştırma büyük/küçük harfe duyarlıdır.

## <a name="rule-description"></a>Kural açıklaması

Kullanıcı tarafından oluşturulan tür adları, dışarıdan görünen türler içeren Başvurulmuş ad alanları adlarıyla eşleşmemelidir. Bu kuralın ihlal olması, kitaplığınızın kullanılabilirliğini azaltabilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Türü, dış olarak görünen türler içeren Başvurulmuş bir ad alanının adıyla eşleşmeyen şekilde yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Yeni geliştirme için, bu kuraldan bir uyarıyı bastırmalısınız hiçbir bilinen senaryo oluşmaz. Uyarıyı bastırmadan önce, kitaplığınızdaki kullanıcıların eşleşen ad ile nasıl karışabileceği hakkında dikkatle düşünün. Gönderim kitaplıkları için, bu kuraldan bir uyarıyı bastırın.
