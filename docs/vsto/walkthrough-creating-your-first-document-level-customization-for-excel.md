---
title: Excel için ilk belge düzeyi özelleştirmeyi oluşturma
description: Microsoft Excel için belge düzeyi özelleştirmesi oluşturun. Bu tür çözümde oluşturduğunuz özellikler yalnızca belirli bir çalışma kitabı açık olduğunda kullanılabilir.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: bd69d27b399f237fddb2f543e28a236edfdb8603
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114998"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma

  bu açıklayıcı izlenecek yol, Microsoft Office Excel için belge düzeyi özelleştirmesi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler yalnızca belirli bir çalışma kitabı açık olduğunda kullanılabilir. Bir belge düzeyinde özelleştirmeyi uygulama genelinde değişiklikler yapmak için kullanamazsınız, örneğin, herhangi bir çalışma kitabı açıkken yeni bir şerit sekmesi görüntüleme.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Excel çalışma kitabı projesi oluşturma.

- Visual Studio tasarımcısında barındırılan bir çalışma sayfasına metin ekleme.

- açıldığında özelleştirilmiş çalışma sayfasına metin eklemek için Excel nesne modelini kullanan kodu yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- Gereksiz derleme dosyalarını ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırmak için tamamlanmış projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Visual Studio içinde yeni bir Excel çalışma kitabı projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.
::: moniker range="vs-2017"
3. şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' yı genişletin.

4. genişletilmiş **Office/SharePoint** düğümü altında **VSTO eklentileri** düğümünü seçin.

5. proje şablonları listesinde bir Excel VSTO çalışma kitabı projesi seçin.

6. **Ad** kutusuna **FirstWorkbookCustomization** yazın.

7. **Tamam**'a tıklayın.

8. **Office için Visual Studio Araçları Project sihirbazından** **yeni belge oluştur** ' u seçin ve **tamam**' ı tıklatın.
::: moniker-end
::: moniker range=">=vs-2019"
3. **yeni Project oluştur** iletişim kutusunda **Excel VSTO çalışma kitabı** projesini seçin.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. **İleri**’ye tıklayın.

5. **Yeni projenizi yapılandırma** Iletişim kutusundaki **ad** kutusuna **FirstWorkbookCustomization** yazın ve **Oluştur**' a tıklayın.

