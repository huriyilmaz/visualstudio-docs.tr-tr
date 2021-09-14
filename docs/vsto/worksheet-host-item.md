---
title: Çalışma sayfası konak öğesi
description: Çalışma Sayfası konak öğesinin, Çalışma Sayfası türünü çalışma sayfası için birincil birlikte çalışma derlemesine genişleten bir tür olduğunu Excel.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9f9f27f9946e7a9e1c66d497c17332c1e194df70
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725525"
---
# <a name="worksheet-host-item"></a>Çalışma sayfası konak öğesi
  Konak <xref:Microsoft.Office.Tools.Excel.Worksheet> öğesi, birincil birlikte çalışma derlemesi olan türü, <xref:Microsoft.Office.Interop.Excel.Worksheet> konaklar için Excel. Konak öğesi bir nesneyle aynı özellikleri, yöntemleri ve olayların hepsini sağlar, ancak ek olayları da açığa çıkarır ve konak denetimleri ve Windows Forms denetimleri <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Worksheet> için kapsayıcı olarak davranır.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Belge düzeyindeki projelerde, tasarım <xref:Microsoft.Office.Tools.Excel.Worksheet> zamanında projenize konak öğeleri ekleyebilirsiniz. Eklenti VSTO içinde, çalışma zamanında konak <xref:Microsoft.Office.Tools.Excel.Worksheet> öğeleri oluşturabilirsiniz.

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Belge düzeyindeki projelerde çalışma sayfası konak öğelerini anlama
 Excel için bir belge düzeyi Visual Studio projesinde otomatik olarak <xref:Microsoft.Office.Tools.Excel.Worksheet> üç konak öğe oluşturur. Çalışma sayfalarının varsayılan adları `Sheet1` , ve `Sheet2` 'tir. `Sheet3` Mevcut çalışma kitabını temel alan bir proje ekleyebilirsiniz, konak öğelerinin sayısı çalışma kitabındaki çalışma sayfalarının sayısına bağlıdır.

 Bu çalışma sayfası sınıfları, özelleştirme işleminizin içinde çalışma sayfasının içeriğini değiştirme gibi temel görevleri gerçekleştirmek için konak öğesinin <xref:Microsoft.Office.Tools.Excel.Worksheet> üyelerine erişmenizi sağlar. Çalışma sayfalarına denetim eklemek için de bu sınıfları kullanabilirsiniz. Farklı denetim kümelerini birleştirerek ve kod yazarak, denetimleri verilere bağlayabilirsiniz, kullanıcıdan bilgi toplayabilirsiniz ve kullanıcı eylemlerini yanıtlayabilirsiniz. Daha fazla bilgi için [bkz. Program belge düzeyi özelleştirmeleri.](../vsto/programming-document-level-customizations.md)

 Çalışma sayfası sınıfları, projenize kod yazmaya başlayacağınız bir konum sağlar. sınıfı, Excel için birincil birlikte çalışma derlemesinde nesneyle aynı özellikleri, yöntemleri ve olayları sağladığı için, bu sınıfları kullanarak <xref:Microsoft.Office.Interop.Excel.Worksheet> Excel'nin nesne modeline erişebilirsiniz. Daha fazla bilgi için [bkz. Excel modeline genel bakış.](../vsto/excel-object-model-overview.md)

 Belge düzeyi projelerde, tasarım zamanında tasarımcıdaki çalışma kitabına yeni bir çalışma sayfası ekleyerek projeye ek <xref:Microsoft.Office.Tools.Excel.Worksheet> konak öğeleri ekleyebilirsiniz.

### <a name="rename-worksheets"></a>Çalışma sayfalarını yeniden adlandırma
 Belge düzeyi bir projede, çalışma sayfalarını Visual Studio tasarımcısında yeniden adlandırabilirsiniz, ancak bu yalnızca çalışma sayfasının görünen adını değiştirir. Programlı ad hala çalışma sayfasının varsayılan adıdır. Özellikler penceresinde çalışma sayfasını yeniden **adlandırdısanız** yalnızca program adı değiştirilir.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Belge düzeyindeki projelerde çalışma sayfası konak öğesinin sınırlamaları
 Belge düzeyi <xref:Microsoft.Office.Tools.Excel.Worksheet> projesinde çalışma zamanında yeni konak öğeleri oluşturamazsınız. Çalışma zamanında yeni Excel çalışma sayfası oluşturmanız, türünde <xref:Microsoft.Office.Interop.Excel.Worksheet> olur. Bir konak öğesi olduğundan, herhangi bir konak denetimi veya form Windows içeramaz. Çalışma zamanında belge oluşturma hakkında daha fazla bilgi için bkz. Nasıl kullanılır: Çalışma kitaplarını program aracılığıyla [yeni çalışma sayfalarına ekleme.](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Eklenti projelerinde çalışma VSTO öğelerini anlama
 Uygulama düzeyindeki projelerde, çalışma zamanında bir konak öğesi oluşturabilirsiniz. Çalışma zamanında, çalışma zamanında açık olan tüm <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma sayfaları Excel. Konak öğesini, ilişkili çalışma sayfasına denetimler eklemek veya nesnelerde mevcut olan olayları <xref:Microsoft.Office.Tools.Excel.Worksheet> işlemek için <xref:Microsoft.Office.Interop.Excel.Worksheet> kullanabilirsiniz.

 Konak öğesi <xref:Microsoft.Office.Tools.Excel.Worksheet> oluşturmak için yöntemini `GetVstoObject` kullanın. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office için denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma kitabı konak öğesi](../vsto/workbook-host-item.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
