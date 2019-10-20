---
title: "CA1404: P-Invoke sonrasında GetLastError 'yi çağırın | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661322"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: P/Invoke ardından hemen GetLastError çağır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_0 yöntemine veya eşdeğer Win32 `GetLastError` işlevine çağrı yapılır ve hemen önce gelen çağrı bir platform çağırma yöntemine değildir.

## <a name="rule-description"></a>Kural Tanımı
 Platform çağırma yöntemi yönetilmeyen koda erişir ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliğinde `Declare` anahtar sözcüğü kullanılarak tanımlanır. Genellikle, hata durumunda yönetilmeyen işlevler, hata ile ilişkili bir hata kodu ayarlamak için Win32 `SetLastError` işlevini çağırır. Başarısız işlevi çağıran, hata kodunu almak ve hatanın nedenini öğrenmek için Win32 `GetLastError` işlevini çağırır. Hata kodu iş parçacığı başına temelinde tutulur ve `SetLastError` ' a bir sonraki çağrıya göre üzerine yazılır. Başarısız platform çağırma yöntemine yapılan çağrıdan sonra, yönetilen kod <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntemini çağırarak hata kodunu alabilir. Hata kodu diğer yönetilen sınıf kitaplığı metotlarından gelen iç çağrılar tarafından üzerine yazılabildiğinden, `GetLastError` veya <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntemi platform çağırma yöntemi çağrısından hemen sonra çağrılmalıdır.

 Kural, platform çağırma yöntemine yapılan çağrı ve <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> çağrısı arasında gerçekleştiklerinde, aşağıdaki yönetilen üyelere yapılan çağrıları yoksayar. Bu Üyeler hata kodunu değiştirmez ve bazı platform çağırma yöntemi çağrılarının başarısını belirlemek için faydalıdır.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için çağrıyı, platform çağırma yöntemine yapılan çağrıyı hemen takip eden <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> taşıyın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Platform çağırma yöntemi çağrısı ve <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntemi çağrısı arasındaki kod, açıkça veya örtük olarak hata kodunun değişmesine neden değilse, bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralını karşılayan bir yöntemi ihlal eden bir yöntemi gösterir.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
