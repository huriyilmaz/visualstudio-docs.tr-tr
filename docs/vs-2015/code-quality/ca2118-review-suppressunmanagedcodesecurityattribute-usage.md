---
title: 'CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçirin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb7404d9add159f182ae44b22444dded1aafca20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658650"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir tür veya üyenin <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> özniteliği vardır.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>, COM birlikte çalışma veya platform çağırma kullanılarak yönetilmeyen kodu çalıştıran Üyeler için varsayılan güvenlik sistemi davranışını değiştirir. Genellikle, sistem, yönetilmeyen kod izni için bir [veri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) sağlar. Bu talep, üyenin her çağrılması için çalışma zamanında gerçekleşir ve izin için çağrı yığınında her çağrıyı denetler. Öznitelik mevcut olduğunda, sistem izin için bir [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) sahip olur: çağıran JIT olarak derlendiğinde, hemen çağıranın izinleri denetlenir.

 Bu öznitelik, öncelikle performansı artırmak için kullanılır; ancak, gelen performans artışı önemli güvenlik riskleri ile gelir. Özniteliği yerel yöntemleri çağıran ortak üyelere yerleştirirseniz, Çağrı yığınındaki çağıranlar (hemen çağıran), yönetilmeyen kodu yürütmek için yönetilmeyen kod iznine gerek kalmaz. Genel üyenin eylemlerine ve giriş işlemeye bağlı olarak, güvenilir olmayan çağıranların normal olarak güvenilir kodla sınırlı işlevlere erişmesine izin verebilir.

 @No__t_0, çağıranların geçerli işlemin adres alanına doğrudan erişim kazanmasını engellemek için güvenlik denetimlerine bağımlıdır. Bu öznitelik normal güvenliği atladığı için, kodunuz işlemin belleğini okumak veya yazmak için kullanılacaksa, kodunuz ciddi bir tehdit doğurur. Riskin işlem belleğine kasıtlı olarak erişim sağlayan yöntemlerle sınırlı olmadığına unutmayın; kötü amaçlı kodun herhangi bir şekilde erişim sağlayabildiği herhangi bir senaryoda (örneğin, ortaya çıkmış, hatalı biçimlendirilmiş veya geçersiz giriş sağlayarak) de mevcuttur.

 Varsayılan güvenlik ilkesi, yerel bilgisayardan yürütülmediği veya aşağıdaki gruplardan birinin üyesi olduğu durumlar dışında, bir derlemeye yönetilmeyen kod iznini vermez:

- Bilgisayarımın bölge kodu grubu

- Microsoft tanımlayıcı ad kod grubu

- ECMA tanımlayıcı ad kodu grubu

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu özniteliğin kesinlikle gerekli olduğundan emin olmak için kodunuzu dikkatle gözden geçirin. Yönetilen kod güvenliğini tanımıyorsanız veya bu özniteliği kullanmanın güvenlik etkilerine ilişkin etkileri anladıysanız, kodunuzu koddan kaldırın. Öznitelik gerekliyse, çağıranların kodunuzu kötü amaçlı olarak kullangerektirmediğinden emin olmanız gerekir. Kodunuzun yönetilmeyen kodu yürütme izni yoksa, bu özniteliğin hiçbir etkisi olmaz ve kaldırılması gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı güvenle bastırmak için, kodunuzun, bir bozucu şekilde kullanılabilecek yerel işlemlere veya kaynaklara çağrı sağlamadıklarından emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını ihlal ediyor.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `DoWork` yöntemi platform çağırma yöntemine `FormatHardDisk` genel olarak erişilebilen bir kod yolu sağlar.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `DoDangerousThing` ortak yöntemi ihlalin oluşmasına neden olur. İhlalin çözülmesi için, `DoDangerousThing` ' ı özel hale gelmelidir ve bu, `DoWork` yönteminde gösterildiği gibi bir güvenlik talebi tarafından güvenliği sağlanmış ortak bir yöntem üzerinden olmalıdır.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [güvenlik Iyileştirmeleri](https://msdn.microsoft.com/cf255069-d85d-4de3-914a-e4625215a7c0) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [bağlantı talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
