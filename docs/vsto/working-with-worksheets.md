---
title: Çalışma sayfalarıyla çalışma
description: Çalışma sayfası ve çalışma sayfası sınıflarının, çalışma sayfalarıyla görevleri gerçekleştirmek için kullandığınız yöntemleri ve özellikleri içerdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], worksheets
- worksheets [Office development in Visual Studio], common tasks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b29fddd4b13df242740fa98922ee9fe762209f3a343c26dd8ef7cceb5293153d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121407973"
---
# <a name="work-with-worksheets"></a>Çalışma sayfalarıyla çalışma
  <xref:Microsoft.Office.Tools.Excel.Worksheet>Ve <xref:Microsoft.Office.Interop.Excel.Worksheet> sınıfları, çalışma sayfalarıyla görevleri gerçekleştirmek için kullandığınız yöntemleri ve özellikleri içerir.

|Görev|Yordam|
|----------|---------------|
|Çalışma kitabına yeni bir çalışma sayfası ekleyin.|[Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)|
|Çalışma kitabının belirli bir konumundaki çalışma sayfasının bir kopyasını oluşturun.|[Nasıl yapılır: program aracılığıyla çalışma sayfalarını kopyalama](../vsto/how-to-programmatically-copy-worksheets.md)|
|Belirtilen çalışma sayfasını silin.|[Nasıl yapılır: çalışma kitaplarındaki çalışma sayfalarını program aracılığıyla silme](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)|
|Kullanıcının seçimini belirtilen çalışma sayfasına taşıyın.|[Nasıl yapılır: program aracılığıyla çalışma sayfaları seçme](../vsto/how-to-programmatically-select-worksheets.md)|
|Tüm çalışma sayfalarının toplanması arasında yineleme yapın.|[Nasıl yapılır: çalışma kitabındaki tüm çalışma sayfalarını program aracılığıyla listeleme](../vsto/how-to-programmatically-list-all-worksheets-in-a-workbook.md)|
|Çalışma sayfasını önizleyin ve yazdırın.|[Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma](../vsto/how-to-programmatically-print-worksheets.md)|
|Çalışma kitabını çalışma kitabındaki yeni bir konuma taşıyın.|[Nasıl yapılır: çalışma kitaplarını program aracılığıyla çalışma kitapları içinde taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)|
|Bir veya daha fazla çalışma sayfasının görünürlüğünü değiştirin.|[Nasıl yapılır: program aracılığıyla çalışma sayfalarını gizleme](../vsto/how-to-programmatically-hide-worksheets.md)|
|Çalışma sayfasının tamamını veya bir kısmını, düzenlenemeyecek şekilde kilitleyin.|[Nasıl yapılır: program aracılığıyla çalışma sayfalarını koruma](../vsto/how-to-programmatically-protect-worksheets.md)|
|Bir çalışma sayfasından kilidi kaldırarak düzenlenebilmesini sağlayın.|[Nasıl yapılır: çalışma sayfalarından program aracılığıyla korumayı kaldırma](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)|
|Açıklamaları ekleyin ve silin.|[Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını ekleme ve silme](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)|
|Tüm açıklamaları göster veya gizle.|[Nasıl yapılır: program aracılığıyla çalışma sayfası açıklamalarını görüntüleme](../vsto/how-to-programmatically-display-worksheet-comments.md)|
|Çalışma sayfalarında gruplar oluşturun.|[Nasıl yapılır: çalışma sayfasında program aracılığıyla satırları gruplama](../vsto/how-to-programmatically-group-rows-in-a-worksheet.md)|
|Bir satırı yalnızca seçili bir hücre içerdiğinde kalın hale getirin.|[Nasıl yapılır: seçili hücreleri içeren çalışma sayfası satırlarında program aracılığıyla biçimlendirmeyi değiştirme](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)|
|Çalışma sayfaları arasında veri kopyalama ve biçimlendirme.|[Nasıl yapılır: çalışma sayfaları arasında program aracılığıyla veri kopyalama ve biçimlendirme](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)|
|Çalışma sayfalarında yazım denetimi yapın.|[Nasıl yapılır: çalışma sayfalarında program aracılığıyla yazımı denetleme](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)|
|Adlandırılmış aralıklarda ve liste nesnelerinde verileri sıralayın.|[Nasıl yapılır: çalışma sayfalarındaki verileri program aracılığıyla sıralama](../vsto/how-to-programmatically-sort-data-in-worksheets.md)|

 Excel görevler ve Excel nesne modeli hakkında daha fazla bilgi için bkz. [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

 bazı durumlarda, VSTO eklentilerde bu görevleri gerçekleştirdiğiniz yollar, bunları belge düzeyi özelleştirmelerde gerçekleştirmenizin yollarından farklıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Aralıklar ile çalışma](../vsto/working-with-ranges.md)
- [Excel çalışma sayfalarında Windows Forms denetimleri kullanma](../vsto/using-windows-forms-controls-on-excel-worksheets.md)
