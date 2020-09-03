---
title: 'İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5135e96125192d7ed125287aa47c839031824fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871927"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme
  Bu izlenecek yol, PowerPoint 'i otomatikleştiren özel bir görev bölmesinin nasıl oluşturulacağını gösterir. Özel görev bölmesi, Kullanıcı özel görev bölmesindeki bir denetime tıkladığında tarihleri bir slayda ekler <xref:System.Windows.Forms.MonthCalendar> .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu anlatım özellikle PowerPoint 'i kullanıyor olsa da, izlenecek yol tarafından gösterilen kavramlar yukarıda listelenen tüm uygulamalar için geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel görev bölmesinin kullanıcı arabirimini tasarlama.

- PowerPoint 'i özel görev bölmesinden otomatikleştirme.

- Özel görev bölmesini PowerPoint 'te görüntüleme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 veya [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Eklenti projesi oluşturma
 İlk adım, PowerPoint için VSTO eklentisi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. PowerPoint eklentisi proje şablonunu kullanarak, **mdın**adlı BIR PowerPoint VSTO eklentisi projesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** veya **ThisAddIn. vb** kod dosyasını açar ve **Çözüm Gezgini**için **mdın** projesini ekler.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlama
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz düzende bir kullanıcı denetimi tasarlayabilirsiniz. Bu izlenecek yolda daha sonra Kullanıcı denetimini özel görev bölmesine ekleyeceksiniz.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlamak için

1. **Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** iletişim kutusunda, Kullanıcı denetiminin adını **MyUserControl**olarak değiştirin ve **Ekle**' ye tıklayın.

     Kullanıcı denetimi tasarımcıda açılır.

3. **Araç kutusunun** **ortak denetimler** sekmesinden, bir **MonthCalendar** denetimini Kullanıcı denetimine sürükleyin.

     **MonthCalendar** denetimi, Kullanıcı denetiminin tasarım yüzeyinden daha büyükse, Kullanıcı denetimini **MonthCalendar** denetimine sığacak şekilde yeniden boyutlandırın.

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Özel görev bölmesinden PowerPoint 'i otomatikleştirin
 VSTO eklentisinin amacı, etkin sununun ilk slaytına seçili bir tarih koyeklemektir. <xref:System.Windows.Forms.MonthCalendar.DateChanged>Her değiştiğinde seçili tarihi eklemek için denetimin olayını kullanın.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>PowerPoint 'i özel görev bölmesinden otomatik hale getirmek için

1. Tasarımcıda denetime çift tıklayın <xref:System.Windows.Forms.MonthCalendar> .

     **MyUserControl.cs** veya **MyUserControl. vb** dosyası açılır ve olay için bir olay işleyicisi <xref:System.Windows.Forms.MonthCalendar.DateChanged> oluşturulur.

2. Aşağıdaki kodu dosyanın en üstüne ekleyin. Bu kod, <xref:Microsoft.Office.Core> ve [PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) ad alanları için diğer adlar oluşturur.

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. Sınıfına aşağıdaki kodu ekleyin `MyUserControl` . Bu kod, bir [Şekil](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) nesnesini öğesinin üyesi olarak bildirir `MyUserControl` . Aşağıdaki adımda, etkin sunudaki bir slayda metin kutusu eklemek için bu [şekli](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) kullanacaksınız.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. `monthCalendar1_DateChanged`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, etkin sunudaki ilk slayda bir metin kutusu ekler ve sonra şu anda seçili tarihi metin kutusuna ekler. Bu kod, `Globals.ThisAddIn` PowerPoint nesne modeline erişmek için nesnesini kullanır.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. **Çözüm Gezgini**, **mdın** projesine sağ tıklayın ve ardından **Oluştur**' a tıklayın. Projenin hata olmadan yapılandırıldığını doğrulayın.

## <a name="display-the-custom-task-pane"></a>Özel görev bölmesini görüntüleme
 VSTO eklentisi başladığında özel görev bölmesini göstermek için, <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisinin olay işleyicisindeki görev bölmesine Kullanıcı denetimini ekleyin.

### <a name="to-display-the-custom-task-pane"></a>Özel görev bölmesini görüntüleme

1. **Çözüm Gezgini**' de **PowerPoint**' i genişletin.

2. **ThisAddIn.cs** veya **ThisAddIn. vb** öğesine sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

3. Sınıfına aşağıdaki kodu ekleyin `ThisAddIn` . Bu kod `MyUserControl` <xref:Microsoft.Office.Tools.CustomTaskPane> , sınıfının üyeleri olarak ve örneklerini bildirir `ThisAddIn` .

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. `ThisAddIn_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, <xref:Microsoft.Office.Tools.CustomTaskPane> nesneyi koleksiyona ekleyerek yeni bir oluşturur `MyUserControl` `CustomTaskPanes` . Kod ayrıca görev bölmesini de görüntüler.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>Eklentiyi test etme
 Projeyi çalıştırdığınızda, PowerPoint açılır ve VSTO eklentisi özel görev bölmesini görüntüler. <xref:System.Windows.Forms.MonthCalendar>Kodu test etmek için denetime tıklayın.

### <a name="to-test-your-vsto-add-in"></a>VSTO eklentisini test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Özel görev bölmesinin görünür olduğunu onaylayın.

3. <xref:System.Windows.Forms.MonthCalendar>Görev bölmesindeki denetimde bir tarihe tıklayın.

     Tarih, etkin sunudaki ilk slayda eklenir.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan özel görev bölmeleri oluşturma hakkında daha fazla bilgi edinebilirsiniz:

- Farklı bir uygulama için VSTO eklentisi içinde özel bir görev bölmesi oluşturun. Özel görev bölmelerini destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

- Özel bir görev bölmesini gizlemek veya göstermek için kullanılabilen bir Şerit düğmesi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: özel görev bölmesini Şerit düğmesi Ile senkronize](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)etme.

- Outlook 'ta açılan her e-posta iletisi için özel bir görev bölmesi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: Outlook 'ta e-posta iletileriyle özel görev bölmeleri görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile senkronize etme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [İzlenecek yol: Outlook 'ta e-posta iletileriyle özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
