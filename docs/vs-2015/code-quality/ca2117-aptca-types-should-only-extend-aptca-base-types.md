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
ms.openlocfilehash: 90c1f66f36fc689ee077ec66f154487d65ee13a1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543617"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Özniteliği içeren bir derlemede ortak veya korumalı tür özniteliği olmayan bir <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> derlemede belirtilen türden devralır.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan olarak, tanımlayıcı adlara sahip derlemelerde ortak veya korumalı türler, tam güven için bir [devralma talebi](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) tarafından örtük olarak korunur. <xref:System.Security.AllowPartiallyTrustedCallersAttribute>(Aptca) özniteliğiyle işaretlenen tanımlayıcı adlı derlemelerin bu koruması yoktur. Öznitelik, devralma talebini devre dışı bırakır. Bu, derlemede belirtilen açık türlerin tam güvene sahip olmayan türler tarafından devralınabilir hale gelmesini sağlar.

 APTCA özniteliği tam olarak güvenilen bir derlemede olduğunda ve derlemedeki bir tür, kısmen güvenilen çağıranlara izin verilmeyen bir türden devralırsa, bir güvenlik açığından yararlanma olasılığı vardır. İki tür varsa `T1` ve `T2` aşağıdaki koşullara uyuyorsa, kötü amaçlı çağıranlar, `T1` koruduğu örtük tam güven devralma talebini atlamak için türünü kullanabilir `T2` :

- `T1`, APTCA özniteliğine sahip tam güvenilir bir derlemede tanımlanmış ortak bir tür.

- `T1``T2`kendi derlemesi dışındaki bir türden devralır.

- `T2`derlemesi APTCA özniteliğine sahip değil ve bu nedenle kısmen güvenilen derlemelerdeki türlere devredilemez.

  Kısmen güvenilen bir tür `X` öğesinden devralınabilir `T1` ve bu, içinde belirtilen devralınan üyelere erişim sağlar `T2` . `T2`APTCA özniteliğine sahip olmadığı için, hemen türetilmiş türü ( `T1` ) tam güven için bir devralma talebini karşılamalıdır; `T1` tam güvene sahip ve bu nedenle bu denetimi karşılar. Güvenlik riski, güvenilir olmayan `X` altsınıflama karşı koruyan devralma talebini karşılamadığına katılmaz `T2` . Bu nedenle, APTCA özniteliğine sahip türler özniteliği olmayan türleri genişletmemelidir.

  Diğer bir güvenlik sorunu ve belki de daha yaygın bir şekilde, türetilmiş türün (), `T1` Programcı hatası aracılığıyla, tam güven gerektiren türden korumalı üyeleri kullanıma sunmasıdır () `T2` . Bu durumda, güvenilmeyen çağıranlar yalnızca tam güvenilir türler için kullanılabilir olması gereken bilgilere erişim elde edebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İhlalin tarafından bildirilen tür APTCA özniteliğini gerektirmeyen bir derlemede ise, kaldırın.

 APTCA özniteliği gerekliyse, türe tam güven için bir devralma talebi ekleyin. Bu, güvenilmeyen türlerin devralınmasını önler.

 İhlalin tarafından bildirilen temel türlerin Derlemeleriyle APTCA özniteliğini ekleyerek ihlalin düzeltilmesi mümkündür. Bu, öncelikle derlemelerdeki tüm kodun ve derlemelere bağlı olan tüm kodun yoğun bir güvenlik incelemesi yapmadan bunu kullanmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı güvenle bastırmak için, sizin oluşturduğunuz korumalı üyelerin, güvenilmeyen çağıranların, zararlı bir şekilde kullanılabilecek gizli bilgilere, işlemlere veya kaynaklara erişmesine doğrudan veya dolaylı olarak izin vermediğinden emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açıklarını göstermek için iki derleme ve bir test uygulaması kullanır. İlk derleme APTCA özniteliğine sahip değil ve kısmen güvenilen türler (önceki tartışmada temsil edilen) tarafından devredilemez olmalıdır `T2` .

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Örnek
 Önceki tartışmaya göre temsil edilen ikinci derleme, `T1` tamamen güvenilirdir ve kısmen güvenilen çağıranlara izin verir.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Örnek
 Önceki tartışmaya göre temsil edilen test türü `X` kısmen güvenilen bir derlemede bulunur.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Shady Glen 2/22/2003 12:00:00 Ile buluşuyor!** 
 **Testten: güneşli Meadow** 
 **Güneşli Meadow 2/22/2003 12:00:00 'de buluşuyor!**
## <a name="related-rules"></a>İlgili kurallar
 [CA2116: APTCA metotları yalnızca APTCA metotlarını çağırmalıdır](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Ayrıca Bkz.
 Kısmen güvenilen kod [Devralma taleplerine](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [ait kitaplıklar kullanılarak](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [kısmen güvenilen kod tarafından çağrılabilir olan derlemelerin .NET Framework](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
