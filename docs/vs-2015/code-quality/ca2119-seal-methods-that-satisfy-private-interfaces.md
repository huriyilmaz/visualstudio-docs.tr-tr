---
title: 'CA2119: özel arabirimleri karşılayan yöntemleri mühürleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af41fc5576cbcd56589680d99c0cd5c0dfd6e6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664762"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Özel arabirimleri karşılayan yöntemleri mühürleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Devralınabilir bir ortak tür, `internal` (Visual Basic) arabirimindeki bir (`Friend`) geçersiz kılınabilir Yöntem uygulamasını sağlar.

## <a name="rule-description"></a>Kural Tanımı
 Arabirim yöntemleri, uygulama türü tarafından değiştirilemeyen genel erişilebilirliği vardır. İç arabirim, arabirimini tanımlayan derlemenin dışında uygulanması amaçlanan bir sözleşme oluşturur. @No__t_0 (Visual Basic `Overridable`) kullanarak bir iç arabirimin yöntemini uygulayan ortak bir tür, metodun, derlemenin dışında olan türetilmiş bir tür tarafından geçersiz kılınmasına izin verir. Tanımlama derlemesinde ikinci bir tür yöntemi çağırırsa ve yalnızca dahili bir sözleşme bekliyorsa, bunun yerine dış derlemede geçersiz kılınan yöntem yürütüldüğünde davranışın güvenliği tehlikeye girebilir. Bu, bir güvenlik açığı oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlal edildiğini onarmak için, aşağıdakilerden birini kullanarak metodun derleme dışında geçersiz kılınmasını engelleyin:

- Bildirim türünü `sealed` (`NotInheritable` Visual Basic) yapın.

- Bildirim türünün erişilebilirliğini `internal` (Visual Basic `Friend`) olarak değiştirin.

- Tüm ortak oluşturucuları bildirim türünden kaldırın.

- Yöntemi `virtual` değiştiricisini kullanmadan uygulayın.

- Yöntemi açıkça uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dikkatli bir gözden geçirdikten sonra, yöntem derleme dışında geçersiz kılınırsa, açıktan yararlanabilen güvenlik sorunları yoksa, bu kuraldan bir uyarıyı gizlemek güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden `BaseImplementation` olan bir türü gösterir.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, önceki örneğin sanal yöntem uygulamasından yararlanır.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Arabirim](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [arabirimleri](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
