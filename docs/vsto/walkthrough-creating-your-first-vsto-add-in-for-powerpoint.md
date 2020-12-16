---
title: 'İzlenecek yol: PowerPoint için ilk VSTO eklentisini oluşturma'
description: Microsoft PowerPoint için uygulama düzeyi eklentisi oluşturun. Bu özellik, hangi sunuların açık olduğuna bakılmaksızın uygulamanın kendisi tarafından kullanılabilir.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e02da3484ce7c2beb35e643d3d90d8e37225e11
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524859"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>İzlenecek yol: PowerPoint için ilk VSTO eklentisini oluşturma
  Bu izlenecek yol, PowerPoint Microsoft Office için VSTO eklentisi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler, hangi sunuların açık olduğuna bakılmaksızın uygulamanın kendisi için kullanılabilir. Daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- PowerPoint için PowerPoint VSTO eklentisi projesi oluşturma.

- Her yeni slayda metin kutusu eklemek için PowerPoint nesne modelini kullanan kodu yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- VSTO eklentisinin geliştirme bilgisayarınızda artık otomatik olarak çalışmamasını sağlamak için projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' i genişletin.

4. Genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

5. Proje şablonları listesinde bir PowerPoint VSTO eklentisi projesi seçin.

6. **Ad** kutusuna **FirstPowerPointAddIn** yazın.

7. **Tamam** düğmesine tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstPowerPointAddIn** projesini oluşturur ve **ThisAddIn** kod dosyasını düzenleyicide açar.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Her yeni slayda metin ekleyen kodu yazın
 Ardından, ThisAddIn kod dosyasına kod ekleyin. Yeni kod, her yeni slayda metin kutusu eklemek için PowerPoint nesne modelini kullanır. Varsayılan olarak, ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi tanımı `ThisAddIn` . Bu sınıf, kodunuz için bir giriş noktası sağlar ve PowerPoint 'in nesne modeline erişim sağlar. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Sınıfın geri kalanı, `ThisAddIn` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `ThisAddIn_Startup`Ve `ThisAddIn_Shutdown` olay işleyicileri. Bu olay işleyicileri, PowerPoint, VSTO eklentinizi yüklerken ve kaldırıldığında çağrılır. Bu olay işleyicilerini, yüklendiğinde VSTO eklentisini başlatmak ve bu etkinlik kaldırıldığında VSTO eklentisi tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-text-box-to-each-new-slide"></a>Her yeni slayda metin kutusu eklemek için

1. ThisAddIn kod dosyasında, sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Bu kod, [uygulama](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) nesnesinin [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olayı için bir olay işleyicisi tanımlar.

    Kullanıcı etkin sunuya yeni bir slayt eklediğinde, bu olay işleyicisi yeni slaydın üst kısmına bir metin kutusu ekler ve metin kutusuna bazı metinler ekler.

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. C# kullanıyorsanız, olay işleyicisine aşağıdaki kodu ekleyin `ThisAddIn_Startup` . `Application_PresentationNewSlide`Olay işleyicisini [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olayına bağlamak için bu kod gereklidir.

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   Yeni bir slaytı değiştirmek için, önceki kod örnekleri aşağıdaki nesneleri kullanır:

- `Application` `ThisAddIn` Sınıfının alanı. `Application`Alan, PowerPoint 'in geçerli örneğini temsil eden bir [uygulama](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) nesnesi döndürür.

- `Sld` [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olayı için olay işleyicisinin parametresi. `Sld`Parametresi, yeni slaytı temsil eden bir [Slayt](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) nesnesidir. Daha fazla bilgi için bkz. [PowerPoint çözümleri](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Projeyi test etme
 Projeyi derleyip çalıştırdığınızda, metin kutusunun bir sunuya eklediğiniz yeni slaytlarda göründüğünü doğrulayın.

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın.

     Projeyi derlediğinizde kod, projenin yapı çıkış klasörüne yerleştirilen bir derlemeye derlenir. Visual Studio Ayrıca, PowerPoint 'In VSTO eklentisini bulmasını ve yüklemesini sağlayan bir kayıt defteri girişleri kümesi oluşturur ve VSTO eklentisinin çalışmasını sağlamak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

2. PowerPoint 'te etkin sunuya yeni bir slayt ekleyin.

3. Slaydın en üstünde yer alan yeni bir metin kutusuna aşağıdaki metnin eklendiğini doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. PowerPoint 'i kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle
 Projeyi geliştirmeyi bitirdiğinizde, VSTO eklenti derlemesini, kayıt defteri girişlerini ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi halde, VSTO eklentisi geliştirme bilgisayarında PowerPoint 'i her açışınızda çalışır.

### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için

1. Visual Studio 'da, **Yapı** menüsünde **Çözümü Temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 PowerPoint için temel bir VSTO eklentisi oluşturduğunuza göre, şu konulardan VSTO eklentileri geliştirme hakkında daha fazla bilgi edinebilirsiniz:

- PowerPoint için VSTO eklentilerinde gerçekleştirebileceğiniz genel programlama görevleri. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- PowerPoint nesne modelini kullanma. Daha fazla bilgi için bkz. [PowerPoint çözümleri](../vsto/powerpoint-solutions.md).

- PowerPoint 'in Kullanıcı arabirimini özelleştirme, örneğin, şerit 'e özel bir sekme ekleyerek veya kendi özel görev bölmenizi oluşturarak. Daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

- PowerPoint için VSTO Eklentilerini derleme ve hata ayıklama. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

- PowerPoint için VSTO eklentileri dağıtma. Daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
