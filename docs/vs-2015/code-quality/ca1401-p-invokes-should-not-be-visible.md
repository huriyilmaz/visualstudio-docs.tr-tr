---
title: 'CA1401: P-Invoke görünür olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3f867f14f7a2eca4482f1f8d5fb48149f02f43f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661367"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invoke'lar görünür olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak bir türdeki ortak veya korumalı yöntemin <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği vardır (Ayrıca [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Declare` anahtar sözcüğü tarafından uygulanır).

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 özniteliğiyle işaretlenen Yöntemler (veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Declare` anahtar sözcüğü kullanılarak tanımlanan Yöntemler), yönetilmeyen koda erişmek için platform çağırma hizmetleri 'ni kullanır. Bu tür yöntemler açıkta kalmamalıdır. Bu yöntemleri özel veya dahili tutarak, kayıt yapanların yönetilmeyen API 'lere, aksi takdirde çağıramazlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için yöntemin erişim düzeyini değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir yöntemi bildirir.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
