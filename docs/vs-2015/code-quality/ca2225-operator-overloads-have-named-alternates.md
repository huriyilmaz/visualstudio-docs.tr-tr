---
title: 'CA2225: Işleç aşırı yüklemelerinin adlandırılmış alternatifleri var | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 212abc1fa5e2debfaf7ca81d82c8d94e9ddb0879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658884"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı.

## <a name="rule-description"></a>Kural Tanımı
 İşleç aşırı yüklemesi, bir tür için hesaplamaları göstermek üzere simgelerin kullanılmasına izin verir. Örneğin, ek için artı simgesini (+) aşırı yükleyen bir tür, genellikle ' Add ' adlı alternatif bir üyeye sahip olur. Adlandırılmış alternatif üye, işleçle aynı işlevselliğe erişim sağlar ve aşırı yüklenmiş işleçleri desteklemeyen dillerde programlayan geliştiriciler için sağlanır.

 Bu kural, aşağıdaki tabloda listelenen işleçleri inceler.

|C#|Visual Basic|C++|Alternatif ad|
|---------|------------------|-----------|--------------------|
|+ (ikili)|+|+ (ikili)|Ekle|
|+=|+=|+=|Ekle|
|&|'|&|Bitwiseve|
|&=|Ve =|&=|Bitwiseve|
|&#124;|Veya|&#124;|Bitwiseveya|
|&#124;=|Or =|&#124;=|Bitwiseveya|
|--|Yok|--|Azaltma|
|/|/|/|Sayısına|
|/=|/=|/=|Sayısına|
|==|=|==|Eşittir|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|Karşılaştır|
|>=|>=|>=|Karşılaştır|
|++|Yok|++|Ilamadı|
|<>|!=|Eşittir|
|<<|<<|<<|Leftshıft|
|<<=|<<=|<<=|Leftshıft|
|<|<|<|Karşılaştır|
|<=|<=|\<=|Karşılaştır|
|&&|Yok|&&|LogicalAnd|
|&#124;&#124;|Yok|&#124;&#124;|LogicalOr|
|!|Yok|!|LogicalNot|
|%|Mod|%|Mod veya geri kalanı|
|%=|Yok|%=|Mod|
|* (ikili)|*|*|Bilirsiniz|
|*=|Yok|*=|Bilirsiniz|
|~|Başlatılmadı|~|Onestamamlayıcısı|
|>>|>>|>>|Sağa kaydırma|
=|Yok|>>=|Sağa kaydırma|
|-(ikili)|-(ikili)|-(ikili)|Çıkarma|
|-=|Yok|-=|Çıkarma|
|true|IsTrue|Yok|IsTrue (özellik)|
|-(birli)|Yok|-|Negate|
|+ (birli)|Yok|+|artı|
|false|IsFalse|False|IsTrue (özellik)|

 Seçili dilde N/A = = aşırı yüklenemez.

 Kural Ayrıca, `ToSomeType` ve `FromSomeType` adlı yöntemleri denetleyerek bir türdeki (`SomeType`) örtük ve açık atama işleçlerini da denetler.

 ' C#De, bir ikili işleç aşırı yüklendiğinde, varsa karşılık gelen atama işleci de dolaylı olarak aşırı yüklenmiştir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, işleci için alternatif yöntemi uygulayın; Önerilen alternatif adı kullanarak adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Paylaşılan bir kitaplık uygulamadıysanız bu kuraldan bir uyarıyı bastırmayın. Uygulamalar bu kuraldan bir uyarıyı yok sayabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir yapıyı tanımlar. Örneği düzeltmek için, yapıya bir ortak `Add(int x, int y)` yöntemi ekleyin.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
