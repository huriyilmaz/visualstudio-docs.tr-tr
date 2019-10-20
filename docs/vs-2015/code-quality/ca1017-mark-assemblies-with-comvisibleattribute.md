---
title: 'CA1017: derlemeleri ComVisibleAttribute ile Işaretleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 505e5780b8a50113aaf98ea7dbac767d280bebb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662062"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Derlemeleri ComVisibleAttribute ile işaretleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir derlemeye <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> özniteliği uygulanmaz.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 özniteliği, COM istemcilerinin yönetilen koda nasıl erişebileceğini belirler. İyi tasarım derlemelerin açıkça COM görünürlüğünde gösterildiğini belirler. Tüm derleme için COM görünürlüğü ayarlanabilir ve sonra bağımsız türler ve tür üyeleri için geçersiz kılınabilir. Özniteliği yoksa, derlemenin içerikleri COM istemcileri tarafından görülebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, derlemeye özniteliğini ekleyin. Derlemenin COM istemcilerine görünür olmasını istemiyorsanız, özniteliğini uygulayın ve değerini `false` olarak ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Derlemenin görünür olmasını istiyorsanız, özniteliğini uygulayın ve değerini `true` olarak ayarlayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, COM istemcilerine görünür olmasını engellemek için <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği uygulanmış bir derlemeyi gösterir.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Birlikte çalışabilirlik Için yönetilmeyen kod niteleyen .net türleriyle](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
