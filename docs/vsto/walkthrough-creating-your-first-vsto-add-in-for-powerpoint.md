---
title: 'adım adım kılavuz: VSTO için İlk Eklentinizi PowerPoint'
description: Microsoft PowerPoint için uygulama düzeyinde bir eklenti oluşturun. Bu özellik, hangi sunumların açık olduğuna bakılmaksızın uygulamanın kendisi tarafından kullanılabilir.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 39998bb7d60b55405be13493900ef936c05c3032
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633761"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>adım adım kılavuz: VSTO için İlk Eklentinizi PowerPoint
  Bu kılavuzda, uygulama için VSTO Eklentinin nasıl Microsoft Office PowerPoint. Bu tür bir çözümde, hangi sunumların açık olduğuna bakılmaksızın uygulamanın kendisinde oluşturabilirsiniz. Daha fazla bilgi için [bkz. Office geliştirmeye genel bakış &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- PowerPoint VSTO için bir Eklenti projesi PowerPoint.

- Her yeni slayta metin kutusu eklemek PowerPoint nesne modelini kullanan kod yazma.

- Projeyi test etmek için bina ve çalıştırma.

- Eklentinin artık geliştirme bilgisayarınızda VSTO şekilde çalışması için projeyi temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.**

3. Şablonlar bölmesinde **Visual C#** veya **Visual Basic'ı** genişletin ve ardından **Office/SharePoint.**

4. Genişletilmiş **Office/SharePoint** altında, Office **düğümünü** seçin.

5. Proje şablonları listesinde, Eklenti projesini PowerPoint VSTO seçin.

6. Ad **kutusuna** **FirstPowerPointAddIn yazın.**

7. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstPowerPointAddIn projesini** oluşturur ve **ThisAddIn** kod dosyasını düzenleyicide açar.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Her yeni slayta metin ekleyen kod yazma
 Ardından ThisAddIn kod dosyasına kod ekleyin. Yeni kod, her yeni slayta PowerPoint metin kutusu eklemek için PowerPoint nesnesinin nesne modelini kullanır. Varsayılan olarak ThisAddIn kod dosyası aşağıdaki oluşturulan kodu içerir:

- Sınıfının kısmi `ThisAddIn` tanımı. Bu sınıf kodunuz için bir giriş noktası sağlar ve kodun nesne modeline PowerPoint. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md) Sınıfın geri `ThisAddIn` kalanı, değiştirmeyebilirsiniz gizli bir kod dosyasında tanımlanır.

- ve `ThisAddIn_Startup` olay `ThisAddIn_Shutdown` işleyicileri. Bu olay işleyicileri, PowerPoint eklentinizi yükler ve VSTO çağrılır. Bu olay işleyicilerini kullanarak VSTO eklentinizi başlatmak ve yüklemesi kaldırılan VSTO kaynaklarınızı temizlemek için kullanın. Daha fazla bilgi için [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-text-box-to-each-new-slide"></a>Her yeni slayta metin kutusu eklemek için

1. ThisAddIn kod dosyasında sınıfına aşağıdaki kodu `ThisAddIn` ekleyin. Bu kod, [Microsoft.Office için bir olay işleyicisi tanımlar. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) [olayı.](/previous-versions/office/developer/office-2010/ff764034(v=office.14))

    Kullanıcı etkin sunuya yeni bir slayt eklerse, bu olay işleyicisi yeni slaytın en üstüne bir metin kutusu ekler ve metin kutusuna metin ekler.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. C# kullanıyorsanız, olay işleyiciye aşağıdaki `ThisAddIn_Startup` kodu ekleyin. Bu kod, olay işleyicisini `Application_PresentationNewSlide` [Microsoft.Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olayı.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Her yeni slaydı değiştirmek için önceki kod örnekleri aşağıdaki nesneleri kullanır:

- `Application`sınıfının `ThisAddIn` alanı. alanı, `Application` [uygulamanın geçerli](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) örneğini temsil eden bir Application PowerPoint.

- `Sld` [Microsoft.Office için olay işleyicisi parametresi. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) olayı. parametresi, `Sld` yeni [slaydı](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) temsil eden bir Slayt nesnesidir. Daha fazla bilgi için [bkz. PowerPoint çözümleri.](../vsto/powerpoint-solutions.md)

## <a name="test-the-project"></a>Projeyi test etme
 Projeyi derleme ve çalıştırma sırasında, metin kutusunun sunuya ekley istediğiniz yeni slaytlarda görüntülendiğinden emin olmak.

### <a name="to-test-the-project"></a>Projeyi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5'e** basın.

     Projeyi derlerken kod, projenin derleme çıkış klasörüne konan bir derlemede derlenmiş olur. Visual Studio, PowerPoint'nin VSTO Eklentisini keşfetmesini ve yüklemesini sağlayan bir kayıt defteri girdisi kümesi de oluşturur ve geliştirme bilgisayarında güvenlik ayarlarını VSTO Eklentinin çalışmasına olanak sağlayacak şekilde yapılandırıyor. Daha fazla bilgi için [bkz. Derleme Office.](../vsto/building-office-solutions.md)

2. Bu PowerPoint etkin sunuya yeni bir slayt ekleyin.

3. Aşağıdaki metnin slaytın üst kısmında yer alan yeni bir metin kutusuna ekli olduğunu doğrulayın.

     **Bu metin kod kullanılarak eklenmiştir.**

4. PowerPoint.

## <a name="clean-up-the-project"></a>Projeyi temizleme
 Bir proje geliştirmeyi tamamlasanız, VSTO derleme, kayıt defteri girdileri ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırın. Aksi takdirde VSTO eklenti, geliştirme bilgisayarına her PowerPoint çalıştırabilirsiniz.

### <a name="to-clean-up-your-project"></a>Projenizi temizlemek için

1. Bu Visual Studio, Derleme **menüsünde Çözümü** Temizle'ye **tıklayın.**

## <a name="next-steps"></a>Sonraki adımlar
 PowerPoint için temel bir VSTO eklenti oluşturduğunuza göre, aşağıdaki konulardan VSTO geliştirme hakkında daha fazla bilgi öğrenebilirsiniz:

- Uygulama için Eklentilerde gerçekleştirebilirsiniz VSTO genel programlama PowerPoint. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

- Uygulamanın nesne modelini PowerPoint. Daha fazla bilgi için [bkz. PowerPoint çözümleri.](../vsto/powerpoint-solutions.md)

- Örneğin Şerit'PowerPoint özel bir sekme ekleyerek veya kendi özel görev bölmenizi oluşturarak kullanıcı arabirimini özelleştirme. Daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

- PowerPoint için VSTO eklentilerini PowerPoint. Daha fazla bilgi için [bkz. Derleme Office.](../vsto/building-office-solutions.md)

- VSTO için PowerPoint. Daha fazla bilgi için [bkz. Bir Office dağıtma.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Yeni Office oluşturma](../vsto/building-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Office şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
