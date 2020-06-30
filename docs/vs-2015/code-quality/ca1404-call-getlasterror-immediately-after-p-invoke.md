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
ms.openlocfilehash: 54ac9a4d56136d9e981ae038a0b219aa4cb4774e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544501"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: P/Invoke ardından hemen GetLastError çağır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>Yöntemine veya eşdeğer Win32 işlevine çağrı yapılır `GetLastError` ve hemen önce gelen çağrı bir platform çağırma yöntemine değildir.

## <a name="rule-description"></a>Kural Tanımı
 Platform çağırma yöntemi yönetilmeyen koda erişir ve `Declare` içinde veya özniteliğinde anahtar sözcüğü kullanılarak tanımlanır [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Genellikle, hata durumunda yönetilmeyen işlevler, hata `SetLastError` ile ilişkili bir hata kodu ayarlamak Için Win32 işlevini çağırır. Başarısız işlevi çağıran, `GetLastError` hata kodunu almak ve hatanın nedenini öğrenmek Için Win32 işlevini çağırır. Hata kodu iş parçacığı başına temelinde tutulur ve sonraki çağrısıyla üzerine yazılır `SetLastError` . Başarısız platform çağırma yöntemine yapılan çağrıdan sonra, yönetilen kod yöntemini çağırarak hata kodunu alabilir <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> . Hata kodu diğer yönetilen sınıf kitaplığı metotlarından gelen iç çağrılar tarafından üzerine yazılabildiğinden, `GetLastError` veya <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntemi platform çağırma yöntemi çağrısından hemen sonra çağrılmalıdır.

 Kural, platform çağırma yöntemine yapılan çağrı ve çağrısı arasında gerçekleştiklerinde, aşağıdaki yönetilen üyelere yapılan çağrıları yoksayar <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> . Bu Üyeler hata kodunu değiştirmez ve bazı platform çağırma yöntemi çağrılarının başarısını belirlemek için faydalıdır.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için çağrıyı, <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Platform çağırma yöntemine yapılan çağrıyı hemen takip eden öğesine taşıyın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Platform çağırma yöntemi çağrısı ve yöntem çağrısı arasındaki kod, <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> açıkça veya örtük olarak hata kodunun değişmesine neden değilse, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralını karşılayan bir yöntemi ihlal eden bir yöntemi gösterir.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1060: NativeMethods sınıfına P/Invoke taşı](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Win32 API'sinin yönetilen eşdeğerlerini kullanın](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
