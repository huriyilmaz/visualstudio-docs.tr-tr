---
title: Taşınabilirlik ve birlikte çalışabilirlik uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509919"
---
# <a name="portability-and-interoperability-warnings"></a>Taşınabilirlik ve birlikte çalışabilirlik uyarıları

Taşınabilirlik uyarıları, farklı platformlarda taşınabilirliği destekler. Birlikte çalışabilirlik uyarıları COM istemcileriyle etkileşimi destekler.

## <a name="in-this-section"></a>Bu Bölümde

| Kural | Açıklama |
| - | - |
| [CA1401: P/Invoke görünür olmamalıdır](../code-quality/ca1401.md) | Ortak bir türdeki ortak veya korumalı yöntemin System.Runtime.InteropServices.DllImportAttribute özniteliği vardır (Ayrıca, Visual Basic Declare anahtar sözcüğü tarafından uygulanır). Bu tür yöntemler açıkta kalmamalıdır. |
| [CA1417: `OutAttribute` P/Invoke için dize parametrelerinde kullanmayın](../code-quality/ca1417.md) | Değeri ile geçirilen dize parametreleri, `OutAttribute` dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir. |