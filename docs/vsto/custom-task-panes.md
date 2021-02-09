---
title: Özel görev bölmeleri
description: Özel görev bölmeleri, kendi görev bölmenizi oluşturmak ve kullanıcılara çözümünüzün özelliklerine erişmek için tanıdık bir arabirim sağlamak için bir yol sağlar.
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
ms.workload:
- office
ms.openlocfilehash: 8ed86cb10f6521e5863562cdb67e768b1a2367d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850041"
---
# <a name="custom-task-panes"></a>Özel görev bölmeleri
  Görev bölmeleri, genellikle bir Microsoft Office uygulamasındaki bir pencerenin bir tarafına yerleştirilen Kullanıcı arabirimi panolardır. Özel görev bölmeleri, kendi görev bölmenizi oluşturmak ve kullanıcılara çözümünüzün özelliklerine erişmek için tanıdık bir arabirim sağlamak için bir yol sağlar. Örneğin, arabirim, belgeleri değiştirmek veya bir veri kaynağındaki verileri göstermek için kodu çalıştıran denetimleri içerebilir.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Özel görev bölmesi, Eylemler bölmesinden farklılık gösterir. Eylemler bölmesi, Microsoft Office Word ve Excel Microsoft Office için belge düzeyi özelleştirmelerinin bir parçasıdır. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Özel görev bölmelerinin avantajları
 Özel görev bölmeleri, özelliklerinizi tanıdık bir kullanıcı arabirimiyle tümleştirmenize imkan tanır. Visual Studio araçlarını kullanarak hızlı bir şekilde özel görev bölmesi oluşturabilirsiniz.

### <a name="familiar-user-interface"></a>Tanıdık kullanıcı arabirimi
 Microsoft Office sistemindeki uygulama kullanıcıları, Word 'de **Stiller ve biçimlendirme** görev bölmesi gibi görev bölmelerini kullanmayı zaten biliyor. Özel görev bölmeleri, Microsoft Office sistemindeki diğer görev bölmeleri gibi davranır. Kullanıcılar özel görev bölmelerini uygulama penceresinin farklı taraflarına sabitleyebilir veya özel görev bölmelerini penceredeki herhangi bir konuma sürükleyebilir. Aynı anda birden çok özel görev bölmesi görüntüleyen bir VSTO eklentisi oluşturabilirsiniz ve kullanıcılar her görev bölmesini ayrı ayrı denetleyebilir.

### <a name="windows-forms-support"></a>Windows Forms desteği
 Visual Studio 'da Office geliştirme araçları 'nı kullanarak oluşturduğunuz özel görev bölmesinin kullanıcı arabirimi Windows Forms denetimlerine dayalıdır. Özel bir görev bölmesi için Kullanıcı arabirimini tasarlamak üzere tanıdık Windows Form Tasarımcısı kullanabilirsiniz. Ayrıca, görev bölmesindeki denetimlere veri kaynağı bağlamak için Windows Forms ' de veri bağlama desteğini de kullanabilirsiniz.

## <a name="create-a-custom-task-pane"></a>Özel görev bölmesi oluşturma
 İki adımda temel bir özel görev bölmesi oluşturabilirsiniz:

1. Bir nesneye Windows Forms denetimleri ekleyerek özel görev bölmenizi için bir kullanıcı arabirimi oluşturun <xref:System.Windows.Forms.UserControl> .

