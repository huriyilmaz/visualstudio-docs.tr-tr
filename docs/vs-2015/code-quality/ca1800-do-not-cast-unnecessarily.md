---
title: 'CA1800: gereksiz yere atama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547803"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Gereksiz tür dönüştürmeler yapmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem bağımsız değişkenlerinin veya yerel değişkenlerinin birinde yinelenen yayınları gerçekleştirir. Bu kurala göre tüm analizler için, sınanan derlemenin hata ayıklama bilgileri kullanılarak oluşturulması gerekir ve ilişkili program veritabanı (. pdb) dosyası kullanılabilir olmalıdır.

## <a name="rule-description"></a>Kural Tanımı
 Özellikle yayınlar sıkıştırılmış yineleme deyiminde gerçekleştirildiğinde yinelenen yayınların performansını azaltır. Açık yinelenen atama işlemleri için, dönüştürme sonucunu yerel bir değişkende depolayın ve yinelenen atama işlemleri yerine yerel değişkeni kullanın.

 C# işleci, `is` gerçek atama gerçekleştirilmeden önce dönüştürmenin başarılı olup olmadığını test etmek için kullanılırsa, bunun yerine işlecin sonucunu test etmeyi düşünün `as` . Bu, işleci tarafından gerçekleştirilen örtük atama işlemi olmadan aynı işlevselliği sağlar `is` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, Yöntem uygulamasını değiştirerek atama işlemlerinin sayısını en aza indirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans sorunu değilse, bu kuraldan bir uyarının veya kuralı tamamen yok saymak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, C# işlecini kullanarak kuralı ihlal eden bir yöntemi gösterir `is` . İkinci bir yöntem `is` işleci bir test ile değiştirerek, işleci bir test ile değiştirerek `as` , iki ' dan birine yineleme başına dönüştürme işlemi sayısını azaltan kuralını karşılar.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir yöntemi gösterir, `start_Click` Bu, kuralı ihlal eden birden çok yinelenen açık oluşturmaya sahiptir ve bir yöntemi, bir `reset_Click` yerel değişkende dönüştürmeyi depolayarak kuralını karşılayan bir yöntemi gösterir.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [as](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [olduğu](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43) gibi
