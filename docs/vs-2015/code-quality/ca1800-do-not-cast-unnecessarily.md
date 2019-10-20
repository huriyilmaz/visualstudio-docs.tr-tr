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
ms.openlocfilehash: 466309cef8905faa9b659e2d3652975d815767fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663098"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Gereksiz atamalar yapmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem bağımsız değişkenlerinin veya yerel değişkenlerinin birinde yinelenen yayınları gerçekleştirir. Bu kurala göre tüm analizler için, sınanan derlemenin hata ayıklama bilgileri kullanılarak oluşturulması gerekir ve ilişkili program veritabanı (. pdb) dosyası kullanılabilir olmalıdır.

## <a name="rule-description"></a>Kural Tanımı
 Özellikle yayınlar sıkıştırılmış yineleme deyiminde gerçekleştirildiğinde yinelenen yayınların performansını azaltır. Açık yinelenen atama işlemleri için, dönüştürme sonucunu yerel bir değişkende depolayın ve yinelenen atama işlemleri yerine yerel değişkeni kullanın.

 Gerçek atama C# gerçekleştirilmeden önce dönüştürmenin başarılı olup olmayacağını sınamak için `is` operatörü kullanılırsa, bunun yerine `as` işlecinin sonucunu test etmeyi göz önünde bulundurun. Bu, `is` işleci tarafından gerçekleştirilen örtük atama işlemi olmadan aynı işlevselliği sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, Yöntem uygulamasını değiştirerek atama işlemlerinin sayısını en aza indirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans sorunu değilse, bu kuraldan bir uyarının veya kuralı tamamen yok saymak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, C# `is` işlecini kullanarak kuralı ihlal eden bir yöntemi gösterir. İkinci bir yöntem `is` işlecini bir test ile değiştirerek `as` işlecinin sonucuna yönelik bir test ile değiştirerek kuralı karşılar. Bu, iki ile yineleme başına dönüştürme işlemi sayısını azaltır.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir yöntemi gösterir, bu, kuralı ihlal eden birden çok yinelenen açık yayını olan `start_Click` ve bir yöntemi, `reset_Click` bir yerel değişkende depolayarak kuralı karşılayan bir yöntem.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [olduğu](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43) gibi
