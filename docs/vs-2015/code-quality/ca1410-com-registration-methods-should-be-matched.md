---
title: 'CA1410: COM kayıt yöntemlerinin eşleşmesi gerekir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30f507f07de858dc222b4824ac6da633c76812ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652738"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM kayıt yöntemleri eşleşmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş ancak <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş bir yöntemi bildirmeyen veya tam tersi bir yöntem bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Bileşen nesne modeli (COM) istemcilerinin bir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] türü oluşturması için öncelikle türün kaydedilmesi gerekir. Varsa, Kullanıcı tarafından belirtilen kodu çalıştırmak için kayıt işlemi sırasında <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> özniteliğiyle işaretlenmiş bir yöntem çağrılır. Kayıt yönteminin işlemlerini tersine çevirmek için, <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> özniteliğiyle işaretlenen karşılık gelen bir yöntem, kayıt silme işlemi sırasında çağrılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için ilgili kayıt veya kayıt silme yöntemini ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir. Açıklamalı kod, ihlalin düzeltmesini gösterir.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1411: COM kayıt yöntemleri görünebilir olmamalıdır](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Ayrıca Bkz.
 COM [Regasm. exe (derleme kayıt aracı)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb) [ile derlemeleri kaydetme](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
