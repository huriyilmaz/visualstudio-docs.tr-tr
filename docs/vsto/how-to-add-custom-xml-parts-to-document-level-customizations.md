---
title: 'Nasıl yapılır: Belge düzeyinde özelleştirmelere özel XML parçaları ekleme'
description: Belge düzeyinde özelleştirmede özel bir XML bölümü oluşturarak XML Microsoft Office Excel bir çalışma kitabında veya Microsoft Office Word belgesinde nasıl depolayabilirsiniz?
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
ms.openlocfilehash: 32d4adc62f816381b0d9cffa0bde5463d0756610d58741f01153928317760cab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424114"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Nasıl yapılır: Belge düzeyinde özelleştirmelere özel XML parçaları ekleme
  Belge düzeyinde özelleştirmede özel bir XML Microsoft Office Excel oluşturarak XML Microsoft Office bir çalışma kitabında veya Word belgesinde depolarsınız. Daha fazla bilgi için bkz. [Özel XML bölümlerine genel bakış.](../vsto/custom-xml-parts-overview.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio, iş için belge düzeyi projeler Microsoft Office PowerPoint. VSTO Eklentisini kullanarak bir PowerPoint XML parçası ekleme hakkında bilgi için bkz. Nasıl kullanılır: VSTO Eklentilerini kullanarak belgelere özel [XML bölümleri ekleme.](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Bir çalışma kitabına özel XML Excel ekleme

1. Çalışma <xref:Microsoft.Office.Core.CustomXMLPart> kitabındaki koleksiyona <xref:Microsoft.Office.Core.CustomXMLParts> yeni bir nesne ekleyin. <xref:Microsoft.Office.Core.CustomXMLPart>, çalışma kitabında depolamak istediğiniz XML dizesini içerir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb" id="Snippet1":::

2. Yöntemi `AddCustomXmlPartToWorkbook` sınıfa eklemek `ThisWorkbook` için bir belge düzeyi projesinde Excel.

3. Projenizin diğer kodlarından yöntemini çağırma. Örneğin, kullanıcı çalışma kitabını açtığında özel XML bölümünü oluşturmak için olay işleyiciden `ThisWorkbook_Startup` yöntemini çağırabilirsiniz.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word belgesine özel XML bölümü eklemek için

1. Belgede <xref:Microsoft.Office.Core.CustomXMLPart> koleksiyona <xref:Microsoft.Office.Core.CustomXMLParts> yeni bir nesne ekleyin. <xref:Microsoft.Office.Core.CustomXMLPart>, belgede depolamak istediğiniz XML dizesini içerir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs" id="Snippet1":::

2. Word `AddCustomXmlPartToDocument` için belge `ThisDocument` düzeyi projesinde sınıfına yöntemini ekleyin.

3. Projenizin diğer kodlarından yöntemini çağırma. Örneğin, kullanıcı belgeyi açtığında özel XML bölümünü oluşturmak için olay işleyiciden `ThisDocument_Startup` yöntemini çağırabilirsiniz.

## <a name="robust-programming"></a>Güçlü programlama
 Kolaylık olması için bu örnek, yönteminde yerel değişken olarak tanımlanan bir XML dizesi kullanır. Genellikle XML'yi dosya veya veritabanı gibi bir dış kaynaktan elde etmek gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)
- [Nasıl kullanılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
