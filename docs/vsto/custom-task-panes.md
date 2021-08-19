---
title: Özel görev bölmeleri
description: Özel görev bölmeleri size kendi görev bölmenizi oluşturmanın ve kullanıcılara çözüm özelliklerine erişmek için tanıdık bir arabirim sağlamanın bir yolunu sağlar.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, task panes
- user interface panels [Office development in Visual Studio]
- task panes [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio]. multiple application windows
- custom task panes [Office development in Visual Studio], multiple application windows
- task panes [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], custom task panes
- multiple applications windows with custom task panes [Office development in Visual Studio]
- add-ins [Office development in Visual Studio], custom task panes
- custom task panes [Office development in Visual Studio]
- task panes [Office development in Visual Studio], about custom task panes
- custom task panes [Office development in Visual Studio], about custom task panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 942ff50e8384cac8d3ed03aeb747868e7eb9f95b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148395"
---
# <a name="custom-task-panes"></a>Özel görev bölmeleri
  Görev bölmeleri, genellikle bir uygulamanın bir penceresindeki bir tarafına yerleştirilen kullanıcı arabirimi Microsoft Office panelleridir. Özel görev bölmeleri size kendi görev bölmenizi oluşturmanın ve kullanıcılara çözüm özelliklerine erişmek için tanıdık bir arabirim sağlamanın bir yolunu sağlar. Örneğin, arabirim, belgeleri değiştirmek veya bir veri kaynağındaki verileri görüntülemek için kod çalıştıran denetimler içerebilir.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Özel görev bölmesi, eylemler bölmesinden farklıdır. Eylemler bölmesi, Word ve Microsoft Office için belge düzeyinde özelleştirmelerin Microsoft Office Excel. Daha fazla bilgi için bkz. [Eylemler bölmesine genel bakış.](../vsto/actions-pane-overview.md)

## <a name="benefits-of-custom-task-panes"></a>Özel görev bölmelerinin avantajları
 Özel görev bölmeleri, özelliklerinizi tanıdık bir kullanıcı arabirimiyle tümleştirebilirsiniz. Özel görev bölmesini hızlı bir şekilde oluşturmak için Visual Studio kullanabilirsiniz.

### <a name="familiar-user-interface"></a>Tanıdık kullanıcı arabirimi
 Microsoft Office sistemdeki uygulamaların kullanıcıları, Word'de Stiller ve Biçimlendirme  görev bölmesi gibi görev bölmelerini kullanmayı zaten biliyor. Özel görev bölmeleri, özel sistemde diğer görev Microsoft Office davranır. Kullanıcılar özel görev bölmelerini uygulama penceresinin farklı tarafına yerleştirebilir veya özel görev bölmelerini pencere içinde herhangi bir konuma sürükleyebilir. Aynı anda birden VSTO özel görev bölmesi görüntüleyen bir eklenti oluşturabilirsiniz ve kullanıcılar her görev bölmesini tek tek kontrol eder.

### <a name="windows-forms-support"></a>Windows formları desteği
 Visual Studio Forms denetimlerini temel alan Office kullanarak Visual Studio özel görev bölmesinin Windows kullanıcı arabirimi. Kullanıcı arabirimini özel bir Windows için tasarlamak üzere FormLar Tasarımcısı'nın tanıdık kullanıcı arabirimini kullanabilirsiniz. Veri kaynağını görev bölmesindeki denetimlere bağlamak Windows Formlar'daki veri bağlama desteğini de kullanabilirsiniz.

## <a name="create-a-custom-task-pane"></a>Özel görev bölmesi oluşturma
 İki adımda temel bir özel görev bölmesi oluşturabilirsiniz:

1. Bir nesneye Formlar denetimleri ekleyerek özel görev bölmeniz için Windows arabirimi <xref:System.Windows.Forms.UserControl> oluşturun.

