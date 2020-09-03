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
ms.openlocfilehash: 17f0a540a436316d3a4fb3b71a2a51b1c5a90a6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535076"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir bütünleştirilmiş koda <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> uygulanmış özniteliği yok.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Özniteliği, com istemcilerinin yönetilen koda nasıl erişebileceğini belirler. İyi tasarım derlemelerin açıkça COM görünürlüğünde gösterildiğini belirler. Tüm derleme için COM görünürlüğü ayarlanabilir ve sonra bağımsız türler ve tür üyeleri için geçersiz kılınabilir. Özniteliği yoksa, derlemenin içerikleri COM istemcileri tarafından görülebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, derlemeye özniteliğini ekleyin. Derlemenin COM istemcilerine görünür olmasını istemiyorsanız, özniteliğini uygulayın ve değerini olarak ayarlayın `false` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Derlemenin görünür olmasını istiyorsanız, özniteliğini uygulayın ve değerini olarak ayarlayın `true` .

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.Runtime.InteropServices.ComVisibleAttribute> com istemcilerine görünür olmasını engellemek için özniteliği uygulanmış bir derlemeyi gösterir.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Birlikte çalışabilirlik Için yönetilmeyen kod niteleyen .net türleriyle](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
