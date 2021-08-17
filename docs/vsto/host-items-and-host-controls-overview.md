---
title: Konak öğeleri ve konak denetimlerine genel bakış
description: konak öğeleri ve konak denetimleri, Office çözümleri için programlama modeli sağlamaya yardımcı olan türler olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ec4c41eca423bd75ee8ef490c3053c43d2c02737
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038025"
---
# <a name="host-items-and-host-controls-overview"></a>Konak öğeleri ve konak denetimlerine genel bakış
  konak öğeleri ve konak denetimleri, Visual Studio Office geliştirme araçları kullanılarak oluşturulan Office çözümleri için programlama modeli sağlamaya yardımcı olan türlerdir. ana bilgisayar öğeleri ve konak denetimleri, Windows Forms denetimleri gibi yönetilen nesnelerle etkileşim kurma gibi Microsoft Office Word ve Microsoft Office Excel nesne modelleriyle etkileşim kurmayı kolaylaştırır.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="host-items"></a>Konak öğeleri
 konak öğeleri, Office projelerinde nesne modeli hiyerarşilerinin en üstünde yer alan türlerdir. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word ve Excel çözümleri için aşağıdaki konak öğelerini tanımlar:

- <xref:Microsoft.Office.Tools.Word.Document>

- <xref:Microsoft.Office.Tools.Excel.Workbook>

- <xref:Microsoft.Office.Tools.Excel.Worksheet>

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  bu türlerin her biri, *yerel bir Office nesnesi* olarak adlandırılan sözcük veya Excel nesne modelinde yerel olarak var olan bir nesneyi genişletir. Örneğin, <xref:Microsoft.Office.Tools.Word.Document> konak öğesi <xref:Microsoft.Office.Interop.Word.Document> , Word için birincil birlikte çalışma derlemesinde tanımlanan nesneyi genişletir.

  ana bilgisayar öğeleri genellikle karşılık gelen Office nesneleriyle aynı temel işlevlere sahiptir, ancak aşağıdaki özelliklerle geliştirilmiştir:

- konak denetimleri ve Windows Forms denetimleri dahil olmak üzere yönetilen denetimleri barındırma özelliği.

- Daha zengin olay modelleri. yerel sözcük ve Excel nesne modelleriyle bazı belge, çalışma kitabı ve çalışma sayfası olayları yalnızca uygulama düzeyinde oluşturulur. Konak öğeleri, bu olayları belge düzeyinde sağlar, böylece belirli bir belge için olayları işlemek daha kolay olur.