6. **Office için Visual Studio Araçları Project sihirbazından** **yeni belge oluştur** ' u seçin ve **tamam**' ı tıklatın.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstWorkbookCustomization** projesini oluşturur ve aşağıdaki dosyaları projeye ekler.

   - *firstworkbookcustomization*.xlsx-projedeki Excel çalışma kitabını temsil eder. Tüm çalışma sayfalarını ve grafikleri içerir.

   - sayfa1 (Visual C# için Visual Basic veya *. cs* dosyası için *. vb* dosyası)-çalışma kitabındaki ilk çalışma sayfasına yönelik tasarım yüzeyi ve kodu sağlayan bir çalışma sayfası. Daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

   - Sheet2 (Visual C# için Visual Basic veya *. cs* dosyası için *. vb* dosyası)-çalışma kitabındaki ikinci çalışma sayfasına yönelik tasarım yüzeyi ve kodu sağlayan bir çalışma sayfası.

   - Sheet3 (Visual C# için Visual Basic veya *. cs* dosyası için *. vb* dosyası)-çalışma kitabındaki üçüncü çalışma sayfasına yönelik tasarım yüzeyi ve kodu sağlayan bir çalışma sayfası.

   - ThisWorkbook (Visual Basic için *. vb* dosyası veya Visual C# için *. cs* dosyası)-tasarım yüzeyini ve çalışma kitabı düzeyi özelleştirmeleri için kodu içerir. Daha fazla bilgi için bkz. [çalışma kitabı konak öğesi](../vsto/workbook-host-item.md).

     Sheet1 kod dosyası tasarımcıda otomatik olarak açılır.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Tasarımcıda çalışma sayfalarını kapatma ve yeniden açma

 Projenizi geliştirirken tasarımcı içindeki bir çalışma kitabını veya çalışma sayfasını kasıtlı olarak veya yanlışlıkla kapatırsanız yeniden açabilirsiniz.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Tasarımcıda çalışma sayfasını kapatmak ve yeniden açmak için

1. Tasarımcı penceresinin **Kapat** düğmesine (X) tıklayarak çalışma kitabını kapatın.

2. **Çözüm Gezgini**, **Sheet1** kod dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' na tıklayın.

     \- veya

     **Çözüm Gezgini**, **Sheet1** kod dosyasına çift tıklayın.

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Tasarımcıda çalışma sayfasına metin ekleme

 Özelleştirmenizin Kullanıcı arabirimini (UI) Tasarımcıda açık olan çalışma sayfasını değiştirerek tasarlayabilirsiniz. örneğin, hücrelere metin ekleyebilir, formüller uygulayabilir veya Excel denetimleri ekleyebilirsiniz. tasarımcıyı kullanma hakkında daha fazla bilgi için, [Visual Studio ortamında Office projeler](../vsto/office-projects-in-the-visual-studio-environment.md)bölümüne bakın.

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Tasarımcıyı kullanarak çalışma sayfasına metin eklemek için

1. Tasarımcıda açık olan çalışma sayfasında **a1** hücresini seçin ve ardından aşağıdaki metni yazın.

     **Bu metin, tasarımcı kullanılarak eklenmiştir.**

> [!WARNING]
> Bu metin satırını **a2** hücresine eklerseniz, bu örnekteki diğer kodla üzerine yazılır.

## <a name="add-text-to-a-worksheet-programmatically"></a>Çalışma sayfasına programlamayla metin ekleme

 Ardından, Sheet1 kod dosyasına kod ekleyin. yeni kod, çalışma kitabına ikinci bir metin satırı eklemek için Excel nesne modelini kullanır. Varsayılan olarak, Sheet1 kod dosyası aşağıdaki oluşturulan kodu içerir:

- `Sheet1`Çalışma sayfasının programlama modelini temsil eden ve Excel nesne modeline erişim sağlayan sınıfının kısmi bir tanımı. Daha fazla bilgi için, [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md) ve [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md). Sınıfın geri kalanı, `Sheet1` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `Sheet1_Startup`Ve `Sheet1_Shutdown` olay işleyicileri. bu olay işleyicileri, Excel özelleştirmeyi yüklediğinde ve kaldırıldığında çağırılır. Bu olay işleyicilerini, yüklendiğinde özelleştirmenizi başlatmak ve özelleştirildiyse özelleştirme tarafından kullanılan kaynakları temizlemek için kullanın. daha fazla bilgi için bkz. [Office projelerindeki olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Kodu kullanarak çalışma sayfasına ikinci bir metin satırı eklemek için

1. **Çözüm Gezgini**, **Sheet1**' e sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Kod dosyası Visual Studio açılır.

2. `Sheet1_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Sayfa1 açıldığında, bu kod çalışma sayfasına ikinci bir metin satırı ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb" id="Snippet1":::

## <a name="test-the-project"></a>Projeyi test etme

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın.

     Projeyi derlediğinizde kod, çalışma kitabıyla ilişkili bir derlemeye derlenir. Visual Studio, çalışma kitabının ve derlemenin kopyasını projenin yapı çıkış klasörüne koyar ve özelleştirmeyi çalıştırmak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. daha fazla bilgi için bkz. [derleme Office çözümleri](../vsto/building-office-solutions.md).

2. Çalışma kitabında aşağıdaki metni gördiğinizi doğrulayın.

     **Bu metin, tasarımcı kullanılarak eklenmiştir.**

     **Bu metin kod kullanılarak eklenmiştir.**

3. Çalışma kitabını kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle

 Projeyi geliştirmeyi bitirdiğinizde derleme çıkış klasöründeki dosyaları ve yapı işlemi tarafından oluşturulan güvenlik ayarlarını kaldırmanız gerekir.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Geliştirme bilgisayarınızda tamamlanmış projeyi temizlemek için

1. Visual Studio, **yapı** menüsünde **çözümü temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

 Excel için temel bir belge düzeyi özelleştirmesi oluşturduğumıza göre, şu konulardan özelleştirmeler geliştirme hakkında daha fazla bilgi edinebilirsiniz:

- Belge düzeyi özelleştirmelerde gerçekleştirebileceğiniz genel programlama görevleri: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

- Excel: [Excel çözümleri](../vsto/excel-solutions.md)için belge düzeyi özelleştirmelerine özgü programlama görevleri.

- Excel nesne modelini kullanma: [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

- Excel kullanıcı arabirimini özelleştirme, örneğin, şerit 'e özel bir sekme ekleyerek veya kendi eylemler bölmenizi oluşturarak: [Office uı özelleştirmesi](../vsto/office-ui-customization.md).

- Excel nesne modeli kullanılarak mümkün olmayan görevleri gerçekleştirmek için Visual Studio Office geliştirme araçları tarafından sunulan genişletilmiş Excel nesneleri kullanma (örneğin, belgelerde yönetilen denetimleri barındırma ve Excel denetimleri verileri verilerle bağlama Windows Forms veri bağlama modelini kullanarak): [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md).

- Excel için belge düzeyi özelleştirmeleri oluşturma ve hata ayıklama: [Office çözümleri derleme](../vsto/building-office-solutions.md).

- Excel için belge düzeyi özelleştirmeleri dağıtma: [bir Office çözümü dağıtın](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel çözümleri](../vsto/excel-solutions.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office çözümleri oluşturun](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
