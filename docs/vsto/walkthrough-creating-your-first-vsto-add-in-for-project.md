---
title: 'izlenecek yol: Project için ilk VSTO eklentiyi oluşturma'
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5eb3a5c91b4ebe9b0c3b447c0705c889c2975c72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031983"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>izlenecek yol: Project için ilk VSTO eklentiyi oluşturma
  bu izlenecek yol, Microsoft Office Project için VSTO eklentisi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler, hangi projelerin açık olduğuna bakılmaksızın uygulamanın kendisi için kullanılabilir. daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Project VSTO eklenti projesi oluşturma.

- yeni bir projeye görev eklemek için Project nesne modelini kullanan kod yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- VSTO eklentisinin geliştirme bilgisayarınızda artık otomatik olarak çalışmamasını sağlamak için tamamlanmış projeyi temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] veya [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-project-in-visual-studio"></a>Visual Studio yeni bir proje oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.

3. şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' yı genişletin.

4. genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

5. proje şablonları listesinde **Project 2010 eklentisi** veya **Project 2013 eklentisi**' ni seçin.

6. **Ad** kutusuna **FirstProjectAddIn** yazın.

7. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstProjectAddIn** projesini oluşturur ve **ThisAddIn** kod dosyasını düzenleyicide açar.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Projeye yeni bir görev ekleyen kodu yazın
 Ardından, ThisAddIn kod dosyasına kod ekleyin. yeni kod, bir projeye yeni bir görev eklemek için Project nesne modelini kullanır. Varsayılan olarak, ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfın kısmi tanımı `ThisAddIn` . Bu sınıf, kodunuz için bir giriş noktası sağlar ve Project nesne modeline erişim sağlar. daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Sınıfın geri kalanı, `ThisAddIn` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `ThisAddIn_Startup`Ve `ThisAddIn_Shutdown` olay işleyicileri. bu olay işleyicileri, Project VSTO eklentinizi yüklediğinde ve kaldırıldığında çağırılır. bu olay işleyicilerini, yüklendiğinde VSTO eklentisini başlatmak ve VSTO eklentisi tarafından kullanılan kaynakları temizleyene kadar temizlemek için kullanın. daha fazla bilgi için bkz. [Office projelerindeki olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Yeni bir projeye görev eklemek için

1. ThisAddIn kod dosyasında, sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Bu kod, sınıfının olayı için bir olay işleyicisini tanımlar `NewProject` `Microsoft.Office.Interop.MSProject.Application` .

    Kullanıcı yeni bir proje oluşturduğunda, bu olay işleyicisi projeye bir görev ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet1":::

   Projeyi değiştirmek için, bu kod örneği aşağıdaki nesneleri kullanır:

- `Application` `ThisAddIn` Sınıfının alanı. `Application`Alan, `Microsoft.Office.Interop.MSProject.Application` Project geçerli örneğini temsil eden bir nesne döndürür.

- `pj`NewProject olayı için olay işleyicisinin parametresi. `pj`Parametresi `Microsoft.Office.Interop.MSProject.Project` , projeyi temsil eden bir nesnedir. daha fazla bilgi için bkz. [Project çözümleri](../vsto/project-solutions.md).

1. C# kullanıyorsanız, olay işleyicisine aşağıdaki kodu ekleyin `ThisAddIn_Startup` . Bu kod, `Application_Newproject` olay Işleyicisini NewProject olayı ile bağlar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet2":::

## <a name="test-the-project"></a>Projeyi test etme
 Projeyi derleyip çalıştırdığınızda yeni görevin ortaya çıkan yeni projede göründüğünü doğrulayın.

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın. Microsoft Project başlar ve yeni boş bir projeyi otomatik olarak açar.

     Projeyi derlediğinizde kod, projenin yapı çıkış klasörüne dahil olan bir derlemeye derlenir. Visual Studio ayrıca, Project VSTO eklentisini bulmasını ve yüklemesini sağlayan bir kayıt defteri girişleri kümesi oluşturur ve VSTO eklentisinin çalışmasını sağlamak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. daha fazla bilgi için bkz. [Office çözüm oluşturma işlemine genel bakış](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Boş projeye yeni bir görevin eklendiğini doğrulayın.

3. Görevin **görev adı** alanında aşağıdaki metnin göründüğünü doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. Microsoft Project kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle
 projeyi geliştirmeyi bitirdiğinizde, VSTO eklenti derlemesini, kayıt defteri girişlerini ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. aksi takdirde, VSTO eklentisi geliştirme bilgisayarında Microsoft Project her açışınızda çalışacaktır.

### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için

1. Visual Studio, **yapı** menüsünde **çözümü temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Project için temel bir VSTO eklentisi oluşturduğunuza göre, şu konulardan VSTO eklentileri geliştirme hakkında daha fazla bilgi edinebilirsiniz:

- Project için VSTO eklentilerinde gerçekleştirebileceğiniz genel programlama görevleri: [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- Project nesne modelini kullanma: [Project çözümleri](../vsto/project-solutions.md).

- Project için VSTO eklentileri oluşturma ve hata ayıklama: [derleme Office çözümleri](../vsto/building-office-solutions.md).

- Project için VSTO eklentileri dağıtma: [bir Office çözümü dağıtın](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Project çözümleri](../vsto/project-solutions.md)
- [Office çözümleri oluşturun](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
