---
title: 'CA2205: Win32 API yönetilen eşdeğerlerini kullan | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609481"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Platform çağırma yöntemi tanımlanır ve [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sınıf kitaplığında denk işlevlere sahip bir yöntem bulunur.

## <a name="rule-description"></a>Kural Tanımı
 Bir platform çağırma yöntemi, yönetilmeyen bir DLL işlevini çağırmak için kullanılır ve <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği veya Visual Basic `Declare` anahtar sözcüğü kullanılarak tanımlanır. Yanlış tanımlanmış bir platform çağırma yöntemi, yanlış adlandırılmış bir işlev, parametre ve dönüş değeri veri türlerinin hatalı eşlemesi ve çağırma kuralı ve karakteri gibi yanlış alan belirtimleri nedeniyle çalışma zamanı özel durumlarına neden olabilir kurmak. Varsa, genellikle daha basit ve yönetilmeyen yöntemi doğrudan çağırdığından, eşdeğer yönetilen yöntemi çağırmak için daha basit ve daha az hataya açıktır. Platform çağırma yöntemini çağırmak, giderilmesi gereken ek güvenlik sorunlarına da yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için yönetilmeyen işleve yapılan çağrıyı, yönetilen eşdeğeri çağrısıyla değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Önerilen değiştirme yöntemi gerekli işlevselliği sağlamıyorsa bu kuraldan bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir platform çağırma yöntemi tanımını gösterir. Ayrıca, platform çağırma yöntemine yapılan çağrılar ve eşdeğer yönetilen yöntem gösterilir.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1404: P/Invoke ardından hemen GetLastError çağırın](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
