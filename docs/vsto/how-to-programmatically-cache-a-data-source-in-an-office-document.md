---
title: Office belgesindeki önbelleğe alma veri kaynağı programlama
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8ec3a38d109de561e3cba77951764dd8dd9479df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544774"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma
  `StartCaching`,, Veya gibi bir konak öğesinin yöntemini çağırarak bir belgedeki veri önbelleğine programlı bir şekilde veri nesnesi ekleyebilirsiniz <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> . Bir konak öğesinin yöntemini çağırarak veri önbelleğinden veri nesnesini kaldırın `StopCaching` .

 `StartCaching`Yöntemi ve `StopCaching` yöntemi hem özeldir, ister IntelliSense 'de görünürler.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri `StartCaching` önbelleğine veri nesnesi eklemek için yöntemini kullandığınızda, veri nesnesinin özniteliğiyle birlikte bildirilmesine gerek yoktur <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Ancak veri nesnesi, veri önbelleğine eklenmek üzere belirli gereksinimleri karşılamalıdır. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Bir veri nesnesini programlı bir şekilde önbelleğe almak için

1. Veri nesnesini bir yöntem içinde değil sınıf düzeyinde bildirin. Bu örnek, <xref:System.Data.DataSet> `dataSet1` programlama yoluyla önbelleğe almak istediğiniz bir adlandırılmış adı bildirdiğinizi varsayar.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Veri nesnesini oluşturun ve sonra `StartCaching` belge veya çalışma sayfası örneği yöntemini çağırın ve veri nesnesinin adını geçirin.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Veri nesnesini önbelleğe almayı durdurmak için

1. `StopCaching`Belge veya çalışma sayfası örneği yöntemini çağırın ve veri nesnesinin adını geçirin. Bu örnek, <xref:System.Data.DataSet> önbelleğe almayı durdurmak istediğiniz bir adlandırılmış olduğunu varsayar `dataSet1` .

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > `StopCaching` `Shutdown` Bir belge veya çalışma sayfası olayı için olay işleyicisinden çağırmayın. `Shutdown`Olayın ortaya çıkarılışında, veri önbelleğini değiştirmek çok geç olur. Olay hakkında daha fazla bilgi için `Shutdown` bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Sunucudaki belgelerdeki verilere erişin](../vsto/accessing-data-in-documents-on-the-server.md)
- [Verileri kaydetme](../data-tools/save-data-back-to-the-database.md)
