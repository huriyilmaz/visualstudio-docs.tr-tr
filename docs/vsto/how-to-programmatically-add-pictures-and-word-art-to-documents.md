---
title: Belgelere program aracılığıyla resim ve Word art ekleme
description: Tasarım zamanında veya çalışma zamanında belgelerinize resimler ve çizim nesneleri ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3f0e284b8307aa60f15f55d2ac5fc5cb5aed5e9c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634006"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Nasıl yapılır: belgelere program aracılığıyla resim ve Word art ekleme
  Belgelerinize, tasarım zamanında veya çalışma zamanında resim ve çizim nesneleri ekleyebilirsiniz. WordArt, Microsoft Office Word belgelerine dekoratif metin eklemenize olanak sağlar. Bu özel metin efektleri, özelleştirebileceğiniz ve belgenize ekleyebileceğiniz çizim nesneleridir.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Tasarım zamanında resim ekleme
 Belge düzeyi özelleştirmesi geliştiriyorsanız, belgeye tasarım zamanında bir resim ekleyebilirsiniz.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Tasarım zamanında Word belgesine resim eklemek için

1. İmlecinizi belgeye eklemek istediğiniz yere yerleştirin.

2. Şeridin **Ekle** sekmesine tıklayın.

3. **Çizimler** grubunda **resim**' e tıklayın.

4. **Resim ekle** iletişim kutusunda, eklemek istediğiniz resme gidin ve **Ekle**' ye tıklayın.

     Resim, geçerli imleç konumundaki belgenize eklenir.

## <a name="add-a-picture-at-run-time"></a>Çalışma zamanında resim ekleme
 Bir belgeye geçerli imleç konumundaki bir resim ekleyebilirsiniz.

### <a name="to-add-a-picture-at-the-cursor-location"></a>İmleç konumuna resim eklemek için

1. <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A>Koleksiyonun yöntemini çağırın <xref:Microsoft.Office.Interop.Word.InlineShapes> ve dosyanın adını geçirin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Tasarım zamanında WordArt Ekle
 Belge düzeyi özelleştirmesi geliştiriyorsanız, belgeye tasarım zamanında WordArt ekleyebilirsiniz.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Tasarım zamanında Word belgesine WordArt eklemek için

1. Belgenizde WordArt eklemek istediğiniz yere imlecinizi yerleştirin.

2. Şeridin **Ekle** sekmesine tıklayın.

3. **Metin** grubunda **WordArt**' ı tıklatın ve ardından bir WordArt stili seçin.

4. Belgede görünmesini istediğiniz metni, **WordArt Metnini Düzenle** iletişim kutusuna ekleyin ve **Tamam**' a tıklayın.

     Metin, Seçili WordArt stili uygulanmış şekilde belgenize eklenir.

## <a name="add-wordart-at-run-time"></a>Çalışma zamanında WordArt Ekle
 Geçerli imleç konumundaki bir belgeye WordArt ekleyebilirsiniz. yordam, belge düzeyi özelleştirmeleri ve VSTO eklentileri için farklıdır.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Belge düzeyi özelleştirmesindeki imleç konumuna WordArt eklemek için

1. Geçerli imleç konumunun sol ve üst konumunu alır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> <xref:Microsoft.Office.Interop.Word.Shapes> Belgedeki nesnesinin yöntemini çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>VSTO eklentisinin imleç konumuna WordArt eklemek için

1. Geçerli imleç konumunun sol ve üst konumunu alır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> <xref:Microsoft.Office.Interop.Word.Shapes> Etkin belgenin nesnesinin (veya belirttiğiniz farklı bir belgenin) yöntemini çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Kodu derle

- C sürücüsünde *SamplePicture.jpg* adlı bir resim bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla varolan belgeleri açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl yapılır: aramadan sonra program aracılığıyla seçimleri geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Nasıl yapılır: program aracılığıyla belgeleri kaydetme](../vsto/how-to-programmatically-save-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
