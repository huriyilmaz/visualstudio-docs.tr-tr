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
ms.openlocfilehash: d1083f7bbdf3b3af78b83aed293b31d898ae7522
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661370"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: P/Invoke giriş noktaları bulunmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir yöntem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> ile işaretlenir. Yönetilmeyen kitaplık bulunamadı ya da yöntem için bir işlev kitaplığında eşleştirilemedi. Kural, yöntem adını tam olarak belirtilen şekilde bulamazsa, yöntem adını ' A ' veya ' W ' ile birlikte düzelterek metodun ANSI veya geniş karakterli sürümlerini arar. Eşleşme bulunmazsa, kural __stdcall ad biçimini kullanarak bir işlevi bulmaya çalışır (_MyMethod@12, burada 12 bağımsız değişkenlerin uzunluğunu temsil eder). Eşleşme bulunmazsa ve Yöntem adı ' # ' ile başlıyorsa, kural, işlevi bir ad başvurusu yerine bir sıralı başvuru olarak arar.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 ile işaretlenmiş yöntemlerin başvurulan yönetilmeyen DLL 'de bulunduğundan emin olmak için derleme zamanı denetimi yoktur. Kitaplıkta belirtilen ada sahip hiçbir işlev yoksa veya metodun bağımsız değişkenleri işlev bağımsız değişkenleriyle eşleşmezse, ortak dil çalışma zamanı bir özel durum oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğine sahip olan yöntemi düzeltin. Yönetilmeyen kitaplığın var olduğundan ve yöntemi içeren derlemeyle aynı dizinde olduğundan emin olun. Kitaplık varsa ve doğru şekilde başvuruluyorsa, yöntem adı, dönüş türü ve bağımsız değişken imzasının kitaplık işleviyle eşleştiğinden emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yönetilmeyen kitaplık, kendisine başvuran yönetilen derlemeyle aynı dizinde olduğunda, bu kuraldan bir uyarıyı bastırmayın. Yönetilmeyen kitaplığın yer aldığı durumlarda bu kuraldan bir uyarıyı gizlemek güvenli olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir. Kernel32. dll içinde `DoSomethingUnmanaged` adlı bir işlev oluşur.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
