---
title: Çalışma sayfası konak öğesi
description: Çalışma sayfası konak öğesinin, Excel için birincil birlikte çalışma derlemesinden çalışma sayfası türünü genişleten bir tür olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b25b921d29bee832ef37b943fd57edc38b7518db
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523218"
---
# <a name="worksheet-host-item"></a>Çalışma sayfası konak öğesi
  <xref:Microsoft.Office.Tools.Excel.Worksheet>Konak öğesi, <xref:Microsoft.Office.Interop.Excel.Worksheet> Excel için birincil birlikte çalışma derlemesinden türü genişleten bir türdür. <xref:Microsoft.Office.Tools.Excel.Worksheet>Konak öğesi, aynı özellikleri, yöntemleri ve olayları bir nesne olarak sağlar <xref:Microsoft.Office.Interop.Excel.Worksheet> , ancak ayrıca ek olaylar sunar ve konak denetimleri ve Windows Forms denetimleri için bir kapsayıcı görevi görür.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Belge düzeyi projelerinde, <xref:Microsoft.Office.Tools.Excel.Worksheet> tasarım zamanında projenize ana bilgisayar öğeleri ekleyebilirsiniz. VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma zamanında konak öğeleri oluşturabilirsiniz.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Belge düzeyi projelerdeki çalışma sayfası konak öğelerini anlama
 Excel için belge düzeyi projesi oluşturduğunuzda, Visual Studio otomatik olarak <xref:Microsoft.Office.Tools.Excel.Worksheet> projede üç konak öğesi oluşturur. Çalışma sayfalarının varsayılan adları `Sheet1` , ve ' dir `Sheet2` `Sheet3` . Var olan bir çalışma kitabını temel alan bir proje oluşturursanız, konak öğelerinin sayısı çalışma kitabındaki çalışma sayfası sayısına bağlıdır.

 Bu çalışma sayfası sınıfları <xref:Microsoft.Office.Tools.Excel.Worksheet> , özelleştirmenizin çalışma sayfasının içeriğini değiştirme gibi temel görevleri yerine getirmek için konak öğesi üyelerine erişmenizi sağlar. Ayrıca, çalışma sayfalarına denetim eklemek için bu sınıfları kullanabilirsiniz. Farklı denetim kümelerini birleştirerek ve kod yazarken, denetimleri verilere bağlayabilir, kullanıcıdan bilgi toplayabilir ve kullanıcı eylemlerine yanıt verebilirsiniz. Daha fazla bilgi için bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

 Çalışma sayfası sınıfları, projenizde kod yazmaya başlayabilmeniz için bir konum sağlar. Sınıfı, Excel için birincil birlikte çalışma derlemesindeki nesne olarak aynı özellikleri, yöntemleri ve olayları sağladığından <xref:Microsoft.Office.Interop.Excel.Worksheet> , Excel 'in nesne modeline erişmek için de bu sınıfları kullanabilirsiniz. Daha fazla bilgi için bkz. [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

 Belge düzeyi projelerinde, <xref:Microsoft.Office.Tools.Excel.Worksheet> Tasarımcıda çalışma kitabına yeni bir çalışma sayfası ekleyerek, tasarım zamanında projeye ek konak öğeleri ekleyebilirsiniz.

### <a name="rename-worksheets"></a>Çalışma sayfalarını yeniden adlandırma
 Belge düzeyi projesinde, Visual Studio tasarımcısında çalışma sayfalarını yeniden adlandırabilirsiniz, ancak bu yalnızca çalışma sayfasının görünen adını değiştirir. Programlı ad, hala çalışma sayfasının varsayılan adıdır. Çalışma sayfasını **Özellikler** penceresinde yeniden adlandırırsanız yalnızca programlı ad değiştirilir.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Belge düzeyi projelerdeki çalışma sayfası konak öğesi sınırlamaları
 <xref:Microsoft.Office.Tools.Excel.Worksheet>Belge düzeyindeki bir projede çalışma zamanında yeni konak öğeleri oluşturamazsınız. Çalışma zamanında yeni bir Excel çalışma sayfası oluşturursanız, bu, türü olacaktır <xref:Microsoft.Office.Interop.Excel.Worksheet> . Konak öğesi olmadığından, hiçbir konak denetimi veya Windows Forms denetimi içeremez. Çalışma zamanında belge oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla yeni çalışma sayfalarını ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>VSTO eklenti projelerinde çalışma sayfası konak öğelerini anlama
 Uygulama düzeyi projelerinde, <xref:Microsoft.Office.Tools.Excel.Worksheet> Excel 'de açık olan herhangi bir çalışma sayfası için çalışma zamanında bir konak öğesi oluşturabilirsiniz. <xref:Microsoft.Office.Tools.Excel.Worksheet>İlişkili çalışma sayfasına denetim eklemek veya nesnelerde kullanılamayan olayları işlemek için konak öğesini kullanabilirsiniz <xref:Microsoft.Office.Interop.Excel.Worksheet> .

 Bir <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğesi oluşturmak için `GetVstoObject` yöntemini kullanın. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
