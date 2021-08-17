---
title: 'Nasıl yapılır: program aracılığıyla belgeleri kaydetme'
description: belge adını değiştirmeden veya yeni bir adla belgeyi programlı bir şekilde kaydetmek için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7571ca0d16bdd1fc8ebb9f8552d6b55618ffa746dc505bf8bdc81ee2e9452306
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351724"
---
# <a name="how-to-programmatically-save-documents"></a>Nasıl yapılır: program aracılığıyla belgeleri kaydetme

Microsoft Office Word belgelerini kaydetmek için birkaç yol vardır. Belge adını değiştirmeden bir belgeyi kaydedebilir veya bir belgeyi yeni bir adla kaydedebilirsiniz.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Adı değiştirmeden bir belgeyi kaydetme

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Belge düzeyi özelleştirmesiyle ilişkili belgeyi kaydetmek için

1. <xref:Microsoft.Office.Tools.Word.Document.Save%2A>Sınıfının yöntemini çağırın <xref:Microsoft.Office.Tools.Word.Document> . Bu kod örneğini kullanmak için `ThisDocument` projenizdeki sınıftan çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet7":::

### <a name="to-save-the-active-document"></a>Etkin belgeyi kaydetmek için

1. <xref:Microsoft.Office.Interop.Word._Document.Save%2A>Etkin belge için yöntemini çağırın. Bu kod örneğini kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet8":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet8":::

   Kaydetmek istediğiniz belgenin etkin belge olup olmadığından emin değilseniz, bu belgeye adına göre başvurabilirsiniz.

### <a name="to-save-a-document-specified-by-name"></a>Ada göre belirtilen bir belgeyi kaydetmek için

1. Koleksiyon için bir bağımsız değişken olarak belge adını kullanın <xref:Microsoft.Office.Interop.Word.Documents> . Bu kod örneğini kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet9":::

## <a name="save-a-document-with-a-new-name"></a>Belgeyi yeni bir adla kaydetme

Yeni bir `SaveAs` ada sahip bir belgeyi kaydetmek için yöntemini kullanın. <xref:Microsoft.Office.Tools.Word.Document>Bir belge düzeyi Word projesinde veya herhangi bir Word projesindeki yerel bir nesne için konak öğesinin bu yöntemini kullanabilirsiniz <xref:Microsoft.Office.Interop.Word.Document> . Bu yöntem, yeni dosya adını belirtmenizi gerektirir, ancak diğer bağımsız değişkenler isteğe bağlıdır.

> [!NOTE]
> Olay işleyicisinin içinde **SaveAs** iletişim kutusunu gösterip <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> `ThisDocument` *Cancel* parametresini **false** olarak ayarlarsanız uygulama beklenmedik şekilde çıkabilir. *Cancel* parametresini **true** olarak ayarlarsanız, otomatik kaydetme 'nin devre dışı bırakıldığını belirten bir hata iletisi görüntülenir.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Belge düzeyi özelleştirmesiyle ilişkili belgeyi yeni bir adla kaydetmek için

1. `SaveAs` `ThisDocument` Tam nitelenmiş bir yol ve dosya adı kullanarak, projenizdeki sınıfının yöntemini çağırın. Bu adda bir dosya zaten varsa, bu klasörde sessizce üzerine yazılır. Bu kod örneğini kullanmak için `ThisDocument` sınıfından çalıştırın.

    > [!NOTE]
    > Bir `SaveAs` hedef dizin yoksa veya dosya kaydetme ile ilgili başka sorunlar varsa yöntemi bir özel durum oluşturur. `try...catch` `SaveAs` Yöntemi etrafında veya çağırma yöntemi içinde bir blok kullanmak iyi bir uygulamadır.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet10":::

### <a name="to-save-a-native-document-with-a-new-name"></a>Yerel bir belgeyi yeni bir adla kaydetmek için

1. <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> <xref:Microsoft.Office.Interop.Word.Document> Tam nitelikli bir yol ve dosya adı kullanarak kaydetmek istediğiniz yöntemini çağırın. Bu adda bir dosya zaten varsa, bu klasörde sessizce üzerine yazılır.

     Aşağıdaki kod örneği, etkin belgeyi yeni bir adla kaydeder. Bu kod örneğini kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

    > [!NOTE]
    > Bir <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> hedef dizin yoksa veya dosya kaydetme ile ilgili başka sorunlar varsa yöntemi bir özel durum oluşturur. TRY kullanmak iyi bir uygulamadır **...** <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> yöntemi etrafında veya çağırma yöntemi içinde catch bloğu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet10":::

## <a name="compile-the-code"></a>Kodu derle

Bu kod örneği şunları gerektirir:

- Belgeyi ada göre kaydetmek için, *NewDocument.doc* adlı bir belge C sürücüsünde *Test* adlı bir dizinde bulunmalıdır.

- Belgeyi yeni bir adla kaydetmek için, C sürücüsünde *Test* adlı bir dizin bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: program aracılığıyla belgeleri kapatma](../vsto/how-to-programmatically-close-documents.md)
- [Nasıl yapılır: program aracılığıyla varolan belgeleri açma](../vsto/how-to-programmatically-open-existing-documents.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
