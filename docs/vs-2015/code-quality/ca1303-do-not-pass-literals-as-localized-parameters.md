---
title: 'CA1303: sabit değerleri yerelleştirilmiş parametreler olarak geçirmeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3ad1f56215d002c03d346b38ce6155e8df7412b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539119"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem, sınıf kitaplığındaki bir oluşturucuya veya yönteme parametre olarak bir dize sabiti geçirir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ve bu dize yerelleştirilebilir olmalıdır.

 Bu uyarı, bir sabit dize bir parametre veya özelliğe değer olarak geçirildiğinde ve aşağıdaki durumlardan biri veya daha fazlası doğru olduğunda tetiklenir:

- <xref:System.ComponentModel.LocalizableAttribute>Parametrenin veya özelliğin özniteliği true olarak ayarlandı.

- Parametre veya özellik adı "metin", "Ileti" veya "başlık" içerir.

- Console. Write veya Console. WriteLine yöntemine geçirilen dize parametresinin adı "Value" ya da "Format" değeridir.

## <a name="rule-description"></a>Kural Tanımı
 Kaynak koda gömülü olan dize sabit değerleri yerelleşebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, dize sabit değerini, sınıfının bir örneği aracılığıyla alınan bir dizeyle değiştirin <xref:System.Resources.ResourceManager> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kod kitaplığı yerelleştirilemez veya dize son kullanıcıya ya da kod kitaplığı kullanan bir geliştiriciye açık değilse, bu kuraldan bir uyarıyı bastırmak güvenlidir.

 Kullanıcılar, adlandırılmış parametre ya da özelliği yeniden adlandırarak veya bu öğeleri koşullu olarak işaretleyerek yerelleştirilmiş dizeleri geçirmemelidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki bağımsız değişkeni aralık dışında bir özel durum oluşturan bir yöntemi gösterir. İlk bağımsız değişken için, özel durum Oluşturucusu bu kuralı ihlal eden bir sabit dize aktardı. İkinci bağımsız değişken için, Oluşturucu bir ile alınan bir dizeyi doğru şekilde geçirdi <xref:System.Resources.ResourceManager> .

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Masaüstü uygulamalarındaki kaynaklar](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
