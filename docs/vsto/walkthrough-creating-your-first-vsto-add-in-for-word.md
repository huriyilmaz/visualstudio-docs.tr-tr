---
title: 'İzlenecek yol: Word için ilk VSTO eklentisini oluşturma'
description: Microsoft Word için uygulama düzeyi eklentisi oluşturun. Bu özellik, hangi belgelerin açık olduğuna bakılmaksızın uygulamanın kendisi için kullanılabilir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc136b1c58f9c627787045b1259d07e27a6b8ad
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527877"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>İzlenecek yol: Word için ilk VSTO eklentisini oluşturma
  Bu açıklayıcı izlenecek yol, Microsoft Office Word için VSTO eklentisi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler, hangi belgelerin açık olduğuna bakılmaksızın uygulamanın kendisi için kullanılabilir.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Word VSTO eklentisi projesi oluşturma.

- Bir belgeye kaydedildiğinde metin eklemek için Word nesne modelini kullanan kod yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- VSTO eklentisinin geliştirme bilgisayarınızda artık otomatik olarak çalışmamasını sağlamak için tamamlanmış projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Visual Studio 'da yeni bir Word VSTO eklentisi projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' i genişletin.

4. Genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

5. Proje şablonları listesinde bir Word VSTO eklenti projesi seçin.

6. **Ad** kutusuna **FirstWordAddIn** yazın.

7. **Tamam** düğmesine tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstWordAddIn** projesini oluşturur ve ThisAddIn kod dosyasını düzenleyicide açar.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Kaydedilen belgeye metin eklemek için kod yazın
 Ardından, ThisAddIn kod dosyasına kod ekleyin. Yeni kod, kaydedilen her belgeye ortak metin eklemek için Word nesne modelini kullanır. Varsayılan olarak, ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi tanımı `ThisAddIn` . Bu sınıf, kodunuz için bir giriş noktası sağlar ve Word nesne modeline erişim sağlar. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Sınıfın geri kalanı, `ThisAddIn` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `ThisAddIn_Startup`Ve `ThisAddIn_Shutdown` olay işleyicileri. Bu olay işleyicileri, Word VSTO eklentinizi yüklediğinde ve kaldırdığında çağrılır. Bu olay işleyicilerini, yüklendiğinde VSTO eklentisini başlatmak ve bu etkinlik kaldırıldığında VSTO eklentisi tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Kaydedilen belgeye metin paragrafı eklemek için

1. ThisAddIn kod dosyasında, sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Yeni kod, <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> bir belge kaydedildiğinde oluşan olay için bir olay işleyicisini tanımlar.

    Kullanıcı bir belge kaydettiğinde, olay işleyicisi belgenin başlangıcında yeni metin ekler.

    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]

   > [!NOTE]
   > Bu kod, koleksiyondaki ilk paragrafa erişmek için 1 olan bir dizin değeri kullanır <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> . Visual Basic ve Visual C# 0 tabanlı diziler kullanmasına karşın, Word nesne modelindeki çoğu koleksiyonun alt dizi sınırları 1 ' dir. Daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

2. C# kullanıyorsanız, olay işleyicisine aşağıdaki gerekli kodu ekleyin `ThisAddIn_Startup` . Bu kod `Application_DocumentBeforeSave` olay işleyicisini olayla bağlamak için kullanılır <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]

   Belgeyi kaydedildiğinde değiştirmek için, önceki kod örnekleri aşağıdaki nesneleri kullanır:

- `Application` `ThisAddIn` Sınıfının alanı. `Application`Alan <xref:Microsoft.Office.Interop.Word.Application> , Word 'ün geçerli örneğini temsil eden bir nesne döndürür.

- `Doc`Olay işleyicisinin olay işleyicisi parametresi <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . `Doc`Parametresi <xref:Microsoft.Office.Interop.Word.Document> , kaydedilen belgeyi temsil eden bir nesnedir. Daha fazla bilgi için bkz. [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Projeyi test etme

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın.

     Projeyi derlediğinizde kod, projenin yapı çıkış klasörüne dahil olan bir derlemeye derlenir. Visual Studio Ayrıca, Word 'Ün VSTO eklentisini bulmasını ve yüklemesini sağlayan bir kayıt defteri girişi kümesi oluşturur ve VSTO eklentisinin çalışmasını sağlamak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

2. Word 'de etkin belgeyi kaydedin.

3. Belgeye aşağıdaki metnin eklendiğini doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. Word 'Ü kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle
 Projeyi geliştirmeyi bitirdiğinizde, VSTO eklenti derlemesini, kayıt defteri girişlerini ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi halde, VSTO eklentisi geliştirme bilgisayarınızda Word 'Ü her açışınızda çalışmaya devam edecektir.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Geliştirme bilgisayarınızda tamamlanmış projeyi temizlemek için

1. Visual Studio 'da, **Yapı** menüsünde **Çözümü Temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Word için temel bir VSTO eklentisi oluşturduğunuza göre, şu konulardan VSTO eklentileri geliştirme hakkında daha fazla bilgi edinebilirsiniz:

- VSTO eklentilerde gerçekleştirebileceğiniz genel programlama görevleri: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- Word VSTO eklentilerine özgü programlama görevleri: [Word çözümleri](../vsto/word-solutions.md).

- Word nesne modelini kullanma: [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).

- Word 'ün Kullanıcı arabirimini özelleştirme, örneğin, şerit 'e özel bir sekme ekleme veya kendi özel görev bölmenizi oluşturma: [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

- Word için VSTO eklentileri oluşturma ve hata ayıklama: [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

- Word için VSTO eklentileri dağıtma: [bir Office çözümü dağıtın](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Word çözümleri](../vsto/word-solutions.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
