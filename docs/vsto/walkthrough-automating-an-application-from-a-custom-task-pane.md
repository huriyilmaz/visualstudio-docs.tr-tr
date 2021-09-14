---
title: 'Adım adım kılavuz: Özel görev bölmesinden uygulamayı otomatikleştirme'
description: Kullanıcı özel görev bölmesinde bir MonthCalendar denetimine tıkladığında bir slayta tarihler ekerek Microsoft PowerPoint'yi otomatikleştiren özel bir görev bölmesi oluşturun.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e31147694042309c77801d3058ea42fcdf6b8828
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725545"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Adım adım kılavuz: Özel görev bölmesinden uygulamayı otomatikleştirme
  Bu adım adım kılavuzda, özel bir görev bölmesinin nasıl oluşturularak otomatikleştir PowerPoint. Özel görev bölmesi, kullanıcı özel görev bölmesindeki bir denetime tıkladığında bir <xref:System.Windows.Forms.MonthCalendar> slayta tarih ekler.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu kılavuzda özellikle PowerPoint olsa da, izlenecek yol tarafından gösterilen kavramlar yukarıda listelenen tüm uygulamalar için geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel görev bölmesinin kullanıcı arabirimini tasarlama.

- Özel PowerPoint bölmesinden otomatik olarak yükleme.

- Özel görev bölmesini PowerPoint.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft® PowerPoint® 2010 veya [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Eklenti projesini oluşturma
 İlk adım, VSTO için bir Eklenti projesi PowerPoint.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. PowerPoint Proje şablonunu kullanarak **MyAddIn** PowerPoint VSTO bir eklenti projesi oluşturun. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** veya **ThisAddIn.vb** kod dosyasını açar ve **MyAddIn** projesini **Çözüm Gezgini.**

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlama
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz düzende bir kullanıcı denetimi tasarleyebilirsiniz. Bu kılavuzda daha sonra, kullanıcı denetimi özel görev bölmesine eklenecektir.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlamak için

1. Uygulama menüsünde **Project** Denetimi **Ekle'ye tıklayın.**

2. Yeni Öğe **Ekle iletişim** kutusunda, kullanıcı denetimi adını **MyUserControl** olarak değiştirin ve Ekle'ye **tıklayın.**

     Kullanıcı denetimi tasarımcıda açılır.

3. Araç **Kutusunun Ortak Denetimler** **sekmesinden bir** **MonthCalendar denetimi** sürükleyerek kullanıcı denetimine sürükleyin.

     **MonthCalendar denetimi,** kullanıcı denetimi tasarım yüzeyinden büyükse, kullanıcı denetimlerini **MonthCalendar** denetimine uyacak şekilde yeniden boyutlandırın.

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Özel PowerPoint bölmesinden otomatikleştirme
 Eklentinin VSTO, etkin sunumun ilk slaydına seçili tarihi koymaktır. Her <xref:System.Windows.Forms.MonthCalendar.DateChanged> değişiklikte seçili tarihi eklemek için denetimin olaylarını kullanın.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Özel PowerPoint bölmesinden otomatikleştirme

1. Tasarımcıda denetime çift <xref:System.Windows.Forms.MonthCalendar> tıklayın.

     **MyUserControl.cs** veya **MyUserControl.vb** dosyası açılır ve olay için bir olay <xref:System.Windows.Forms.MonthCalendar.DateChanged> işleyicisi oluşturulur.

2. Aşağıdaki kodu dosyanın en üstüne ekleyin. Bu kod, ad alanları için diğer <xref:Microsoft.Office.Core> [PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) oluşturur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet1":::

3. Aşağıdaki kodu `MyUserControl` sınıfına ekleyin. Bu kod, bir [Shape](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) nesnesini üyesi olarak `MyUserControl` bildirer. Aşağıdaki adımda bu Şekli kullanarak etkin [sunuda](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) bir slayta metin kutusu ekleyen bir metin kutusu eksersiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet2":::

4. Olay `monthCalendar1_DateChanged` işleyicisini aşağıdaki kodla değiştirin. Bu kod, etkin sunuda ilk slayta bir metin kutusu ekler ve ardından seçili olan tarihi metin kutusuna ekler. Bu kod, `Globals.ThisAddIn` nesnesini kullanarak uygulamanın nesne modeline PowerPoint.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet3":::

5. Bu **Çözüm Gezgini,** **MyAddIn projesine sağ tıklayın** ve ardından Derleme'ye **tıklayın.** Projenin hatasız olarak derlemesini doğrulayın.

## <a name="display-the-custom-task-pane"></a>Özel görev bölmesini görüntüleme
 Eklenti başlatıldığında özel görev bölmesini VSTO için, kullanıcı denetimi kullanıcı denetimlerini eklentinin olay işleyicisinde <xref:Microsoft.Office.Tools.AddIn.Startup> görev bölmesine VSTO ekleyin.

### <a name="to-display-the-custom-task-pane"></a>Özel görev bölmesini görüntülemek için

1. içinde **Çözüm Gezgini** genişletin ve **PowerPoint.**

2. **ThisAddIn.cs veya** **ThisAddIn.vb'ye** sağ tıklayın ve Kodu **Görüntüle'ye tıklayın.**

3. Aşağıdaki kodu `ThisAddIn` sınıfına ekleyin. Bu kod, ve örneklerini `MyUserControl` <xref:Microsoft.Office.Tools.CustomTaskPane> sınıfının üyeleri olarak `ThisAddIn` bildirer.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet4":::

4. Olay `ThisAddIn_Startup` işleyicisini aşağıdaki kodla değiştirin. Bu kod, nesnesini <xref:Microsoft.Office.Tools.CustomTaskPane> koleksiyona ekleyerek `MyUserControl` yeni bir `CustomTaskPanes` oluşturur. Kod, görev bölmesini de görüntüler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-add-in"></a>Eklentiyi Test Etmek
 Projeyi çalıştırarak PowerPoint açılır ve VSTO özel görev bölmesi görüntülenir. Kodu <xref:System.Windows.Forms.MonthCalendar> test etmek için denetime tıklayın.

### <a name="to-test-your-vsto-add-in"></a>Eklentinizi VSTO için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Özel görev bölmesinin görünür olduğunu onaylayın.

3. Görev bölmesinde <xref:System.Windows.Forms.MonthCalendar> denetimde bir tarihe tıklayın.

     Tarih, etkin sunuda ilk slayta eklenir.

## <a name="next-steps"></a>Sonraki adımlar
 Özel görev bölmeleri oluşturma hakkında daha fazla bilgi edinmek için şu konu başlıklarını kullanabilirsiniz:

- Farklı bir uygulama için bir VSTO özel görev bölmesi oluşturun. Özel görev bölmelerini destekleyen uygulamalar hakkında daha fazla bilgi için [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

- Özel görev bölmesini gizlemek veya görüntülemek için kullanılan bir Şerit düğmesi oluşturun. Daha fazla bilgi için [bkz. Adım adım: Şerit düğmesiyle özel görev bölmesini eşitleme.](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)

- Uygulama içinde açılan her e-posta iletisi için özel bir görev Outlook. Daha fazla bilgi için [bkz. Adım adım: Özel görev bölmelerini e-posta iletileriyle birlikte Outlook.](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Nasıl ekleyebilirsiniz: Uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Adım adım kılavuz: Özel görev bölmesini Şerit düğmesiyle eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Adım adım kılavuz: Özel görev bölmelerini e-posta iletileriyle birlikte Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
