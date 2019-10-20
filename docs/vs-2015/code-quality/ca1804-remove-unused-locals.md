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
ms.openlocfilehash: 824a65e765f21748b97292beea64ea6c9bd64a1b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671559"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Kullanılmayan yerel öğeleri kaldırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem yerel bir değişken bildirir, ancak muhtemelen bir atama ifadesinin alıcısı olarak bu değişkeni kullanmaz. Bu kurala göre analiz için, sınanan derleme hata ayıklama bilgileri ile oluşturulmalıdır ve ilişkili program veritabanı (. pdb) dosyası kullanılabilir olmalıdır.

## <a name="rule-description"></a>Kural Tanımı
 Kullanılmayan yerel değişkenler ve gereksiz atamaların derleme boyutunu artırır ve performansı düşürür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yerel değişkeni kaldırın veya kullanın. @No__t_1 ile birlikte C# gelen derleyicinin, `optimize` seçeneği etkinken kullanılmayan yerel değişkenleri kaldırdığına unutmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Değişken derleyicinin yayıldıysa, bu kuraldan bir uyarı gizleyin. Bu kuraldan bir uyarıyı gizlemek veya performans ve kod Bakımı birincil endişeleriniz değilse kuralı devre dışı bırakmak de güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kullanılmamış bazı yerel değişkenleri gösterir.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1809: Aşırı yerel öğelerden kaçın](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Kullanılmayan parametreleri gözden geçir](../code-quality/ca1801-review-unused-parameters.md)
