---
title: "CA1401: P-Invoke'lar görünür olmamalıdır"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b06aa26b046743b06f8fdd274da7a804a5ec06f6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440728"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invoke'lar görünür olmamalıdır

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategori|Microsoft. çalışabilirliği|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Ortak bir türdeki ortak veya korumalı yöntemin <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği vardır (Ayrıca [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ' deki `Declare` anahtar sözcüğü tarafından da uygulanır).

## <a name="rule-description"></a>Kural açıklaması
@No__t-0 özniteliğiyle işaretlenen Yöntemler (veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ' deki `Declare` anahtar sözcüğü kullanılarak tanımlanan Yöntemler), yönetilmeyen koda erişmek için platform çağırma hizmetleri 'ni kullanır. Bu tür yöntemler açıkta kalmamalıdır. Bu yöntemleri özel veya dahili tutarak, kayıt yapanların yönetilmeyen API 'lere, aksi takdirde çağıramazlar.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için yöntemin erişim düzeyini değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, bu kuralı ihlal eden bir yöntemi bildirir.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]
