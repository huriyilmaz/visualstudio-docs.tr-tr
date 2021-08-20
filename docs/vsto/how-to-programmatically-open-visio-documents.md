---
title: 'Nasıl Visio: Program aracılığıyla Visio açma'
description: Open veya OpenEx Visual Studio bir belgeyi program aracılığıyla Visio için Visio nasıl kullanabileceğiniz hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1c3126f3f5ac73632996079a070c426afc20d656
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155830"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Nasıl Visio: Program aracılığıyla Visio açma
  Mevcut belgeleri açmak için iki yöntem Microsoft Office Visio vardır: Open ve OpenEx. OpenEx yöntemi Open yöntemiyle aynıdır, ancak çağıranın belgenin nasıl aç olduğunu belirterek bağımsız değişkenler sağladığını gösterir.

 Nesne modeli hakkında ayrıntılı bilgi için, nesne modellerine ilişkin VBA [ başvuruMicrosoft.Office.Interop.Visio.Docbakın. Yöntemi](/office/vba/api/Visio.Documents.Open) açın [ veMicrosoft.Office.Interop.Visio.Docaçın. OpenEx](/office/vba/api/Visio.Documents.OpenEx) yöntemi.

## <a name="open-a-visio-document"></a>Bir belgeyi Visio açma

### <a name="to-open-a-visio-document"></a>Bir belgeyi Visio için

- yöntemini `Microsoft.Office.Interop.Visio.Documents.Open` çağırma ve bu belgenin tam yolunu Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>Belirtilen bağımsız Visio bir belge açma

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Bir belgeyi Visio salt okunur ve yerleştirildi olarak açmak için

- yöntemini çağırın, Visio belgesinin tam yolunu s ekleyin ve kullanmak istediğiniz bağımsız değişkenleri (bu durumda Docked ve `Microsoft.Office.Interop.Visio.Documents.OpenEx` Salt Okunur) ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneği için aşağıdakiler gerekir:

- adlı Visio belge, Belgelerim klasöründe (Windows XP ve önceki sürümler için) veya Belgeler klasöründe `myDrawing.vsd` `Test` (Windows Vista için) olmalıdır.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visio çözümleri](../vsto/visio-solutions.md)
- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Nasıl kullanılır: Program aracılığıyla yeni Visio oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio kapatma](../vsto/how-to-programmatically-close-visio-documents.md)
- [Nasıl Visio: Program aracılığıyla Visio kaydetme](../vsto/how-to-programmatically-save-visio-documents.md)
- [Nasıl kullanılır: Program aracılığıyla Visio yazdırma](../vsto/how-to-programmatically-print-visio-documents.md)