### <a name="understand-host-items-in-document-level-projects"></a>Belge düzeyi projelerdeki konak öğelerini anlama
 Belge düzeyi projelerinde, konak öğeleri kodunuz için bir giriş noktası sağlar ve çözümünüzü geliştirmenize yardımcı olan tasarımcılara sahiptir.

 <xref:Microsoft.Office.Tools.Word.Document>ve <xref:Microsoft.Office.Tools.Excel.Worksheet> ana bilgisayar öğelerinde, Windows Forms tasarımcısı gibi belge veya çalışma sayfasının görsel temsili olan ilişkili tasarımcılar vardır. bu tasarımcıyı kullanarak belge veya çalışma sayfasının içeriğini doğrudan Word veya Excel içinde değiştirebilir ve denetimleri tasarım yüzeyine sürükleyebilirsiniz. Daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md) ve [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook>Konak öğesi, Kullanıcı arabirimine sahip denetimler için kapsayıcı görevi yapmaz. Bunun yerine, bu konak öğesi için tasarımcı, bir bileşeni gibi bir bileşeni tasarım yüzeyine sürüklemenize olanak tanıyan bir bileşen tepsisi işlevi görür <xref:System.Data.DataSet> . Daha fazla bilgi için bkz. [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).

 Konak öğeleri belge düzeyi projelerde program aracılığıyla oluşturulamaz. bunun yerine, `ThisDocument` `ThisWorkbook` `Sheet` tasarım zamanında Visual Studio otomatik olarak bir şekilde oluşturduğu, veya *n* sınıflarını kullanın. Oluşturulan bu sınıflar konak öğelerinden türetilir ve kodunuz için bir giriş noktası sağlar. Daha fazla bilgi için bkz. [konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="understand-host-items-in-vsto-add-in-projects"></a>VSTO eklentisi projelerinde konak öğelerini anlayın
 bir VSTO eklentisi oluşturduğunuzda, varsayılan olarak herhangi bir konak öğesine erişiminiz olmaz. ancak, <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> çalışma zamanında Word ve Excel VSTO eklentilerinde öğeleri oluşturabilir, ve barındırabilirsiniz.

 Bir konak öğesi oluşturduktan sonra belgelere denetim ekleme gibi görevleri gerçekleştirebilirsiniz. daha fazla bilgi için bkz. [çalışma zamanında VSTO eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="host-controls"></a>Konak denetimleri
 konak denetimleri, ve gibi nesneleri Excel nesne modellerinde çeşitli kullanıcı arabirimi (uı) nesnelerini genişletir `Microsoft.Office.Interop.Word.ContentControl` <xref:Microsoft.Office.Interop.Excel.Range> .

 aşağıdaki konak denetimleri Excel projeleri için kullanılabilir:

- [Grafik denetimi](../vsto/chart-control.md)

- [ListObject denetimi](../vsto/listobject-control.md)

- [NamedRange denetimi](../vsto/namedrange-control.md)

- [XmlMappedRange denetimi](../vsto/xmlmappedrange-control.md)

  Aşağıdaki konak denetimleri Word projeleri için kullanılabilir:

- [Yer işareti denetimi](../vsto/bookmark-control.md)

- [İçerik denetimleri](../vsto/content-controls.md)

- [XMLNode denetimi](../vsto/xmlnode-control.md)

- [XMLNodes denetimi](../vsto/xmlnodes-control.md)

  Office belgelerine eklenen konak denetimleri, yerel Office nesneleri gibi davranır; Ancak, ana bilgisayar denetimleri, olaylar ve veri bağlama özellikleri dahil olmak üzere ek işlevlere sahiptir. örneğin, Excel bir yerel nesnenin olaylarını yakalamak istediğinizde <xref:Microsoft.Office.Interop.Excel.Range> , önce çalışma sayfasının değişiklik olayını işlemeniz gerekir. Ardından, değişikliğin içinde oluşup oluşmadığını belirlemelisiniz <xref:Microsoft.Office.Interop.Excel.Range> . Buna karşılık, <xref:Microsoft.Office.Tools.Excel.NamedRange> konak denetiminin <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> doğrudan işleyebilmeniz için bir olayı vardır.

  konak öğesi ve konak denetimleri arasındaki ilişki, bir Windows formu ve Windows Forms denetimleri arasındaki ilişkiye benzer. bir Windows Form üzerinde metin kutusu denetimi yerleştirdiğiniz gibi, bir <xref:Microsoft.Office.Tools.Excel.NamedRange> konak öğesine bir denetim yerleştirebilirsiniz <xref:Microsoft.Office.Tools.Excel.Worksheet> . Aşağıdaki çizimde konak öğeleri ve konak denetimleri arasındaki ilişki gösterilmektedir.

  ![Konak öğeleri ve konak denetimleri arasındaki ilişki](../vsto/media/hostitemscontrols.png "Konak öğeleri ve konak denetimleri arasındaki ilişki")

  Office çözümlerinizde Windows Forms denetimleri, doğrudan Word ve Excel belge yüzeyine ekleyerek de kullanabilirsiniz. daha fazla bilgi için bkz. [Office belgelere genel bakış Windows Forms denetimleri](../vsto/windows-forms-controls-on-office-documents-overview.md).

> [!NOTE]
> bir Word alt belgesinde konak denetimleri veya Windows Forms denetimleri ekleme desteklenmez.

### <a name="add-host-controls-to-your-documents"></a>Belgelerinize konak denetimleri ekleyin
 belge düzeyi projelerinde, Word belgelerinize Excel veya tasarım zamanında çalışma sayfalarına aşağıdaki yollarla konak denetimleri ekleyebilirsiniz:

- Belgenize, bir yerel nesne ekleyeceğiniz şekilde tasarım zamanında konak denetimleri ekleyin.

- **Araç kutusundan** , ana bilgisayar denetimlerini belgelerinize ve çalışma sayfalarına sürükleyin. Excel konak denetimleri, Excel projelerindeki **Excel denetimleri** sekmesinde kullanılabilir ve word konak denetimleri word projeleri ' nde word **denetimleri** sekmesinde kullanılabilir.

- Konak denetimlerini, **veri kaynakları** penceresinden belge ve çalışma sayfalarına sürükleyin. Bu, verilere zaten bağlanan denetimler eklemenize olanak sağlar. daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

  belge düzeyi ve VSTO eklentisi projelerinde, çalışma zamanında belgelere bazı konak denetimleri de ekleyebilirsiniz. daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Belgelere konak denetimleri ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)

- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

- [Nasıl yapılır: Word belgelerine Içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)

### <a name="name-host-controls"></a>Konak denetimlerini Adlandır
 **Araç kutusundan** bir konak denetimini belgenize sürüklediğinizde Denetim, sonunda artımlı bir sayı ile denetim türü kullanılarak otomatik olarak adlandırılır. Örneğin, yer işaretleri **Bookmark1**, **bookmark2** vb. olarak adlandırılır. denetimi eklemek için Word 'ün veya Excel yerel işlevlerini kullanırsanız, oluşturduğunuz zamanda buna özel bir ad verebilirsiniz. Ayrıca, **Özellikler** penceresinde **ad** özelliğinin değerini değiştirerek denetimlerinizi yeniden adlandırabilirsiniz.

> [!NOTE]
> Konak denetimlerini adlandırmak için ayrılmış sözcükler kullanamazsınız. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange> bir çalışma sayfasına bir denetim ekler ve adı **sistem** olarak değiştirirseniz, projeyi oluşturduğunuzda hatalar oluşur.

### <a name="delete-host-controls"></a>Konak denetimlerini Sil
 belge düzeyi projelerinde, Excel çalışma sayfasındaki veya Word belgesindeki denetimi seçerek ve **delete** tuşuna basarak, tasarım zamanında konak denetimlerini silebilirsiniz. ancak, denetimleri silmek için Excel içinde **ad tanımla** iletişim kutusunu kullanmanız gerekir <xref:Microsoft.Office.Tools.Excel.NamedRange> .

 Tasarım zamanında bir belgeye bir ana bilgisayar denetimi eklerseniz, bu denetimi kodda bir sonraki kez kullanmaya çalıştığınızda bir özel durum oluşturulur. `Delete`Bir konak denetiminin yöntemi yalnızca çalışma zamanında belgeye eklenen konak denetimlerini kaldırır. `Delete`Tasarım zamanında oluşturulan bir konak denetiminin yöntemini çağırırsanız, bir özel durum oluşturulur.

 Örneğin, bir ' <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> ın yöntemi <xref:Microsoft.Office.Tools.Excel.NamedRange> , <xref:Microsoft.Office.Tools.Excel.NamedRange> programlı olarak çalışma sayfasına eklendiyse, bu, dinamik olarak konak denetimleri oluşturma olarak bilinen öğesini siler. Dinamik olarak oluşturulan konak denetimleri `Remove` , veya özelliğinin yöntemine denetim adı geçirerek de kaldırılabilir <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> . daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Son kullanıcılar, çalışma zamanında belgeden bir konak denetimini siler, çözüm beklenmedik yollarla başarısız olabilir. konak denetimlerinin silinmesini sağlamak için Word ve Excel belge koruma özelliklerini kullanabilirsiniz. daha fazla bilgi için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md).

> [!NOTE]
> `Shutdown`Belge veya çalışma sayfasının olay işleyicisi sırasında denetimleri program aracılığıyla kaldırmayın. Olay gerçekleştiğinde UI öğeleri artık kullanılamaz `Shutdown` . Uygulama kapanmadan önce denetimleri kaldırmak istiyorsanız, kodunuzu veya gibi başka bir olay işleyicisine ekleyin `BeforeClose` `BeforeSave` .

### <a name="program-against-host-control-events"></a>Konak denetim olaylarına karşı program
 konak denetimlerinin Office nesneleri genişletmesinin bir yolu olay eklemektir. örneğin, <xref:Microsoft.Office.Interop.Excel.Range> Word içindeki Excel ve nesnedeki nesnenin <xref:Microsoft.Office.Interop.Word.Bookmark> olayları yoktur, ancak [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bu nesneleri programlanabilir olaylar ekleyerek genişletir. bu olaylara karşı, Visual Basic ve C# içindeki olay özelliği sayfasındaki olay açılan listesi aracılığıyla Windows Forms: denetim olaylarına aynı şekilde erişim sağlayabilirsiniz. Daha fazla bilgi için bkz. [Walkthrough: bir NamedRange denetimindeki olaylara karşı](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)programlama.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> <xref:Microsoft.Office.Interop.Excel.Application> Excel nesnesinin özelliğini **false** olarak ayarlamanız gerekir. bu özelliğin **false** olarak ayarlanması, Excel konak denetimlerinin olayları da dahil olmak üzere tüm olayları oluşturmasını engeller.

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
