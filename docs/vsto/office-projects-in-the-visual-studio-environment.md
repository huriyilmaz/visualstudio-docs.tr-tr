---
title: Visual Studio ortamında Office projeleri
description: Microsoft Office projelerinin, Visual Studio 'da Windows Forms projeleri gibi diğer proje türlerine benzer bir geliştirme deneyimine sahip olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88abd7294a96b4fe4989630753253b16f036ab7c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892014"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Visual Studio ortamında Office projeleri
  Microsoft Office projeleri, Visual Studio'daki diğer proje türlerine (Windows Forms projeleri gibi) benzer bir geliştirme deneyimine sahiptir. Bir Office projesi oluşturduğunuzda veya açtığınızda, proje öğeleri **Çözüm Gezgini** görüntülenir. Belge düzeyinde projeler için, belge (yani, Word belgesi veya Excel çalışma kitabı) Visual Studio'da açılır ve belge bir görsel tasarımcı gibi davranır.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="project-items-in-solution-explorer"></a>Çözüm Gezgini proje öğeleri
 Belge düzeyi projesinde, **Çözüm Gezgini** aşağıdaki varsayılan öğeleri görüntüler:

- Projenin özelleştirdiği belge, çalışma kitabı ve sayfa düğümleri. Bu düğümler; belge, çalışma kitabı ve sayfalar ile ilişkili kod dosyaları için kapsayıcı işlevi görür.

- Projenin özelleştirdiği belge, çalışma kitabı ve sayfalar ile ilişkili kod dosyaları. Word projelerinde, kod dosyaları Word belgesi veya şablonu ile ilişkilidir. Excel projelerinde, kod dosyaları Excel çalışma kitabı veya şablonuyla ve çalışma kitabı veya şablondaki her bir çalışma sayfası ve grafik sayfası ile ilişkilidir.

