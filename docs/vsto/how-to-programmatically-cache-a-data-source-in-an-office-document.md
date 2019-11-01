---
title: Office belgesindeki önbelleğe alma veri kaynağı programlama
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241ce42c2d411fdaf611f3a7f2b52eb40c8c32a2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189589"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma
  Bir belge içindeki veri önbelleğine, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>veya <xref:Microsoft.Office.Tools.Excel.Worksheet>gibi bir konak öğesinin `StartCaching` yöntemini çağırarak programlı bir şekilde veri nesnesi ekleyebilirsiniz. Bir konak öğesinin `StopCaching` yöntemini çağırarak veri önbelleğinden veri nesnesini kaldırın.

 `StartCaching` yöntemi ve `StopCaching` yöntemi hem özeldir, ister IntelliSense 'de görünürler.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri önbelleğine veri nesnesi eklemek için `StartCaching` yöntemini kullandığınızda, veri nesnesinin <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliğiyle birlikte bildirilmesine gerek yoktur. Ancak veri nesnesi, veri önbelleğine eklenmek üzere belirli gereksinimleri karşılamalıdır. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Bir veri nesnesini programlı bir şekilde önbelleğe almak için

1. Veri nesnesini bir yöntem içinde değil sınıf düzeyinde bildirin. Bu örnekte, programlama yoluyla önbelleğe almak istediğiniz `dataSet1` adlı <xref:System.Data.DataSet> bildirdiğiniz varsayılır.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Veri nesnesini oluşturun ve sonra belge veya çalışma sayfası örneğinin `StartCaching` yöntemini çağırın ve veri nesnesinin adını geçirin.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Veri nesnesini önbelleğe almayı durdurmak için

1. Belge veya çalışma sayfası örneğinin `StopCaching` yöntemini çağırın ve veri nesnesinin adını geçirin. Bu örnek, `dataSet1` adlı ve önbelleğe almayı durdurmak istediğiniz <xref:System.Data.DataSet> olduğunu varsayar.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > Bir belge veya çalışma sayfasının `Shutdown` olayı için olay işleyicisinden `StopCaching` çağırmayın. `Shutdown` olayın ortaya çıkarılışında, veri önbelleğini değiştirmek çok geç. `Shutdown` olayı hakkında daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Sunucudaki belgelerdeki verilere erişin](../vsto/accessing-data-in-documents-on-the-server.md)
- [Verileri kaydetme](../data-tools/save-data-back-to-the-database.md)
