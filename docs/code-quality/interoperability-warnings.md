---
title: Taşınabilirlik ve birlikte çalışabilirlik uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808606"
---
# <a name="portability-and-interoperability-rules"></a>Taşınabilirlik ve birlikte çalışabilirlik kuralları

Taşınabilirlik kuralları farklı platformlarda taşınabilirliği destekler. Birlikte çalışabilirlik kuralları COM istemcileriyle etkileşimi destekler.

## <a name="in-this-section"></a>Bu Bölümde

| Kural | Açıklama |
| - | - |
| [CA1401: P/Invoke görünür olmamalıdır](../code-quality/ca1401.md) | Ortak bir türdeki ortak veya korumalı yöntemin System.Runtime.InteropServices.DllImportAttribute özniteliği vardır (Ayrıca, Visual Basic Declare anahtar sözcüğü tarafından uygulanır). Bu tür yöntemler açıkta kalmamalıdır. |
| [CA1416: Platform uyumluluğunu doğrula](../code-quality/ca1416.md) | Bir bileşende platforma bağımlı API 'Lerin kullanılması, kodun artık tüm platformlarda çalışmamasına neden olur. |
| [CA1417: `OutAttribute` P/Invoke için dize parametrelerinde kullanmayın](../code-quality/ca1417.md) | Değeri ile geçirilen dize parametreleri, `OutAttribute` dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir. |
