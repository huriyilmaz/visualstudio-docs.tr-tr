---
title: Özel görev bölmesini Şerit düğmesi ile senkronize etme
description: Şeritteki bir iki durumlu düğmeye tıklayarak kullanıcıların gizleyebileceğiniz veya görüntüleyeceği özel bir görev bölmesi oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7453d221cf57188a2c2f589492e4df59817f2cd9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526086"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>İzlenecek yol: özel görev bölmesini Şerit düğmesi ile senkronize etme
  Bu izlenecek yol, Şeritteki iki durumlu düğmeye tıklayarak kullanıcıların gizleyebileceğiniz veya görüntüleyeceği özel bir görev bölmesi oluşturmayı gösterir. Microsoft Office uygulamalar, kullanıcıların özel görev bölmelerini göstermek veya gizlemek için varsayılan bir yol sağlamadığından, bir düğme gibi her zaman bir kullanıcı arabirimi (UI) öğesi oluşturmalısınız.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu izlenecek yol Excel 'i özel olarak kullanıyor olsa da, izlenecek yol tarafından gösterilen kavramlar yukarıda listelenen tüm uygulamalar için geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel görev bölmesinin kullanıcı arabirimini tasarlama.

- Şerit 'e iki durumlu düğme ekleme.

- İki durumlu düğmeyi özel görev bölmesiyle eşitleme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel veya Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Eklenti projesi oluşturma
 Bu adımda, Excel için bir VSTO eklentisi projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Excel eklentisi proje şablonunu kullanarak **SynchronizeTaskPaneAndRibbon** adlı bir Excel eklentisi projesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn.cs** veya **ThisAddIn. vb** kod dosyasını açar ve **SynchronizeTaskPaneAndRibbon** projesini **Çözüm Gezgini** ekler.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Şerit 'e iki durumlu düğme Ekle
 Office uygulaması tasarım yönergelerinden biri, kullanıcıların her zaman Office uygulaması kullanıcı arabirimi denetimine sahip olması gerekir. Kullanıcıların özel görev bölmesini denetlemesine olanak tanımak için, görev bölmesini gösteren ve gizleyen bir şerit iki durumlu düğme ekleyebilirsiniz. İki durumlu düğme oluşturmak için projeye **Şerit (görsel Tasarımcı)** öğesi ekleyin. Tasarımcı denetimleri eklemenize ve konumlandıramanıza, denetim özelliklerini ayarlamanıza ve denetim olaylarını işleymenize yardımcı olur. Daha fazla bilgi için bkz. [Şerit Tasarımcısı](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Şerit 'e iki durumlu düğme eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şeridin adını **ManageTaskPaneRibbon** olarak değiştirin ve **Ekle**' ye tıklayın.

     **ManageTaskPaneRibbon.cs** veya **ManageTaskPaneRibbon. vb** dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit tasarımcısında, **grup1**' e tıklayın.

5. **Özellikler** penceresinde, **etiket** özelliğini **görev bölmesi Yöneticisi** olarak ayarlayın.

6. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden, **görev bölmesi Yöneticisi** grubuna bir **ToggleButton** sürükleyin.

7. **ToggleButton1** tıklayın.

8. **Özellikler** penceresinde, **etiket** özelliğini **görev bölmesini göster** olarak ayarlayın.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlama
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz düzende bir kullanıcı denetimi tasarlayabilirsiniz. Bu izlenecek yolda daha sonra Kullanıcı denetimini özel görev bölmesine ekleyeceksiniz.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlamak için

1. **Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** iletişim kutusunda, Kullanıcı denetiminin adını **TaskPaneControl** olarak değiştirin ve **Ekle**' ye tıklayın.

     Kullanıcı denetimi tasarımcıda açılır.

3. **Araç kutusunun** **ortak denetimler** sekmesinden kullanıcı denetimine bir **TextBox** denetimi sürükleyin.

## <a name="create-the-custom-task-pane"></a>Özel görev bölmesini oluşturma
 VSTO eklentisi başladığında özel görev bölmesini oluşturmak için, <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisinin olay işleyicisindeki görev bölmesine Kullanıcı denetimini ekleyin. Varsayılan olarak, özel görev bölmesi görünür olmayacaktır. Bu izlenecek yolda daha sonra, Kullanıcı Şerit 'e eklediğiniz iki durumlu düğmeye tıkladığında görev bölmesini görüntüleyecek veya gizleyecek kodu ekleyeceksiniz.

### <a name="to-create-the-custom-task-pane"></a>Özel görev bölmesini oluşturmak için

1. **Çözüm Gezgini**, **Excel**' i genişletin.

2. **ThisAddIn.cs** veya **ThisAddIn. vb** öğesine sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

3. Aşağıdaki kodu `ThisAddIn` sınıfına ekleyin. Bu kod, üyesi olarak bir örneğini bildirir `TaskPaneControl` `ThisAddIn` .

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. `ThisAddIn_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, `TaskPaneControl` nesnesini `CustomTaskPanes` alana ekler, ancak özel görev bölmesini görüntülemez (varsayılan olarak, <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> <xref:Microsoft.Office.Tools.CustomTaskPane> sınıfının özelliği **false**'dur). Visual C# kodu ayrıca olaya bir olay işleyicisi ekler <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> .

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu yöntem olayı işler <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> . Kullanıcı, **Kapat** düğmesine (X) tıklayarak görev bölmesini kapattığında, bu yöntem Şeritteki iki durumlu düğmenin durumunu güncelleştirir.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. Sınıfına aşağıdaki özelliği ekleyin `ThisAddIn` . Bu özellik özel `myCustomTaskPane1` nesneyi diğer sınıflara gösterir. Bu izlenecek yolda daha sonra `MyRibbon` Bu özelliği kullanan sınıfa kod ekleyeceksiniz.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>İki durumlu düğmeyi kullanarak özel görev bölmesini gizleme ve görüntüleme
 Son adım, Kullanıcı Şeritteki iki durumlu düğmeye tıkladığında özel görev bölmesini görüntüleyen veya gizleyen kodu eklemektir.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>İki durumlu düğmeyi kullanarak özel görev bölmesini görüntüleme ve gizleme

1. Şerit tasarımcısında **görev bölmesini göster** iki durumlu düğmesine çift tıklayın.

     Visual Studio, `toggleButton1_Click` <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olayını işleyen adlı bir olay işleyicisini otomatik olarak oluşturur. Visual Studio Ayrıca kod düzenleyicisinde *MyRibbon.cs* veya *MyRibbon. vb* dosyasını açar.

2. `toggleButton1_Click`Olay işleyicisini aşağıdaki kodla değiştirin. Kullanıcı iki durumlu düğmeye tıkladığında, bu kod geçiş düğmesine basıldığında veya basılmamış olmasına bağlı olarak özel görev bölmesini görüntüler veya gizler.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>Eklentiyi test etme
 Projeyi çalıştırdığınızda, Excel özel görev bölmesini görüntülemeden açılır. Kodu test etmek için Şeritteki iki durumlu düğmeye tıklayın.

### <a name="to-test-your-vsto-add-in"></a>VSTO eklentisini test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

     Excel 'in açıldığını ve şeritte **Eklentiler sekmesinin göründüğünü** onaylayın.

2. Şeritteki **Eklentiler** sekmesine tıklayın.

3. **Görev bölmesi Yöneticisi** grubunda **görev bölmesini göster** iki durumlu düğmesine tıklayın.

     İki durumlu düğmeye tıkladığınızda görev bölmesinin alternatif olarak görüntülendiğini ve gizlendiğini doğrulayın.

4. Görev bölmesi görünür olduğunda, görev bölmesinin köşesindeki **Kapat** düğmesine (X) tıklayın.

     İki durumlu düğmenin basılmamış göründüğünü doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan özel görev bölmeleri oluşturma hakkında daha fazla bilgi edinebilirsiniz:

- Farklı bir uygulama için VSTO eklentisi içinde özel bir görev bölmesi oluşturun. Özel görev bölmelerini destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

- Bir uygulamayı özel görev bölmesinden otomatikleştirin. Daha fazla bilgi için bkz. [Izlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Outlook 'ta açılan her e-posta iletisi için özel bir görev bölmesi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: Outlook 'ta e-posta iletileriyle özel görev bölmeleri görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [İzlenecek yol: Outlook 'ta e-posta iletileriyle özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
