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
ms.openlocfilehash: 0afa6950a6ad876cdcfdcc1a56dd143422b9d44f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544358"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Özel arabirimleri karşılayan metotları mühürleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Devralınabilir bir ortak tür, bir `internal` (Visual Basic) arabiriminde geçersiz kılınabilir bir yöntem uygulamasını sağlar `Friend` .

## <a name="rule-description"></a>Kural Tanımı
 Arabirim yöntemleri, uygulama türü tarafından değiştirilemeyen genel erişilebilirliği vardır. İç arabirim, arabirimini tanımlayan derlemenin dışında uygulanması amaçlanan bir sözleşme oluşturur. (Visual Basic) değiştiricisini kullanarak bir iç arabirimin yöntemini uygulayan ortak tür, `virtual` `Overridable` metodun, derlemenin dışında olan türetilmiş bir tür tarafından geçersiz kılınmasına izin verir. Tanımlama derlemesinde ikinci bir tür yöntemi çağırırsa ve yalnızca dahili bir sözleşme bekliyorsa, bunun yerine dış derlemede geçersiz kılınan yöntem yürütüldüğünde davranışın güvenliği tehlikeye girebilir. Bu, bir güvenlik açığı oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlal edildiğini onarmak için, aşağıdakilerden birini kullanarak metodun derleme dışında geçersiz kılınmasını engelleyin:

- Bildirim türünü `sealed` ( `NotInheritable` Visual Basic) yapın.

- Bildirim türünün erişilebilirliğini `internal` ( `Friend` Visual Basic) olarak değiştirin.

- Tüm ortak oluşturucuları bildirim türünden kaldırın.

- Değiştiricisini kullanmadan yöntemi uygulayın `virtual` .

- Yöntemi açıkça uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Dikkatli bir gözden geçirdikten sonra, yöntem derleme dışında geçersiz kılınırsa, açıktan yararlanabilen güvenlik sorunları yoksa, bu kuraldan bir uyarıyı gizlemek güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `BaseImplementation` Bu kuralı ihlal eden bir türü gösterir.

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
