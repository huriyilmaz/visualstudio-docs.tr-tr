---
title: 'İzlenecek yol: Outlook için ilk VSTO eklentisini oluşturma'
description: Microsoft Outlook için uygulama düzeyi eklentisi oluşturun. Bu özellik, hangi Outlook öğesinin açık olduğuna bakılmaksızın uygulamanın kendisi tarafından kullanılabilir.
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
ms.workload:
- office
ms.openlocfilehash: 16f735e2902527307ac812922495a2a0cb3b377e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966597"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>İzlenecek yol: Outlook için ilk VSTO eklentisini oluşturma
  Bu izlenecek yol, Outlook Microsoft Office için VSTO eklentisi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler, hangi Outlook öğesinin açık olduğuna bakılmaksızın uygulamanın kendisi tarafından kullanılabilir. Daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Outlook için Outlook VSTO eklentisi projesi oluşturma.

- Yeni bir posta iletisinin konusuna ve gövdesine metin eklemek için Outlook 'un nesne modelini kullanan kod yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- VSTO eklentisinin geliştirme bilgisayarınızda artık otomatik olarak çalışmamasını sağlamak için tamamlanmış projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Visual Studio 'da yeni bir Outlook projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' i genişletin.

4. Genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

5. Proje şablonları listesinde bir Outlook VSTO eklentisi projesi seçin.

6. **Ad** kutusuna **FirstOutlookAddIn** yazın.

7. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstOutlookAddIn** projesini oluşturur ve **ThisAddIn** kod dosyasını düzenleyicide açar.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Her yeni posta iletisine metin ekleyen kodu yazın
 Ardından, ThisAddIn kod dosyasına kod ekleyin. Yeni kod, her yeni posta iletisine metin eklemek için Outlook nesne modelini kullanır. Varsayılan olarak, ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi tanımı `ThisAddIn` . Bu sınıf, kodunuz için bir giriş noktası sağlar ve Outlook 'un nesne modeline erişim sağlar. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Sınıfın geri kalanı, `ThisAddIn` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `ThisAddIn_Startup`Ve `ThisAddIn_Shutdown` olay işleyicileri. Bu olay işleyicileri Outlook, VSTO eklentinizi yüklerken ve kaldırıldığında çağrılır. Bu olay işleyicilerini, yüklendiğinde VSTO eklentisini başlatmak ve bu etkinlik kaldırıldığında VSTO eklentisi tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Her yeni posta iletisinin konusuna ve gövdesine metin eklemek için

1. ThisAddIn kod dosyasında sınıfında adlı bir alan bildirin `inspectors` `ThisAddIn` . Bu `inspectors` alan, geçerli Outlook örneğindeki Inspector pencerelerinin koleksiyonuna bir başvuru tutar. Bu başvuru, çöp toplayıcısının olay işleyicisini içeren belleği boşaltmasını önler <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. `ThisAddIn_Startup` yöntemini aşağıdaki kodla değiştirin. Bu kod, olaya bir olay işleyicisi ekler <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. ThisAddIn kod dosyasında, sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Bu kod, olay için bir olay işleyicisini tanımlar <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> .

    Kullanıcı yeni bir posta iletisi oluşturduğunda, bu olay işleyicisi metin konu satırına ve iletinin gövdesine metin ekler.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   Her yeni posta iletisini değiştirmek için, önceki kod örnekleri aşağıdaki nesneleri kullanır:

- `Application` `ThisAddIn` Sınıfının alanı. `Application`Alan <xref:Microsoft.Office.Interop.Outlook.Application> , geçerli Outlook örneğini temsil eden bir nesne döndürür.

- `Inspector`Olay işleyicisinin olay işleyicisi parametresi <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> . `Inspector`Parametresi <xref:Microsoft.Office.Interop.Outlook.Inspector> , yeni posta iletisinin Inspector penceresini temsil eden bir nesnedir. Daha fazla bilgi için bkz. [Outlook çözümleri](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Projeyi test etme
 Projeyi derleyip çalıştırdığınızda, metnin konu satırında ve yeni bir posta iletisinin gövdesinde göründüğünü doğrulayın.

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın.

     Projeyi derlediğinizde kod, projenin yapı çıkış klasörüne dahil olan bir derlemeye derlenir. Visual Studio Ayrıca, Outlook 'un VSTO eklentisini bulmasını ve yüklemesini sağlayan bir kayıt defteri girişi kümesi oluşturur ve VSTO eklentisinin çalışmasını sağlamak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. Daha fazla bilgi için bkz. [Office çözümü derleme işlemine genel bakış](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. Outlook 'ta yeni bir posta iletisi oluşturun.

3. Aşağıdaki metnin hem konu satırına hem de iletinin gövdesine eklendiğini doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. Outlook 'U kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle
 Projeyi geliştirmeyi bitirdiğinizde, VSTO eklenti derlemesini, kayıt defteri girişlerini ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi halde, VSTO eklentisi geliştirme bilgisayarında Outlook 'U her açışınızda çalışır.

### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için

1. Visual Studio 'da, **Yapı** menüsünde **Çözümü Temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Outlook için temel bir VSTO eklentisi oluşturduğunuza göre, şu konulardan VSTO eklentileri geliştirme hakkında daha fazla bilgi edinebilirsiniz:

- Outlook için VSTO Eklentilerini kullanarak gerçekleştirebileceğiniz genel programlama görevleri. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- Outlook 'un nesne modelini kullanma. Daha fazla bilgi için bkz. [Outlook çözümleri](../vsto/outlook-solutions.md).

- Outlook 'un Kullanıcı arabirimini özelleştirme, örneğin, Şerite özel bir sekme ekleyerek veya kendi özel görev bölmenizi oluşturarak. Daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

- Outlook için VSTO eklentileri oluşturma ve hata ayıklama. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

- Outlook için VSTO eklentileri dağıtılıyor. Daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Outlook çözümleri](../vsto/outlook-solutions.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
