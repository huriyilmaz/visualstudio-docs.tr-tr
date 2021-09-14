---
title: 'Nasıl ekleyebilirsiniz: Çalışma sayfalarına Grafik denetimleri ekleme'
description: Tasarım zamanında ve çalışma zamanında belge düzeyinde özelleştirmeler Microsoft Office Excel çalışma sayfasına Grafik denetimleri ekleme hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2e714f486ebfb83f6cf5b6374e722b7d83cd3de3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725600"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Nasıl ekleyebilirsiniz: Çalışma sayfalarına Grafik denetimleri ekleme
  Bir çalışma <xref:Microsoft.Office.Tools.Excel.Chart> sayfasına tasarım zamanında Microsoft Office Excel çalışma zamanında belge düzeyinde özelleştirmeler içinde denetimler ekleyebilirsiniz. Ayrıca, <xref:Microsoft.Office.Tools.Excel.Chart> eklentilerde çalışma zamanında denetimler VSTO abilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Bu konuda aşağıdaki görevler açıklanmıştır:

- [Tasarım zamanında Grafik denetimleri ekleme](#designtime)

- [Belge düzeyindeki bir projede çalışma zamanında Grafik denetimleri ekleme](#runtimedoclevel)

- [VSTO Add-in projesine çalışma zamanında Grafik denetimleri ekleme](#runtimeaddin)

  Denetimler hakkında daha fazla <xref:Microsoft.Office.Tools.Excel.Chart> bilgi için bkz. [Grafik denetimi.](../vsto/chart-control.md)

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında Grafik denetimleri ekleme
 Denetimi çalışma <xref:Microsoft.Office.Tools.Excel.Chart> sayfanıza, uygulamanın içinde grafik ekley istediğiniz şekilde ekleyebilirsiniz.

> [!NOTE]
> Denetim <xref:Microsoft.Office.Tools.Excel.Chart> Araç Kutusundan veya **Veri** Kaynakları **penceresinden kullanılamaz.**

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Çalışma sayfasındaki bir çalışma sayfasına Grafik konak denetimi Excel

1. Ekle **sekmesindeki** **Grafikler** grubunda Sütun'a **tıklayın,** grafik kategorisine tıklayın ve ardından istediğiniz grafik türüne tıklayın.

2. Grafik **Ekle iletişim kutusunda** Tamam'a **tıklayın.**

3. Tasarım **sekmesindeki** Veri grubunda **Veri** **Seç'e tıklayın.**

4. Veri **Kaynağı Seç iletişim** kutusunda Grafik veri aralığı **kutusuna tıklayın** **ve** varsayılan seçimleri temizleyin.

5. Grafik **verileri sayfası'nın** Grafik için verileri içeren hücre aralığını seçin **(A5** ile **D8** hücreleri).

6. Veri Kaynağı **Seç iletişim kutusunda** Tamam'a **tıklayın.**

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede çalışma zamanında grafik denetimleri ekleme
 Denetimi çalışma zamanında <xref:Microsoft.Office.Tools.Excel.Chart> dinamik olarak ekleme. Belge kapatıldığında dinamik olarak oluşturulan grafikler belgede konak denetimleri olarak kalıcı olmaz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Çalışma sayfasına program aracılığıyla Grafik denetimi eklemek için

1. olay <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> işleyicisinde, `Sheet1` denetimi eklemek için aşağıdaki kodu <xref:Microsoft.Office.Tools.Excel.Chart> ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet1":::

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>VSTO Add-in projesine çalışma zamanında grafik denetimleri ekleme
 Bir denetim eklenti <xref:Microsoft.Office.Tools.Excel.Chart> projesinde açık olan herhangi bir çalışma sayfasına program aracılığıyla VSTO ekleyebilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

 Dinamik olarak oluşturulan grafik denetimleri, çalışma sayfası kapatıldığında konak denetimleri olarak çalışma sayfasında kalıcı olmaz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelere Denetim Ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Çalışma sayfasına program aracılığıyla Grafik denetimi eklemek için

1. Aşağıdaki kod, açık çalışma sayfasını temel alan bir çalışma sayfası konak öğesi oluşturur ve ardından bir denetim <xref:Microsoft.Office.Tools.Excel.Chart> ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet9":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnekte aşağıdaki gereksinimler vardır:

- Grafikte yer alan ve çalışma sayfasındaki A5 ile D8 aralığında depolanan veriler.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Grafik denetimi](../vsto/chart-control.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
