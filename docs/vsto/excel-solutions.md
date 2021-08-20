---
title: Excel çözümleri
description: Proje şablonlarını kullanarak kullanıcı arabirimini (UI) Excel, Excel özelliklerini genişletebileceğinizi ve Excel özelleştirebileceğinizi öğrenin
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8bd3ab0ac5705a5af994ef51e1edde9d250124e2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122923"
---
# <a name="excel-solutions"></a>Excel çözümleri
  Visual Studio, belge düzeyinde özelleştirmeler oluşturmak ve VSTO için VSTO proje şablonları Microsoft Office Excel. Bu çözümleri kullanarak Excel, Excel özelliklerini genişletebilir ve Excel arabirimini (UI) özelleştirebilirsiniz. Belge düzeyi özelleştirmeler ve ek eklentiler arasındaki farklar hakkında daha fazla VSTO için bkz. [Office çözüm geliştirmeye genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [otomatikleştirme Excel.](#automating)

- Excel için [belge düzeyinde özelleştirmeler geliştirin.](#doclevel)

- [VSTO için yeni eklentiler Excel.](#applevel)

- [uygulamanın kullanıcı arabirimini Excel.](#UI)

## <a name="automate-excel"></a><a name="automating"></a>Otomatikleştirme Excel
 Bu Excel modeli, veri türlerini otomatikleştirmek için kullanabileceğiniz birçok Excel. Örneğin, program aracılığıyla grafikler oluşturabilir, çalışma sayfalarını biçimlendirebilirsiniz ve aralıkların ve hücrelerin değerlerini ayarlayabilirsiniz. Daha fazla bilgi için [bkz. Excel modeline genel bakış.](../vsto/excel-object-model-overview.md)

 Bu Excel geliştirme Visual Studio, çözümleriniz içinde konak *öğelerini ve* *konak denetimlerini* de kullanabilirsiniz. Bunlar, ve nesneleri gibi bir nesne Excel yaygın olarak kullanılan belirli nesneleri genişleten <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> nesnelerdir. Genişletilmiş nesneler, temel alınan Excel nesneleri gibi davranır, ancak nesnelere ek olaylar ve veri bağlama özellikleri ekler. Daha fazla bilgi için [bkz. Genişletilmiş Excel kullanarak otomatikleştirme.](../vsto/automating-excel-by-using-extended-objects.md)

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a>Excel için belge düzeyinde özelleştirmeler geliştirme
 Belirli bir çalışma kitabıyla Microsoft Office Excel bir derlemeden oluşan bir belge düzeyi özelleştirmesi. Derleme genellikle kullanıcı arabirimini özelleştirerek ve kullanıcı arabirimini otomatiklaştırarak çalışma kitabını Excel. Bir VSTO eklentinin aksine, Excel bir özelleştirmede uygulayan işlevsellik yalnızca ilişkili çalışma kitabı Excel.

 Excel için belge düzeyi özelleştirme projesi oluşturmak üzere Excel yeni çalışma kitabı veya Excel yeni çalışma  kitabı iletişim kutusundaki Project şablon proje şablonlarını Visual Studio. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

 Belge düzeyinde özelleştirmelerin nasıl iş olduğu hakkında daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerin mimarisi.](../vsto/architecture-of-document-level-customizations.md)

### <a name="excel-customization-programming-model"></a>Excel özelleştirme programlama modeli
 Excel için belge düzeyi Visual Studio, çözümünüz için temel olan birkaç sınıf üretir: `ThisWorkbook` , , `Sheet1` ve `Sheet2` `Sheet3` . Bu sınıflar çözümünüzle ilişkili çalışma kitabını ve çalışma sayfalarını temsil ediyor ve kodunuzu yazmak için bir başlangıç noktası sunuyor.

 Bu oluşturulan sınıflar ve belge düzeyi projesinde kullanabileceğiniz diğer özellikler hakkında daha fazla bilgi için bkz. [Program belge düzeyi özelleştirmeleri.](../vsto/programming-document-level-customizations.md)

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a>VSTO için ek eklentiler Excel
 VSTO için bir Microsoft Office Excel, bir derleme tarafından yüklenen bir derlemeden Excel. Derleme genellikle kullanıcı Excel özelleştirerek ve kullanıcı arabirimini otomatik Excel. Belirli bir çalışma kitabıyla ilişkilendirilmiş olan belge düzeyi özelleştirmeden farklı olarak, eklentide VSTO işlevi tek bir çalışma kitabıyla sınırlı değildir.

 Excel için VSTO Eklenti projesi oluşturmak üzere, Excel'nin Yeni Project iletişim kutusundaki Excel çalışma kitabını veya **Excel** şablon proje şablonlarını Visual Studio. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

 Eklentilerin nasıl VSTO genel bilgi için [bkz. VSTO Eklentilerinin Mimarisi.](../vsto/architecture-of-vsto-add-ins.md)

### <a name="excel-add-in-programming-model"></a>Excel Eklenti programlama modeli
 Excel VSTO Eklenti projesini Visual Studio çözüm Visual Studio adlı `ThisAddIn` bir sınıf oluşturulur. Bu sınıf kodunuzu yazmak için bir başlangıç noktası sağlar ve aynı zamanda uygulamanın nesne modelini Excel eklentinize VSTO gösterir.

 Bir eklentide kullanabileceğiniz sınıf ve diğer Visual Studio özellikleri hakkında daha `ThisAddIn` fazla bilgi VSTO için bkz. Program VSTO [Eklentileri.](../vsto/programming-vsto-add-ins.md)

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a>Uygulamanın kullanıcı arabirimini Excel
 Uygulamanın kullanıcı arabirimini özelleştirmenin birkaç farklı Excel. Bazı seçenekler tüm proje türleri tarafından kullanılabilir ve diğer seçenekler yalnızca eklentilerde VSTO belge düzeyinde özelleştirmeler için kullanılabilir.

### <a name="options-for-all-project-types"></a>Tüm proje türleri için seçenekler
 Aşağıdaki tabloda hem belge düzeyi özelleştirmeler hem de eklentiler için kullanılabilen VSTO seçenekleri listelemektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Şeridi özelleştirin.|[Şerit'e genel bakış](../vsto/ribbon-overview.md)|
|Belge Windows özelleştirmesi için özelleştirilmiş çalışma kitabındaki bir çalışma sayfasına veya VSTO Eklenti için açık bir çalışma kitabına form formları Excel denetimleri veya genişletilmiş VSTO ekleyin.|[Nasıl kullanılır: Windows form denetimleri Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Nasıl ekleyebilirsiniz: Çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Nasıl ekleyebilirsiniz: Çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Belge düzeyi özelleştirme seçenekleri
 Aşağıdaki tabloda, yalnızca belge düzeyinde özelleştirmeler için kullanılabilen özelleştirme seçenekleri listelemektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Çalışma kitabına bir eylemler bölmesi ekleyin.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)<br /><br /> [Nasıl kullanılır: Word belgelerine veya çalışma kitaplarını Excel bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Çalışma sayfasına XML düğümleriyle eşlenen genişletilmiş aralık denetimleri ekleyin.|[Nasıl yapılır: Çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Eklenti VSTO seçenekleri
 Aşağıdaki tabloda, yalnızca eklentilerde kullanılabilen özelleştirme VSTO listele.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [Excel modeline genel bakış](../vsto/excel-object-model-overview.md) | Veri nesnesi modeli tarafından sağlanan ana türlere genel Excel sağlar. |
| [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md) | Farklı çözümlerde kullanabileceğiniz genişletilmiş nesneler (tarafından [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sağlanır) hakkında Excel sağlar. |
| [Excel çözümlerinin genelleştirilmesi ve yerelleştirilmesi](../vsto/globalization-and-localization-of-excel-solutions.md) | İngilizce olmayan ayarlara sahip bilgisayarlarda Excel çözümlerle ilgili önemli noktalar hakkında bilgi Windows. |
| [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md) | Çalışma sayfalarına Formlar Windows nasıl Excel açıklar. |
| [Adım adım kılavuz: Belge düzeyi için ilk belge düzeyi özelleştirmenizi Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Uygulama için temel bir belge düzeyi özelleştirmesi oluşturma Excel. |
| [Adım adım kılavuz: VSTO için İlk Eklentinizi Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Uygulama için temel bir Eklenti VSTO oluşturma Excel. |
| [Adım adım kılavuz: Eklenti projesinde çalışma zamanında çalışma VSTO çalışma sayfasına denetimler ekleme](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Çalışma zamanında çalışma zamanında Windows Formlar düğmesi, , ve bir ekleme VSTO <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> gösterir. |
| [Ortak yazma ve Eklentileri anlama](./understanding-coauthoring-and-addins.md) | Birlikte kimlik doğrulamasına uyum sağlayacak şekilde çözümleriniz için gerekli ayarlamaları açıklar. |
| [Excel geliştirmede 2010 Office geliştirme](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Uygulama çözümleri geliştirmeyle ilgili makalelere ve başvuru belgelerine Excel sağlar. Bunlar, özel bir Office geliştirme Visual Studio. |
