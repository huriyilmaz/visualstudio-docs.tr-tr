---
title: Word tablolarını program aracılığıyla belge özellikleriyle doldurmak
description: Bir tabloyu bir Visual Studio belgesinde belge özellikleriyle program aracılığıyla doldurmak için Microsoft Word öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document properties, inserting in Word tables
- documents [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 90a41bd7013ad7c28579712e80b1c7553f3838c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122650"
---
# <a name="how-to-programmatically-populate-word-tables-with-document-properties"></a>Nasıl kullanılır: Word tablolarını belge özellikleriyle program aracılığıyla doldurmak
  Aşağıdaki örnek, Microsoft Office üst kısmında bir Word tablosu oluşturur ve bunu ana bilgisayar belgesinin özellikleriyle doldurmak için kullanılır.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="populate-tables-in-a-document-level-customization"></a>Tabloları belge düzeyinde özelleştirmeyle doldurmak

### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>Tablo oluşturmak ve belge özellikleriyle doldurmak için

1. Aralığı belgenin en üstüne ayarlayın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet90":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet90":::

2. Tablo için bir başlık ekler ve paragraf işaretleri ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet91":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet91":::

3. Tabloyu belgeye aralıkta ekleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet92":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet92":::

4. Tabloyu biçimlendirin ve bir stil uygulama.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet93":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet93":::

5. Belge özelliklerini hücrelere ekleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet94":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet94":::

   Aşağıdaki örnekte yordamın tamamlanmıştır. Bu kodu kullanmak için projenizin `ThisDocument` sınıfından çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet89":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet89":::

## <a name="populate-tables-in-a-vsto-add-in"></a>Tablo ekleme VSTO tablolarını doldurmak

### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>Tablo oluşturmak ve belge özellikleriyle doldurmak için

1. Aralığı belgenin en üstüne ayarlayın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet90":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet90":::

2. Tablo için bir başlık ekler ve paragraf işaretleri ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet91":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet91":::

3. Tabloyu belgeye aralıkta ekleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet92":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet92":::

4. Tabloyu biçimlendirin ve bir stil uygulama.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet93":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet93":::

5. Belge özelliklerini hücrelere ekleyin.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet94":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet94":::

   Aşağıdaki örnekte yordamın tamamlanmıştır. Bu kodu kullanmak için projenizin `ThisAddIn` sınıfından çalıştırın.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet89":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet89":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılanlar: Program aracılığıyla Word tabloları oluşturma](../vsto/how-to-programmatically-create-word-tables.md)
- [Nasıl yapılanlar: Word tablolarında hücrelere program aracılığıyla metin ve biçimlendirme ekleme](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Nasıl kullanılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
