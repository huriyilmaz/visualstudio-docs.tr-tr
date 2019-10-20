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
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662788"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms giriş noktalarını STAThread ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir derleme <xref:System.Windows.Forms> ad alanına başvurur ve giriş noktası <xref:System.STAThreadAttribute?displayProperty=fullName> özniteliğiyle işaretlenmez.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.STAThreadAttribute>, uygulamanın COM iş parçacığı modelinin tek iş parçacıklı Apartment olduğunu gösterir. Bu öznitelik Windows Forms kullanan herhangi bir uygulamanın girişinde sunulur; atlanırsa, Windows bileşenleri doğru çalışmayabilir. Özniteliği yoksa, uygulama Windows Forms için desteklenmeyen çok iş parçacıklı grup modelini kullanır.

> [!NOTE]
> Uygulama çerçevesini kullanan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projelerin, STAThread ile **Main** metodunu işaretlemek gerekmez. @No__t_0 derleyicisi bunu otomatik olarak yapar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, giriş noktasına <xref:System.STAThreadAttribute> özniteliğini ekleyin. @No__t_0 özniteliği varsa kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 @No__t_0 özniteliğinin gerekli olmadığı ve desteklenmediği .NET Compact Framework için geliştiriyorsanız, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örneklerde <xref:System.STAThreadAttribute> doğru kullanımı gösterilmektedir.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
