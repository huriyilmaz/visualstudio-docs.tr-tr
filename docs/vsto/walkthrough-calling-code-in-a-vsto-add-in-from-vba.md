---
title: "Kılavuz: VBA'dan VSTO eklentisinde kod çağırma"
description: Visual Basic for Applications (VBA) ve COM eklentilerini içeren VSTO eklentisinde bir nesneyi Microsoft Office eklentisinde nasıl VSTO öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: edde3dc96ed0440981b79828c82331608e0f2f7a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726101"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Kılavuz: VBA'dan VSTO eklentisinde kod çağırma
  Bu kılavuzda, Visual Basic for Applications (VBA) ve COM eklentilerini içeren VSTO Eklentisinde bir nesnenin Microsoft Office çözümlerde nasıl VSTO gösterileceğini gösterir.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Bu kılavuzda özellikle Excel olsa da, izlenecek yol tarafından gösterilen kavramlar, VSTO proje şablonu tarafından sağlanan tüm Visual Studio.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Diğer çözüm çözümlerine açık olan bir sınıf Office tanımlama.

- Sınıfı diğer çözüm çözümlerine Office.

- VBA kodundan sınıfının yöntemini çağırma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>VSTO Eklenti projesini oluşturma
 İlk adım, VSTO için bir eklenti projesi Excel.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. Excel VSTO Excel VSTO Add-in proje şablonunu kullanarak **ExcelImportData** Excel VSTO bir Eklenti projesi oluşturun. Daha fazla bilgi için, [bkz. How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** veya **ThisAddIn.vb** kod dosyasını açar ve **ExcelImportData** projesini **Çözüm Gezgini.**

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Diğer çözüm çözümlerine açık bir sınıf Office tanımlama
 Bu kılavuzda amaç, VBA kodundan eklentiyi kullanarak VSTO `ImportData` `AddInUtilities` yöntemine çağrı yapmaktır. Bu yöntem, etkin çalışma sayfasının A1 hücresine bir dize yazar.

 Sınıfı diğer `AddInUtilities` çözüm çözümlerine Office için, sınıfı genel ve COM'da görünür hale gelir. Ayrıca sınıfında [IDispatch arabirimini](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) de açığa çıkarmalısiniz. Aşağıdaki yordamda yer alan kod, bu gereksinimleri karşılamanın bir yolunu gösteriyor. Daha fazla bilgi için [bkz. Diğer VSTO Çözümlerinden Eklentilerde Kod Office Çağırma.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Diğer çözüm çözümlerine açık bir sınıf Office için

1. Yeni **Project** Sınıf Ekle'ye **tıklayın.**

2. Yeni Öğe **Ekle iletişim** kutusunda, yeni sınıfın adını **AddInUtilities olarak değiştirin** ve Ekle'ye **tıklayın.**

     **Kod Düzenleyicisi'nde AddInUtilities.cs** veya **AddInUtilities.vb** dosyası açılır.

3. Aşağıdaki yönergeleri dosyanın en üstüne ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. sınıfını `AddInUtilities` aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     Bu kod, `AddInUtilities` sınıfı COM'da görünür hale gelir ve `ImportData` sınıfına yöntemini ekler. [IDispatch arabirimini](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ortaya çıkarmak için sınıfı özniteliğine de sahiptir ve `AddInUtilities` COM tarafından <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> görülebilen bir arabirim uygulamaz.

## <a name="expose-the-class-to-other-office-solutions"></a>Sınıfını diğer Office ortaya çıkarma
 Sınıfı diğer `AddInUtilities` çözüm çözümlerine Office için <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> sınıfındaki yöntemini geçersiz `ThisAddIn` kılın. Geçersiz kılmada sınıfının bir örneğini `AddInUtilities` geri dön.

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>AddInUtilities sınıfını diğer Office çözümlerine göstermek için

1. içinde **Çözüm Gezgini** genişletin ve **Excel.**

2. **ThisAddIn.cs veya** **ThisAddIn.vb**'ye sağ tıklayın ve ardından Kodu **Görüntüle'ye tıklayın.**

3. Aşağıdaki kodu `ThisAddIn` sınıfına ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

     Çözümün hatasız olarak derlemesi olduğunu doğrulayın.

## <a name="test-the-vsto-add-in"></a>VSTO Eklentiyi Test
 Çeşitli farklı türlerde `AddInUtilities` çözümlerden sınıfına çağrı Office. Bu kılavuzda, bir çalışma kitabında VBA Excel kullansınız. Kullanabileceğiniz diğer Office hakkında daha fazla bilgi için bkz. Diğer VSTO çözümlerinden [eklentilerde kod Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

### <a name="to-test-your-vsto-add-in"></a>Eklentinizi VSTO için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Bu Excel çalışma kitabını çalışma kitabı (*.xlsm) Excel Macro-Enabled çalışma kitabı olarak kaydedin. Masaüstü gibi uygun bir konuma kaydedin.

3. Şeritte Geliştirici **sekmesine** tıklayın.

    > [!NOTE]
    > Geliştirici **sekmesi** görünmüyorsa, önce bunu göstermeniz gerekir. Daha fazla bilgi için [Bkz. Nasıl 2. Nasıl? Şeritte geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

4. Kod **grubunda,** öğesini **seçin** Visual Basic.

     Visual Basic Düzenleyicisi açılır.

5. Yeni **Project** **ThisWorkbook'a çift tıklayın.**

     Nesnenin kod `ThisWorkbook` dosyası açılır.

6. Aşağıdaki VBA kodunu kod dosyasına ekleyin. Bu kod önce **ExcelImportData** ve Eklentiyi temsil eden bir COMAddIn VSTO alır. Ardından kod, yöntemini çağıran COMAddIn nesnesinin Object özelliğini `ImportData` kullanır.

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. **F5 tuşuna basın.**

8. Çalışma kitabına yeni **bir İçe** Aktarılan Veri sayfası ekli olduğunu doğrulayın. Ayrıca A1 hücresinde Bu verilerim **dizesini içerdiğini doğrulayın.**

9. Çıkış Excel.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan ek eklentilerini VSTO programlama hakkında daha fazla bilgi edinmek için:

- Konak uygulamasını `ThisAddIn` otomatikleştirmek ve eklenti projelerinde diğer görevleri gerçekleştirmek VSTO sınıfını kullanın. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

- Bir eklentide özel bir VSTO bölmesi oluşturun. Daha fazla bilgi için [bkz. Özel görev bölmeleri](../vsto/custom-task-panes.md) [ve Nasıl ekleyebilirsiniz: Uygulamaya özel görev bölmesi ekleme.](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

- Eklentinin bir VSTO özelleştirin. Daha fazla bilgi için [bkz.](../vsto/ribbon-overview.md) [Şerit'e genel bakış ve Kullanmaya başlayın özelleştirme.](../vsto/how-to-get-started-customizing-the-ribbon.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Diğer VSTO çözümlerinden eklentilerde kod Office çağırma](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Genişletilebilirlik arabirimlerini kullanarak kullanıcı arabirimi özelliklerini özelleştirme](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
