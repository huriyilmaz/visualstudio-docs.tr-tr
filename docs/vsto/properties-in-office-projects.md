---
title: Office projelerinde özellikler
description: Office'daki Visual Studio için kullanılabilen özellikler hakkında bilgi Özellikler penceresi.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b26826769c86bc23064f9475df595a10abd47050
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155596"
---
# <a name="properties-in-office-projects"></a>Office projelerinde özellikler
  Visual Studio'daki projelerin Office birçok önemli Visual Studio. Bu özelliklere Özellikler **penceresinden erişilebilir.**

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Konak öğesi için ad alanı
 Visual C# **projelerinde** konak öğesi sınıfları (örneğin, , veya sınıfları) için ad alanını değiştirmek üzere Konak Öğesi için Ad `ThisAddIn` Alanı özelliğini `ThisWorkbook` `ThisDocument` kullanın. Bu özellik,  bir belge düzeyi projedeki belge düğümünü *(ExcelWorkbook1.xlsx* veya *WordDocument1.docx* gibi) veya bir VSTO Eklenti projesinde (Excel veya Word gibi) uygulama düğümünü **Çözüm Gezgini.**

 Visual C# Office projesini 7.000.000'e kadar tamamlarsınız. Kod dosyalarını doğrudan düzenlemek yerine ad **alanını değiştirmek** için Konak Öğesi için Ad Alanı özelliğini kullanmanız önerilir. Bu özelliği kullanırken, hem oluşturulan (gizli) kod dosyalarında hem de görünür kod dosyalarında ad alanı değiştirilir.

## <a name="cacheindocument"></a>CacheInDocument
 Önbellek tasarımcısında bir örneği  seçerek belge düzeyi projelerin Özellikler penceresinde **CacheInDocument** <xref:System.Data.DataSet> Visual Studio görünür. Yalnızca genel üyeler önbelleğe alınarak; Bir **önbelleğe almak için** Değiştiriciler **özelliğinin Genel** olarak ayarlanmış olduğundan emin <xref:System.Data.DataSet> olmak.

 Bu özellik bir Boole değeri alır:

- Belgede veri kümesi önbelleğe eklemek için **true'yi** seçin.

- Veri  kümesinde belgede önbelleğe alınmak istemiyorsanız false seçeneğini kullanın.

  Verileri önbelleğe alma hakkında daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler.](../vsto/cached-data-in-document-level-customizations.md)

## <a name="value2"></a>Değer2
 **Value2 özelliği** yalnızca çalışma kitabı Excel şablon projelerinde kullanılabilir. Çalışma sayfası tasarımcısında bir denetim seçerek Özellikler **penceresindeki** **Databindings** <xref:Microsoft.Office.Tools.Excel.NamedRange> özellik düğümü altında görünür.

 özelliğini veri kaynağınız **içinde** bir alana bağlamak için Özellikler **penceresindeki Value2** <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğini <xref:Microsoft.Office.Tools.Excel.NamedRange> kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [Office projelerinde olaylar](../vsto/events-in-office-projects.md)
