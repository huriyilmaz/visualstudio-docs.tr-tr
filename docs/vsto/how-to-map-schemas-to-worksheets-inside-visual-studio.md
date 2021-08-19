---
title: 'Nasıl ekleyebilirsiniz: Şemaları çalışma sayfalarıyla eşleme Visual Studio'
description: Çalışma sayfası bir çalışma sayfasında açıkken xml Microsoft Office Excel çalışma sayfasına nasıl eşleyebilirsiniz Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
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
ms.openlocfilehash: a2d82c4b55fbc037843f80fef113ba2f7a3e1502
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100016"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Nasıl ekleyebilirsiniz: Şemaları çalışma sayfalarıyla eşleme Visual Studio
  Bir XML şemasını çalışma sayfası açıkken çalışma sayfasına eşleyebilirsiniz Visual Studio. Çalışma kitabı, Microsoft Office Excel dışında açık olduğunda kullanılan aynı Visual Studio. Bu Office proje, şemayı çalışma sayfasıyla eşledikten önce veya sonra aynı nesneleri oluşturur ve Excel oluşturur.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Çok parçalı XML şemalarını çok parçalı xml Excel kullanılamaz.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Xml şemasını Excel çalışma Visual Studio

1. Çalışma kitabı Excel şablon projesini Visual Studio.

2. Odağı tasarımcıya taşımak için çalışma sayfasına tıklayın.

3. Şeritte Geliştirici **sekmesine** tıklayın.

    > [!NOTE]
    > Geliştirici **sekmesi** görünmüyorsa, önce bunu göstermeniz gerekir. Daha fazla bilgi için [şeritteki Geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. XML **grubunda Kaynak'a** **tıklayın.**

     **XML Kaynağı** penceresi açılır.

5. XML Kaynağı **penceresinde XML** **kaynağı'Haritalar.**

     **XML Haritalar** iletişim kutusu açılır.

6. XML dosyası **iletişim Haritalar** Ekle'ye **tıklayın.**

7. Şema dosyanıza göz atarak dosyayı seçin ve ardından Aç'a **tıklayın.**

8. **Tamam**'a tıklayın.

     Şema XML Kaynağı penceresinde **gösterilir.** Projeniz içinde, <xref:System.Data.DataSet> şemaya göre bir türü oluşturulur ve <xref:System.Windows.Forms.BindingSource> bir oluşturulur.

9. XML Kaynağı **penceresindeki öğeleri** çalışma sayfanızda karşılık gelen denetimlerin oluşturulacak yerlere sürükleyin.

     Yinelenen olmayan bir şema öğesini sürüklersanız, Office projesi otomatik olarak öğesine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> bağlı bir denetim <xref:System.Windows.Forms.BindingSource> üretir.

     Yinelenen bir şema öğesini sürüklersanız, Office projesi otomatik olarak bir veri kaynağına <xref:Microsoft.Office.Tools.Excel.ListObject> bağlı olan bir denetim üretir. Daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde XML şemaları ve verileri.](../vsto/xml-schemas-and-data-in-document-level-customizations.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Belge düzeyinde özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
