---
title: 'CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09fa055fbf1b11e06b1dde32df5a316a3ec39848
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658653"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 @No__t_0 özniteliğine sahip bir derlemede ortak veya korumalı tür özniteliği olmayan bir derlemede belirtilen türden devralır.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan olarak, tanımlayıcı adlara sahip derlemelerde ortak veya korumalı türler, tam güven için bir [devralma talebi](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) tarafından örtük olarak korunur. @No__t_0 (APTCA) özniteliğiyle işaretlenen tanımlayıcı adlı derlemelerin bu koruması yoktur. Öznitelik, devralma talebini devre dışı bırakır. Bu, derlemede belirtilen açık türlerin tam güvene sahip olmayan türler tarafından devralınabilir hale gelmesini sağlar.

 APTCA özniteliği tam olarak güvenilen bir derlemede olduğunda ve derlemedeki bir tür, kısmen güvenilen çağıranlara izin verilmeyen bir türden devralırsa, bir güvenlik açığından yararlanma olasılığı vardır. İki tür `T1` ve `T2` aşağıdaki koşullara uyuyorsa, kötü amaçlı arayanlar `T2` ' i koruyan örtük tam güven devralma talebini atlamak için `T1` türünü kullanabilir:

- `T1`, APTCA özniteliğine sahip tam güvenilir bir derlemede tanımlanan ortak bir tür.

- `T1`, derleme dışında `T2` türünden devralır.

- `T2` derlemesi APTCA özniteliğine sahip değil ve bu nedenle kısmen güvenilen derlemelerdeki türlere devredilemez.

  @No__t_0 kısmen güvenilir bir tür `T1` devralabilir ve bu, `T2` tarafından belirtilen devralınan üyelere erişim sağlar. @No__t_0 APTCA özniteliğine sahip olmadığından, anlık türetilmiş türü (`T1`) tam güven için bir devralma talebini karşılamalıdır;  `T1` tam güvene sahiptir ve bu nedenle bu denetimi karşılar. Güvenlik riski, `X` güvenilmeyen altsınıflama 'tan `T2` koruyan devralma taleplerini karşılamadığına katılmaz. Bu nedenle, APTCA özniteliğine sahip türler özniteliği olmayan türleri genişletmemelidir.

  Diğer bir güvenlik sorunu ve belki de daha yaygın bir deyişle, türetilmiş türün (`T1`), programcı hatası aracılığıyla, tam güven gerektiren türden korumalı üyeleri kullanıma sunmasıdır (`T2`). Bu durumda, güvenilmeyen çağıranlar yalnızca tam güvenilir türler için kullanılabilir olması gereken bilgilere erişim elde edebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İhlalin tarafından bildirilen tür APTCA özniteliğini gerektirmeyen bir derlemede ise, kaldırın.

 APTCA özniteliği gerekliyse, türe tam güven için bir devralma talebi ekleyin. Bu, güvenilmeyen türlerin devralınmasını önler.

 İhlalin tarafından bildirilen temel türlerin Derlemeleriyle APTCA özniteliğini ekleyerek ihlalin düzeltilmesi mümkündür. Bu, öncelikle derlemelerdeki tüm kodun ve derlemelere bağlı olan tüm kodun yoğun bir güvenlik incelemesi yapmadan bunu kullanmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı güvenle bastırmak için, sizin oluşturduğunuz korumalı üyelerin, güvenilmeyen çağıranların, zararlı bir şekilde kullanılabilecek gizli bilgilere, işlemlere veya kaynaklara erişmesine doğrudan veya dolaylı olarak izin vermediğinden emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açıklarını göstermek için iki derleme ve bir test uygulaması kullanır. İlk derleme APTCA özniteliğine sahip değil ve kısmen güvenilen türler (önceki tartışmadaki `T2` ile temsil edilir) tarafından devredilemez olmalıdır.

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Örnek
 Önceki tartışmada `T1` ile temsil edilen ikinci derleme, tamamen güvenilirdir ve kısmen güvenilen çağıranlara izin verir.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Örnek
 Önceki tartışmada `X` ile temsil edilen test türü kısmen güvenilen bir derlemede yer.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Shady Glen 2/22/2003 12:00:00 Ile buluşuyor!** **testten 
: güneşli Meadow** 
 **, güneşli Meadow 2/22/2003 12:00:00 ile buluşuyor!**
## <a name="related-rules"></a>İlgili kurallar
 [CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Ayrıca Bkz.
 Kısmen güvenilen kod [Devralma taleplerine](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [ait kitaplıklar kullanılarak](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [kısmen güvenilen kod tarafından çağrılabilir olan derlemelerin .NET Framework](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
