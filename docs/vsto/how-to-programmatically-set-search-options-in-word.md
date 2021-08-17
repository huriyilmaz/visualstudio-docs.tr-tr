---
title: "Nasıl yapabilirsiniz: Word'de arama seçeneklerini program aracılığıyla ayarlama"
description: Visual Studio kullanarak Visual Studio seçenekleri program aracılığıyla ayarlamayı Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c96533e9b6adf6367a8980f8315f84cc1c3ffe24cc8177ba799983e03bd9852e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394231"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Nasıl yapabilirsiniz: Word'de arama seçeneklerini program aracılığıyla ayarlama
  Word belgelerde seçim arama seçeneklerini ayarlamanın iki Microsoft Office vardır:

- Bir nesnenin tek tek özelliklerini <xref:Microsoft.Office.Interop.Word.Find> ayarlayın.

- Bir nesnenin yönteminin <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> bağımsız değişkenlerini <xref:Microsoft.Office.Interop.Word.Find> kullanın.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Bul nesnesinin özelliklerini kullanma
 Aşağıdaki kod, geçerli seçim içinde <xref:Microsoft.Office.Interop.Word.Find> metin aramak için bir nesnenin özelliklerini ayarlar. İleriye arama, sarmalama ve aranan metin gibi arama ölçütlerinin nesnenin özellikleri olduğunu <xref:Microsoft.Office.Interop.Word.Find> fark edersiniz.

 yönteminde parametrelerle aynı özellikleri belirtmeniz gerekenden, C# kodu yazarken nesnenin özelliklerinin her <xref:Microsoft.Office.Interop.Word.Find> birini ayarlama yararlı <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> olmaz. Bu nedenle bu örnek yalnızca Visual Basic içerir.

### <a name="to-set-search-options-using-a-find-object"></a>Bul nesnesini kullanarak arama seçeneklerini ayarlamak için

1. Metnin beni bulma <xref:Microsoft.Office.Interop.Word.Find> seçiminde ileri doğru arama yapmak için nesnesinin **özelliklerini ayarlayın.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Execute yöntemi bağımsız değişkenlerini kullanma
 Aşağıdaki kod, geçerli <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> seçim içindeki <xref:Microsoft.Office.Interop.Word.Find> metinleri aramak için nesnesinin yöntemini kullanır. İleriye arama, sarmalama ve aranma metni gibi arama ölçütlerinin yöntemin parametreleri olarak geçirildiklerini <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> fark etmek.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute metodu bağımsız değişkenlerini kullanarak arama seçeneklerini ayarlamak için

1. Arama ölçütlerini yönteminin parametreleri olarak ileterek metin seçiminde <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> arama yapmak için beni **bulun.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgelerde program aracılığıyla metin arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl kullanılır: Belgelerde bulunan öğelerde program aracılığıyla döngü](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Nasıl kurulur: Arama sonrasındaki seçimleri program aracılığıyla geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
