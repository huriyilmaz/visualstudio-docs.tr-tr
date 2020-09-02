---
title: 'Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c53d820170c359e568b0a7b0ab5711a632d9eba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538326"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme
  <xref:Microsoft.Office.Tools.Excel.ListObject>Tasarım zamanında bir Microsoft Office Excel çalışma sayfasına ve belge düzeyi projelerinde çalışma zamanında denetim ekleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Ayrıca, <xref:Microsoft.Office.Tools.Excel.ListObject> VSTO eklenti projelerinde çalışma zamanında denetim ekleyebilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında ListObject denetimleri ekleme](#designtime)

- [Belge düzeyindeki bir projede çalışma zamanında ListObject denetimleri ekleme](#runtimedoclevel)

- [VSTO eklenti projesindeki ListObject denetimlerini çalışma zamanında ekleme](#runtimeaddin)

  Denetimler hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.ListObject> bkz. [ListObject denetimi](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında ListObject denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>Tasarım zamanında belge düzeyindeki bir projedeki çalışma sayfasına denetim eklemenin birkaç yolu vardır: Excel içinden, Visual Studio **araç kutusundan**ve **veri kaynakları** penceresinden.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Şeriti Excel 'de kullanmak için

1. **Ekle** sekmesinde, **Tablolar** grubunda, **tablo**' ya tıklayın.

2. Listeye eklemek istediğiniz hücreyi veya hücreleri seçin ve **Tamam**' a tıklayın.

#### <a name="to-use-the-toolbox"></a>Araç kutusunu kullanmak için

1. **Araç kutusunun** **Excel denetimleri** sekmesinden, <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasına sürükleyin.

     **ListObject denetimi Ekle** iletişim kutusu görüntülenir.

2. Listeye eklemek istediğiniz hücreyi veya hücreleri seçin ve **Tamam**' a tıklayın.

     Varsayılan adı korumak istemiyorsanız, adı **Özellikler** penceresinde değiştirebilirsiniz.

#### <a name="to-use-the-data-sources-window"></a>Veri Kaynakları penceresini kullanmak için

1. **Veri kaynakları** penceresini açın ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

2. **Veri kaynakları** penceresinden bir tabloyu çalışma sayfanıza sürükleyin.

     Çalışma sayfasına veriye dayalı bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim eklenir. Daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede çalışma zamanında ListObject denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>Denetimi çalışma zamanında dinamik olarak ekleyebilirsiniz. Bu, olaylara yanıt olarak konak denetimleri oluşturmanızı sağlar. Çalışma sayfası kapatıldığında dinamik olarak oluşturulan liste nesneleri çalışma sayfasında konak denetimleri olarak kalıcı olmaz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına programlı bir ListObject denetimi eklemek için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>' In olay işleyicisinde `Sheet1` , <xref:Microsoft.Office.Tools.Excel.ListObject> **a1** ile **a4**arası hücrelere bir denetim eklemek için aşağıdaki kodu ekleyin.

     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> VSTO eklenti projesindeki ListObject denetimlerini çalışma zamanında ekleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>VSTO eklenti projesindeki herhangi bir açık çalışma sayfasına programlı olarak bir denetim ekleyebilirsiniz. Dinamik olarak oluşturulan liste nesneleri, çalışma sayfası kaydedilip kapatıldığında konak denetimleri olarak çalışma sayfasında kalıcı olmaz. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına programlı bir ListObject denetimi eklemek için

1. Aşağıdaki kod, açık çalışma sayfasına dayalı bir çalışma sayfası konak öğesi oluşturur ve sonra <xref:Microsoft.Office.Tools.Excel.ListObject> **a1** ile **a4**arası hücrelere bir denetim ekler.

     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
