---
title: 'nasıl yapılır: program aracılığıyla Visio belgeye şekil ekleme'
description: kalıptan ana şablonları alarak ve etkin sayfadaki şekilleri bırakarak Microsoft Office bir Visio belgesine şekil ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: abe165dc59aa5782bd555c7034e17924ac3d8015
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046704"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>nasıl yapılır: program aracılığıyla Visio belgeye şekil ekleme
  ana şablonları bir kalıpdan alarak ve etkin sayfadaki şekilleri bırakarak bir Microsoft Office Visio belgesine şekil ekleyebilirsiniz.

 Daha fazla bilgi için,Microsoft.Office.Interop.Visio.Documtları için VBA başvuru belgelerine bakın [. Add](/office/vba/api/Visio.Documents.Add) yöntemi, [Microsoft. Office. Derlemesinde. Visio. Application. ActivePage](/office/vba/api/Visio.Application.ActivePage) özelliği ve [Microsoft. Office. Derlemesinde. Visio. Page. Drop](/office/vba/api/Visio.Page.Drop) yöntemi.

## <a name="add-shapes-to-a-visio-document"></a>Visio belgeye şekil ekleme

### <a name="to-add-shapes-to-a-visio-document"></a>Visio belgeye şekil eklemek için

- Bir belge etkinken Documents. Master koleksiyonundan ana şablonları alın ve şekilleri etkin belgeye bırakın. Bir ana şablonu dizin veya ana adı kullanarak alabilirsiniz.

     aşağıdaki kod örneği boş bir Visio belgesi oluşturur ve ardından **temel şekiller** kalıbı yerleştirilen ile açar. Daha sonra kod, birkaç şekli alır ve etkin sayfada bırakır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Visio şekilleriyle çalışma](../vsto/working-with-visio-shapes.md)
- [nasıl yapılır: Visio belgeye program aracılığıyla şekilleri kopyalama ve yapıştırma](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
