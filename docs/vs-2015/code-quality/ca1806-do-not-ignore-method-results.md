---
title: 'CA1806: metot sonuçlarını yoksayma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f68ab71d9ce4fab1b0612f15d866c58e302a317e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671501"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Yöntem sonuçlarını yoksaymayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bu uyarının birkaç olası nedeni vardır:

- Yeni bir nesne oluşturulur ancak hiç kullanılmaz.

- Yeni bir dize oluşturan ve döndüren bir yöntem çağrılır ve yeni dize hiçbir şekilde kullanılmaz.

- Hiçbir zaman kullanılmayan bir HRESULT veya hata kodu döndüren bir COM veya P/Invoke yöntemi. Kural Tanımı

  Gereksiz nesne oluşturma ve kullanılmayan nesnenin ilişkili atık toplaması, performansı düşürür.

  Dizeler sabittir ve String. ToUpper gibi yöntemler, çağıran yöntemde dize örneğini değiştirmek yerine bir dizenin yeni bir örneğini döndürür.

  HRESULT veya hata kodu yok sayılıyor, hata koşullarında veya düşük kaynak koşullarında beklenmeyen davranışlara neden olabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 A yöntemi, hiç kullanılmamış bir B nesnesinin yeni bir örneğini oluşturursa, örneği bir bağımsız değişken olarak başka bir metoda geçirin veya örneği bir değişkene atayın. Nesne oluşturma gereksiz ise, bunu kaldırın.-veya-

 If yöntemi B yöntemini çağırırsa, ancak B yönteminin döndürdüğü yeni dize örneğini kullanmaz. Örneği bir bağımsız değişken olarak başka bir yönteme geçirin, örneği bir değişkene atayın. Ya da gerekli değilse çağrıyı kaldırın.

 veya

 If yöntemi B yöntemini çağırırsa, ancak yöntemin döndürdüğü HRESULT veya hata kodunu kullanmaz. Sonucu bir koşullu ifadede kullanın, sonucu bir değişkene atayın ya da başka bir yönteme bağımsız değişken olarak geçirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Nesne oluşturma eylemi bir amaca hizmet etmediği takdirde bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek String. Trim çağırma sonucunu yok sayan bir sınıfı gösterir.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Örnek
 Aşağıdaki örnek, dizesinin sonucunu atayarak önceki ihlalin düzeltir. çağrıldığı değişkene geri kırpın.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Örnek
 Aşağıdaki örnek, oluşturduğu bir nesneyi kullanmayan bir yöntemi gösterir.

> [!NOTE]
> Bu ihlalin Visual Basic çoğaltılamaz.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir nesnenin gereksiz şekilde oluşturulmasını kaldırarak önceki ihlalin düzeltir.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, GetShortPathName yerel yönteminin döndürdüğü hata kodunu yok sayan bir yöntemi gösterir.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, hata kodunu denetleyerek ve çağrı başarısız olduğunda bir özel durum oluşturarak önceki ihlalin düzeltir.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]