- Doğrudan düzenlemeniz için tasarlanmamış gizli proje dosyaları. Daha fazla bilgi için bkz. [gizli proje dosyaları](#hiddenfiles).

  VSTO eklenti projesinde, **Çözüm Gezgini** aşağıdaki varsayılan öğeleri görüntüler:

- Uygulama düğümü. Bu düğüm, **Word**, **Excel** veya **Outlook** gibi ana bilgisayar uygulamasıyla aynı ada sahiptir. Bu uygulama düğümü ThisAddIn kod dosyasını içerir. Ayrıca **konak öğesi özelliği Için ad alanı** sağlar. Bu özellik hakkında daha fazla bilgi için bkz. [Office projelerindeki Özellikler](../vsto/properties-in-office-projects.md).

- ThisAddIn kod dosyası. Bu dosya, `ThisAddIn` VSTO eklentisi için oluşturulan sınıfı içerir. Bu sınıf hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- Doğrudan düzenlemeniz için tasarlanmamış gizli proje dosyaları. Daha fazla bilgi için bkz. [gizli proje dosyaları](#hiddenfiles).

### <a name="temporary-certificates"></a>Geçici Sertifikalar
 Office projeleri ayrıca *Proje adı* _TemporaryKey. pfx adlı geçici bir sertifika içerir. Bu sertifika, geliştirme sırasında projenin uygulama ve dağıtım bildirimlerini imzalamak için kullanılır. Daha fazla bilgi için bkz. [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md) ve [Office çözümlerini güvenli hale getirme](../vsto/securing-office-solutions.md).

### <a name="hidden-project-files"></a><a name="hiddenfiles"></a> Gizli proje dosyaları
 Bazı proje dosyaları varsayılan olarak gizlidir. Bu dosyalar Visual Studio tarafından oluşturulur ve proje türüne göre farklılık gösterir. Gizli dosyaları görüntülemek için **Çözüm Gezgini** **tüm dosyaları göster** ' e tıklayın.

 Gizli proje dosyalarında değişiklik yapmayın. Bu dosyaların doğrudan değiştirilmesi desteklenmez ve projenizin bozulmasına neden olabilir. Gizli proje dosyaları, belgede belirli değişiklikler olduğu durumlarda yeniden oluşturulur. Gizli bir proje dosyasında el ile değişiklikler yaparsanız, dosya yeniden oluşturulduğunda bu değişiklikler kaybolur.

## <a name="document-designer-in-document-level-projects"></a>Belge düzeyi projelerde belge Tasarımcısı
 Excel ve Word için belge düzeyinde projeler, Visual Studio'da projenizle ilişkili belgeyi barındıran bir tasarımcı sunar. Tasarımcı, Visual Studio ortamının dışına çıkmadan belgede değişiklik yapmanızı sağlar.

 Tasarımcıda bir belge açmak için, belgeyle ilişkili **Çözüm Gezgini** kod dosyasına çift tıklayın. Örneğin **, çalışma sayfasını** Tasarımcıda bir Excel projesinde açmak için **Sheet1** kod dosyasına çift tıklayın.

 Belgeyi tasarımcıda değiştirirken, Office uygulamasının yerel işlevselliğinden yararlanabilirsiniz. Örneğin, belgeye veya bir çalışma sayfasına metin girebilir veya tablo ya da grafik ekleme gibi görevleri gerçekleştirmek için Şerit'i kullanabilirsiniz. Varsayılan olarak, klavye kısayolu eşlemeleri Visual Studio eşlemelerine varsayılan olur. Bunun yerine Office klavye kısayol eşlemelerini kullanmak için **Araçlar** menüsündeki **Seçenekler** Iletişim kutusunda bulunan **klavye ayarları düğümü Microsoft Office** ayarlarını değiştirin.

### <a name="controls-on-documents"></a>Belgeler Üzerindeki Denetimler
 Visual Studio **araç kutusundan** belge tasarım yüzeyine *konak denetimleri* ve Windows Forms denetimleri sürükleyebilirsiniz. Konak denetimleri Office nesnelerinin özelleşmiş sürümleri olup (Word içerik denetimleri ve Excel aralıkları gibi), Visual Studio ile oluşturulmuş Office projelerinde kullanılabilirler. Konak denetimlerinin karşılık gelen Office nesnelerinde bulunmayan, veri bağlama ve ek olaylar gibi ilave özellikleri vardır.

 Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) ve [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).

### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Tasarımcıda Excel çalışma sayfaları ve çalışma kitapları
 Bir çalışma sayfasını tasarımcıda açtığınızda, çalışma sayfasını doğrudan Excel'de açtığınızda yaptığınız gibi değiştirebilirsiniz. Bir çalışma sayfası hücresine çift tıklarsanız hücre düzenleme moduna geçer. Konak denetimi içeren bir hücreye çift tıklarsanız, kod Düzenleyicisi açılır ve Visual Studio denetim için varsayılan olay işleyicisini oluşturur. Diğer çalışma sayfalarına gitmek için tasarımcının en altında çalışma sayfası sekmelerine tıklayabilirsiniz.

 Çalışma kitabını tasarımcıda açtığınızda tasarım yüzeyi bulunmaz. Çalışma kitabına ilişkin tasarım görünümü tasarımcıyı dolduran büyük bir bileşen alanıdır.

 Çalışma kitabının ve çalışma kitabındaki tüm sayfaların ilişkili birer kod dosyası vardır. Her kod dosyası, çalışma kitabını veya sayfasını temsil eden oluşturulmuş bir *konak öğesi* sınıfını içerir. Daha fazla bilgi için bkz. [genişletilmiş nesneleri kullanarak Excel 'ı otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md).

### <a name="word-documents-in-the-designer"></a>Tasarımcıda Word belgeleri
 Belgeyi tasarımcıda açtığınızda, doğrudan Word'de açtığınızda yaptığınız gibi değiştirebilirsiniz. Belgedeki bir sözcüğe çift tıklarsanız, sözcük seçili hale gelir. Ancak sözcük bir konak denetiminin içindeyse, kod düzenleyicisi açılır ve Visual Studio denetim için varsayılan olay işleyicisini oluşturur.

 Belgenin ilişkili bir kod dosyası vardır. Kod dosyası, belgeyi temsil eden oluşturulmuş bir *konak öğesi* sınıfını içerir. Daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md).

### <a name="design-mode-vs-runtime-mode"></a>Tasarım modu ile çalışma zamanı modu
 Visual Studio ortamında bir belge açıldığında, her zaman *Tasarım modundadır*. Bazı görevler (örneğin, belge yüzeyine bir konak denetimi sürüklemek gibi) sadece tasarım modunda gerçekleştirebilir.

 Belgeyi *çalışma zamanı modunda* görüntülemek için, uygulamayı ve belgeyi Visual Studio 'nun dışında açmanız gerekir. Ayrıca, projeyi derleyip çalıştırabilirsiniz ve böylece, belge ve uygulama otomatik olarak Visual Studio'nun dışında açılır.

## <a name="code-editor"></a>Kod Düzenleyicisi
 Kod Düzenleyicisi çözümünüzdeki görünür kod dosyalarını görüntüleyip değiştirebilmenizi sağlar. Bu dosyalar çözümünüzün davranışını tanımlayan kodu içerir.

 Kod Düzenleyicisi hakkında daha fazla bilgi için bkz. kod [ve metin düzenleyicisinde kod yazma](../ide/writing-code-in-the-code-and-text-editor.md). Office projelerinde kod yazma hakkında daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

## <a name="properties-window"></a>Özellik penceresi
 **Özellikler** penceresi **Çözüm Gezgini**' de seçilen proje öğelerinin özelliklerini ve tasarımcıda seçilen kullanıcı arabirimi öğelerini (örneğin, denetimler veya belge düzeyindeki bir proje) görüntüler. Bazı özellikler uygulamaya ve belgeye özgü olurken, bazı özellikler tüm projeler genelinde aynıdır.

## <a name="data-sources-window"></a>Veri Kaynakları penceresi
 Belge düzeyi Office projelerindeki **veri kaynakları** penceresini kullanarak bir veri kaynağını belgenize sürükleyebilir ve veri kaynağına bağlanan bir denetim oluşturabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office projelerindeki Özellikler](../vsto/properties-in-office-projects.md)
