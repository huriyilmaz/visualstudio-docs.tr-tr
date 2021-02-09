---
title: Çalışma kitabı konak öğesi
description: Çalışma kitabı konak öğesinin, Microsoft Excel için birincil birlikte çalışma derlemesinden çalışma kitabı türünü genişleten bir tür olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel workbooks
- Workbook host items
- host items [Office development in Visual Studio], Workbook
- workbooks, Excel
- Workbook host items, events
- workbooks
- Excel [Office development in Visual Studio], workbooks
- workbooks, events
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24f32f8799d2bac5c23a0f8a2ef92857d2a6f7c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847602"
---
# <a name="workbook-host-item"></a>Çalışma kitabı konak öğesi
  <xref:Microsoft.Office.Tools.Excel.Workbook>Konak öğesi, <xref:Microsoft.Office.Interop.Excel.Workbook> Excel için birincil birlikte çalışma derlemesinden türü genişleten bir türdür. <xref:Microsoft.Office.Tools.Excel.Workbook>Konak öğesi, aynı özellikleri, yöntemleri ve olayları bir nesne olarak sağlar <xref:Microsoft.Office.Interop.Excel.Workbook> , ancak ek özellikler de sağlar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Belge düzeyi projelerinde, <xref:Microsoft.Office.Tools.Excel.Workbook> projenizdeki çalışma kitabını temsil eden bir varsayılan konak öğesi vardır. VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Excel.Workbook> çalışma zamanında konak öğeleri oluşturabilirsiniz.

## <a name="understand-the-workbook-host-item-in-document-level-projects"></a>Belge düzeyi projelerdeki çalışma kitabı konak öğesini anlayın
 Projenizdeki çalışma kitabına erişmek için `ThisWorkbook` sınıfını kullanın. `ThisWorkbook`Sınıfı, <xref:Microsoft.Office.Tools.Excel.Workbook> özelleştirmeinizdeki temel görevleri (çalışma kitabı açıldığında veya kapandığında kodu çalıştırmak gibi) gerçekleştirmek için konak öğesinin üyelerine erişmenizi sağlar. Daha fazla bilgi için bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

 `ThisWorkbook`Sınıfı, projenizde kod yazmaya başlayabilmeniz için bir konum sağlar. Sınıfı, Excel için birincil birlikte çalışma derlemesindeki nesne olarak aynı özellikleri, yöntemleri ve olayları sağladığından <xref:Microsoft.Office.Interop.Excel.Workbook> `ThisWorkbook` Excel 'in nesne modeline erişmek için de kullanabilirsiniz. Daha fazla bilgi için bkz. [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

 Çalışma kitabı tasarımcısını görüntülemek ve **Özellikler** penceresinde çalışma kitabının özelliklerini ve olaylarını görüntülemek için **Çözüm Gezgini** içindeki **ThisWorkbook** proje öğesine çift tıklayın.

### <a name="limitations-of-the-workbook-host-item-in-document-level-projects"></a>Belge düzeyi projelerdeki çalışma kitabı konak öğesi sınırlamaları
 Belge düzeyindeki bir proje yalnızca bir <xref:Microsoft.Office.Tools.Excel.Workbook> konak öğesi (yani, `ThisWorkbook` sınıfı) içerebilir. <xref:Microsoft.Office.Tools.Excel.Workbook>Tasarım zamanında projenize yeni konak öğeleri ekleyemez ve <xref:Microsoft.Office.Tools.Excel.Workbook> çalışma zamanında belge düzeyi özelleştirmesindeki yeni konak öğeleri oluşturamazsınız.

 Çalışma zamanında yeni bir Excel çalışma kitabı oluşturursanız, bu, türü olacaktır <xref:Microsoft.Office.Interop.Excel.Workbook> . Konak öğesi olmadığından, hiçbir konak denetimi veya Windows Forms denetimi içeremez. Çalışma zamanında çalışma kitapları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook>Konak öğesi konak denetimleri için bir kapsayıcı görevi yapmaz. Bu nedenle, çalışma kitabına görünür denetimleri ekleyemezsiniz, ancak <xref:System.Data.DataSet> bileşenlerin tüm çalışma sayfaları tarafından paylaşılabilmesi için gibi bileşenler ekleyebilirsiniz. Belge düzeyindeki bir projede, çalışma kitabı için kullanılabilen bileşenler **bileşen** sekmesi, **veri** sekmesi ve **araç kutusunun** **tüm Windows Forms** sekmelerinde bulunabilir.

> [!NOTE]
> Visual Studio 'da Office geliştirme araçları paylaşılan çalışma kitaplarını desteklemez.

## <a name="understand-workbook-host-items-in-vsto-add-in-projects"></a>VSTO eklenti projelerinde çalışma kitabı konak öğelerini anlama
 VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Excel.Workbook> Excel 'de açık olan herhangi bir çalışma kitabı için çalışma zamanında bir konak öğesi oluşturabilirsiniz. Bir <xref:Microsoft.Office.Tools.Excel.Workbook> konak öğesi oluşturmak için `GetVstoObject` yöntemini kullanın. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
