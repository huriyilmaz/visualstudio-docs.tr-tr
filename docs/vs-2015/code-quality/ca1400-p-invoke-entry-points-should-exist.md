---
title: 'CA1400: P-Invoke giriş noktaları var olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548310"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: P/Invoke giriş noktaları bulunmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir yöntem ile işaretlenir <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Yönetilmeyen kitaplık bulunamadı ya da yöntem için bir işlev kitaplığında eşleştirilemedi. Kural, yöntem adını tam olarak belirtilen şekilde bulamazsa, yöntem adını ' A ' veya ' W ' ile birlikte düzelterek metodun ANSI veya geniş karakterli sürümlerini arar. Eşleşme bulunmazsa, kural __stdcall adı biçimini kullanarak bir işlevi bulmaya çalışır ( _MyMethod@12 burada, 12 bağımsız değişkenlerin uzunluğunu temsil eder). Eşleşme bulunmazsa ve Yöntem adı ' # ' ile başlıyorsa, kural, işlevi bir ad başvurusu yerine bir sıralı başvuru olarak arar.

## <a name="rule-description"></a>Kural Tanımı
 İle işaretlenen yöntemlerin <xref:System.Runtime.InteropServices.DllImportAttribute> başvurulan YÖNETILMEYEN dll 'de bulunduğundan emin olmak için derleme zamanı denetimi kullanılamaz. Kitaplıkta belirtilen ada sahip hiçbir işlev yoksa veya metodun bağımsız değişkenleri işlev bağımsız değişkenleriyle eşleşmezse, ortak dil çalışma zamanı bir özel durum oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için özniteliğine sahip olan yöntemi düzeltin <xref:System.Runtime.InteropServices.DllImportAttribute> . Yönetilmeyen kitaplığın var olduğundan ve yöntemi içeren derlemeyle aynı dizinde olduğundan emin olun. Kitaplık varsa ve doğru şekilde başvuruluyorsa, yöntem adı, dönüş türü ve bağımsız değişken imzasının kitaplık işleviyle eşleştiğinden emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yönetilmeyen kitaplık, kendisine başvuran yönetilen derlemeyle aynı dizinde olduğunda, bu kuraldan bir uyarıyı bastırmayın. Yönetilmeyen kitaplığın yer aldığı durumlarda bu kuraldan bir uyarıyı gizlemek güvenli olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir. kernel32.dll adında hiçbir işlev `DoSomethingUnmanaged` oluşmaz.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
