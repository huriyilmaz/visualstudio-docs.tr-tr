---
title: 'Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme'
description: çalışma sayfası Visual Studio açıkken bir XML şemasını Microsoft Office Excel çalışma sayfasına nasıl eşleyeceğinizi öğrenin.
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
ms.openlocfilehash: 9fb7a8a2a3ae7a8b0f7f3898fdf5b13b105f58886f1d5586f98ad625cbaa5d0a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424131"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme
  Çalışma sayfası Visual Studio açıkken bir XML şemasını çalışma sayfasıyla eşleyebilirsiniz. çalışma kitabı Visual Studio dışında açtığınızda kullandığınız Microsoft Office Excel araçlarını kullanırsınız. Office projesi, şemayı, Excel çözümünüzü oluşturmadan önce veya sonra çalışma sayfasıyla eşleştirdiğinizde aynı nesneleri oluşturur.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Excel çözümlerinde çok parçalı XML şemaları kullanamazsınız.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>bir XML şemasını bir Excel çalışma sayfasıyla eşlemek için Visual Studio

1. Excel çalışma kitabını veya şablon projesini Visual Studio içinde açın.

2. Odağı tasarımcıya taşımak için çalışma sayfasına tıklayın.

3. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. **XML** grubunda **kaynak**' a tıklayın.

     **XML kaynağı** penceresi açılır.

5. **xml kaynağı** penceresinde, **xml Haritalar**' ye tıklayın.

     **XML Haritalar** iletişim kutusu açılır.

6. **XML Haritalar** iletişim kutusunda **ekle**' ye tıklayın.

7. Şema dosyanıza gidin, dosyayı seçin ve ardından **Aç**' a tıklayın.

8. **Tamam**'a tıklayın.

     Şema, **XML kaynak** penceresinde temsil edilir. Projenizde, <xref:System.Data.DataSet> bir türü şema temel alınarak oluşturulur ve <xref:System.Windows.Forms.BindingSource> oluşturulur.

9. Öğeleri **XML kaynak** penceresinden çalışma sayfanızda, ilgili denetimlerin oluşturulmasını istediğiniz yerlere sürükleyin.

     tekrarlamayan bir şema öğesini sürüklerseniz Office projesi <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , otomatik olarak öğesine bağlanan bir denetim oluşturur <xref:System.Windows.Forms.BindingSource> .

     yinelenen bir şema öğesini sürüklerseniz, Office projesi <xref:Microsoft.Office.Tools.Excel.ListObject> bir veri kaynağına otomatik olarak bağlanmamış bir denetim oluşturur. Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
