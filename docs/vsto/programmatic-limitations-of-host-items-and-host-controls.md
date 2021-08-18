---
title: Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları
description: Konak öğelerinin davranışı ve konak denetimleri ile çalışma zamanında yerel Office arasındaki temel farklar hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0e7d64c06657695833d84764770506dec91251b8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032270"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları
  Her konak öğesi ve konak denetimi, ek işlevlerle word veya Microsoft Office yerel Microsoft Office Excel gibi davranacak şekilde tasarlanmıştır. Ancak, konak öğelerinin davranışı ile konak denetimleri ile çalışma zamanında yerel Office arasında bazı temel farklar vardır.

 Konak öğeleri ve konak denetimleri hakkında genel bilgi için bkz. [Konak öğeleri ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Program aracılığıyla konak öğeleri oluşturma
 Word veya Excel nesne modelini kullanarak çalışma zamanında program aracılığıyla bir belge, çalışma kitabı veya çalışma sayfası ekleyebilirsiniz, bu öğe bir konak öğesi değildir. Bunun yerine, yeni nesne yerel bir Office nesnesidir. Örneğin, çalışma zamanında yeni bir Word belgesi oluşturmak için yöntemini kullanırsanız, bu bir konak öğesi <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> yerine yerel bir nesne <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> olur. Benzer şekilde, çalışma zamanında yöntemini kullanarak yeni bir çalışma sayfası <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> oluşturursanız, konak öğe yerine yerel bir nesne elde <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Tools.Excel.Worksheet> edersiniz.

 Belge düzeyi projelerde, çalışma zamanında konak öğeleri oluşturamazsınız. Konak öğeleri yalnızca belge düzeyi projelerde tasarım zamanında oluşturulabilir. Daha fazla bilgi için [bkz. Belge konak öğesi,](../vsto/document-host-item.md) [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)ve Çalışma sayfası konak [öğesi.](../vsto/worksheet-host-item.md)

 Eklenti VSTO, çalışma zamanında , veya <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> konak öğeleri <xref:Microsoft.Office.Tools.Excel.Worksheet> oluşturabilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="programmatically-create-host-controls"></a>Program aracılığıyla konak denetimleri oluşturma
 Çalışma zamanında bir veya konak öğesine program <xref:Microsoft.Office.Tools.Word.Document> aracılığıyla konak denetimleri <xref:Microsoft.Office.Tools.Excel.Worksheet> ekleme. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Konak denetimlerini yerel veya 'a <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> ekamazsiniz.

> [!NOTE]
> Aşağıdaki konak denetimleri çalışma sayfalarına veya belgelere program aracılığıyla ek olamaz: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> ve <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Konak öğeleri, konak denetimleri ve yerel konak nesneleri arasındaki tür Office anlama
 Her konak öğesi ve konak denetimi için, Word veya Microsoft Office bir yerel Microsoft Office Excel olur. Konak öğesinin veya konak denetimin InnerObject özelliğini kullanarak temel alınan nesneye erişebilirsiniz. Ancak, yerel bir konak nesnesini karşılık gelen konak Office denetimine attırmanın hiçbir yolu yoktur. Yerel bir konak nesnesini Office konak öğesi veya konak denetimi türüne türetebilirsiniz, <xref:System.InvalidCastException> bir oluşturur.

 Konak öğelerinin ve konak denetimlerinin türleri ile temel alınan yerel konak nesneleri arasındaki farkların kodunuzu etkilediği Office senaryolar vardır.

### <a name="pass-host-controls-to-methods-and-properties"></a>Konak denetimlerini yöntemlere ve özelliklere iletir
 Word'de, bir konak denetimi, parametre olarak yerel bir Word nesnesi gerektiren bir yönteme veya özelliye geçemezsiniz. Temel alınan yerel Word nesnesini geri dönmek için konak denetiminde InnerObject özelliğini kullanabilirsiniz. Örneğin, bir nesnesini <xref:Microsoft.Office.Interop.Word.Bookmark> yöntemine, konak denetimi özelliğini <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> yöntemine geçerek geçebilirsiniz.

 Bu Excel, yöntem veya özellik temel alınan nesne için ana bilgisayar denetimi bekliyorsa, konak denetimi bir yöntem veya özellik için ana bilgisayar denetimi InnerObject Excel gerekir.

 Aşağıdaki örnek bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim oluşturur ve bunu yöntemine <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> iletir. Kod, yöntemi <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> tarafından gerekli olan temel alınan Office <xref:Microsoft.Office.Interop.Excel.Range> için adlandırılmış aralığın özelliğini <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> kullanır.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet28":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet28":::

### <a name="return-types-of-native-office-methods-and-properties"></a>Yerel yöntem ve Office türleri dönüş
 Konak öğelerinin çoğu yöntem ve özellikleri, konak öğesinin Office temel alınan yerel nesnelerini geri döner. Örneğin, bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> konak denetimi özelliği Excel bir konak öğesi yerine bir nesnesi <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Tools.Excel.Worksheet> döndürür. Benzer şekilde, <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> Word'de bir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> konak denetimi özelliği bir konak öğesi yerine bir nesnesi <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> döndürür.

### <a name="access-collections-of-host-controls"></a>Konak denetimleri koleksiyonlarına erişme
 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her tür konak denetimi için ayrı koleksiyonlar sağlamaz. Bunun yerine, belge veya çalışma sayfasındaki tüm yönetilen denetimlerde (hem konak denetimleri hem de Windows Forms denetimleri) yineler ve ardından ilgilendiğiniz konak denetimi türüyle eşan öğelere bakmak için bir konak öğesinin Controls özelliğini kullanın. Aşağıdaki kod örneği Bir Word belgesinde her denetimi inceler ve denetimin bir olup olmadığını <xref:Microsoft.Office.Tools.Word.Bookmark> belirler.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet10":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet10":::

 Konak öğelerinin Controls özelliği hakkında daha fazla bilgi için bkz. Çalışma zamanında [Office belgelere denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Word ve Excel nesne modelleri, belgeler ve çalışma sayfaları üzerinde yerel denetim koleksiyonlarını ortaya çıkaran özellikler içerir. Bu özellikleri kullanarak yönetilen denetimlere erişesiniz. Örneğin, bir veya özelliğinin özelliğini kullanarak bir belgede her konak <xref:Microsoft.Office.Tools.Word.Bookmark> <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> <xref:Microsoft.Office.Interop.Word.Document> denetimine numara <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> vermek mümkün <xref:Microsoft.Office.Tools.Word.Document> değildir. Bu özellikler yalnızca <xref:Microsoft.Office.Interop.Word.Bookmark> belgede yer alan denetimleri içerir; belgede <xref:Microsoft.Office.Tools.Word.Bookmark> konak denetimlerini içermez.

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
