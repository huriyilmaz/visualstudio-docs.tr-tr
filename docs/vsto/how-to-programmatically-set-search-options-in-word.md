---
title: "Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama"
description: Microsoft Word seçimlere yönelik arama seçeneklerini programlı bir şekilde ayarlamak için Visual Studio nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 8916affc89cdf179cf3981e5900d155731ded6c8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726710"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Nasıl yapılır: Word 'de program aracılığıyla arama seçeneklerini ayarlama
  Microsoft Office Word belgelerindeki seçimler için arama seçeneklerini kurmanın iki yolu vardır:

- Bir nesnenin tek tek özelliklerini ayarlayın <xref:Microsoft.Office.Interop.Word.Find> .

- <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>Bir nesnenin yönteminin bağımsız değişkenlerini kullanın <xref:Microsoft.Office.Interop.Word.Find> .

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Find nesnesinin özelliklerini kullanma
 Aşağıdaki kod, <xref:Microsoft.Office.Interop.Word.Find> geçerli seçim içinde metin aramak için bir nesnenin özelliklerini ayarlar. Aranan, kaydırma ve metin araması gibi arama ölçütlerinin nesnenin özellikleri olduğunu unutmayın <xref:Microsoft.Office.Interop.Word.Find> .

 Yöntemin özelliklerinin her birinin ayarlanması, <xref:Microsoft.Office.Interop.Word.Find> Yöntem içindeki parametrelerle aynı özellikleri belirtmeniz gerektiği Için C# kodu yazdığınızda yararlı değildir <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> . bu nedenle bu örnek yalnızca Visual Basic kodu içerir.

### <a name="to-set-search-options-using-a-find-object"></a>Find nesnesi kullanarak arama seçeneklerini ayarlamak için

1. Bir nesnenin özelliklerini, <xref:Microsoft.Office.Interop.Word.Find> **beni bul** metin için bir seçimi ileri doğru arayacak şekilde ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Execute yöntemi bağımsız değişkenlerini kullanma
 Aşağıdaki kod, <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> <xref:Microsoft.Office.Interop.Word.Find> geçerli seçim içinde metin aramak için bir nesnesinin yöntemini kullanır. Arama, kaydırma ve metin arama gibi arama ölçütlerinin yöntemin parametreleri olarak geçtiğini unutmayın <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute metodu bağımsız değişkenlerini kullanarak arama seçeneklerini ayarlamak için

1. Arama ölçütünü, <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> **beni bul** metin için bir seçimi ileri doğru aramak üzere metodun parametreleri olarak geçirin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Nasıl yapılır: belgelerdeki bulunan öğeler aracılığıyla program aracılığıyla döngü yapma](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
