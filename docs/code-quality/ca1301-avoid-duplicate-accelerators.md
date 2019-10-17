---
title: 'CA1301: Yinelenen hızlandırıcılardan kaçının'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1970eefee70fa14179c77566f23f213f09026646
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444386"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Yinelenen hızlandırıcılardan kaçının

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategori|Microsoft. Globalization|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
Bir tür <xref:System.Windows.Forms.Control?displayProperty=fullName> ' i genişletir ve bir kaynak dosyasında depolanan aynı erişim anahtarlarına sahip iki veya daha fazla üst düzey denetim içerir.

## <a name="rule-description"></a>Kural açıklaması

Hızlandırıcı olarak da bilinen bir erişim anahtarı, **alt** tuşunu kullanarak bir denetime klavye erişimi sağlar. Birden çok denetim aynı erişim anahtarına sahip olduğunda, erişim anahtarının davranışı iyi tanımlanmamıştır. Kullanıcı, erişim anahtarını kullanarak amaçlanan denetime erişemeyebilir ve hedeflenen bir denetim etkinleştirilebilir. Bu, bir denetim etkin olabilir.

Bu kuralın geçerli uygulanması menü öğelerini yoksayar. Ancak, aynı alt menüdeki menü öğeleri aynı erişim anahtarlarına sahip olmamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, tüm denetimler için benzersiz erişim anahtarları tanımlayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
Aşağıdaki örnekte, aynı erişim anahtarlarına sahip iki denetim içeren en az bir form gösterilmektedir. Anahtarlar, gösterilmemiş bir kaynak dosyasında depolanır. Ancak, değerleri, açıklama `checkBox.Text` satırlarında görüntülenir. Yinelenen hızlandırıcıların davranışı, `checkBox.Text` satırları, yorumlanma karşılıkları ile değiştirerek incelenebilir. Ancak, bu durumda, örnek kuraldan bir uyarı oluşturmaz.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Masaüstü Uygulamalarındaki Kaynaklar](/dotnet/framework/resources/index)
