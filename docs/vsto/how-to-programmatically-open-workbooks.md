---
title: 'Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma'
description: bir Microsoft Excel çalışma kitabını programlı olarak açmak veya var olan bir çalışma kitabıyla çalışmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 529b957613ae954d35c2284870d6512c7357ac64
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105970"
---
# <a name="how-to-programmatically-open-workbooks"></a>Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma
  <xref:Microsoft.Office.Interop.Excel.Workbooks>Microsoft Office Excel koleksiyon, tüm açık çalışma kitapları ile çalışmayı ve çalışma kitaplarını açmayı olanaklı kılar.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Mevcut bir çalışma kitabını açmak için

1. <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> <xref:Microsoft.Office.Interop.Excel.Workbooks> Çalışma kitabının yolunu geçirerek koleksiyonun yöntemini kullanın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği şunları gerektirir:

- Adlı bir çalışma kitabı `YourWorkbook.xls` , C sürücüsünde adlı bir dizinde bulunmalıdır `Test` .

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla metin dosyalarını çalışma kitabı olarak açma](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