2. Kullanıcı denetimini VSTO eklentiinizdeki nesneye geçirerek özel görev bölmesini örnek penceresinde oluşturun <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> . Bu koleksiyon <xref:Microsoft.Office.Tools.CustomTaskPane> , görev bölmesinin görünümünü değiştirmek ve Kullanıcı olaylarına yanıt vermek için kullanabileceğiniz yeni bir nesnesi döndürür.

   Daha fazla bilgi için bkz. [nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma
 Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan tüm özel görev bölmeleri bir <xref:System.Windows.Forms.UserControl> nesnesi içerir. Bu Kullanıcı denetimi, özel görev bölmenizi Kullanıcı arabirimi sağlar. Tasarım zamanında veya çalışma zamanında Kullanıcı denetimi oluşturabilirsiniz. Tasarım zamanında Kullanıcı denetimini oluşturursanız, görev bölmenizi Kullanıcı arabirimini oluşturmak için Windows Form Tasarımcısı kullanabilirsiniz.

### <a name="instantiate-the-custom-task-pane"></a>Özel görev bölmesini oluşturma
 Özel görev bölmesinin kullanıcı arabirimini içeren bir kullanıcı denetimi oluşturduktan sonra, örneğini oluşturmanız gerekir <xref:Microsoft.Office.Tools.CustomTaskPane> . Bunu yapmak için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> yöntemlerinden birini çağırarak Kullanıcı DENETIMINI VSTO eklentiinizdeki öğesine geçirin <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> . Bu koleksiyon, `CustomTaskPanes` sınıfının alanı olarak sunulur `ThisAddIn` . Aşağıdaki kod örneği sınıfından çalıştırılmak üzere tasarlanmıştır `ThisAddIn` .

 [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
 [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>Yöntemler yeni bir nesne döndürür <xref:Microsoft.Office.Tools.CustomTaskPane> . Görev bölmesinin görünümünü değiştirmek ve Kullanıcı olaylarına yanıt vermek için bu nesneyi kullanabilirsiniz.

### <a name="control-the-task-pane-in-multiple-windows"></a>Görev bölmesini birden çok pencere içinde denetleme
 Özel görev bölmeleri, kullanıcıya bir belge veya öğe görünümü sunan bir belge çerçevesi penceresiyle ilişkilendirilir. Görev bölmesi yalnızca ilişkili pencere görünür olduğunda görülebilir.

 Hangi pencerenin özel görev bölmesini görüntüleyeceğini öğrenmek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesini oluştururken uygun yöntem aşırı yüklemesini kullanın:

- Görev bölmesini etkin pencere ile ilişkilendirmek için <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemini kullanın.

- Görev bölmesini belirtilen bir pencere tarafından barındırılan bir belgeyle ilişkilendirmek için <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemini kullanın.

  Bazı Office uygulamaları, birden fazla pencere açıldığında görev bölmenizi ne zaman oluşturacağınız veya görüntüleyeceği hakkında açık yönergeler gerektirir. Bu, görev bölmesinin uygulamadaki uygun belge veya öğelerle göründüğünden emin olmak için kodunuzda özel görev bölmesinin nerede örneklendirilemekte yarar sağlar. Daha fazla bilgi için bkz. [uygulama Windows 'ta özel görev bölmelerini yönetme](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Görev bölmesinden uygulamaya erişme
 Uygulamayı kullanıcı denetiminden otomatikleştirebilmek istiyorsanız, kodunuzda kullanarak nesne modeline doğrudan erişebilirsiniz `Globals.ThisAddIn.Application` . Statik `Globals` sınıf, nesnesine erişim sağlar `ThisAddIn` . `Application`Bu nesnenin alanı, uygulamanın nesne modeline giriş noktasıdır.

 Nesnenin alanı hakkında daha fazla bilgi için `Application` `ThisAddIn` bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Bir uygulamayı özel görev bölmesinden nasıl otomatikleştirebileceğinizi gösteren bir anlatım için, bkz. [Izlenecek yol: özel bir görev bölmesinden otomatik uygulama](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). Sınıfı hakkında daha fazla bilgi için `Globals` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Görev bölmesinin kullanıcı arabirimini yönetme
 Görev bölmesini oluşturduktan sonra, görev bölmesinin <xref:Microsoft.Office.Tools.CustomTaskPane> Kullanıcı arabirimini denetlemek ve Kullanıcı görev bölmesini değiştirdiğinde yanıt vermek için nesnenin özelliklerini ve olaylarını kullanabilirsiniz.

### <a name="make-the-custom-task-pane-visible"></a>Özel görev bölmesini görünür yapma
 Varsayılan olarak, görev bölmesi görünür değildir. Görev bölmesini görünür yapmak için <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> özelliği **true** olarak ayarlamanız gerekir.

 Kullanıcılar, görev bölmesinin köşesindeki **Kapat** düğmesine (X) tıklayarak istediğiniz zaman bir görev bölmesini kapatabilir. Ancak, kullanıcıların özel görev bölmesini yeniden açması için varsayılan bir yol yoktur. Bir kullanıcı özel bir görev bölmesini kapatırsa, onu görüntülemek için bir yol sağlamadığınız takdirde bu kullanıcı özel görev bölmesini görüntüleyemez.

 VSTO eklentiinizdeki özel bir görev bölmesi oluşturursanız, kullanıcıların özel görev bölmenizi görüntülemesi veya gizleyebilmek için, düğme gibi bir kullanıcı arabirimi öğesi de oluşturmanız gerekir. Şeriti özelleştirmeyi destekleyen bir Microsoft Office uygulamasında özel bir görev bölmesi oluşturursanız, özel görev bölmenizi görüntüleyen veya gizleyen bir düğme ile Şerite bir denetim grubu ekleyebilirsiniz. Bunun nasıl yapılacağını gösteren bir anlatım için bkz. [Izlenecek yol: özel görev bölmesini Şerit düğmesi Ile senkronize](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)etme.

 Şeriti özelleştirmeyi desteklemeyen bir Microsoft Office uygulamasında özel bir görev bölmesi oluşturursanız, <xref:Microsoft.Office.Core.CommandBarButton> özel görev bölmenizi görüntüleyen veya gizleyen bir ekleyebilirsiniz.

### <a name="modify-the-appearance-of-the-task-pane"></a>Görev bölmesinin görünümünü değiştirme
 Nesnenin özelliklerini kullanarak özel bir görev bölmesinin boyutunu ve konumunu kontrol edebilirsiniz <xref:Microsoft.Office.Tools.CustomTaskPane> . Özel görev bölmesinde bulunan nesnenin özelliklerini kullanarak özel görev bölmesinin görünümünde birçok farklı değişiklik yapabilirsiniz <xref:System.Windows.Forms.UserControl> . Örneğin, Kullanıcı denetiminin özelliğini kullanarak özel görev bölmesi için bir arka plan görüntüsü belirtebilirsiniz <xref:System.Windows.Forms.Control.BackgroundImage%2A> .

 Aşağıdaki tabloda, özellikleri kullanarak özel bir görev bölmesinde yapabileceğiniz değişiklikler listelenmiştir <xref:Microsoft.Office.Tools.CustomTaskPane> .

|Görev|Özellik|
|----------|--------------|
|Görev bölmesinin boyutunu değiştirmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.Height%2A><br /><br /> <xref:Microsoft.Office.Tools.CustomTaskPane.Width%2A>|
|Görev bölmesinin konumunu değiştirmek için|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPosition%2A>|
|Görev bölmesini gizleme veya görünür hale getirme|<xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>|
|Kullanıcının görev bölmesinin konumunu değiştirmesini engellemek için|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionRestrict%2A>|

### <a name="program-custom-task-pane-events"></a>Program özel görev bölmesi olayları
 Kullanıcı özel görev bölmesini değiştirdiğinde VSTO eklentisinin yanıt vermesini isteyebilirsiniz. Örneğin, Kullanıcı bölmenin hizalamasını dikeyden yataya değiştirirse, denetimleri yeniden konumlandırmak isteyebilirsiniz.

 Aşağıdaki tabloda, kullanıcının özel görev bölmesine yaptığı değişikliklere yanıt vermek için işleyebilmeniz gereken olaylar listelenmektedir.

|Görev|Olay|
|----------|-----------|
|Kullanıcı görev bölmesinin konumunu değiştirdiğinde yanıt vermek için.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Kullanıcı görev bölmesini gizlediğini veya görünür hale getiren yanıt vermek için.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Görev bölmesi tarafından kullanılan kaynakları Temizleme
 Özel bir görev bölmesi oluşturduktan sonra, <xref:Microsoft.Office.Tools.CustomTaskPane> VSTO eklentisi çalıştığı sürece nesne bellekte kalır. Kullanıcı görev bölmesinin köşesindeki **Kapat** düğmesine (X) tıkladıktan sonra bile, nesne bellekte kalır.

 VSTO eklentisi çalışmaya devam ederken görev bölmesi tarafından kullanılan kaynakları temizlemek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> veya <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> yöntemlerini kullanın. Bu yöntemler <xref:Microsoft.Office.Tools.CustomTaskPane> , belirtilen nesneyi `CustomTaskPanes` koleksiyondan kaldırır ve `Dispose` nesnenin yöntemini çağırır.

 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi kaldırıldığında özel görev bölmesi tarafından kullanılan kaynakları otomatik olarak temizler. <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> Projenizdeki olay işleyicisinde veya yöntemlerini çağırmayın `ThisAddIn_Shutdown` . <xref:System.ObjectDisposedException>Daha [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] önce nesne tarafından kullanılan kaynakları temizleyerek, bu yöntemler bir oluşturur <xref:Microsoft.Office.Tools.CustomTaskPane> `ThisAddIn_Shutdown` . Hakkında daha fazla bilgi için `ThisAddIn_Shutdown` bkz. [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Birden çok uygulama penceresinde özel görev bölmelerini yönetme
 Belgeleri ve diğer öğeleri göstermek için birden çok pencere kullanan bir uygulamada özel bir görev bölmesi oluşturduğunuzda, Kullanıcı onu beklediğinde görev bölmesinin görünebildiğinden emin olmak için ek adımlar gerçekleştirmeniz gerekir.

 Tüm uygulamalardaki özel görev bölmeleri, kullanıcıya bir belge veya öğe görünümü sunan bir belge çerçevesi penceresiyle ilişkilendirilir. Görev bölmesi yalnızca ilişkili pencere görünür olduğunda görülebilir. Ancak, tüm uygulamalar belge çerçevesi pencerelerini aynı şekilde kullanmaz.

 Aşağıdaki uygulama grupları farklı geliştirme gereksinimlerine sahiptir:

- [Outlook](#Outlook)

- [Word, InfoPath ve PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a> Office
 Outlook için özel bir görev bölmesi oluşturduğunuzda, özel görev bölmesi belirli bir gezgin veya Inspector penceresiyle ilişkilendirilir. Araştırıcılar, bir klasörün içeriğini görüntüleyen ve Inspectors, bir e-posta iletisi veya bir görev gibi bir öğe görüntüleyen bir Windows.

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

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Outlook 'ta özel görev bölmesinin birden çok örneğini önleme
 Outlook Windows 'un bir özel görev bölmesinin birden çok örneğini görüntülemesini engellemek için, özel görev bölmesini, `CustomTaskPanes` `ThisAddIn` her pencere kapatıldığında sınıfın koleksiyonundan açıkça kaldırın. Yöntemi, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> veya gibi bir pencere kapatıldığında oluşan bir olayda çağırın <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close> .

 Özel görev bölmesini açıkça kaldırmadıysanız Outlook Windows, özel görev bölmesinin birden fazla örneğini gösterebilir. Outlook bazen Windows 'u geri dönüştürür ve geri dönüşümlü Windows, bunlara eklenmiş olan özel görev bölmeleriyle ilgili başvuruları korur.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a> Word, InfoPath ve PowerPoint
 Word, InfoPath ve PowerPoint her bir belgeyi farklı bir belge çerçevesi penceresinde görüntüler. Bu uygulamalar için özel bir görev bölmesi oluşturduğunuzda, özel görev bölmesi yalnızca belirli bir belgeyle ilişkilendirilir. Kullanıcı farklı bir belge açarsa, önceki belge yeniden görünene kadar özel görev bölmesi gizlenir.

 Birden çok belgeyle özel bir görev bölmesi göstermek istiyorsanız, Kullanıcı yeni bir belge oluşturduğunda veya var olan bir belgeyi açtığında özel görev bölmesinin yeni bir örneğini oluşturun. Bunu yapmak için, bir belge oluşturulduğunda veya açıldığında oluşturulan olayları işleyin ve ardından olay işleyicilerinde görev bölmesini oluşturun. Ayrıca, hangi belgenin görünür olduğuna bağlı olarak görev bölmelerini gizlemek veya göstermek için belge olaylarını işleyebilirsiniz.

 Görev bölmesini belirli bir belge penceresiyle ilişkilendirmek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesini oluşturmak için yöntemini kullanın ve <xref:Microsoft.Office.Interop.Word.Window> pencere parametresine (Word için), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (InfoPath Için) veya [DocumentWindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) 'a (PowerPoint için)  geçiş yapın.

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

### <a name="powerpoint-events"></a>PowerPoint olayları
 PowerPoint 'teki Belge pencerelerinin durumunu izlemek için aşağıdaki olayları işleyebilirsiniz:

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft.Office.Interop.PowerPoint.EApplication_Event. WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile senkronize etme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [İzlenecek yol: Outlook 'ta e-posta iletileriyle özel görev bölmelerini görüntüleme](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
