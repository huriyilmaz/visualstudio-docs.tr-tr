---
title: 'CA1301: yinelenen hızlandırıcılardan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 647fef2968971cddb6a14cc19e53eed979b9c151
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661514"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Yinelenen hızlandırıcılardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür <xref:System.Windows.Forms.Control?displayProperty=fullName> genişletir ve bir kaynak dosyasında depolanan aynı erişim anahtarlarına sahip iki veya daha fazla üst düzey denetim içerir.

## <a name="rule-description"></a>Kural Tanımı
 Giriş anahtarı, bir hızlandırıcı olarak da bilinir, ALT anahtarını kullanarak klavye giriş denetimini sağlar. Birden çok denetimin yinelenen erişim tuşları varsa, erişim tuşunun davranışı iyi tanımlı değildir. Kullanıcı, erişim anahtarını kullanarak amaçlanan denetime erişemeyebilir ve hedeflenen bir denetim etkinleştirilmiş olabilir.

 Bu kuralın geçerli uygulanması menü öğelerini yoksayar. Ancak, aynı alt menüdeki menü öğeleri aynı erişim anahtarlarına sahip olmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, tüm denetimler için benzersiz erişim anahtarları tanımlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, aynı erişim anahtarlarına sahip iki denetim içeren en az bir form gösterilmektedir. Anahtarlar, gösterilmemiş bir kaynak dosyasında depolanır; Ancak, değerleri açıklamalı `checkBox.Text` satırlarda görüntülenir. Yinelenen hızlandırıcıların davranışı, `checkBox.Text` satırları, yorumlanma karşılıkları ile değiştirerek incelenebilir. Ancak, bu durumda, örnek kuraldan bir uyarı oluşturmaz.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [masaüstü uygulamalarında kaynakları](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890) <xref:System.Resources.ResourceManager?displayProperty=fullName>
