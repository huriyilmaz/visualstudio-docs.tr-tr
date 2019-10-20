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
ms.openlocfilehash: ce85a3a933d9453c63ef118d5dfd9e0b17cbf130
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661454"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntemi, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Sınıf kitaplığındaki bir oluşturucuya veya yönteme parametre olarak bir dize sabiti geçirir ve bu dize yerelleştirilebilir olmalıdır.

 Bu uyarı, bir sabit dize bir parametre veya özelliğe değer olarak geçirildiğinde ve aşağıdaki durumlardan biri veya daha fazlası doğru olduğunda tetiklenir:

- Parametrenin veya özelliğin <xref:System.ComponentModel.LocalizableAttribute> özniteliği true olarak ayarlandı.

- Parametre veya özellik adı "metin", "Ileti" veya "başlık" içerir.

- Console. Write veya Console. WriteLine yöntemine geçirilen dize parametresinin adı "Value" ya da "Format" değeridir.

## <a name="rule-description"></a>Kural Tanımı
 Kaynak koda gömülü olan dize sabit değerleri yerelleşebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, dize sabit değerini <xref:System.Resources.ResourceManager> sınıfının bir örneği aracılığıyla alınan bir dizeyle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kod kitaplığı yerelleştirilemez veya dize son kullanıcıya ya da kod kitaplığı kullanan bir geliştiriciye açık değilse, bu kuraldan bir uyarıyı bastırmak güvenlidir.

 Kullanıcılar, adlandırılmış parametre ya da özelliği yeniden adlandırarak veya bu öğeleri koşullu olarak işaretleyerek yerelleştirilmiş dizeleri geçirmemelidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki bağımsız değişkeni aralık dışında bir özel durum oluşturan bir yöntemi gösterir. İlk bağımsız değişken için, özel durum Oluşturucusu bu kuralı ihlal eden bir sabit dize aktardı. İkinci bağımsız değişken için, Oluşturucu <xref:System.Resources.ResourceManager> ile alınan bir dizeyi doğru şekilde geçirdi.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Masaüstü Uygulamalarındaki Kaynaklar](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
