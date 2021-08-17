---
title: 'Adım adım kılavuz: VSTO için İlk Eklentinizi Outlook'
description: Microsoft Outlook için uygulama düzeyinde bir eklenti oluşturun. Bu özellik, hangi öğenin açık olduğuna bakılmaksızın Outlook kullanılabilir.
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
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 189cbe343ed1cdc6fad135a7bb4614e7423f2b9d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059861"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Adım adım kılavuz: VSTO için İlk Eklentinizi Outlook
  Bu kılavuzda, Microsoft Office Outlook için VSTO Eklenti oluşturma Microsoft Office Outlook. Bu tür bir çözümde, hangi öğenin açık olduğuna bakılmaksızın uygulamanın Outlook özellikleri kullanılabilir. Daha fazla bilgi için [bkz. Office çözüm geliştirmeye genel bakış &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Outlook VSTO için bir Eklenti projesi Outlook.

- Yeni bir posta iletisinin konu ve gövdesine metin eklemek için Outlook nesnesinin nesne modelini kullanan kod yazma.

- Projeyi test etmek için bina ve çalıştırma.

- Tamamlanan projeyi temizleyen VSTO artık geliştirme bilgisayarınızda otomatik olarak çalışmaz.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Yeni bir Outlook proje oluşturmak Visual Studio

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.**

3. Şablonlar bölmesinde Visual **C#** veya **Visual Basic'ı** genişletin ve sonra **Office/SharePoint.**

4. Genişletilmiş **Office/SharePoint** altında, **Office düğümünü** seçin.

5. Proje şablonları listesinde, eklenti projesini Outlook VSTO seçin.

6. Ad **kutusuna** **FirstOutlookAddIn yazın.**

7. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstOutlookAddIn projesini** oluşturur ve **ThisAddIn** kod dosyasını düzenleyicide açar.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Her yeni posta iletisine metin ekleyen kod yazma
 Ardından ThisAddIn kod dosyasına kod ekleyin. Yeni kod, her yeni posta Outlook eklemek için Outlook nesnesinin nesne modelini kullanır. Varsayılan olarak ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi `ThisAddIn` tanımı. Bu sınıf kodunuz için bir giriş noktası sağlar ve kodun nesne modeline Outlook. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md) Sınıfın geri `ThisAddIn` kalanı, değiştirmeyebilirsiniz gizli bir kod dosyasında tanımlanır.

- ve `ThisAddIn_Startup` olay `ThisAddIn_Shutdown` işleyicileri. Bu olay işleyicileri, Outlook eklentinizi yüklerken ve VSTO yüklerken çağrılır. Bu olay işleyicilerini kullanarak VSTO eklentinizi başlatıp yüklemesi kaldırılan eklentiniz tarafından VSTO kaynakları temizleyin. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Her yeni posta iletisinin konu ve gövdesine metin eklemek için

1. ThisAddIn kod dosyasında sınıfında adlı bir `inspectors` alan `ThisAddIn` bildirin. alanı, `inspectors` geçerli örnek içinde Denetçi pencerelerinin koleksiyonuna bir başvuru Outlook sağlar. Bu başvuru, atık toplayıcının olay için olay işleyicisini içeren belleği serbest bırakarak <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> önlemesini sağlar.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. `ThisAddIn_Startup` yöntemini aşağıdaki kodla değiştirin. Bu kod, olayına bir olay <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> işleyicisi iliştirer.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet2":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet2":::

3. ThisAddIn kod dosyasında sınıfına aşağıdaki kodu `ThisAddIn` ekleyin. Bu kod, olay için bir olay <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> işleyicisi tanımlar.

    Kullanıcı yeni bir posta iletisi oluşturduğunda, bu olay işleyicisi konu satırına ve iletinin gövdesine metin ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet3":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet3":::

   Önceki kod örnekleri, her yeni posta iletisini değiştirmek için aşağıdaki nesneleri kullanır:

- `Application`sınıfının `ThisAddIn` alanı. alanı, `Application` geçerli örneği temsil eden bir nesne döndürür <xref:Microsoft.Office.Interop.Outlook.Application> Outlook.

- `Inspector`Olay için olay işleyicisi <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> parametresi. parametresi, `Inspector` yeni <xref:Microsoft.Office.Interop.Outlook.Inspector> posta iletisinin Denetçi penceresini temsil eden bir nesnesidir. Daha fazla bilgi için [bkz. Outlook çözümleri.](../vsto/outlook-solutions.md)

## <a name="test-the-project"></a>Projeyi test etme
 Projeyi derlemek ve çalıştırmak için metnin konu satırı ve yeni posta iletisinin gövdesinde görüntülendiğinden emin olur.

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5'e** basın.

     Projeyi derlerken kod, projenin derleme çıkış klasörüne dahil edilen bir derlemede derlenmiş olur. Visual Studio, Outlook'ın VSTO Eklentisini bulması ve yüklemesini sağlayan bir kayıt defteri girdileri kümesi de oluşturur ve geliştirme bilgisayarına güvenlik ayarlarını VSTO Eklentinin çalışmasına olanak sağlayacak şekilde yapılandırıyor. Daha fazla bilgi için [bkz. Office derleme sürecine genel bakış.](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

2. Bu Outlook yeni bir posta iletisi oluşturun.

3. Aşağıdaki metnin hem konu satırına hem de iletinin gövdesine ekli olduğunu doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. Outlook.

## <a name="clean-up-the-project"></a>Projeyi temizleme
 Bir proje geliştirmeyi tamamlasanız, VSTO derleme, kayıt defteri girdileri ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi takdirde VSTO eklenti, geliştirme bilgisayarına her Outlook çalıştırabilirsiniz.

### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için

1. Bu Visual Studio, Derleme **menüsünde Çözümü** Temizle'ye **tıklayın.**

## <a name="next-steps"></a>Sonraki adımlar
 Outlook için temel VSTO eklenti oluşturduğunuza göre, VSTO eklentilerini geliştirme hakkında daha fazla bilgi edinmek için şu konulardan bilgi sebilirsiniz:

- Genel programlama görevleri için VSTO Eklentilerini kullanarak gerçekleştirebilirsiniz Outlook. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

- Uygulamanın nesne modelini Outlook. Daha fazla bilgi için [bkz. Outlook çözümleri.](../vsto/outlook-solutions.md)

- Örneğin Şerit'Outlook özel bir sekme ekleyerek veya kendi özel görev bölmenizi oluşturarak kullanıcı arabirimini özelleştirme. Daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

- Uygulama için VSTO ve hata ayıklama Outlook. Daha fazla bilgi için [bkz. Derleme Office.](../vsto/building-office-solutions.md)

- VSTO için Outlook. Daha fazla bilgi için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Outlook çözümleri](../vsto/outlook-solutions.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Yeni Office oluşturma](../vsto/building-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Office şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
