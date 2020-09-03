---
title: 'CA1014: Derlemeleri CLSCompliantAttribute ile Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c6dc131a2bb5f0c54943213fbb42561a0c72d95c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545476"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Derlemeleri CLSCompliantAttribute ile işaretle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir bütünleştirilmiş koda <xref:System.CLSCompliantAttribute?displayProperty=fullName> uygulanmış özniteliği yok.

## <a name="rule-description"></a>Kural Tanımı
 Ortak Dil Tanımlaması (CLS) ad kısıtlamalarını, veri türlerini ve karşıt programlama dillerini kullanırsa derlemelerin uyması zorunlu olan kuralları tanımlar. İyi tasarım, tüm derlemelerin ile birlikte CLS uyumluluğunu açıkça belirtmeyeceğini belirler <xref:System.CLSCompliantAttribute> . Öznitelik bir derlemede yoksa, derleme uyumlu değildir.

 CLS uyumlu bir derlemenin uyumlu olmayan türler veya tür üyeleri içermesi mümkündür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, derlemeye özniteliğini ekleyin. Tüm derlemeyi uyumsuz olarak işaretlemek yerine, hangi tür veya tür üyelerinin uyumlu olduğunu belirlemelisiniz ve bu öğeleri bu öğe olarak işaretleyebilirsiniz. Mümkünse, uyumsuz Üyeler için CLS uyumlu bir alternatif sağlamanız gerekir; böylece, en olası hedef kitle, derlemenizin tüm işlevlerine erişebilir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Derlemenin uyumlu olmasını istemiyorsanız, özniteliğini uygulayın ve değerini olarak ayarlayın `false` .

## <a name="example"></a>Örnek
 Aşağıdaki örnek, tarafından <xref:System.CLSCompliantAttribute?displayProperty=fullName> CLS uyumlu olduğunu bildiren özniteliği uygulayan bir derlemeyi gösterir.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>[Dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
