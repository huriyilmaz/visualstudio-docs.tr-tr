---
title: 'Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme'
description: belge düzeyi özelleştirmesinde özel bir xml bölümü oluşturarak bir Microsoft Office Excel çalışma kitabında veya Microsoft Office Word belgesinde XML verilerini nasıl depolayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 217bb0178a09822a7f44af91ed475fd9364dc09d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083511"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme
  belge düzeyi özelleştirmesinde özel bir xml bölümü oluşturarak, xml verilerini bir Microsoft Office Excel çalışma kitabında veya Microsoft Office Word belgesinde saklayabilirsiniz. Daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio, Microsoft Office PowerPoint için belge düzeyi projeleri sağlamıyor. bir VSTO eklentisi kullanarak bir PowerPoint sunumuna özel xml bölümü ekleme hakkında bilgi için bkz. [nasıl yapılır: belgelere özel xml bölümleri ekleme VSTO eklentileri kullanarak](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Excel çalışma kitabına özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Çalışma kitabındaki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Core.CustomXMLParts> . , <xref:Microsoft.Office.Core.CustomXMLPart> Çalışma kitabında depolamak ISTEDIĞINIZ XML dizesini içerir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Yöntemi, `AddCustomXmlPartToWorkbook` `ThisWorkbook` Excel için belge düzeyindeki bir projede sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı çalışma kitabını açtığında özel XML bölümünü oluşturmak için `ThisWorkbook_Startup` olay işleyicisinden yöntemi çağırın.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word belgesine özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Belgedeki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Core.CustomXMLParts> . , <xref:Microsoft.Office.Core.CustomXMLPart> Belgede depolamak ISTEDIĞINIZ XML dizesini içerir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. `AddCustomXmlPartToDocument` `ThisDocument` Word için belge düzeyindeki bir projede yöntemi sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı belgeyi açtığında özel XML bölümünü oluşturmak için `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

## <a name="robust-programming"></a>Güçlü programlama
 Kolaylık olması için bu örnek, yönteminde yerel değişken olarak tanımlanan bir XML dizesi kullanır. Genellikle, XML dosyasını bir dosya veya veritabanı gibi bir dış kaynaktan edinmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)
- [nasıl yapılır: VSTO eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
