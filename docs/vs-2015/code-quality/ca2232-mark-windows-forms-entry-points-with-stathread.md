---
title: 'CA2232: Windows Forms giriş noktalarını STAThread ile Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540289"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir bütünleştirilmiş kod <xref:System.Windows.Forms> ad alanına başvurur ve giriş noktası <xref:System.STAThreadAttribute?displayProperty=fullName> özniteliğiyle işaretlenmez.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.STAThreadAttribute>uygulama için COM iş parçacığı modelinin tek iş parçacıklı apartman olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir. Özniteliği yoksa, uygulama Windows Forms için desteklenmeyen çok iş parçacıklı grup modelini kullanır.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Uygulama çerçevesini kullanan projeler, STAThread ile **Main** metodunu işaretlemek zorunda değildir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Derleyici bunu otomatik olarak yapar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, <xref:System.STAThreadAttribute> giriş noktasına özniteliğini ekleyin. <xref:System.MTAThreadAttribute?displayProperty=fullName>Öznitelik varsa kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Özniteliğin gereksiz ve desteklenmeyen .NET Compact Framework için geliştirme yapıyorsanız, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir <xref:System.STAThreadAttribute> .

## <a name="example"></a>Örnek
 Aşağıdaki örnekler, öğesinin doğru kullanımını gösterir <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
