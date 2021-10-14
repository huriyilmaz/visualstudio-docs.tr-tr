---
title: 'Nasıl ekleyebilirsiniz: Şemaları çalışma sayfalarıyla eşleme Visual Studio'
description: Çalışma sayfası bir çalışma sayfasında açıkken xml Microsoft Office Excel çalışma sayfasına nasıl eşleyebilirsiniz Visual Studio.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0ce52089a8ae859f2ef41fb3f1a46df3f95d2c48
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969014"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Nasıl ekleyebilirsiniz: Şemaları çalışma sayfalarıyla eşleme Visual Studio
  Çalışma sayfası açıkken bir XML şemasını çalışma sayfasına eşleyebilirsiniz Visual Studio. Çalışma kitabı, Microsoft Office Excel dışında açık olduğunda kullanılan aynı Visual Studio. Bu Office proje, şemayı çalışma sayfasıyla eşlemeden önce veya sonra aynı nesneleri oluşturur ve Excel oluşturur.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Çok parçalı XML şemalarını çok parçalı xml Excel kullanılamaz.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Xml şemasını Excel çalışma Visual Studio

1. Excel çalışma kitabını veya şablon projesini Visual Studio.

2. Odağı tasarımcıya taşımak için çalışma sayfasına tıklayın.

3. Şeritte Geliştirici **sekmesine** tıklayın.

    > [!NOTE]
    > Geliştirici **sekmesi** görünmüyorsa, önce bunu göstermeniz gerekir. Daha fazla bilgi için [şeritteki Geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. XML **grubunda Kaynak'a** **tıklayın.**

     **XML Kaynağı** penceresi açılır.

5. XML Kaynağı **penceresinde XML** **kaynağına Haritalar.**

     **XML Haritalar** iletişim kutusu açılır.

6. XML dosyası **iletişim Haritalar** Ekle'ye **tıklayın.**

7. Şema dosyanıza göz atarak dosyayı seçin ve ardından Aç'a **tıklayın.**

8. **Tamam**'a tıklayın.

     Şema XML Kaynağı penceresinde **gösterilir.** Projeniz içinde, <xref:System.Data.DataSet> şemaya göre bir türü oluşturulur ve <xref:System.Windows.Forms.BindingSource> bir oluşturulur.

9. XML Kaynağı **penceresindeki öğeleri** çalışma sayfanızda karşılık gelen denetimlerin oluşturulacak yerlere sürükleyin.

     Yinelenen olmayan bir şema öğesini sürüklersanız, Office projesi otomatik olarak öğesine bağlı <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> bir denetim <xref:System.Windows.Forms.BindingSource> üretir.

     Yinelenen bir şema öğesini sürüklersanız, Office projesi otomatik olarak bir veri kaynağına <xref:Microsoft.Office.Tools.Excel.ListObject> bağlı olan bir denetim üretir. Daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde XML şemaları ve verileri.](../vsto/xml-schemas-and-data-in-document-level-customizations.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Belge düzeyinde özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
