---
title: 'CA1300: MessageBoxOptions belirtin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663616"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem, <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> bağımsız değişkeni olmayan <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> yönteminin aşırı yüklemesini çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Sağdan sola okuma düzeni kullanan kültürler için bir ileti kutusunu doğru bir şekilde göstermek için, <xref:System.Windows.Forms.MessageBoxOptions> numaralandırmanın <xref:System.Windows.Forms.MessageBoxOptions> ve <xref:System.Windows.Forms.MessageBoxOptions> üyeleri <xref:System.Windows.Forms.MessageBox.Show%2A> yöntemine geçirilmesi gerekir. Sağdan sola okuma düzeni kullanılıp kullanılmayacağını öğrenmek için içeren denetimin <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> özelliğini inceleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, bir <xref:System.Windows.Forms.MessageBoxOptions> bağımsız değişkeni alan <xref:System.Windows.Forms.MessageBox.Show%2A> yönteminin bir aşırı yüklemesini çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kod kitaplığı, sağdan sola okuma düzeni kullanan bir kültür için yerelleştirilmez, bu kuraldan bir uyarı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kültürün okuma düzeni için uygun olan seçeneklere sahip bir ileti kutusu görüntüleyen bir yöntemi gösterir. Örnek oluşturmak için, gösterilmemiş bir kaynak dosyası gereklidir. Örneği bir kaynak dosyası olmadan derlemek ve sağdan sola özelliği test etmek için örnekteki açıklamaları izleyin.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [masaüstü uygulamalarında kaynakları](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890) <xref:System.Resources.ResourceManager?displayProperty=fullName>
