---
title: Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları
description: Çalışma zamanında konak öğelerinin ve konak denetimlerinin ve yerel Office nesnelerinin davranışı arasındaki temel farklılıklar hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: fbc3258f3ea7e0b3cc93a2887dfff5a3bfefb19d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891897"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları
  Her konak öğesi ve konak denetimi, karşılık gelen bir yerel Microsoft Office kelime veya Microsoft Office Excel nesnesi gibi davranacak şekilde tasarlanmıştır. Ancak, çalışma zamanında konak öğelerinin ve konak denetimlerinin ve yerel Office nesnelerinin davranışları arasında bazı temel farklılıklar vardır.

 Konak öğeleri ve konak denetimleri hakkında genel bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Program aracılığıyla konak öğeleri oluşturma
 Çalışma zamanında Word veya Excel nesne modelini kullanarak bir belgeyi, çalışma kitabını veya çalışma sayfasını program aracılığıyla oluşturduğunuzda veya açtığınızda, öğe bir konak öğesi değildir. Bunun yerine, yeni nesne yerel bir Office nesnesidir. Örneğin, <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> çalışma zamanında yeni bir Word belgesi oluşturmak için yöntemini kullanırsanız, <xref:Microsoft.Office.Interop.Word.Document> konak öğesi yerine yerel bir nesne olur <xref:Microsoft.Office.Tools.Word.Document> . Benzer şekilde, yöntemini kullanarak çalışma zamanında yeni bir çalışma sayfası oluşturduğunuzda <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> , <xref:Microsoft.Office.Interop.Excel.Worksheet> konak öğesi yerine yerel bir nesne alırsınız <xref:Microsoft.Office.Tools.Excel.Worksheet> .

 Belge düzeyi projelerinde, çalışma zamanında konak öğeleri oluşturamazsınız. Ana bilgisayar öğeleri, yalnızca belge düzeyi projelerde tasarım zamanında oluşturulabilir. Daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md), [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)ve [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

 VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma zamanında öğeleri oluşturabilir, veya barındırabilirsiniz. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Program aracılığıyla konak denetimleri oluşturma
 <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Worksheet> Çalışma zamanında bir veya ana bilgisayar öğesine programlı olarak konak denetimleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Yerel veya ana bilgisayar denetimleri ekleyemezsiniz <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> .

> [!NOTE]
> Aşağıdaki konak denetimleri, çalışma sayfalarına veya belgelere program aracılığıyla eklenemez: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> , ve <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Konak öğeleri, konak denetimleri ve yerel Office nesneleri arasındaki tür farklarını anlayın
 Her konak öğesi ve konak denetimi için, temel alınan bir Microsoft Office kelime veya Microsoft Office Excel nesnesi vardır. Konak öğesinin veya konak denetiminin InnerObject özelliğini kullanarak temel nesneye erişebilirsiniz. Ancak, yerel bir Office nesnesini ilgili konak öğesine veya konak denetimine dönüştürmenin bir yolu yoktur. Yerel bir Office nesnesini konak öğesi veya konak denetimi türüne dönüştürmeye çalışırsanız, bir oluşturulur <xref:System.InvalidCastException> .

 Konak öğeleri ve konak denetimleri ve temel alınan yerel Office nesneleri arasındaki farklılıklarınızın kodunuzu etkilediği çeşitli senaryolar vardır.

### <a name="pass-host-controls-to-methods-and-properties"></a>Yöntemlere ve özelliklere konak denetimleri geçirin
 Word 'de, bir konak denetimini bir parametre olarak yerel bir Word nesnesi gerektiren bir yönteme veya özelliğe geçiremezsiniz. Temel alınan yerel Word nesnesini döndürmek için konak denetiminin InnerObject özelliğini kullanmanız gerekir. Örneğin, <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> ana bilgisayar denetiminin özelliğini yöntemine geçirerek bir nesneyi bir yönteme geçirebilirsiniz <xref:Microsoft.Office.Tools.Word.Bookmark> .

 Excel 'de, yöntem veya özellik temeldeki Excel nesnesini beklediği zaman, konak denetimini bir yönteme veya özelliğe geçirmek için konak denetiminin InnerObject özelliğini kullanmanız gerekir.

 Aşağıdaki örnek bir denetim oluşturur <xref:Microsoft.Office.Tools.Excel.NamedRange> ve <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> yöntemine geçirir. Kod, <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> yöntemi için gereken temel Office 'i döndürmek için adlandırılmış aralığın özelliğini kullanır <xref:Microsoft.Office.Interop.Excel.Range> <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Yerel Office yöntemlerinin ve özelliklerinin dönüş türleri
 Konak öğelerinin çoğu yöntemi ve özellikleri, ana bilgisayar öğesinin temel aldığı temel yerel Office nesnesini döndürür. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel 'deki bir konak denetiminin özelliği, <xref:Microsoft.Office.Interop.Excel.Worksheet> bir konak öğesi yerine bir nesne döndürür <xref:Microsoft.Office.Tools.Excel.Worksheet> . Benzer şekilde, <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Word içindeki bir konak denetiminin özelliği, <xref:Microsoft.Office.Interop.Word.Document> bir konak öğesi yerine bir nesne döndürür <xref:Microsoft.Office.Tools.Word.Document> .

### <a name="access-collections-of-host-controls"></a>Konak denetimleri koleksiyonlarına erişin
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Her konak denetimi türü için ayrı koleksiyonlar sağlamaz. Bunun yerine, belge veya çalışma sayfasındaki tüm yönetilen denetimleri (konak denetimleri ve Windows Forms denetimleri) yinelemek için bir konak öğesinin Controls özelliğini kullanın ve ardından ilgilendiğiniz konak denetiminin türüyle eşleşen öğeleri arayın. Aşağıdaki kod örneği, bir Word belgesindeki her denetimi inceler ve denetimin bir olup olmadığını belirler <xref:Microsoft.Office.Tools.Word.Bookmark> .

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Konak öğelerinin denetimler özelliği hakkında daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Word ve Excel nesne modelleri, belgeler ve çalışma sayfalarında yerel denetimlerin koleksiyonlarını ortaya çıkaran özellikleri içerir. Bu özellikleri kullanarak yönetilen denetimlere erişemezsiniz. Örneğin, bir belgedeki her bir <xref:Microsoft.Office.Tools.Word.Bookmark> konak denetimini bir <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> veya özelliğinin özelliğini kullanarak numaralandırmak mümkün değildir <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> <xref:Microsoft.Office.Tools.Word.Document> . Bu özellikler yalnızca <xref:Microsoft.Office.Interop.Word.Bookmark> belgedeki denetimleri içerir; <xref:Microsoft.Office.Tools.Word.Bookmark> belgedeki konak denetimlerini içermez.

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Belge konak öğesi](../vsto/document-host-item.md)
