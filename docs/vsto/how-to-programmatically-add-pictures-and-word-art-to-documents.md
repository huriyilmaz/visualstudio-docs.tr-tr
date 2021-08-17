---
title: Belgelere program aracılığıyla resim ve Word Art ekleme
description: Tasarım zamanında veya çalışma zamanında belgelerinize resim ekleme ve nesneleri çizme hakkında bilgi.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046730"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Nasıl kullanılır: Belgelere program aracılığıyla resim ve Word Art ekleme
  Belgelerinize tasarım zamanında veya çalışma zamanında resim ekleyebilir ve nesneleri çizebilirsiniz. WordArt, Word belgelerine dekoratif metin Microsoft Office sağlar. Bu özel metin etkileri, özelleştirebileceğiniz ve belgenize ekleyebileceğiniz nesneler çizmenizi sağlar.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Tasarım zamanında resim ekleme
 Belge düzeyinde özelleştirme geliştiriyorsanız, tasarım zamanında belgeye resim ekleyebilirsiniz.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Tasarım zamanında Word belgesine resim eklemek için

1. İmlecinizi, belgeye resim eklemek istediğiniz yere yerleştirebilirsiniz.

2. Şeridin **Ekle** sekmesine tıklayın.

3. Çizimler **grubunda Resim'e** **tıklayın.**

4. Resim **Ekle iletişim** kutusunda, eklemek istediğiniz resme gidin ve Ekle'ye **tıklayın.**

     Resim, geçerli imleç konumdaki belgenize eklenir.

## <a name="add-a-picture-at-run-time"></a>Çalışma zamanında resim ekleme
 Geçerli imleç konumdaki bir belgeye resim ekleyebilirsiniz.

### <a name="to-add-a-picture-at-the-cursor-location"></a>İmleç konuma resim eklemek için

1. Koleksiyonun <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> yöntemini <xref:Microsoft.Office.Interop.Word.InlineShapes> çağırarak dosyanın adını girin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet108":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet108":::

## <a name="add-wordart-at-design-time"></a>Tasarım zamanında WordArt ekleme
 Belge düzeyinde özelleştirme geliştiriyorsanız wordart'ı tasarım zamanında belgeye ekleyebilirsiniz.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Tasarım zamanında Word belgesine WordArt eklemek için

1. İmlecinizi WordArt'ı belgeye eklemek istediğiniz yere yerleştirebilirsiniz.

2. Şeridin  Ekle sekmesine tıklayın.

3. Metin **grubunda** **WordArt'a tıklayın** ve ardından bir WordArt stili seçin.

4. Belgede görünmesini istediğiniz metni WordArt Metnini Düzenle iletişim kutusuna ekleyin ve **Tamam'a** **tıklayın.**

     Metin, seçilen WordArt stili uygulanmış şekilde belgenize eklenir.

## <a name="add-wordart-at-run-time"></a>Çalışma zamanında WordArt ekleme
 WordArt'ı geçerli imleç konumdaki bir belgeye ekleyebilirsiniz. Yordam, belge düzeyi özelleştirmeler ve VSTO farklıdır.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Belge düzeyinde özelleştirmede imleç konuma WordArt eklemek için

1. Geçerli imleç konumunun sol ve üst konumunu alır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet109":::

2. Belgede <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> <xref:Microsoft.Office.Interop.Word.Shapes> nesnesinin yöntemini çağırma.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet110":::

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>WordArt'ı bir eklentinin imleç VSTO eklemek için

1. Geçerli imleç konumunun sol ve üst konumunu alır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet109":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet109":::

2. Etkin <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> belgenin <xref:Microsoft.Office.Interop.Word.Shapes> nesnesinin yöntemini (veya belirttiğiniz farklı bir belgeyi) çağırma.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet110":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet110":::

## <a name="compile-the-code"></a>Kodu derleme

- C *sürücüsündeSamplePicture.jpg* adlı bir resim mevcut olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Mevcut belgeleri program aracılığıyla açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Nasıl kurulur: Arama sonrasındaki seçimleri program aracılığıyla geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Nasıl kullanılır: Belgeleri program aracılığıyla kaydetme](../vsto/how-to-programmatically-save-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
