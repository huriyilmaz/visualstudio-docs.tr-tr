---
title: 'Nasıl kullanılır: Özel belge özellikleri oluşturma ve değiştirme'
description: Belgeyle depolamak istediğiniz ek bilgiler varsa özel belge özellikleri oluşturma ve değiştirme hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5c9cd9ea47ef21ea8cef2349ccd9ccb9e3a47141
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046977"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Nasıl kullanılır: Özel belge özellikleri oluşturma ve değiştirme
  Yukarıda Microsoft Office uygulamalar belgelerle depolanan yerleşik özellikler sağlar. Ayrıca, belgeyle depolamak istediğiniz ek bilgiler varsa özel belge özellikleri oluşturabilir ve değiştirebilirsiniz.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Özel özelliklerle çalışmak için bir belgenin CustomDocumentProperties özelliğini kullanın. Örneğin, bir belge düzeyi projesinde Microsoft Office Excel sınıfının <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> özelliğini `ThisWorkbook` kullanın. Bir VSTO projesinde Excel <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> nesnesinin özelliğini <xref:Microsoft.Office.Interop.Excel.Workbook> kullanın. Bu özellikler, <xref:Microsoft.Office.Core.DocumentProperties> bir nesne koleksiyonu olan nesnesini geri <xref:Microsoft.Office.Core.DocumentProperty> verir. Koleksiyon içindeki `Item` dizine göre veya adıyla belirli bir özelliği almak için koleksiyonun özelliğini kullanabilirsiniz.

 Aşağıdaki örnekte, belge düzeyi özelleştirmede özel bir özelliğin nasıl ek Excel ve ona bir değer atanma adımları yer almaktadır.

## <a name="example"></a>Örnek
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet6":::

## <a name="robust-programming"></a>Güçlü programlama
 Tanımsız özellikler `Value` için özelliğine erişme girişimi bir özel durum oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl kullanılır: Belge özelliklerinden okuma ve belgeye yazma](../vsto/how-to-read-from-and-write-to-document-properties.md)
