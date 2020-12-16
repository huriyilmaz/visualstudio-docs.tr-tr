---
title: Office projelerindeki Özellikler
description: Özellikler penceresi aracılığıyla Visual Studio 'da Office projeleri için kullanılabilen özellikler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdc54de3935646e36f9d4f09727037de4c373c92
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528033"
---
# <a name="properties-in-office-projects"></a>Office projelerindeki Özellikler
  Visual Studio 'da Office projeleri için kullanılabilen çeşitli önemli özellikler vardır. Bu özelliklere **Özellikler** penceresinden erişilebilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Konak öğesi için ad alanı
 Visual C# projelerindeki konak öğesi sınıflarının (örneğin,, veya sınıfların) ad alanını değiştirmek için **konak öğesi özelliği Için ad alanını** kullanın `ThisAddIn` `ThisWorkbook` `ThisDocument` . Bu özellik, belge düzeyindeki bir projede belge düğümünü ( *ExcelWorkbook1.xlsx* veya *WordDocument1.docx*) veya **Çözüm Gezgini** Içindeki bir VSTO eklenti projesindeki (Excel veya Word gibi) uygulama düğümünü seçerken **Özellikler** penceresinde görünür.

 Visual C# Office projesi oluşturduğunuzda, ana bilgisayar öğelerine projenin adına göre ad alanı verilir. Kod dosyalarını doğrudan düzenlemek yerine, ad alanını değiştirmek için **konak öğesi özelliği Için ad alanını** kullanmanız önerilir. Bu özelliği kullandığınızda, ad alanı oluşturulan (gizli) kod dosyalarında ve görünür kod dosyalarında değiştirilir.

## <a name="cacheindocument"></a>CacheInDocument
 Visual Studio tasarımcısında bir örneğini seçtiğinizde, belge düzeyi projeleri için **Özellikler** penceresinde **CacheInDocument** özelliği görüntülenir <xref:System.Data.DataSet> . Yalnızca ortak Üyeler önbelleğe alınabilir; bir önbelleğe almak istiyorsanız **değiştiriciler** özelliğinin **ortak** olarak ayarlandığından emin olun <xref:System.Data.DataSet> .

 Bu özellik bir Boolean değeri alır:

- Veri kümesini belgede önbelleğe almak için **true** seçeneğini belirleyin.

- Veri kümesinin belgede önbelleğe alınmasını istemiyorsanız **false** ' ı seçin.

  Verileri önbelleğe alma hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Value2
 **Değer2** özelliği yalnızca Excel çalışma kitabı veya şablon projeleri için kullanılabilir. Çalışma sayfası tasarımcısında bir denetim seçtiğinizde **Özellikler** penceresindeki **DataBindings** Özelliği düğümünün altında görüntülenir <xref:Microsoft.Office.Tools.Excel.NamedRange> .

 Öğesinin özelliğini   <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> veri kaynağınızdaki bir alana bağlamak için Özellikler penceresindeki değer2 özelliğini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md)
