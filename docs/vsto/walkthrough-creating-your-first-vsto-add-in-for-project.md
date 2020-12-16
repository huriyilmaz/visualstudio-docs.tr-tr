---
title: 'İzlenecek yol: proje için ilk VSTO eklentisini oluşturma'
description: Microsoft Project için uygulama düzeyi eklentisi oluşturun. Bu özellik, hangi projelerin açık olduğuna bakılmaksızın uygulamanın kendisi için kullanılabilir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f4774b8f5ba55d54e05e3a9ef18f8ea13fd48fc
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527902"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>İzlenecek yol: proje için ilk VSTO eklentisini oluşturma
  Bu izlenecek yol, Microsoft Office projesi için bir VSTO eklentisi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler, hangi projelerin açık olduğuna bakılmaksızın uygulamanın kendisi için kullanılabilir. Daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Proje VSTO eklentisi projesi oluşturma.

- Yeni bir projeye görev eklemek için projenin nesne modelini kullanan kodu yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- VSTO eklentisinin geliştirme bilgisayarınızda artık otomatik olarak çalışmamasını sağlamak için tamamlanmış projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] veya [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-project-in-visual-studio"></a>Visual Studio 'da yeni bir proje oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' i genişletin.

4. Genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

5. Proje şablonları listesinde **project 2010 eklentisi** veya **Project 2013 eklentisi**' ni seçin.

6. **Ad** kutusuna **FirstProjectAddIn** yazın.

7. **Tamam** düğmesine tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstProjectAddIn** projesini oluşturur ve **ThisAddIn** kod dosyasını düzenleyicide açar.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Projeye yeni bir görev ekleyen kodu yazın
 Ardından, ThisAddIn kod dosyasına kod ekleyin. Yeni kod, projeye yeni bir görev eklemek için proje nesne modelini kullanır. Varsayılan olarak, ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi tanımı `ThisAddIn` . Bu sınıf, kodunuz için bir giriş noktası sağlar ve projenin nesne modeline erişim sağlar. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Sınıfın geri kalanı, `ThisAddIn` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `ThisAddIn_Startup`Ve `ThisAddIn_Shutdown` olay işleyicileri. Bu olay işleyicileri, proje VSTO eklentinizi yüklediğinde ve kaldırıldığında çağrılır. Bu olay işleyicilerini, yüklendiğinde VSTO eklentisini başlatmak ve bu etkinlik kaldırıldığında VSTO eklentisi tarafından kullanılan kaynakları temizlemek için kullanın. Daha fazla bilgi için bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Yeni bir projeye görev eklemek için

1. ThisAddIn kod dosyasında, sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Bu kod, sınıfının olayı için bir olay işleyicisini tanımlar `NewProject` `Microsoft.Office.Interop.MSProject.Application` .

    Kullanıcı yeni bir proje oluşturduğunda, bu olay işleyicisi projeye bir görev ekler.

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   Projeyi değiştirmek için, bu kod örneği aşağıdaki nesneleri kullanır:

- `Application` `ThisAddIn` Sınıfının alanı. `Application`Alan, `Microsoft.Office.Interop.MSProject.Application` projenin geçerli örneğini temsil eden bir nesne döndürür.

- `pj`NewProject olayı için olay işleyicisinin parametresi. `pj`Parametresi `Microsoft.Office.Interop.MSProject.Project` , projeyi temsil eden bir nesnedir. Daha fazla bilgi için bkz. [proje çözümleri](../vsto/project-solutions.md).

1. C# kullanıyorsanız, olay işleyicisine aşağıdaki kodu ekleyin `ThisAddIn_Startup` . Bu kod, `Application_Newproject` olay Işleyicisini NewProject olayı ile bağlar.

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>Projeyi test etme
 Projeyi derleyip çalıştırdığınızda yeni görevin ortaya çıkan yeni projede göründüğünü doğrulayın.

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın. Microsoft Project başlar ve yeni boş bir projeyi otomatik olarak açar.

     Projeyi derlediğinizde kod, projenin yapı çıkış klasörüne dahil olan bir derlemeye derlenir. Visual Studio Ayrıca, proje 'nin VSTO eklentisini bulmasını ve yüklemesini sağlayan bir kayıt defteri girişleri kümesi oluşturur ve VSTO eklentisinin çalışmasını sağlamak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. Daha fazla bilgi için bkz. [Office çözümü derleme işlemine genel bakış](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Boş projeye yeni bir görevin eklendiğini doğrulayın.

3. Görevin **görev adı** alanında aşağıdaki metnin göründüğünü doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. Microsoft Project 'i kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle
 Projeyi geliştirmeyi bitirdiğinizde, VSTO eklenti derlemesini, kayıt defteri girişlerini ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi halde, Microsoft Project 'i geliştirme bilgisayarında her açışınızda VSTO eklentisi çalışacaktır.

### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için

1. Visual Studio 'da, **Yapı** menüsünde **Çözümü Temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Project için temel bir VSTO eklentisi oluşturduğunuza göre, şu konulardan VSTO eklentileri geliştirme hakkında daha fazla bilgi edinebilirsiniz:

- Proje için VSTO eklentileri içinde gerçekleştirebileceğiniz genel programlama görevleri: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- Projenin nesne modelini kullanma: [proje çözümleri](../vsto/project-solutions.md).

- Proje için VSTO eklentileri oluşturma ve hata ayıklama: [Office çözümlerini derleme](../vsto/building-office-solutions.md).

- Proje için VSTO eklentileri dağıtma: [bir Office çözümü dağıtın](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Proje çözümleri](../vsto/project-solutions.md)
- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
