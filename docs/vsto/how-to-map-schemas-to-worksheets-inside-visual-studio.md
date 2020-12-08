---
title: 'Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme'
description: Visual Studio 'da çalışma sayfası açıkken bir XML şemasını Microsoft Office Excel çalışma sayfasına nasıl eşleyeceğinizi öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a7e1a06e644536ce9ce881d9b9f1dc23aae03f1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848215"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme
  Çalışma sayfası Visual Studio 'da açıkken bir XML şemasını çalışma sayfasıyla eşleyebilirsiniz. Çalışma kitabı Visual Studio dışında açıldığında kullandığınız Microsoft Office Excel araçlarını kullanırsınız. Office projesi, Excel çözümünüzü oluşturmadan önce veya sonra, şemayı çalışma sayfasıyla eşleştirdiğinizde aynı nesneleri oluşturur.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Excel çözümlerinde çok parçalı XML şemaları kullanamazsınız.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Visual Studio 'da bir Excel çalışma sayfasıyla bir XML şemasını eşlemek için

1. Visual Studio içinde Excel çalışma kitabı veya şablon projesini açın.

2. Odağı tasarımcıya taşımak için çalışma sayfasına tıklayın.

3. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. **XML** grubunda **kaynak**' a tıklayın.

     **XML kaynağı** penceresi açılır.

5. **XML kaynağı** penceresinde, **XML eşlemeleri**' ne tıklayın.

     **XML eşlemeleri** iletişim kutusu açılır.

6. **XML eşlemeleri** Iletişim kutusunda **Ekle**' ye tıklayın.

7. Şema dosyanıza gidin, dosyayı seçin ve ardından **Aç**' a tıklayın.

8. **Tamam** düğmesine tıklayın.

     Şema, **XML kaynak** penceresinde temsil edilir. Projenizde, <xref:System.Data.DataSet> bir türü şema temel alınarak oluşturulur ve <xref:System.Windows.Forms.BindingSource> oluşturulur.

9. Öğeleri **XML kaynak** penceresinden çalışma sayfanızda, ilgili denetimlerin oluşturulmasını istediğiniz yerlere sürükleyin.

     Tekrarlamayan bir şema öğesini sürüklerseniz Office projesi <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , otomatik olarak öğesine bağlanan bir denetim oluşturur <xref:System.Windows.Forms.BindingSource> .

     Yinelenen bir şema öğesini sürüklerseniz, Office projesi <xref:Microsoft.Office.Tools.Excel.ListObject> bir veri kaynağına otomatik olarak bağlanmamış bir denetim oluşturur. Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Belge düzeyi özelleştirmelerde XML şemaları ve verileri](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
