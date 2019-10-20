---
title: "CA1415: P-Invoke 'ı doğru olarak bildir | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 922cd713867e1e1017a0f13490a08c0950b2afbf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652681"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invoke'ları doğru bildirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Bölünmez olmayan-parametreyi bildiren P/Invoke derleme dışında görülemez. Parçalama-parametreyi bildiren P/Invoke, derleme dışında görünebilirler.|

## <a name="cause"></a>Sebep
 Platform çağırma yöntemi yanlış bir şekilde bildirilmiştir.

## <a name="rule-description"></a>Kural Tanımı
 Platform çağırma yöntemi yönetilmeyen koda erişir ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> `Declare` anahtar sözcüğü kullanılarak tanımlanır. Şu anda, bu kural ÇAKıŞAN bir yapı parametresine işaretçi olan Win32 işlevlerini hedefleyen platform çağırma yöntemi bildirimlerini arar ve karşılık gelen yönetilen parametre <xref:System.Threading.NativeOverlapped?displayProperty=fullName> yapısına yönelik bir işaretçi değildir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için platform çağırma yöntemini doğru bir şekilde bildirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden ve kuralı karşılayan platform çağırma yöntemlerini gösterir.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen Kod ile Birlikte Çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
