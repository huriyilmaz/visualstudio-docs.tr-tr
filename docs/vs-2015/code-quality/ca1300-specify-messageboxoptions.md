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
ms.openlocfilehash: af0017a7ee6918a80a93ca90c7cf3de78885d61f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539197"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions belirt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Yöntemi, <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> bağımsız değişken olmayan yöntemin aşırı yüklemesini çağırır <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Sağdan sola okuma düzeni kullanan kültürler için bir ileti kutusunu doğru bir şekilde göstermek için, <xref:System.Windows.Forms.MessageBoxOptions> <xref:System.Windows.Forms.MessageBoxOptions> numaralandırmanın ve üyelerinin <xref:System.Windows.Forms.MessageBoxOptions> metoduna geçirilmesi gerekir <xref:System.Windows.Forms.MessageBox.Show%2A> . <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>Sağdan sola okuma düzeni kullanılıp kullanılmayacağını öğrenmek için içeren denetimin özelliğini inceleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, <xref:System.Windows.Forms.MessageBox.Show%2A> bir bağımsız değişken alan metodun aşırı yüklemesini çağırın <xref:System.Windows.Forms.MessageBoxOptions> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kod kitaplığı, sağdan sola okuma düzeni kullanan bir kültür için yerelleştirilmez, bu kuraldan bir uyarı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kültürün okuma düzeni için uygun olan seçeneklere sahip bir ileti kutusu görüntüleyen bir yöntemi gösterir. Örnek oluşturmak için, gösterilmemiş bir kaynak dosyası gereklidir. Örneği bir kaynak dosyası olmadan derlemek ve sağdan sola özelliği test etmek için örnekteki açıklamaları izleyin.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Resources.ResourceManager?displayProperty=fullName>[Masaüstü uygulamalarındaki kaynaklar](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
