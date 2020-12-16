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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4183e84a930957b7cf87a6cc1e6fabcb21420785
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527948"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma

  Bu açıklayıcı izlenecek yol, Excel Microsoft Office için belge düzeyi özelleştirmesi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler yalnızca belirli bir çalışma kitabı açık olduğunda kullanılabilir. Bir belge düzeyinde özelleştirmeyi uygulama genelinde değişiklikler yapmak için kullanamazsınız, örneğin, herhangi bir çalışma kitabı açıkken yeni bir şerit sekmesi görüntüleme.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Excel çalışma kitabı projesi oluşturma.

- Visual Studio tasarımcısında barındırılan bir çalışma sayfasına metin ekleme.

- Açıldığında özelleştirilmiş çalışma sayfasına metin eklemek için Excel nesne modelini kullanan kodu yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- Gereksiz derleme dosyalarını ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırmak için tamamlanmış projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Visual Studio 'da yeni bir Excel çalışma kitabı projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.
::: moniker range="vs-2017"
3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' i genişletin.

4. Genişletilmiş **Office/SharePoint** düğümü altında **VSTO eklentileri** düğümünü seçin.

5. Proje şablonları listesinde bir Excel VSTO çalışma kitabı projesi seçin.

6. **Ad** kutusuna **FirstWorkbookCustomization** yazın.

7. **Tamam** düğmesine tıklayın.

8. **Office projesi için Visual Studio Araçları** **Yeni belge oluştur** ' u seçin ve **Tamam**' ı tıklatın.
::: moniker-end
::: moniker range=">=vs-2019"
3. **Yeni proje oluştur** Iletişim kutusunda **Excel VSTO çalışma kitabı** projesini seçin.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. **İleri**’ye tıklayın.

5. **Yeni projenizi yapılandırma** Iletişim kutusundaki **ad** kutusuna **FirstWorkbookCustomization** yazın ve **Oluştur**' a tıklayın.

6. **Office projesi için Visual Studio Araçları** **Yeni belge oluştur** ' u seçin ve **Tamam**' ı tıklatın.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstWorkbookCustomization** projesini oluşturur ve aşağıdaki dosyaları projeye ekler.

   - *FirstWorkbookCustomization*. xlsx-projedeki Excel çalışma kitabını temsil eder. Tüm çalışma sayfalarını ve grafikleri içerir.

   - Sayfa1 (Visual C# için Visual Basic veya *. cs* dosyası için *. vb* dosyası)-çalışma kitabındaki ilk çalışma sayfasına yönelik tasarım yüzeyi ve kodu sağlayan bir çalışma sayfası. Daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

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

 Özelleştirmenizin Kullanıcı arabirimini (UI) Tasarımcıda açık olan çalışma sayfasını değiştirerek tasarlayabilirsiniz. Örneğin, hücrelere metin ekleyebilir, formüller uygulayabilir veya Excel denetimleri ekleyebilirsiniz. Tasarımcıyı kullanma hakkında daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Tasarımcıyı kullanarak çalışma sayfasına metin eklemek için

1. Tasarımcıda açık olan çalışma sayfasında **a1** hücresini seçin ve ardından aşağıdaki metni yazın.

     **Bu metin, tasarımcı kullanılarak eklenmiştir.**

> [!WARNING]
> Bu metin satırını **a2** hücresine eklerseniz, bu örnekteki diğer kodla üzerine yazılır.

## <a name="add-text-to-a-worksheet-programmatically"></a>Çalışma sayfasına programlamayla metin ekleme

 Ardından, Sheet1 kod dosyasına kod ekleyin. Yeni kod, çalışma kitabına ikinci bir metin satırı eklemek için Excel nesne modelini kullanır. Varsayılan olarak, Sheet1 kod dosyası aşağıdaki oluşturulan kodu içerir:

- `Sheet1`Çalışma sayfasının programlama modelini temsil eden ve Excel 'in nesne modeline erişim sağlayan sınıfının kısmi bir tanımı. Daha fazla bilgi için, [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md) ve [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md). Sınıfın geri kalanı, `Sheet1` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `Sheet1_Startup`Ve `Sheet1_Shutdown` olay işleyicileri. Bu olay işleyicileri, Excel özelleştirmeyi yüklerken ve kaldırdığınızda çağrılır. Bu olay işleyicilerini, yüklendiğinde özelleştirmenizi başlatmak ve özelleştirildiyse özelleştirme tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Kodu kullanarak çalışma sayfasına ikinci bir metin satırı eklemek için

1. **Çözüm Gezgini**, **Sheet1**' e sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Kod dosyası Visual Studio 'da açılır.

2. `Sheet1_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Sayfa1 açıldığında, bu kod çalışma sayfasına ikinci bir metin satırı ekler.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Projeyi test etme

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın.

     Projeyi derlediğinizde kod, çalışma kitabıyla ilişkili bir derlemeye derlenir. Visual Studio, çalışma kitabının ve derlemenin bir kopyasını projenin yapı çıktı klasörüne koyar ve özelleştirmeyi çalıştırmak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

2. Çalışma kitabında aşağıdaki metni gördiğinizi doğrulayın.

     **Bu metin, tasarımcı kullanılarak eklenmiştir.**

     **Bu metin kod kullanılarak eklenmiştir.**

3. Çalışma kitabını kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle

 Projeyi geliştirmeyi bitirdiğinizde derleme çıkış klasöründeki dosyaları ve yapı işlemi tarafından oluşturulan güvenlik ayarlarını kaldırmanız gerekir.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Geliştirme bilgisayarınızda tamamlanmış projeyi temizlemek için

1. Visual Studio 'da, **Yapı** menüsünde **Çözümü Temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

 Excel için temel bir belge düzeyi özelleştirmesi oluşturduğumıza göre, şu konulardan nasıl özelleştirme geliştirileceği hakkında daha fazla bilgi edinebilirsiniz:

- Belge düzeyi özelleştirmelerde gerçekleştirebileceğiniz genel programlama görevleri: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

- Excel için belge düzeyi özelleştirmelerine özgü programlama görevleri: [Excel çözümleri](../vsto/excel-solutions.md).

- Excel nesne modelini kullanma: [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

- Excel 'in Kullanıcı arabirimini özelleştirme, örneğin, Şerite özel bir sekme ekleyerek veya kendi eylemler bölmenizi oluşturarak: [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

- Excel nesne modeli kullanılarak mümkün olmayan görevleri gerçekleştirmek için Visual Studio 'da Office geliştirme araçları tarafından sunulan genişletilmiş Excel nesnelerini kullanma (örneğin, belgelerde yönetilen denetimleri barındırma ve Windows Forms veri bağlama modeli kullanarak Excel denetimlerini verilere bağlama): [genişletilmiş nesneleri kullanarak Excel 'ı otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md).

- Excel için belge düzeyinde özelleştirmeler oluşturma ve hata ayıklama: [Office çözümleri oluşturun](../vsto/building-office-solutions.md).

- Excel için belge düzeyi özelleştirmeleri dağıtma: [bir Office çözümü dağıtın](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel çözümleri](../vsto/excel-solutions.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
