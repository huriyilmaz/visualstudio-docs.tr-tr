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
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546711"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: COM kayıt metotları eşleşmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş ancak özniteliğiyle işaretlenmiş bir yöntemi bildirmeyen bir yöntemi bildirir <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> veya tam tersi de geçerlidir.

## <a name="rule-description"></a>Kural Tanımı
 Bileşen nesne modeli (COM) istemcilerinin bir tür oluşturması için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] öncelikle türün kaydedilmesi gerekir. Varsa, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> Kullanıcı tarafından belirtilen kodu çalıştırmak için kayıt işlemi sırasında özniteliğiyle işaretlenmiş bir yöntem çağrılır. Kayıt yönteminin işlemlerini tersine çevirmek için, özniteliği ile işaretlenen karşılık gelen bir yöntem, <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> kayıt silme işlemi sırasında çağrılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için ilgili kayıt veya kayıt silme yöntemini ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir. Açıklamalı kod, ihlalin düzeltmesini gösterir.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1411: COM kayıt metotları görünebilir olmamalıdır](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[DERLEMELERI COMRegasm.exe kaydetme](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(derleme kayıt aracı)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
