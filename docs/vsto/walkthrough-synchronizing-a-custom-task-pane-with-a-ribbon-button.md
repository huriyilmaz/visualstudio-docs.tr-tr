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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e76b25516001143842422481eb6055be95a99178
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135591"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>İzlenecek yol: özel görev bölmesini Şerit düğmesi ile senkronize etme
  Bu izlenecek yol, Şeritteki iki durumlu düğmeye tıklayarak kullanıcıların gizleyebileceğiniz veya görüntüleyeceği özel bir görev bölmesi oluşturmayı gösterir. Microsoft Office uygulamalar, kullanıcıların özel görev bölmelerini göstermek veya gizlemek için varsayılan bir yol sağlamadığından, bir düğme gibi her zaman bir kullanıcı arabirimi (uı) öğesi oluşturmalısınız.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 bu izlenecek yol özellikle Excel kullanıyor olsa da, izlenecek yol tarafından gösterilen kavramlar yukarıda listelenen tüm uygulamalar için geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel görev bölmesinin kullanıcı arabirimini tasarlama.

- Şerit 'e iki durumlu düğme ekleme.

- İki durumlu düğmeyi özel görev bölmesiyle eşitleme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel veya Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Eklenti projesi oluşturma
 bu adımda, Excel için VSTO bir eklenti projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Excel eklentisi proje şablonunu kullanarak, **SynchronizeTaskPaneAndRibbon** adlı bir Excel eklentisi projesi oluşturun. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ThisAddIn. cs** veya **ThisAddIn. vb** kod dosyasını açar ve **SynchronizeTaskPaneAndRibbon** projesini **Çözüm Gezgini** ekler.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Şerit 'e iki durumlu düğme Ekle
 Office uygulama tasarım yönergelerinden biri, kullanıcıların Office uygulama kullanıcı arabirimine her zaman denetim sahibi olması gerekir. Kullanıcıların özel görev bölmesini denetlemesine olanak tanımak için, görev bölmesini gösteren ve gizleyen bir şerit iki durumlu düğme ekleyebilirsiniz. İki durumlu düğme oluşturmak için projeye **Şerit (görsel Tasarımcı)** öğesi ekleyin. Tasarımcı denetimleri eklemenize ve konumlandıramanıza, denetim özelliklerini ayarlamanıza ve denetim olaylarını işleymenize yardımcı olur. Daha fazla bilgi için bkz. [Şerit Tasarımcısı](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Şerit 'e iki durumlu düğme eklemek için

1. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şeridin adını **ManageTaskPaneRibbon** olarak değiştirin ve **Ekle**' ye tıklayın.

     **ManageTaskPaneRibbon. cs** veya **ManageTaskPaneRibbon. vb** dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit tasarımcısında, **grup1**' e tıklayın.

5. **Özellikler** penceresinde, **etiket** özelliğini **görev bölmesi Yöneticisi** olarak ayarlayın.

6. **araç kutusunun** **Office şerit denetimleri** sekmesinden, **görev bölmesi yöneticisi** grubuna bir **ToggleButton** sürükleyin.

7. **ToggleButton1** tıklayın.

8. **Özellikler** penceresinde, **etiket** özelliğini **görev bölmesini göster** olarak ayarlayın.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlama
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz düzende bir kullanıcı denetimi tasarlayabilirsiniz. Bu izlenecek yolda daha sonra Kullanıcı denetimini özel görev bölmesine ekleyeceksiniz.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlamak için

1. **Project** menüsünde **kullanıcı denetimi ekle**' ye tıklayın.

2. **Yeni öğe Ekle** iletişim kutusunda, Kullanıcı denetiminin adını **TaskPaneControl** olarak değiştirin ve **Ekle**' ye tıklayın.

     Kullanıcı denetimi tasarımcıda açılır.

3. **Araç kutusunun** **ortak denetimler** sekmesinden kullanıcı denetimine bir **TextBox** denetimi sürükleyin.

## <a name="create-the-custom-task-pane"></a>Özel görev bölmesini oluşturma
 VSTO eklentisi başlatıldığında özel görev bölmesini oluşturmak için, <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisinin olay işleyicisinde görev bölmesine kullanıcı denetimini ekleyin. Varsayılan olarak, özel görev bölmesi görünür olmayacaktır. Bu izlenecek yolda daha sonra, Kullanıcı Şerit 'e eklediğiniz iki durumlu düğmeye tıkladığında görev bölmesini görüntüleyecek veya gizleyecek kodu ekleyeceksiniz.

### <a name="to-create-the-custom-task-pane"></a>Özel görev bölmesini oluşturmak için

1. **Çözüm Gezgini**' de **Excel**' ı genişletin.

2. **ThisAddIn. cs** veya **ThisAddIn. vb** öğesine sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

3. Aşağıdaki kodu `ThisAddIn` sınıfına ekleyin. Bu kod, üyesi olarak bir örneğini bildirir `TaskPaneControl` `ThisAddIn` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet1":::

4. `ThisAddIn_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, `TaskPaneControl` nesnesini `CustomTaskPanes` alana ekler, ancak özel görev bölmesini görüntülemez (varsayılan olarak, <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> <xref:Microsoft.Office.Tools.CustomTaskPane> sınıfının özelliği **false**'dur). Visual C# kodu ayrıca olaya bir olay işleyicisi ekler <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet2":::

5. Sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Bu yöntem olayı işler <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> . Kullanıcı, **Kapat** düğmesine (X) tıklayarak görev bölmesini kapattığında, bu yöntem Şeritteki iki durumlu düğmenin durumunu güncelleştirir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet3":::

6. Sınıfına aşağıdaki özelliği ekleyin `ThisAddIn` . Bu özellik özel `myCustomTaskPane1` nesneyi diğer sınıflara gösterir. Bu izlenecek yolda daha sonra `MyRibbon` Bu özelliği kullanan sınıfa kod ekleyeceksiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet4":::

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>İki durumlu düğmeyi kullanarak özel görev bölmesini gizleme ve görüntüleme
 Son adım, Kullanıcı Şeritteki iki durumlu düğmeye tıkladığında özel görev bölmesini görüntüleyen veya gizleyen kodu eklemektir.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>İki durumlu düğmeyi kullanarak özel görev bölmesini görüntüleme ve gizleme

1. Şerit tasarımcısında **görev bölmesini göster** iki durumlu düğmesine çift tıklayın.

     Visual Studio `toggleButton1_Click` , <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olayını işleyen adlı bir olay işleyicisini otomatik olarak oluşturur. Visual Studio ayrıca kod düzenleyicisinde *myribbon. cs* veya *myribbon. vb* dosyasını açar.

2. `toggleButton1_Click`Olay işleyicisini aşağıdaki kodla değiştirin. Kullanıcı iki durumlu düğmeye tıkladığında, bu kod geçiş düğmesine basıldığında veya basılmamış olmasına bağlı olarak özel görev bölmesini görüntüler veya gizler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs" id="Snippet5":::

## <a name="test-the-add-in"></a>Eklentiyi test etme
 projeyi çalıştırdığınızda, Excel özel görev bölmesini görüntülemeden açılır. Kodu test etmek için Şeritteki iki durumlu düğmeye tıklayın.

### <a name="to-test-your-vsto-add-in"></a>VSTO eklentisini test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

     Excel açıldığını ve şeritte **eklentiler** sekmesi göründüğünü onaylayın.

2. Şeritteki **Eklentiler** sekmesine tıklayın.

3. **Görev bölmesi Yöneticisi** grubunda **görev bölmesini göster** iki durumlu düğmesine tıklayın.

     İki durumlu düğmeye tıkladığınızda görev bölmesinin alternatif olarak görüntülendiğini ve gizlendiğini doğrulayın.

4. Görev bölmesi görünür olduğunda, görev bölmesinin köşesindeki **Kapat** düğmesine (X) tıklayın.

     İki durumlu düğmenin basılmamış göründüğünü doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan özel görev bölmeleri oluşturma hakkında daha fazla bilgi edinebilirsiniz:

- farklı bir uygulama için VSTO eklenti içinde özel bir görev bölmesi oluşturun. Özel görev bölmelerini destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

- Bir uygulamayı özel görev bölmesinden otomatikleştirin. Daha fazla bilgi için bkz. [Izlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Outlook ' de açılan her e-posta iletisi için özel bir görev bölmesi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: Outlook e-posta iletileriyle özel görev bölmeleri görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [İzlenecek yol: Outlook 'da e-posta iletileriyle özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
