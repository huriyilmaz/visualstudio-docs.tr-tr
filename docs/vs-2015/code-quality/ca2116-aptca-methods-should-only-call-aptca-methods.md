---
title: 'CA2116Ç: APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 115c0e733716994ba463eada938f8ff908612d0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547764"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA metotları yalnızca APTCA metotlarını çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Özniteliği olan derlemedeki bir yöntem özniteliği olmayan bir <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> derlemede bir yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan olarak, tanımlayıcı adlara sahip derlemelerde ortak veya korumalı Yöntemler, tam güven için [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) dolaylı olarak korunur; yalnızca tam güvenilir çağıranlar, tanımlayıcı adlı bir derlemeye erişebilir. <xref:System.Security.AllowPartiallyTrustedCallersAttribute>(Aptca) özniteliğiyle işaretlenen tanımlayıcı adlı derlemelerin bu koruması yoktur. Öznitelik, bir intranet veya Internet 'ten çalıştırılan kod gibi, derlemeyi tam güvene sahip olmayan çağıranlar için erişilebilir hale getirerek bağlantı talebini devre dışı bırakır.

 APTCA özniteliği tam olarak güvenilen bir derlemede olduğunda ve derleme kodu, kısmen güvenilen çağıranlara izin verilmeyen başka bir derlemede yürüttüğünde, bir güvenlik açığından yararlanma olasılığı vardır. İki yöntem `M1` ve `M2` aşağıdaki koşulları karşılıyorsa, kötü amaçlı arayanlar, `M1` koruduğu örtük tam güven bağlantısı talebini atlamak için yöntemini kullanabilir `M2` :

- `M1` , APTCA özniteliğine sahip tam güvenilir bir derlemede bildirildiği ortak bir yöntemdir.

- `M1` derleme dışında bir yöntemi çağırır `M2` `M1` .

- `M2`derlemesinin APTCA özniteliği yok ve bu nedenle, kısmen güvenilen çağıranlar adına veya tarafından yürütülmemelidir.

  Kısmen güvenilen bir çağıran `X` yöntemi çağırabilir `M1` ve çağrıya neden olur `M1` `M2` . , `M2` APTCA özniteliğine sahip olmadığından, hemen çağıranın ( `M1` ) tam güven için bir bağlantı talebini karşılaması gerekir; `M1` tam güvene sahip ve bu nedenle bu denetimi karşılar. Güvenlik riski, `X` Güvenilmeyen çağıranların koruduğu bağlantı talebini karşılamadığına katılmaz `M2` . Bu nedenle, APTCA özniteliğine sahip Yöntemler özniteliği olmayan yöntemleri çağırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 APCTA özniteliği gerekliyse, tam güven derlemesine çağıran yöntemi korumak için bir talep kullanın. Talep ettiğiniz tam izinler, yönteminiz tarafından sunulan işlevlere bağlıdır. Mümkünse, temel işlevselliğin kısmen güvenilen çağıranlara açık olmamasını sağlamak için yöntemi tam güven için bir talep ile koruyun. Bu mümkün değilse, sunulan işlevleri etkin bir şekilde koruyan bir izin kümesi seçin. Talepler hakkında daha fazla bilgi için bkz. [talepler](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı güvenle bastırmak için, yönteminiz tarafından sunulan işlevselliğin doğrudan veya dolaylı olarak, çağıranların bozucu bir şekilde kullanılabilecek gizli bilgilere, işlemlere veya kaynaklara erişmesine izin vermez.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açıklarını göstermek için iki derleme ve bir test uygulaması kullanır. İlk derleme APTCA özniteliğine sahip değil ve kısmen güvenilen çağıranlar tarafından erişilememelidir (önceki tartışmada tarafından temsil edilir `M2` ).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Örnek
 İkinci derleme tamamen güvenilirdir ve kısmen güvenilen çağıranlar ( `M1` önceki tartışmada tarafından temsil edilir) sağlar.

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Örnek
 Test uygulaması ( `X` önceki tartışmada tarafından temsil edilir) kısmen güvenilirdir.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Tam güven talebi: istek başarısız oldu.** 
 **Classkarşılandığından ıringfulltrust. DoWork çağrıldı.**
## <a name="related-rules"></a>İlgili kurallar
 [CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kısmen güvenilen kod taleplerine ait kitaplıklar kullanılarak](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Demands](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [kısmen güvenilen kod tarafından çağrılabilir olan derlemelerin .NET Framework](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [bağlantı talep](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
