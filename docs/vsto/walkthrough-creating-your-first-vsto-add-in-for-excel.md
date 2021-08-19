---
title: 'Adım adım kılavuz: VSTO için İlk Eklentinizi Excel'
description: Uygulama düzeyinde bir Eklenti oluşturun Microsoft Excel. Hangi çalışma kitaplarının açık olduğu ne olursa olsun, uygulamanın kendisinde oluşturabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4a3dedc8a954f278e1446667c0623ea7da5d6fa5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147615"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Adım adım kılavuz: VSTO için İlk Eklentinizi Excel
  Bu giriş niteliğindeki kılavuzda, uygulama düzeyinde bir eklentinin nasıl oluşturularak Microsoft Office Excel. Bu tür bir çözümde, hangi çalışma kitaplarının açık olduğu ne olursa olsun uygulamanın kendisinde oluşturabilirsiniz.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Excel VSTO için bir Eklenti projesi Excel.

- Kaydedilen çalışma kitabına metin eklemek Excel nesne modelini kullanan kod yazma.

- Projeyi test etmek için bina ve çalıştırma.

- Tamamlanan projeyi temizleyen VSTO artık geliştirme bilgisayarınızda otomatik olarak çalışmaz.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Yeni bir eklenti Excel VSTO proje oluşturmak için Visual Studio

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.**

3. Şablonlar bölmesinde **Visual C#** veya **Visual Basic'ı** genişletin ve sonra **Office/SharePoint.**

4. Genişletilmiş **Office/SharePoint** altında, **Office düğümünü** seçin.

5. Proje şablonları listesinde, Excel **2010** Eklentisini veya Excel **2013 Eklentisini seçin.**

6. Ad **kutusuna** **FirstExcelAddIn yazın.**

7. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstExcelAddIn projesini** oluşturur ve ThisAddIn kod dosyasını düzenleyicide açar.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Kaydedilen çalışma kitabına metin eklemek için kod yazma
 Ardından ThisAddIn kod dosyasına kod ekleyin. Yeni kod, etkin çalışma sayfasının Excel metin eklemek için Excel nesnesinin nesne modelini kullanır. Etkin çalışma sayfası, kullanıcı çalışma kitabını kaydederken açık olan çalışma sayfasıdır. Varsayılan olarak ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi `ThisAddIn` tanımı. Bu sınıf kodunuz için bir giriş noktası sağlar ve kodun nesne modeline Excel. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md) Sınıfın geri `ThisAddIn` kalanı, değiştirmeyebilirsiniz gizli bir kod dosyasında tanımlanır.

- ve `ThisAddIn_Startup` olay `ThisAddIn_Shutdown` işleyicileri. Bu olay işleyicileri, Excel eklentinizi yükler ve VSTO çağrılır. Bu olay işleyicilerini kullanarak VSTO eklentinizi başlatacak ve kaldırılan eklentiniz tarafından kullanılan kaynakları temizleyebilirsiniz. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Kaydedilen çalışma kitabına bir metin satırı eklemek için

1. ThisAddIn kod dosyasında sınıfına aşağıdaki kodu `ThisAddIn` ekleyin. Yeni kod, olay için bir olay <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> işleyicisi tanımlar ve bu işleyici çalışma kitabı kaydedilebilir.

    Kullanıcı bir çalışma kitabını kaydederken, olay işleyicisi etkin çalışma sayfasının başlangıcına yeni metin ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. C# kullanıyorsanız, olay işleyiciye aşağıdaki gerekli `ThisAddIn_Startup` kodu ekleyin. Bu kod, olay `Application_WorkbookBeforeSave` işleyicisini olayla bağlamak için <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> kullanılır.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Çalışma kitabı kaydedilirken değiştirmek için, önceki kod örnekleri aşağıdaki nesneleri kullanır:

- `Application`sınıfının `ThisAddIn` alanı. alanı, `Application` geçerli örneği temsil eden bir nesne döndürür <xref:Microsoft.Office.Interop.Excel.Application> Excel.

- `Wb`Olay için olay işleyicisi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> parametresi. parametresi, `Wb` kaydedilen çalışma kitabını temsil eden bir <xref:Microsoft.Office.Interop.Excel.Workbook> nesnesidir. Daha fazla bilgi için [bkz. Excel modeline genel bakış.](../vsto/excel-object-model-overview.md)

## <a name="test-the-project"></a>Projeyi test etme

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5'e** basın.

     Projeyi derlerken kod, projenin derleme çıkış klasörüne dahil edilen bir derlemede derlenmiş olur. Visual Studio, Excel'nin VSTO Eklentisini bulması ve yüklemesini sağlayan bir kayıt defteri girdileri kümesi de oluşturur ve geliştirme bilgisayarında güvenlik ayarlarını VSTO Eklentinin çalışmasına olanak sağlayacak şekilde yapılandırıyor. Daha fazla bilgi için [bkz. Derleme Office.](../vsto/building-office-solutions.md)

2. Bu Excel çalışma kitabını kaydedin.

3. Çalışma kitabına aşağıdaki metnin ekli olduğunu doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. Excel.

## <a name="clean-up-the-project"></a>Projeyi temizleme
 Bir proje geliştirmeyi tamamlasanız, VSTO derleme, kayıt defteri girdileri ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi takdirde VSTO eklenti, geliştirme bilgisayarınızda her Excel çalışmaya devam eder.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Geliştirme bilgisayarınızda tamamlanan projeyi temizlemek için

1. Bu Visual Studio, Derleme **menüsünde Çözümü** Temizle'ye **tıklayın.**

## <a name="next-steps"></a>Sonraki adımlar
 Excel için temel bir VSTO eklenti oluşturduğunuza göre, bu konulardan VSTO eklentilerini geliştirme hakkında daha fazla bilgi öğrenebilirsiniz:

- Eklentilerde gerçekleştirebilirsiniz genel programlama VSTO: Program VSTO [Eklentileri.](../vsto/programming-vsto-add-ins.md)

- Excel VSTO Eklentilerine özgü programlama görevleri: [Excel çözümleri.](../vsto/excel-solutions.md)

- Excel: Excel [modeline genel bakış.](../vsto/excel-object-model-overview.md)

- Örneğin Şerit'e özel bir sekme ekleyerek veya kendi özel görev bölmenizi oluşturarak Excel kullanıcı arabirimini (UI) özelleştirme: [Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

- Excel için VSTO oluşturma ve hata ayıklama: Office [çözümleri.](../vsto/building-office-solutions.md)

- Excel için VSTO eklentileri dağıtma: Office çözümü [dağıtın.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel çözümleri](../vsto/excel-solutions.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Excel modeline genel bakış](../vsto/excel-object-model-overview.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Yeni Office oluşturma](../vsto/building-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Office şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
