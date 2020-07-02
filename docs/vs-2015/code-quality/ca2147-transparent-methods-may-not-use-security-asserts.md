---
title: 'CA2147: Saydam yöntemler güvenlik onayları kullanmayabilir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 45639afc9946aa43df121a5a1881174371413c25
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546386"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Saydam metotlar güvenlik onay deyimlerini kullanmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Olarak işaretlenen koda, onay <xref:System.Security.SecurityTransparentAttribute> için yeterli izin verilmez.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, bir derlemedeki tüm yöntemleri ve türleri %100 saydam ya da saydam/kritik olarak analiz eder ve herhangi bir bildirime dayalı ya da kesinlik kullanımını işaretler <xref:System.Security.CodeAccessPermission.Assert%2A> .

 Çalışma zamanında, saydam koddan yapılan tüm çağrılar <xref:System.Security.CodeAccessPermission.Assert%2A> bir oluşturulmasına neden olur <xref:System.InvalidOperationException> . Bu, hem %100 saydam derlemede hem de bir yöntem ya da türün saydam olarak bildirildiği, ancak bildirime dayalı veya zorunlu bir onay içeren karışık saydam/kritik derlemelerde meydana gelebilir.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2,0, *Saydamlık*adlı bir özellik sunmuştur. Tek tek Yöntemler, alanlar, arabirimler, sınıflar ve türler saydam ya da kritik olabilir.

 Saydam kodun güvenlik ayrıcalıklarını yükseltmesine izin verilmiyor. Bu nedenle, verilen veya talep edilen tüm izinler otomatik olarak kod aracılığıyla arayan veya ana bilgisayar uygulama etki alanına geçirilir. Yükseltme örnekleri, onaylar, Linktaleplerini, SuppressUnmanagedCode ve `unsafe` Code içerir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sorunu çözmek için, onayı çağıran kodu işaretleyin ya da <xref:System.Security.SecurityCriticalAttribute> onayı kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir ileti bastırmayın.

## <a name="example"></a>Örnek
 Bu kod, saydam ise `SecurityTestClass` , `Assert` Yöntem bir oluşturduğunda başarısız olur <xref:System.InvalidOperationException> .

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Örnek
 Bir seçenek, aşağıdaki örnekteki SecurityTransparentMethod yöntemini gözden geçirin ve yöntemin yükseltme için güvenli olarak kabul edilmesi durumunda, SecurityTransparentMethod, güvenli-kritik ile Mark, bu, yöntemde oluşan herhangi bir çağrı ile birlikte yöntem üzerinde, ayrıntılı, tam ve hata içermeyen bir güvenlik denetiminin gerçekleştirilmesi gerekir:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Diğer bir seçenek de koddan yapılan onayı kaldırmak ve sonraki dosya g/ç izin taleplerini, SecurityTransparentMethod ' nin çağıranına dışına akmasını sağlar. Bu, güvenlik denetimlerini mümkün bir şekilde sunar. Bu durumda, izin talepleri arayan ve/veya uygulama etki alanına akacağından, güvenlik denetimi genellikle gerekli değildir. İzin talepleri, güvenlik ilkesi, barındırma ortamı ve kod kaynağı izin onayları aracılığıyla yakından denetlenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenlik uyarıları](../code-quality/security-warnings.md)
