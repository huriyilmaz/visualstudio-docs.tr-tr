---
title: 'CA1016: Derlemeleri AssemblyVersionAttribute ile Işaretleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f1498624d4f79a60854a624ee5c4053a3343f515
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663164"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Derlemeleri AssemblyVersionAttribute ile işaretleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Derlemenin sürüm numarası yok.

## <a name="rule-description"></a>Kural Tanımı
 Bir derlemenin kimliği aşağıdaki bilgilerden oluşur:

- Bütünleştirilmiş kod adı

- Sürüm numarası

- ayarı

- Ortak anahtar (kesin adlandırılmış derlemeler için).

  @No__t_0, derlemeyi benzersiz bir şekilde tanımlamak ve kesin adlandırılmış derlemelerdeki türlere bağlamak için sürüm numarasını kullanır. Sürüm numarası, sürüm ve yayımcı ilkesi ile birlikte kullanılır. Varsayılan olarak uygulamalar yalnızca oluşturulmuş derleme sürümlerini çalıştırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> özniteliğini kullanarak derlemeye bir sürüm numarası ekleyin. Aşağıdaki örnekte bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Üçüncü taraflar tarafından veya bir üretim ortamında kullanılan derlemeler için bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.Reflection.AssemblyVersionAttribute> özniteliği uygulanmış bir derlemeyi gösterir.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme sürüm oluşturma](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [nasıl yapılır: Yayımcı ilkesi oluşturma](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