2. Özel görev bölmesinin örneğini oluşturmak için kullanıcı denetimi eklentinizin VSTO <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> ekleyin. Bu koleksiyon, görev <xref:Microsoft.Office.Tools.CustomTaskPane> bölmesinin görünümünü değiştirmek ve kullanıcı olaylarına yanıt vermek için kullanabileceğiniz yeni bir nesne döndürür.

   Daha fazla bilgi [için, bkz. How to: Add a custom task pane to an application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma
 uygulama geliştirme araçları kullanılarak oluşturulan tüm özel Office bölmeleri Visual Studio <xref:System.Windows.Forms.UserControl> içerir. Bu kullanıcı denetimi, özel görev bölmenizin kullanıcı arabirimini sağlar. Kullanıcı denetimi tasarım zamanında veya çalışma zamanında oluşturabilirsiniz. Tasarım zamanında kullanıcı denetimi oluşturursanız, görev bölmenizin kullanıcı arabirimini oluşturmak için Windows Forms Tasarımcısı'nda kullanabilirsiniz.

### <a name="instantiate-the-custom-task-pane"></a>Özel görev bölmesinin örneğini oluşturma
 Özel görev bölmesinin kullanıcı arabirimini içeren bir kullanıcı denetimi oluşturduk sonra, bir örneği oluşturmanız <xref:Microsoft.Office.Tools.CustomTaskPane> gerekir. Bunu yapmak için, yöntemlerinden birini çağırarak VSTO eklentinizin içinde kullanıcı <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> denetimine geçiş. Bu koleksiyon, sınıfının `CustomTaskPanes` alanı olarak ortaya `ThisAddIn` çıkar. Aşağıdaki kod örneğinin sınıfından çalışması `ThisAddIn` amaçlanan bir örnektir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

 Yöntemler <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yeni bir nesnesi geri <xref:Microsoft.Office.Tools.CustomTaskPane> döner. Görev bölmesinin görünümünü değiştirmek ve kullanıcı olaylarına yanıt vermek için bu nesneyi kullanabilirsiniz.

### <a name="control-the-task-pane-in-multiple-windows"></a>Görev bölmesini birden çok windows'da denetleme
 Özel görev bölmeleri, kullanıcıya bir belgenin veya öğenin görünümünü sunan bir belge çerçevesi penceresiyle ilişkilendirildi. Görev bölmesi yalnızca ilişkili pencere görünür olduğunda görünür.

 Özel görev bölmesini hangi pencerede görüntüleyeni belirlemek için, görev bölmesini <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> ekleyebilirsiniz:

- Görev bölmesini etkin pencereyle ilişkilendirmek için yöntemini <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> kullanın.

- Görev bölmesini belirtilen bir pencere tarafından barındırılan bir belgeyle ilişkilendirmek için yöntemini <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> kullanın.

  Bazı Office uygulamaları, görev bölmenizi oluşturmak veya görüntülemek için birden fazla pencere açık olduğunda açık yönergeler gerektirir. Bu, görev bölmesinin uygulamadaki uygun belgeler veya öğelerle birlikte göründüğünden emin olmak için kodunda özel görev bölmesinin nerede örneğini oluşturmanın gerekli olduğunu göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. Uygulama pencerelerde özel görev bölmelerini yönetme.](#Managing)

## <a name="access-the-application-from-the-task-pane"></a>Uygulamaya Görev Bölmesinden erişme
 Uygulamayı kullanıcı denetiminden otomatikleştirmek için kodunda kullanarak nesne modeline `Globals.ThisAddIn.Application` doğrudan erişebilirsiniz. Statik `Globals` sınıf nesnesine erişim `ThisAddIn` sağlar. Bu `Application` nesnenin alanı, uygulamanın nesne modeline giriş noktasıdır.

 Nesnesinin alanı hakkında `Application` daha fazla bilgi için `ThisAddIn` bkz. Program VSTO [Eklentileri.](../vsto/programming-vsto-add-ins.md) Bir uygulamayı özel görev bölmesinden otomatikleştirmeyi gösteren bir kılavuz için bkz. Adım adım kılavuz: Özel görev [bölmesinden uygulama otomatikleştirme.](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) sınıfı hakkında daha fazla `Globals` bilgi için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

## <a name="manage-the-user-interface-of-the-task-pane"></a>Görev Bölmesinin kullanıcı arabirimini yönetme
 Görev bölmesini oluşturdukta, görev bölmesinin kullanıcı arabirimini kontrol etmek ve kullanıcı görev bölmesini değiştirirken yanıt vermek için nesnenin özelliklerini <xref:Microsoft.Office.Tools.CustomTaskPane> ve olaylarını kullanabilirsiniz.

### <a name="make-the-custom-task-pane-visible"></a>Özel Görev Bölmesini görünür yapma
 Görev bölmesi varsayılan olarak görünür değildir. Görev bölmesini görünür yapmak için özelliğini <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> true olarak **ayarlayabilirsiniz.**

 Kullanıcılar, görev bölmesinin köşesindeki Kapat  düğmesine (X) tıklayarak bir görev bölmesini istediğiniz zaman kapatabilirsiniz. Ancak, kullanıcıların özel görev bölmesini yeniden açması için varsayılan bir yol yoktur. Bir kullanıcı özel görev bölmesini kapatırsa, özel görev bölmesini görüntülemenin bir yolunu sağlamadıkça bu kullanıcı özel görev bölmesini yeniden görüntüleyebilirsiniz.

 VSTO Eklentiniz içinde özel bir görev bölmesi ekleyebilirsiniz. Ayrıca, kullanıcıların özel görev bölmenizi görüntülemek veya gizlemek için tıklayabilirsiniz düğme gibi bir kullanıcı arabirimi öğesi de oluşturmanız gerekir. Şerit özelleştirmeyi destekleyen bir Microsoft Office uygulama içinde özel bir görev bölmesi ekleyebilirsiniz, özel görev bölmenizi görüntüleyen veya gizleyen bir düğmeyle Şerit'e bir denetim grubu ekleyebilirsiniz. Bunun nasıl olduğunu gösteren bir izlenecek yol için bkz. [Kılavuz: Şerit düğmesiyle özel görev bölmesini eşitleme.](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)

 Şerit özelleştirmesini desteklemez bir Microsoft Office özel görev bölmesi ekleyebilirsiniz, özel görev bölmenizi görüntüler <xref:Microsoft.Office.Core.CommandBarButton> veya gizler.

### <a name="modify-the-appearance-of-the-task-pane"></a>Görev bölmesinin görünümünü değiştirme
 Nesnenin özelliklerini kullanarak özel görev bölmesinin boyutunu ve konumunu <xref:Microsoft.Office.Tools.CustomTaskPane> kontrolleyebilirsiniz. Özel görev bölmesinde bulunan nesnenin özelliklerini kullanarak özel görev bölmesinin <xref:System.Windows.Forms.UserControl> görünümüne başka birçok değişiklik yapabilirsiniz. Örneğin, kullanıcı denetimi özelliğini kullanarak özel görev bölmesi için bir arka <xref:System.Windows.Forms.Control.BackgroundImage%2A> plan görüntüsü belirtebilirsiniz.

 Aşağıdaki tabloda, özellikleri kullanarak özel görev bölmesinde gerçekleştirebilirsiniz değişiklikler <xref:Microsoft.Office.Tools.CustomTaskPane> listeleyebilirsiniz.

|Görev|Özellik|
|----------|--------------|
|Görev bölmesinin boyutunu değiştirmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Görev bölmesinin konumunu değiştirmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Görev bölmesini gizlemek veya görünür hale etmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Kullanıcının görev bölmesinin konumunu değiştirmesini önlemek için|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Program özel görev bölmesi olayları
 Kullanıcı özel görev bölmesini VSTO için eklentinizin yanıt vermelerini istemeniz gerekir. Örneğin, kullanıcı bölmenin yönünü dikeyden yataya değiştirirse denetimleri yeniden konumlandırmak iyi olabilir.

 Aşağıdaki tabloda, kullanıcının özel görev bölmesine ekleyebilirsiniz değişikliklere yanıt vermek için işleyebilirsiniz olayları listeler.

|Görev|Olay|
|----------|-----------|
|Kullanıcı görev bölmesinin konumunu değiştirirken yanıt vermek için.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Kullanıcı görev bölmesini gizler veya görünür hale geldiğinde yanıt vermek için.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Görev bölmesi tarafından kullanılan kaynakları temizleme
 Özel bir görev bölmesi oluşturdukta, eklentinizin çalışma VSTO <xref:Microsoft.Office.Tools.CustomTaskPane> nesne bellekte kalır. Kullanıcı görev bölmesinin köşesindeki Kapat  düğmesine (X) tıkladığında bile nesne bellekte kalır.

 Görev bölmesi tarafından kullanılan kaynakları, VSTO çalışırken temizlemek için veya <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> yöntemlerini kullanın. Bu yöntemler belirtilen nesneyi <xref:Microsoft.Office.Tools.CustomTaskPane> koleksiyondan `CustomTaskPanes` kaldırır ve `Dispose` nesnesinin yöntemini çağırarak.

 , özel görev bölmesi tarafından kullanılan kaynakları, eklenti [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO otomatik olarak temizler. Projenizin olay <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> işleyicisinde veya yöntemlerini `ThisAddIn_Shutdown` çağırmayın. Bu yöntemler, nesnesi tarafından <xref:System.ObjectDisposedException> kullanılan [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kaynakları çağrılmadan önce temizleyene <xref:Microsoft.Office.Tools.CustomTaskPane> bir `ThisAddIn_Shutdown` oluşturur. hakkında daha fazla bilgi için `ThisAddIn_Shutdown` [bkz. Office projelerinde olaylar.](../vsto/events-in-office-projects.md)

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Birden çok uygulama penceresinde özel görev bölmelerini yönetme
 Belge ve diğer öğeleri görüntülemek için birden çok pencere kullanan bir uygulamada özel görev bölmesi ekleyebilirsiniz. Kullanıcı, görev bölmesinin görünür olmasını beklediğinizde görev bölmesinin görünür olduğundan emin olmak için ek adımlar atması gerekir.

 Tüm uygulamalarda özel görev bölmeleri, bir belge veya öğenin kullanıcıya görünümünü sunan bir belge çerçevesi penceresiyle ilişkilendirilmektedir. Görev bölmesi yalnızca ilişkili pencere görünür olduğunda görünür. Ancak, tüm uygulamalar belge çerçevesi pencerelerini aynı şekilde kullanmaz.

 Aşağıdaki uygulama gruplarının farklı geliştirme gereksinimleri vardır:

- [Outlook](#Outlook)

- [Word, InfoPath ve PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a>Outlook
 Outlook için özel bir görev bölmesi oluşturduğunuzda, özel görev bölmesi belirli bir gezgin veya ınspector penceresiyle ilişkilendirilir. Araştırıcılar, bir klasörün içeriğini görüntüleyen ve Inspectors, bir e-posta iletisi veya bir görev gibi bir öğe görüntüleyen bir Windows.

 Birden çok gezgin veya Inspector penceresi içeren özel bir görev bölmesi göstermek istiyorsanız, bir gezgin veya Denetçi penceresi açıldığında özel görev bölmesinin yeni bir örneğini oluşturmanız gerekir. Bunu yapmak için, bir gezgin veya Denetçi penceresi oluşturulduğunda oluşan bir olayı işleyin ve ardından olay işleyicisinde görev bölmesini oluşturun. Ayrıca, hangi pencerenin görünür olduğuna bağlı olarak görev bölmelerini gizlemek veya göstermek için Gezgin ve Inspector olaylarını da işleyebilirsiniz.

 Görev bölmesini belirli bir gezgin veya Inspector ile ilişkilendirmek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemini kullanarak görev bölmesini oluşturun ve <xref:Microsoft.Office.Interop.Outlook.Explorer> veya <xref:Microsoft.Office.Interop.Outlook.Inspector> nesnesini *pencere* parametresine geçirin. Özel görev bölmeleri oluşturma hakkında daha fazla bilgi için bkz. [özel görev bölmeleri genel bakış](../vsto/custom-task-panes.md).

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Inspector pencerelerinin durumunu izlemek için, Inspector ile ilgili aşağıdaki olayları işleyebilirsiniz:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Outlook bir özel görev bölmesinin birden fazla örneğini engelle
 Outlook windows 'un bir özel görev bölmesinin birden çok örneğini görüntülemesini engellemek için, `CustomTaskPanes` her pencere kapatıldığında özel görev bölmesini sınıfın koleksiyonundan açıkça kaldırın `ThisAddIn` . Yöntemi, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> veya gibi bir pencere kapatıldığında oluşan bir olayda çağırın <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close> .

 özel görev bölmesini açıkça kaldırmadıysanız Outlook windows, özel görev bölmesinin birden fazla örneğini görüntüleyebilir. Outlook bazen pencereleri geri dönüştürür ve geri dönüşümlü pencereler, bunlara eklenmiş olan özel görev bölmeleriyle ilgili başvuruları korur.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a>Word, InfoPath ve PowerPoint
 Word, ınfopath ve PowerPoint her bir belgeyi farklı bir belge çerçevesi penceresinde görüntüler. Bu uygulamalar için özel bir görev bölmesi oluşturduğunuzda, özel görev bölmesi yalnızca belirli bir belgeyle ilişkilendirilir. Kullanıcı farklı bir belge açarsa, önceki belge yeniden görünene kadar özel görev bölmesi gizlenir.

 Birden çok belgeyle özel bir görev bölmesi göstermek istiyorsanız, Kullanıcı yeni bir belge oluşturduğunda veya var olan bir belgeyi açtığında özel görev bölmesinin yeni bir örneğini oluşturun. Bunu yapmak için, bir belge oluşturulduğunda veya açıldığında oluşturulan olayları işleyin ve ardından olay işleyicilerinde görev bölmesini oluşturun. Ayrıca, hangi belgenin görünür olduğuna bağlı olarak görev bölmelerini gizlemek veya göstermek için belge olaylarını işleyebilirsiniz.

 görev bölmesini belirli bir belge penceresiyle ilişkilendirmek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesini oluşturmak için yöntemini kullanın ve <xref:Microsoft.Office.Interop.Word.Window> pencere parametresine (for Word), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (ınfopath için) veya [documentwindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (PowerPoint için) geçirin. 

### <a name="word-events"></a>Word olayları
 Word 'deki Belge pencerelerinin durumunu izlemek için aşağıdaki olayları işleyebilirsiniz:

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>InfoPath olayları
 InfoPath 'teki Belge pencerelerinin durumunu izlemek için aşağıdaki olayları işleyebilirsiniz:

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>PowerPoint olaylar
 PowerPoint belge pencerelerinin durumunu izlemek için aşağıdaki olayları işleyebilirsiniz:

- [MICROSOFT. Office. Derlemesinde. PowerPoint. EApplication_Event. AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [MICROSOFT. Office. Derlemesinde. PowerPoint. EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [MICROSOFT. Office. Derlemesinde. PowerPoint. EApplication_Event. NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [MICROSOFT. Office. Derlemesinde. PowerPoint. EApplication_Event. PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [MICROSOFT. Office. Derlemesinde. PowerPoint. EApplication_Event. WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [MICROSOFT. Office. Derlemesinde. PowerPoint. EApplication_Event. WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile senkronize etme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [İzlenecek yol: Outlook 'da e-posta iletileriyle özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
