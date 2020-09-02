---
title: Excel çözümleri
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53351354a470eb5770f07b9afd527b81c4e587b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986075"
---
# <a name="excel-solutions"></a>Excel çözümleri
  Visual Studio, Microsoft Office Excel için belge düzeyi özelleştirmeler ve VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Excel 'i otomatikleştirmek, Excel özelliklerini genişletmek ve Excel Kullanıcı arabirimini (UI) özelleştirmek için bu çözümleri kullanabilirsiniz. Belge düzeyi özelleştirmeleri ve VSTO eklentileri arasındaki farklar hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Excel 'ı otomatikleştirin](#automating).

- [Excel için belge düzeyi özelleştirmesi geliştirin](#doclevel).

- [Excel IÇIN VSTO eklentileri geliştirin](#applevel).

- [Excel 'in Kullanıcı arabirimini özelleştirin](#UI).

## <a name="automate-excel"></a><a name="automating"></a> Excel 'i otomatikleştirin
 Excel nesne modeli, Excel 'i otomatik hale getirmek için kullanabileceğiniz birçok türü kullanıma sunar. Örneğin, program aracılığıyla grafik oluşturabilir, çalışma sayfalarını biçimlendirebilir ve Aralık ve hücre değerlerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

 Visual Studio 'da Excel çözümleri geliştirirken, çözümlerinizde *konak öğelerini* ve *konak denetimlerini* de kullanabilirsiniz. Bunlar, ve nesneleri gibi Excel nesne modelinde yaygın olarak kullanılan belirli nesneleri genişleten nesnelerdir <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> . Genişletilmiş nesneler, temel aldığı Excel nesneleri gibi davranır, ancak nesnelere ek olaylar ve veri bağlama özellikleri ekler. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Excel 'ı otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> Excel için belge düzeyi özelleştirmesi geliştirme
 Microsoft Office Excel için belge düzeyi özelleştirmesi, belirli bir çalışma kitabıyla ilişkili bir derlemeden oluşur. Derleme, genellikle kullanıcı arabirimini özelleştirerek ve Excel 'i otomatikleştirerek çalışma kitabını genişletir. Excel ile ilişkili olan VSTO eklentisinin aksine, bir özelleştirmeye uyguladığınız işlevsellik yalnızca ilişkili çalışma kitabı Excel 'de açık olduğunda kullanılabilir.

 Excel için belge düzeyi özelleştirme projesi oluşturmak için, Visual Studio 'nun **Yeni proje** Iletişim kutusundaki Excel çalışma kitabı veya Excel Şablonu proje şablonları ' nı kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Belge düzeyi özelleştirmelerinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Excel özelleştirme programlama modeli
 Excel için belge düzeyi projesi oluşturduğunuzda, Visual Studio çözümünüzün temeli olan birkaç sınıf oluşturur: `ThisWorkbook` ,, `Sheet1` `Sheet2` ve `Sheet3` . Bu sınıflar, çözümünüzle ilişkili çalışma kitabını ve çalışma sayfalarını temsil eder ve kodunuzu yazmak için bir başlangıç noktası sağlar.

 Bu oluşturulan sınıflar ve belge düzeyinde bir projede kullanabileceğiniz diğer özellikler hakkında daha fazla bilgi için bkz. [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> Excel için VSTO eklentileri geliştirme
 Microsoft Office Excel için VSTO eklentisi Excel tarafından yüklenen bir derlemeden oluşur. Derleme, genellikle kullanıcı arabirimini özelleştirerek ve Excel 'i otomatikleştirerek Excel 'i genişletir. Belirli bir çalışma kitabıyla ilişkili olan belge düzeyi özelleştirmesinden farklı olarak, bir VSTO eklentisi içinde uyguladığınız işlevsellik tek bir çalışma kitabıyla sınırlı değildir.

 Excel için VSTO eklentisi projesi oluşturmak için, Visual Studio 'nun **Yeni proje** Iletişim kutusundaki Excel çalışma kitabı veya Excel Şablonu proje şablonları ' nı kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

 VSTO eklentilerinin nasıl çalıştığı hakkında genel bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Excel eklentisi programlama modeli
 Excel VSTO eklentisi projesi oluşturduğunuzda, Visual Studio çözümünüzün temeli olan adlı bir sınıf oluşturur `ThisAddIn` . Bu sınıf, kodunuzun yazılması için bir başlangıç noktası sağlar ve ayrıca Excel 'in nesne modelini VSTO eklentinize gösterir.

 `ThisAddIn`BIR VSTO eklentisi içinde kullanabileceğiniz sınıf ve diğer Visual Studio özellikleri hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> Excel 'in Kullanıcı arabirimini özelleştirme
 Excel 'in Kullanıcı arabirimini özelleştirmenin birkaç farklı yolu vardır. Bazı seçenekler tüm proje türleri için kullanılabilir ve diğer seçenekler yalnızca VSTO eklentileri veya belge düzeyi özelleştirmeleri için kullanılabilir.

### <a name="options-for-all-project-types"></a>Tüm proje türleri için seçenekler
 Aşağıdaki tabloda hem belge düzeyi özelleştirmeleri hem de VSTO eklentileri için kullanılabilen özelleştirme seçenekleri listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Şeridi özelleştirin.|[Şerite genel bakış](../vsto/ribbon-overview.md)|
|Belge düzeyi özelleştirmesi veya VSTO eklentisinin açık çalışma kitabında, özelleştirilmiş çalışma kitabındaki çalışma sayfasına Windows Forms denetimleri veya genişletilmiş Excel denetimleri ekleyin.|[Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Belge düzeyi özelleştirmeleri seçenekleri
 Aşağıdaki tabloda yalnızca belge düzeyinde özelleştirmeler için kullanılabilen özelleştirme seçenekleri listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Çalışma kitabına bir eylemler bölmesi ekleyin.|[Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)<br /><br /> [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Çalışma sayfasına XML düğümlerine eşlenmiş genişletilmiş Aralık denetimleri ekleyin.|[Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>VSTO eklentileri seçenekleri
 Aşağıdaki tabloda yalnızca VSTO eklentileri için kullanılabilen özelleştirme seçenekleri listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>İlgili konular

| Başlık | Açıklama |
| - | - |
| [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md) | Excel nesne modeli tarafından sağlanan ana türlere genel bir bakış sağlar. |
| [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md) | Excel çözümlerinde kullanabileceğiniz Genişletilmiş nesneler (tarafından sağlanan) hakkında bilgiler sağlar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . |
| [Excel Çözümlerini Genelleştirme ve yerelleştirme](../vsto/globalization-and-localization-of-excel-solutions.md) | Windows için Ingilizce olmayan ayarlara sahip bilgisayarlarda çalıştırılacak Excel çözümlerine yönelik özel hususlar hakkında bilgiler içerir. |
| [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md) | Excel çalışma sayfalarına Windows Forms denetimleri nasıl ekleyebileceğiniz açıklanmaktadır. |
| [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Excel için temel bir belge düzeyi özelleştirmesi oluşturmayı gösterir. |
| [İzlenecek yol: Excel için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Excel için temel bir VSTO eklentisi oluşturmayı gösterir. |
| [İzlenecek yol: çalışma zamanında VSTO eklenti projesindeki çalışma sayfasına denetimler ekleme](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | <xref:Microsoft.Office.Tools.Excel.NamedRange>VSTO eklentisi kullanılarak çalışma zamanında bir Windows Forms düğme, a ve bir <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasına nasıl ekleneceğini gösterir. |
| [Ortak yazma ve eklentileri anlama](./understanding-coauthoring-and-addins.md) | Birlikte yazmayı karşılamak için çözümlerinizde yapmanız gerekebilecek ayarlamaları açıklar. |
| [Office geliştirmede Excel 2010](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Excel çözümleri geliştirme hakkında makalelerin ve başvuru belgelerinin bağlantılarını sağlar. Bunlar Visual Studio kullanarak Office geliştirmeye özgü değildir. |
