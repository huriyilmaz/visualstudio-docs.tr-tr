---
title: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme
description: VSTO eklentilerde özel bir XML bölümü oluşturarak XML verilerini aşağıdaki belge türlerinde nasıl depolayabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 31c2364213d3b4dae16558f395ad7bdd93231787
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827870"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Nasıl yapılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme
  VSTO eklentilerde özel bir XML bölümü oluşturarak XML verilerini aşağıdaki belge türlerinde saklayabilirsiniz:

- Microsoft Office bir Excel çalışma kitabı.

- Bir Microsoft Office Word belgesi.

- PowerPoint sunusu Microsoft Office.

  Daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

  **Uygulama hedefi:** Bu konudaki bilgiler Excel, PowerPoint ve Word için uygulama düzeyi projelere yöneliktir. Daha fazla bilgi için bkz. [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Excel çalışma kitabına özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Çalışma kitabındaki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> . , <xref:Microsoft.Office.Core.CustomXMLPart> Çalışma kitabında depolamak ISTEDIĞINIZ XML dizesini içerir.

     Aşağıdaki kod örneği, belirtilen çalışma kitabına özel bir XML bölümü ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Yöntemi, `AddCustomXmlPartToWorkbook` `ThisAddIn` Excel IÇIN bir VSTO eklenti projesindeki sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı bir çalışma kitabını açtığında özel XML bölümünü oluşturmak için olay işleyicisinde yöntemi çağırın <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> .

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Word belgesine özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Belgedeki koleksiyona yeni bir nesne ekleyin <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> . , <xref:Microsoft.Office.Core.CustomXMLPart> Belgede depolamak ISTEDIĞINIZ XML dizesini içerir.

     Aşağıdaki kod örneği, belirtilen belgeye özel bir XML bölümü ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs" id="Snippet1":::

2. Yöntemi, `AddCustomXmlPartToDocument` `ThisAddIn` Word IÇIN bir VSTO eklenti projesindeki sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı bir belge açtığında özel XML bölümü oluşturmak için, olayı için olay işleyicisinden yöntemi çağırın <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Bir PowerPoint sunusuna özel bir XML bölümü eklemek için

1. <xref:Microsoft.Office.Core.CustomXMLPart>Sunudaki [Microsoft.Office.Interop.PowerPoint._Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) koleksiyonuna yeni bir nesne ekleyin. , <xref:Microsoft.Office.Core.CustomXMLPart> Sunuda depolamak ISTEDIĞINIZ XML dizesini içerir.

     Aşağıdaki kod örneği, belirtilen sunuya özel bir XML bölümü ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb" id="Snippet1":::

2. Yöntemi, `AddCustomXmlPartToPresentation` `ThisAddIn` POWERPOINT Için VSTO eklenti projesindeki sınıfına ekleyin.

3. Projenizdeki diğer koddan yöntemi çağırın. Örneğin, Kullanıcı bir sunu açtığında özel XML bölümü oluşturmak için, [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) olayına yönelik bir olay işleyicisinden yöntemi çağırın.

## <a name="robust-programming"></a>Güçlü programlama
 Kolaylık olması için bu örnek, yönteminde yerel değişken olarak tanımlanan bir XML dizesi kullanır. Genellikle, XML dosyasını bir dosya veya veritabanı gibi bir dış kaynaktan edinmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md)
- [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
