---
title: Farklı Eklentiler kullanarak belgelere özel XML VSTO ekleme
description: Xml verilerini aşağıdaki belge türlerinde depolamayı öğrenmek için bir eklentide özel xml VSTO öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 84e769cd1d841a5116750963dcee4c0cb1186bf4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046964"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Nasıl kullanılır: Özel XML parçalarını kullanarak belgelere VSTO ekleme
  Xml verilerini aşağıdaki belge türlerinde depolarken özel XML bölümü oluşturarak VSTO indirebilirsiniz:

- Bir Microsoft Office Excel çalışma kitabı.

- Bir Microsoft Office Word belgesi.

- Bir Microsoft Office PowerPoint sunusu.

  Daha fazla bilgi için bkz. [Özel XML bölümlerine genel bakış.](../vsto/custom-xml-parts-overview.md)

  **Aşağıdakiler için geçerlidir:** Bu konudaki bilgiler Excel, PowerPoint ve Word için uygulama düzeyindeki projeler için geçerlidir. Daha fazla bilgi için [bkz. Uygulama ve Office tarafından kullanılabilen özellikler.](../vsto/features-available-by-office-application-and-project-type.md)

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Bir çalışma kitabına özel XML Excel ekleme

1. Çalışma <xref:Microsoft.Office.Core.CustomXMLPart> kitabındaki koleksiyona <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> yeni bir nesne ekleyin. <xref:Microsoft.Office.Core.CustomXMLPart>, çalışma kitabında depolamak istediğiniz XML dizesini içerir.

     Aşağıdaki kod örneği, belirtilen çalışma kitabına özel bir XML bölümü ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs" id="Snippet1":::

2. yöntemi, Excel için `AddCustomXmlPartToWorkbook` `ThisAddIn` VSTO Eklenti projesinde sınıfına Excel.

3. Projenizin diğer kodlarından yöntemini çağırma. Örneğin, kullanıcı bir çalışma kitabını açtığında özel XML bölümü oluşturmak için, olay için bir olay işleyiciden yöntemini <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> çağırma.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word belgesine özel XML bölümü eklemek için

1. Belgede <xref:Microsoft.Office.Core.CustomXMLPart> koleksiyona <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> yeni bir nesne ekleyin. <xref:Microsoft.Office.Core.CustomXMLPart>, belgede depolamak istediğiniz XML dizesini içerir.

     Aşağıdaki kod örneği, belirtilen belgeye özel bir XML bölümü ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Word `AddCustomXmlPartToDocument` için bir `ThisAddIn` eklenti projesinde VSTO yöntemi ekleyin.

3. Projenizin diğer kodlarından yöntemini çağırma. Örneğin, kullanıcı bir belgeyi açtığında özel XML bölümü oluşturmak için, olay için bir olay işleyiciden yöntemini <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> çağırma.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Özel xml bölümünü bir sunuma PowerPoint için

1. <xref:Microsoft.Office.Core.CustomXMLPart> [Microsoft.Office. Birlikte çalış -abilir -lik. PowerPoint._Presentation.CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) koleksiyonu. <xref:Microsoft.Office.Core.CustomXMLPart>, sunuda depolamak istediğiniz XML dizesini içerir.

     Aşağıdaki kod örneği, belirtilen sunuya özel bir XML bölümü ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb" id="Snippet1":::

2. yöntemi, PowerPoint için `AddCustomXmlPartToPresentation` `ThisAddIn` bir VSTO Eklenti projesinde sınıfına ekleyin.

3. Projenizin diğer kodlarından yöntemini çağırma. Örneğin, kullanıcı bir sunu açtığında özel XML bölümünü oluşturmak için Microsoft.Office için bir olay [işleyiciden yöntemini Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) olayı.

## <a name="robust-programming"></a>Güçlü programlama
 Kolaylık olması için bu örnek, yönteminde yerel değişken olarak tanımlanan bir XML dizesi kullanır. Genellikle XML'yi dosya veya veritabanı gibi bir dış kaynaktan elde etmek gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)
- [Nasıl yapılır: Belge düzeyinde özelleştirmelere özel XML parçaları ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
