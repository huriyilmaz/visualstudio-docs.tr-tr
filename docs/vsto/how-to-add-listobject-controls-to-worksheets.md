---
title: 'Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme'
description: tasarım zamanında ve belge düzeyi projelerindeki çalışma zamanında bir Microsoft Office Excel çalışma sayfasına ListObject denetimleri nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0d10d82a404ec5248e06c3d4f71d622c793f62ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083524"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme
  <xref:Microsoft.Office.Tools.Excel.ListObject>bir Microsoft Office Excel çalışma sayfasına tasarım zamanında ve çalışma zamanında belge düzeyi projelerinde denetim ekleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ayrıca, <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma zamanında VSTO eklenti projelerinde denetim ekleyebilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında ListObject denetimleri ekleme](#designtime)

- [Belge düzeyindeki bir projede çalışma zamanında ListObject denetimleri ekleme](#runtimedoclevel)

- [VSTO eklentisi projesinde çalışma zamanında ListObject denetimleri ekleme](#runtimeaddin)

  Denetimler hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.ListObject> bkz. [ListObject denetimi](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında ListObject denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>tasarım zamanında belge düzeyindeki bir projedeki çalışma sayfasına denetim eklemenin birkaç yolu vardır: Excel içinden, Visual Studio **araç kutusundan** ve **veri kaynakları** penceresinden.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Excel içinde şeridi kullanmak için

1. **Ekle** sekmesinde, **Tablolar** grubunda, **tablo**' ya tıklayın.

2. Listeye eklemek istediğiniz hücreyi veya hücreleri seçin ve **Tamam**' a tıklayın.

#### <a name="to-use-the-toolbox"></a>Araç kutusunu kullanmak için

1. **araç kutusunun** **Excel denetimleri** sekmesinden, öğesini <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasına sürükleyin.

     **ListObject denetimi Ekle** iletişim kutusu görüntülenir.

2. Listeye eklemek istediğiniz hücreyi veya hücreleri seçin ve **Tamam**' a tıklayın.

     Varsayılan adı korumak istemiyorsanız, adı **Özellikler** penceresinde değiştirebilirsiniz.

#### <a name="to-use-the-data-sources-window"></a>Veri Kaynakları penceresini kullanmak için

1. **Veri kaynakları** penceresini açın ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

2. **Veri kaynakları** penceresinden bir tabloyu çalışma sayfanıza sürükleyin.

     Çalışma sayfasına veriye dayalı bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetim eklenir. daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede çalışma zamanında ListObject denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>Denetimi çalışma zamanında dinamik olarak ekleyebilirsiniz. Bu, olaylara yanıt olarak konak denetimleri oluşturmanızı sağlar. Çalışma sayfası kapatıldığında dinamik olarak oluşturulan liste nesneleri çalışma sayfasında konak denetimleri olarak kalıcı olmaz. daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına programlı bir ListObject denetimi eklemek için

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>' In olay işleyicisinde `Sheet1` , <xref:Microsoft.Office.Tools.Excel.ListObject> **a1** ile **a4** arası hücrelere bir denetim eklemek için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet2":::

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>VSTO eklentisi projesinde çalışma zamanında ListObject denetimleri ekleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>VSTO eklenti projesindeki herhangi bir açık çalışma sayfasına programlı olarak bir denetim ekleyebilirsiniz. Dinamik olarak oluşturulan liste nesneleri, çalışma sayfası kaydedilip kapatıldığında konak denetimleri olarak çalışma sayfasında kalıcı olmaz. daha fazla bilgi için bkz. [çalışma zamanında VSTO eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Bir çalışma sayfasına programlı bir ListObject denetimi eklemek için

1. Aşağıdaki kod, açık çalışma sayfasına dayalı bir çalışma sayfası konak öğesi oluşturur ve sonra <xref:Microsoft.Office.Tools.Excel.ListObject> **a1** ile **a4** arası hücrelere bir denetim ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet8":::

## <a name="see-also"></a>Ayrıca bkz.
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
