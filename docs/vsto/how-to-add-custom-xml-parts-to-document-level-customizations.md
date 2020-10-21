---
title: 'Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74bceeeabdaa46e6c1a35b5ab76de6a180d16d53
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298446"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme
  XML verilerini bir Microsoft Office Excel çalışma kitabında veya Microsoft Office Word belgesinde, belge düzeyi özelleştirmesinde özel bir XML bölümü oluşturarak saklayabilirsiniz. Daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio, PowerPoint Microsoft Office için belge düzeyi projeleri sağlamaz. VSTO eklentisini kullanarak bir PowerPoint sunusuna özel XML bölümü ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Excel çalışma kitabına özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Çalışma kitabındaki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Core.CustomXMLParts> . , <xref:Microsoft.Office.Core.CustomXMLPart> Çalışma kitabında depolamak ISTEDIĞINIZ XML dizesini içerir.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2. Yöntemi, `AddCustomXmlPartToWorkbook` `ThisWorkbook` Excel için belge düzeyindeki bir projede sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı çalışma kitabını açtığında özel XML bölümünü oluşturmak için `ThisWorkbook_Startup` olay işleyicisinden yöntemi çağırın.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word belgesine özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Belgedeki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Core.CustomXMLParts> . , <xref:Microsoft.Office.Core.CustomXMLPart> Belgede depolamak ISTEDIĞINIZ XML dizesini içerir.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2. `AddCustomXmlPartToDocument` `ThisDocument` Word için belge düzeyindeki bir projede yöntemi sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı belgeyi açtığında özel XML bölümünü oluşturmak için `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

## <a name="robust-programming"></a>Güçlü programlama
 Kolaylık olması için bu örnek, yönteminde yerel değişken olarak tanımlanan bir XML dizesi kullanır. Genellikle, XML dosyasını bir dosya veya veritabanı gibi bir dış kaynaktan edinmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)
- [Nasıl yapılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
