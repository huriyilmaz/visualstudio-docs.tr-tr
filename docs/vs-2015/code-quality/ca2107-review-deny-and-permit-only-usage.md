---
title: 'CA2107: Gözden geçirme ve yalnızca kullanım izni verme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547777"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Gözden geçirmeyi reddedin ve yalnızca kullanımına izin verin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir yöntem, PermitOnly veya güvenlik reddetme eylemini belirten bir güvenlik denetimi içerir.

## <a name="rule-description"></a>Kural Tanımı
 [Permıtonly yönteminin](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) ve <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> güvenlik eylemlerinin kullanılması yalnızca gelişmiş bir güvenlik bilgisine sahip olanlar tarafından kullanılmalıdır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu güvenlik eylemlerini kullanan kod güvenlik incelemesi altından geçmelidir.

 Reddet, bir güvenlik talebine yanıt olarak oluşan yığın ilerimizin varsayılan davranışını değiştirir. Çağrı yığınındaki çağıranların gerçek izinlerinden bağımsız olarak reddetme yöntemi süresince verilmemelidir olması gereken izinleri belirtmenize olanak tanır. Yığın ilerleyerek reddetme tarafından güvenliği sağlanmış bir yöntemi algılarsa ve istenen izin reddedilen izinlere dahil ediliyorsa, yığın ilerleme durumunda başarısız olur. PermitOnly Ayrıca yığın yürüme 'nin varsayılan davranışını değiştirir. Kod, çağıranların izinlerinden bağımsız olarak yalnızca izin verilen izinleri belirtmesini sağlar. Yığın, PermitOnly tarafından güvenliği sağlanan bir yöntemi algılarsa ve istenen izin PermitOnly tarafından belirtilen izinlere dahil edilmezse, yığın ilerleme durumunda başarısız olur.

 Bu eylemlere dayanan kod, sınırlı kullanışlılığı ve hafif davranışları nedeniyle güvenlik açıklarına karşı dikkatle değerlendirilmelidir. Aşağıdaki topluluklara bir göz atın:

- [Bağlantı talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) deny veya PermitOnly 'dan etkilenmez.

- Reddetme veya PermitOnly, yığının ilerlemesini neden olan talebe göre aynı yığın çerçevesinde gerçekleşirse, güvenlik eylemlerinin hiçbir etkisi olmaz.

- Yol tabanlı izinleri oluşturmak için kullanılan değerler, genellikle birden çok şekilde belirtilebilir. Bir yolun tek bir biçimine erişiminin reddedilmesi tüm formlara erişimi reddedemez. Örneğin, bir dosya paylaşımı \\ \Server\share bir ağ sürücüsüne eşlenmişse, paylaşımdaki bir dosyaya erişimi reddetmek için \\ \Server\share\file, x:\Dosya ve dosyaya erişen tüm diğer yolları reddetmeniz gerekir.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>Reddet veya PermitOnly 'a ulaşılmadan önce bir yığını sonlandırabilir.

- Bir reddetme işlemi herhangi bir etkiye sahipse, bir çağıranın reddetme tarafından engellenen bir izni olduğunda, çağıran doğrudan korumalı kaynağa erişimi Reddet seçeneğini atlayarak doğrudan erişebilir. Benzer şekilde, çağıranın reddetme izni yoksa, yığın yürüme olmadan başarısız olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu güvenlik eylemlerinin herhangi bir kullanımı ihlale neden olur. İhlalin giderilmesi için bu güvenlik eylemlerini kullanmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı yalnızca bir güvenlik incelemesini tamamladıktan sonra gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, reddetme kısıtlamaları gösterilmektedir.

 Aşağıdaki kitaplık, bunları koruyan güvenlik talepleri hariç olmak üzere iki yöntemi olan bir sınıfı içerir.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kitaplıktan güvenli yöntemlerle reddetme etkilerini gösterir.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Talep: arayanın reddi, onaylanan izin Ile isteğe bağlı olarak hiçbir etkiye sahip değildir.** 
 **LinkDemand: arayanın reddetme işlemi, onaylanan Izinle LinkDemand üzerinde hiçbir etkiye sahip değildir.** 
 **LinkDemand: arayanın reddi, LinkDemand ile korunan kodla hiçbir etkiye sahip değildir.** 
 **LinkDemand: Bu reddetme, LinkDemand ile korunan kodla hiçbir etkiye sahip değildir.**
## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [PermitOnly yöntemini kullanarak](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) [güvenlik denetimlerini geçersiz kılan](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
