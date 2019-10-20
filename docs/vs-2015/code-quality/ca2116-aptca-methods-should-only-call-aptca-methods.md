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
ms.openlocfilehash: c9de5178b585275ef410ad3179ba320b663536bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658686"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 @No__t_0 özniteliği olan derlemedeki bir yöntem, özniteliği olmayan bir derlemede bir yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan olarak, tanımlayıcı adlara sahip derlemelerde ortak veya korumalı Yöntemler, tam güven için [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) dolaylı olarak korunur; yalnızca tam güvenilir çağıranlar, tanımlayıcı adlı bir derlemeye erişebilir. @No__t_0 (APTCA) özniteliğiyle işaretlenen tanımlayıcı adlı derlemelerin bu koruması yoktur. Öznitelik, bir intranet veya Internet 'ten çalıştırılan kod gibi, derlemeyi tam güvene sahip olmayan çağıranlar için erişilebilir hale getirerek bağlantı talebini devre dışı bırakır.

 APTCA özniteliği tam olarak güvenilen bir derlemede olduğunda ve derleme kodu, kısmen güvenilen çağıranlara izin verilmeyen başka bir derlemede yürüttüğünde, bir güvenlik açığından yararlanma olasılığı vardır. İki yöntem `M1` ve `M2` aşağıdaki koşullara uyuyorsa, kötü amaçlı arayanlar `M2` koruyan örtük tam güven bağlantısı talebini atlamak için `M1` yöntemini kullanabilir:

- `M1`, APTCA özniteliğine sahip tam güvenilir bir derlemede tanımlanan ortak bir yöntemdir.

- `M1`, `M1` ' nin bütünleştirilmiş kodu dışında `M2` yöntemini çağırır.

- `M2` derlemesi APTCA özniteliğine sahip değil ve bu nedenle, kısmen güvenilen çağıranlar adına veya tarafından yürütülmemelidir.

  Kısmen güvenilir bir arayan `X` Yöntem `M1` çağırabilir, bu da `M1` `M2` çağırmasına neden olur. @No__t_0 APTCA özniteliğine sahip olmadığından, hemen arayanın (`M1`) tam güven için bir bağlantı talebini karşılaması gerekir;  `M1` tam güvene sahiptir ve bu nedenle bu denetimi karşılar. Güvenlik riski, `X` ' ın, güvenilmeyen çağıranlardan `M2` ' i koruyan bağlantı talebini karşılamadığına katılmadığından. Bu nedenle, APTCA özniteliğine sahip Yöntemler özniteliği olmayan yöntemleri çağırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 APCTA özniteliği gerekliyse, tam güven derlemesine çağıran yöntemi korumak için bir talep kullanın. Talep ettiğiniz tam izinler, yönteminiz tarafından sunulan işlevlere bağlıdır. Mümkünse, temel işlevselliğin kısmen güvenilen çağıranlara açık olmamasını sağlamak için yöntemi tam güven için bir talep ile koruyun. Bu mümkün değilse, sunulan işlevleri etkin bir şekilde koruyan bir izin kümesi seçin. Talepler hakkında daha fazla bilgi için bkz. [talepler](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı güvenle bastırmak için, yönteminiz tarafından sunulan işlevselliğin doğrudan veya dolaylı olarak, çağıranların bozucu bir şekilde kullanılabilecek gizli bilgilere, işlemlere veya kaynaklara erişmesine izin vermez.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açıklarını göstermek için iki derleme ve bir test uygulaması kullanır. İlk derleme APTCA özniteliğine sahip değil ve kısmen güvenilen çağıranlar tarafından erişilememelidir (önceki tartışmadaki `M2` ile temsil edilir).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Örnek
 İkinci derleme tamamen güvenilirdir ve kısmen güvenilen çağıranlara (önceki tartışmada `M1` ile temsil edilir) izin verir.

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Örnek
 Test uygulaması (önceki tartışmada `X` ile temsil edilir) kısmen güvenilirdir.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Tam güven talebi: istek başarısız oldu.** 
**Classkarşılandığından ıringfulltrust. DoWork çağrıldı.**
## <a name="related-rules"></a>İlgili kurallar
 [CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Kısmen güvenilen kod taleplerine ait kitaplıklar kullanılarak](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [kısmen güvenilen kod tarafından çağrılabilir olan derlemelerin .NET Framework](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [bağlantı talep](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
