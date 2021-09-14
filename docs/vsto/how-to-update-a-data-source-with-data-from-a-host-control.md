---
title: 'Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme'
description: Bir konak denetimine veri kaynağı bağlamayı ve veri kaynağını denetimde verilerde yapılan değişikliklerle güncelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d389e4f3e2b8bdf4348508760b6894c0eeaf1ec7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725548"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme
  Bir konak denetimi bir veri kaynağına bağlanabilir ve veri kaynağını denetimde verilerde yapılan değişikliklerle güncelleştirebilirsiniz. Bu süreçte iki ana adım vardır:

1. Bellek içinde veri kaynağını denetimde değiştirilen verilerle güncelleştirin. Genellikle, bellek içinde veri kaynağı bir <xref:System.Data.DataSet> , veya başka bir veri <xref:System.Data.DataTable> nesnesidir.

2. Veritabanını bellek içinde veri kaynağında değiştirilen verilerle güncelleştirin. Bu yalnızca veri kaynağı SQL Server veya Access veritabanı gibi bir arka uç veritabanına Microsoft Office geçerlidir.

   Konak denetimleri ve veri bağlama hakkında daha fazla bilgi için bkz. Konak [öğelerine](../vsto/host-items-and-host-controls-overview.md) ve konak denetimlerine genel bakış ve Office [bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Bellek içinde veri kaynağını güncelleştirme
 Varsayılan olarak, basit veri bağlamayı etkinleştiren konak denetimleri (Word belgesinde içerik denetimleri veya Excel çalışma sayfasındaki adlandırılmış aralık denetimi gibi) veri değişikliklerini bellek içinde veri kaynağına kaydetmez. Başka bir ifadeyle, son kullanıcı bir konak denetiminde bir değeri değiştirir ve ardından denetimden uzaklara gidilirse, denetimde yeni değer otomatik olarak veri kaynağına kaydedlanmaz.

 Verileri veri kaynağına kaydetmek için, çalışma zamanında belirli bir etkinliğe yanıt olarak veri kaynağını güncelleştiren kod yazabilir veya denetimi, denetimde değer değişirken veri kaynağını otomatik olarak güncelleştiracak şekilde yapılandırabilirsiniz.

 Bellek içinde veri <xref:Microsoft.Office.Tools.Excel.ListObject> kaynağında yapılan değişiklikleri kaydetmeniz gerek değildir. Bir denetimi verilere bağlayabilirsiniz. Denetim, ek kod gerektirmeden değişiklikleri bellek içinde <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> veri kaynağına otomatik olarak kaydeder.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Bellek içinde veri kaynağını çalışma zamanında güncelleştirmek için

- Denetimi <xref:System.Windows.Forms.Binding.WriteValue%2A> veri <xref:System.Windows.Forms.Binding> kaynağına bağlayan nesnesinin yöntemini çağırma.

     Aşağıdaki örnek, çalışma sayfasındaki bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimde Excel yapılan değişiklikleri veri kaynağına kaydeder. Bu örnekte, bir veri kaynağında <xref:Microsoft.Office.Tools.Excel.NamedRange> bir alana bağlı olan `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğiyle adlı bir denetimin olduğu varsaymaktadır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet1":::

### <a name="automatically-update-the-in-memory-data-source"></a>Bellek içinde veri kaynağını otomatik olarak güncelleştirme
 Ayrıca, bellek içinde veri kaynağını otomatik olarak güncelleştirmesi için bir denetim yapılandırabilirsiniz. Belge düzeyindeki bir projede, bunu kod veya tasarımcı kullanarak yapabiliriz. Bir VSTO projesinde kod kullan gerekir.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Kod kullanarak bellek içinde veri kaynağını otomatik olarak güncelleştirmek için bir denetim ayarlamak için

1. Sistem'i kullanın. Windows. Denetimi veri kaynağına bağlayan nesnenin Forms.DataSourceUpdateMode.OnPropertyChanged <xref:System.Windows.Forms.Binding> modu. Veri kaynağını güncelleştirmek için iki seçenek vardır:

   - Denetim doğrulandıktan sonra veri kaynağını güncelleştirmek için bu özelliği Sistem olarak ayarlayın. Windows. Forms.DataSourceUpdateMode.OnValidation.

   - Denetimin veriye bağlı özelliğinin değeri değişirken veri kaynağını güncelleştirmek için bu özelliği Sistem olarak ayarlayın. Windows. Forms.DataSourceUpdateMode.OnPropertyChanged.

     > [!NOTE]
     > Sistem. Windows. Forms.DataSourceUpdateMode.OnPropertyChanged seçeneği Word konak denetimleri için geçerli değildir çünkü Word belge değişikliği veya denetim değişikliği bildirimleri sunmaz. Ancak, bu seçenek Word belge Windows Formlar denetimleri için kullanılabilir.

     Aşağıdaki örnek, denetimde <xref:Microsoft.Office.Tools.Excel.NamedRange> değer değişirken veri kaynağını otomatik olarak güncelleştirmek için bir denetim yapılandırıyor. Bu örnekte, bir veri kaynağında <xref:Microsoft.Office.Tools.Excel.NamedRange> bir alana bağlı olan `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğiyle adlı bir denetimin olduğu varsaymaktadır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet19":::

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Tasarımcıyı kullanarak bellek içinde veri kaynağını otomatik olarak güncelleştirmek için bir denetim ayarlamak için

1. Bu Visual Studio Word belgesini veya Excel çalışma kitabını tasarımcıda açın.

2. Veri kaynağını otomatik olarak güncelleştirmek istediğiniz denetime tıklayın.

3. Özellikler **penceresinde** **(DataBindings) özelliğini** genişletin.

4. **(Gelişmiş) özelliğinin** yanındaki üç nokta düğmesine tıklayın (![VisualStudioEllipsesButton ekran görüntüsü).](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton ekran görüntüsü")

5. Biçimlendirme **ve Gelişmiş Bağlama iletişim** kutusunda  Veri Kaynağı Güncelleştirme Modu açılan listesine tıklayın ve aşağıdaki değerlerden birini seçin:

    - Denetim doğrulandıktan sonra veri kaynağını güncelleştirmek için **OnValidation'ı seçin.**

    - Denetimin veriye bağlı özelliğinin değeri değişirken veri kaynağını güncelleştirmek için **OnPropertyChanged öğesini seçin.**

        > [!NOTE]
        > Word belge değiştirme veya denetim değişikliği bildirimleri sunmaysa da **OnPropertyChanged** seçeneği Word konak denetimleri için geçerli değildir. Ancak, bu seçenek Word belge Windows Formlar denetimleri için kullanılabilir.

6. Biçimlendirme **ve Gelişmiş Bağlama iletişim** kutusunu kapatın.

## <a name="update-the-database"></a>Veritabanını güncelleştirme
 Bellek içinde veri kaynağı bir veritabanıyla ilişkili ise, veritabanını veri kaynağında yapılan değişikliklerle güncelleştirmeniz gerekir. Veritabanını güncelleştirme hakkında daha fazla bilgi için [bkz. Verileri veritabanına](../data-tools/save-data-back-to-the-database.md)  geri kaydetme ve [TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) kullanarak verileri güncelleştirme.

### <a name="to-update-the-database"></a>Veritabanını güncellemek için

1. denetimi <xref:System.Windows.Forms.BindingSource.EndEdit%2A> için yöntemini <xref:System.Windows.Forms.BindingSource> çağırma.

     <xref:System.Windows.Forms.BindingSource>, tasarım zamanında bir belgeye veya çalışma kitabına veriye bağlı denetim eklerken otomatik olarak oluşturulur. <xref:System.Windows.Forms.BindingSource>, denetimi projenizin türüne sahip veri kümesine bağlar. Daha fazla bilgi için bkz. [BindingSource bileşenine genel bakış.](/dotnet/framework/winforms/controls/bindingsource-component-overview)

     Aşağıdaki kod örneği projenizin adlı bir içerdiğini <xref:System.Windows.Forms.BindingSource> `customersBindingSource` varsayıyor.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet20":::

2. Projeniz `Update` içinde oluşturulan TableAdapter yöntemini çağırma.

     TableAdapter, tasarım zamanında bir belgeye veya çalışma kitabına veriye bağlı denetim eklerken otomatik olarak oluşturulur. TableAdapter, projenizin türü doğru olan veri kümesini veritabanına bağlar. Daha fazla bilgi için bkz. [TableAdapter'a genel bakış.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Aşağıdaki kod örneğinde, Northwind veritabanındaki Customers tablosuyla bağlantınız olduğu ve projenizin adlı bir TableAdapter ve adlı bir türe sahip veri kümesi içerdiği `customersTableAdapter` `northwindDataSet` varsayılmaktadır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet21":::

## <a name="see-also"></a>Ayrıca bkz.
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Nasıl kullanılır: Çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Nasıl kullanılır: Çalışma sayfalarını veritabanındaki verilerle doldurmak](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri hizmet verileriyle doldurmak](../vsto/how-to-populate-documents-with-data-from-services.md)
