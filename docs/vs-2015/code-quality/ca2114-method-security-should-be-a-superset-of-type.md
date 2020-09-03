---
title: 'CA2114: metot güvenliği, türün bir üst kümesi olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534712"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Metot güvenliği türün bir üst kümesi olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir tür bildirime dayalı güvenliğe sahiptir ve yöntemlerinden biri aynı güvenlik eylemi için bildirim güvenliğine sahiptir ve güvenlik eylemi [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) veya [Devralma taleplerine](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)sahip değildir ve tür tarafından denetlenen izinler, yöntem tarafından denetlenen izinlerin bir alt kümesi değildir.

## <a name="rule-description"></a>Kural Tanımı
 Bir yöntemde aynı eylem için hem Yöntem düzeyinde hem de tür düzeyinde bildirime sahip bir güvenlik bulunmalıdır. İki denetim birleştirilmez; yalnızca Yöntem düzeyi talep uygulanır. Örneğin, bir tür taleplerine izin varsa `X` ve metotlarından biri izin isterse `Y` , kodun yöntemi yürütme izni olması gerekmez `X` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Her iki eylemin de gerekli olduğundan emin olmak için kodunuzu gözden geçirin. Her iki eylem de gerekliyse, yöntem düzeyi eyleminin tür düzeyinde belirtilen güvenliği içerdiğinden emin olun. Örneğin, türü için izin talebinde bulunursa `X` ve yöntemi de isteğe bağlı izin içeriyorsa `Y` , yöntemi açık bir şekilde talep etmelidir `X` ve olmalıdır `Y` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yöntemin tür tarafından belirtilen güvenliği gerektirmiyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir. Ancak, bu sıradan bir senaryo değildir ve dikkatli bir tasarım incelemesi gereksinimini gösterebilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden tehlikeleri göstermek için ortam izinlerini kullanır. Bu örnekte, uygulama kodu tür için gereken izni reddetmeden önce güvenli türde bir örnek oluşturur. Gerçek hayatta bir tehdit senaryosunda, uygulamanın bir nesne örneği elde etmek için başka bir yol gerekir.

 Aşağıdaki örnekte, kitaplık bir yöntem için yazma izni talep ediyor ve bir yöntem için okuma iznine sahip.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama kodu, tür düzeyi güvenlik gereksinimini karşılamadığında bile yöntemi çağırarak kitaplığın güvenlik açığını gösterir.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **[Tüm izinler] kişisel bilgiler: 6/16/1964 12:00:00** 
 **[Yazma Izni yok (türe göre talep edilmiş)] kişisel bilgiler: 6/16/1964 12:00:00** 
 **[Okuma Izni yok (yöntem tarafından talep edilen)] kişisel bilgilere erişilemedi: istek başarısız oldu.**
## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Devralma talepleri](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [bağlantı talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
