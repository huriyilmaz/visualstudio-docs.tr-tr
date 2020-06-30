---
title: 'CA1804: kullanılmayan yerelleri kaldır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543890"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Kullanılmayan yerelleri kaldırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem yerel bir değişken bildirir, ancak muhtemelen bir atama ifadesinin alıcısı olarak bu değişkeni kullanmaz. Bu kurala göre analiz için, sınanan derleme hata ayıklama bilgileri ile oluşturulmalıdır ve ilişkili program veritabanı (. pdb) dosyası kullanılabilir olmalıdır.

## <a name="rule-description"></a>Kural Tanımı
 Kullanılmayan yerel değişkenler ve gereksiz atamaların derleme boyutunu artırır ve performansı düşürür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yerel değişkeni kaldırın veya kullanın. İle birlikte bulunan C# derleyicisinin, [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] seçeneği etkinken kullanılmayan yerel değişkenleri kaldırdığına göz önünde çıkarın `optimize` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Değişken derleyicinin yayıldıysa, bu kuraldan bir uyarı gizleyin. Bu kuraldan bir uyarıyı gizlemek veya performans ve kod Bakımı birincil endişeleriniz değilse kuralı devre dışı bırakmak de güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kullanılmamış bazı yerel değişkenleri gösterir.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1809: Aşırı yerellerden kaçının](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Çağırılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklenmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Kullanılmayan parametreleri gözden geçirin](../code-quality/ca1801-review-unused-parameters.md)
