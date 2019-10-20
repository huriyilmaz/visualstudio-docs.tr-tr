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
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610154"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Saydam türler güvenlik bildirimlerini kullanmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 @No__t_0 olarak işaretlenen koda, onaylama için yeterli izin verilmez.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, bir derlemedeki tüm yöntemleri ve türleri, %100 saydam veya saydam/kritik karışık/kritik olarak analiz eder ve <xref:System.Security.CodeAccessPermission.Assert%2A> bildirime dayalı ya da kesinlik kullanımını işaretler.

 Çalışma zamanında, saydam koddan <xref:System.Security.CodeAccessPermission.Assert%2A> yapılan çağrılar <xref:System.InvalidOperationException> oluşturulmasına neden olur. Bu, hem %100 saydam derlemede hem de bir yöntem ya da türün saydam olarak bildirildiği, ancak bildirime dayalı veya zorunlu bir onay içeren karışık saydam/kritik derlemelerde meydana gelebilir.

 @No__t_0 2,0, *Saydamlık*adlı bir özellik sunmuştur. Tek tek Yöntemler, alanlar, arabirimler, sınıflar ve türler saydam ya da kritik olabilir.

 Saydam kodun güvenlik ayrıcalıklarını yükseltmesine izin verilmiyor. Bu nedenle, verilen veya talep edilen tüm izinler otomatik olarak kod aracılığıyla arayan veya ana bilgisayar uygulama etki alanına geçirilir. Yükseltme örnekleri, onaylar, Linktaleplerini, SuppressUnmanagedCode ve `unsafe` kodu içerir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sorunu çözmek için, <xref:System.Security.SecurityCriticalAttribute> onayı çağıran kodu işaretleyin ya da onayı kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir ileti bastırmayın.

## <a name="example"></a>Örnek
 @No__t_1 yöntemi bir <xref:System.InvalidOperationException> oluşturduğunda `SecurityTestClass` saydamsa Bu kod başarısız olur.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Örnek
 Bir seçenek, aşağıdaki örnekteki SecurityTransparentMethod yöntemini gözden geçirmeniz ve yöntemin yükseltme için güvenli olarak kabul edilmesi durumunda, SecurityTransparentMethod 'i güvenli kritik ile işaretlemek, ayrıntılı, tam ve hata içermeyen bir güvenlik gerektirir Denetim, yöntemde, onay altındaki yöntemde gerçekleşen tüm çağrı aşımları ile birlikte gerçekleştirilmelidir:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Diğer bir seçenek de koddan yapılan onayı kaldırmak ve sonraki dosya g/ç izin taleplerini, SecurityTransparentMethod ' nin çağıranına dışına akmasını sağlar. Bu, güvenlik denetimlerini mümkün bir şekilde sunar. Bu durumda, izin talepleri arayan ve/veya uygulama etki alanına akacağından, güvenlik denetimi genellikle gerekli değildir. İzin talepleri, güvenlik ilkesi, barındırma ortamı ve kod kaynağı izin onayları aracılığıyla yakından denetlenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenlik Uyarıları](../code-quality/security-warnings.md)
