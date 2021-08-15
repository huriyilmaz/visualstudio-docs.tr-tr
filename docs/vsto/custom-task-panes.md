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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 80421e85832d43d5dbdd0816ccd19139312236952a8d0397748faa9403a80f90
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121314777"
---
# <a name="custom-task-panes"></a>Özel görev bölmeleri
  görev bölmeleri, genellikle bir Microsoft Office uygulamasındaki bir pencerenin bir tarafına yerleştirilen kullanıcı arabirimi panolardır. Özel görev bölmeleri, kendi görev bölmenizi oluşturmak ve kullanıcılara çözümünüzün özelliklerine erişmek için tanıdık bir arabirim sağlamak için bir yol sağlar. Örneğin, arabirim, belgeleri değiştirmek veya bir veri kaynağındaki verileri göstermek için kodu çalıştıran denetimleri içerebilir.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Özel görev bölmesi, Eylemler bölmesinden farklılık gösterir. eylemler bölmesi Microsoft Office Word ve Microsoft Office Excel için belge düzeyi özelleştirmelerinin bir parçasıdır. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

## <a name="benefits-of-custom-task-panes"></a>Özel görev bölmelerinin avantajları
 Özel görev bölmeleri, özelliklerinizi tanıdık bir kullanıcı arabirimiyle tümleştirmenize imkan tanır. Visual Studio araçlarını kullanarak hızlıca bir özel görev bölmesi oluşturabilirsiniz.

### <a name="familiar-user-interface"></a>Tanıdık kullanıcı arabirimi
 Microsoft Office sistemindeki uygulama kullanıcıları, Word 'de **stiller ve biçimlendirme** görev bölmesi gibi görev bölmelerini kullanmayı zaten biliyor. özel görev bölmeleri, Microsoft Office sistemindeki diğer görev bölmeleri gibi davranır. Kullanıcılar özel görev bölmelerini uygulama penceresinin farklı taraflarına sabitleyebilir veya özel görev bölmelerini penceredeki herhangi bir konuma sürükleyebilir. aynı anda birden çok özel görev bölmesi görüntüleyen bir VSTO eklentisi oluşturabilirsiniz ve kullanıcılar her görev bölmesini ayrı ayrı denetleyebilir.

### <a name="windows-forms-support"></a>Windows forms desteği
 Visual Studio ' de Office geliştirme araçlarını kullanarak oluşturduğunuz özel görev bölmesinin kullanıcı arabirimi Windows Forms denetimlerine dayalıdır. özel bir görev bölmesi için kullanıcı arabirimini tasarlamak üzere tanıdık Windows Form Tasarımcısı kullanabilirsiniz. ayrıca, görev bölmesindeki denetimlere veri kaynağı bağlamak için Windows Forms ' de veri bağlama desteğini de kullanabilirsiniz.

## <a name="create-a-custom-task-pane"></a>Özel görev bölmesi oluşturma
 İki adımda temel bir özel görev bölmesi oluşturabilirsiniz:

1. bir nesneye Windows Forms denetimleri ekleyerek özel görev bölmenizi için bir kullanıcı arabirimi oluşturun <xref:System.Windows.Forms.UserControl> .

2. kullanıcı denetimini VSTO eklentisinin nesnesine geçirerek özel görev bölmesini örnek penceresinde oluşturun <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> . Bu koleksiyon <xref:Microsoft.Office.Tools.CustomTaskPane> , görev bölmesinin görünümünü değiştirmek ve Kullanıcı olaylarına yanıt vermek için kullanabileceğiniz yeni bir nesnesi döndürür.

   Daha fazla bilgi için bkz. [nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma
 Visual Studio Office geliştirme araçları kullanılarak oluşturulan tüm özel görev bölmeleri bir <xref:System.Windows.Forms.UserControl> nesnesi içerir. Bu Kullanıcı denetimi, özel görev bölmenizi Kullanıcı arabirimi sağlar. Tasarım zamanında veya çalışma zamanında Kullanıcı denetimi oluşturabilirsiniz. tasarım zamanında kullanıcı denetimini oluşturursanız, görev bölmenizi kullanıcı arabirimini oluşturmak için Windows Form Tasarımcısı kullanabilirsiniz.

### <a name="instantiate-the-custom-task-pane"></a>Özel görev bölmesini oluşturma
 Özel görev bölmesinin kullanıcı arabirimini içeren bir kullanıcı denetimi oluşturduktan sonra, örneğini oluşturmanız gerekir <xref:Microsoft.Office.Tools.CustomTaskPane> . bunu yapmak için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection> yöntemlerden birini çağırarak kullanıcı denetimini VSTO eklentiinizdeki öğesine geçirin <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> . Bu koleksiyon, `CustomTaskPanes` sınıfının alanı olarak sunulur `ThisAddIn` . Aşağıdaki kod örneği sınıfından çalıştırılmak üzere tasarlanmıştır `ThisAddIn` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

 <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A>Yöntemler yeni bir nesne döndürür <xref:Microsoft.Office.Tools.CustomTaskPane> . Görev bölmesinin görünümünü değiştirmek ve Kullanıcı olaylarına yanıt vermek için bu nesneyi kullanabilirsiniz.

### <a name="control-the-task-pane-in-multiple-windows"></a>Görev bölmesini birden çok pencere içinde denetleme
 Özel görev bölmeleri, kullanıcıya bir belge veya öğe görünümü sunan bir belge çerçevesi penceresiyle ilişkilendirilir. Görev bölmesi yalnızca ilişkili pencere görünür olduğunda görülebilir.

 Hangi pencerenin özel görev bölmesini görüntüleyeceğini öğrenmek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> görev bölmesini oluştururken uygun yöntem aşırı yüklemesini kullanın:

- Görev bölmesini etkin pencere ile ilişkilendirmek için <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemini kullanın.

- Görev bölmesini belirtilen bir pencere tarafından barındırılan bir belgeyle ilişkilendirmek için <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> yöntemini kullanın.

  bazı Office uygulamalar, birden fazla pencere açıldığında görev bölmenizi ne zaman oluşturacağınız veya görüntüleyeceği hakkında açık yönergeler gerektirir. Bu, görev bölmesinin uygulamadaki uygun belge veya öğelerle göründüğünden emin olmak için kodunuzda özel görev bölmesinin nerede örneklendirilemekte yarar sağlar. Daha fazla bilgi için bkz. [uygulama Windows 'ta özel görev bölmelerini yönetme](#Managing).

## <a name="access-the-application-from-the-task-pane"></a>Görev bölmesinden uygulamaya erişme
 Uygulamayı kullanıcı denetiminden otomatikleştirebilmek istiyorsanız, kodunuzda kullanarak nesne modeline doğrudan erişebilirsiniz `Globals.ThisAddIn.Application` . Statik `Globals` sınıf, nesnesine erişim sağlar `ThisAddIn` . `Application`Bu nesnenin alanı, uygulamanın nesne modeline giriş noktasıdır.

 nesnenin alanı hakkında daha fazla bilgi için `Application` `ThisAddIn` bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md). Bir uygulamayı özel görev bölmesinden nasıl otomatikleştirebileceğinizi gösteren bir anlatım için, bkz. [Izlenecek yol: özel bir görev bölmesinden otomatik uygulama](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md). sınıfı hakkında daha fazla bilgi için `Globals` bkz. [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="manage-the-user-interface-of-the-task-pane"></a>Görev bölmesinin kullanıcı arabirimini yönetme
 Görev bölmesini oluşturduktan sonra, görev bölmesinin <xref:Microsoft.Office.Tools.CustomTaskPane> Kullanıcı arabirimini denetlemek ve Kullanıcı görev bölmesini değiştirdiğinde yanıt vermek için nesnenin özelliklerini ve olaylarını kullanabilirsiniz.

### <a name="make-the-custom-task-pane-visible"></a>Özel görev bölmesini görünür yapma
 Varsayılan olarak, görev bölmesi görünür değildir. Görev bölmesini görünür yapmak için <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> özelliği **true** olarak ayarlamanız gerekir.

 Kullanıcılar, görev bölmesinin köşesindeki **Kapat** düğmesine (X) tıklayarak istediğiniz zaman bir görev bölmesini kapatabilir. Ancak, kullanıcıların özel görev bölmesini yeniden açması için varsayılan bir yol yoktur. Bir kullanıcı özel bir görev bölmesini kapatırsa, onu görüntülemek için bir yol sağlamadığınız takdirde bu kullanıcı özel görev bölmesini görüntüleyemez.

 VSTO eklentisi içinde özel bir görev bölmesi oluşturursanız, kullanıcıların özel görev bölmenizi görüntülemesi veya gizleyebilmek için, düğme gibi bir kullanıcı arabirimi öğesi de oluşturmanız gerekir. şeriti özelleştirmeyi destekleyen bir Microsoft Office uygulamasında özel bir görev bölmesi oluşturursanız, özel görev bölmenizi görüntüleyen veya gizleyen bir düğme ile şerite bir denetim grubu ekleyebilirsiniz. Bunun nasıl yapılacağını gösteren bir anlatım için bkz. [Izlenecek yol: özel görev bölmesini Şerit düğmesi Ile senkronize](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)etme.

 şeriti özelleştirmeyi desteklemeyen bir Microsoft Office uygulamasında özel bir görev bölmesi oluşturursanız, <xref:Microsoft.Office.Core.CommandBarButton> özel görev bölmenizi görüntüleyen veya gizleyen bir ekleyebilirsiniz.

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
 kullanıcı özel görev bölmesini değiştirdiğinde VSTO eklentisinin yanıt vermesini isteyebilirsiniz. Örneğin, Kullanıcı bölmenin hizalamasını dikeyden yataya değiştirirse, denetimleri yeniden konumlandırmak isteyebilirsiniz.

 Aşağıdaki tabloda, kullanıcının özel görev bölmesine yaptığı değişikliklere yanıt vermek için işleyebilmeniz gereken olaylar listelenmektedir.

|Görev|Olay|
|----------|-----------|
|Kullanıcı görev bölmesinin konumunu değiştirdiğinde yanıt vermek için.|<xref:Microsoft.Office.Tools.CustomTaskPane.DockPositionChanged>|
|Kullanıcı görev bölmesini gizlediğini veya görünür hale getiren yanıt vermek için.|<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>|

## <a name="clean-up-resources-used-by-the-task-pane"></a>Görev bölmesi tarafından kullanılan kaynakları Temizleme
 özel bir görev bölmesi oluşturduktan sonra, <xref:Microsoft.Office.Tools.CustomTaskPane> VSTO eklentisi çalıştığı sürece nesne bellekte kalır. Kullanıcı görev bölmesinin köşesindeki **Kapat** düğmesine (X) tıkladıktan sonra bile, nesne bellekte kalır.

 VSTO eklentisi çalışmaya devam ederken görev bölmesi tarafından kullanılan kaynakları temizlemek için, <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> veya <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> yöntemlerini kullanın. Bu yöntemler <xref:Microsoft.Office.Tools.CustomTaskPane> , belirtilen nesneyi `CustomTaskPanes` koleksiyondan kaldırır ve `Dispose` nesnenin yöntemini çağırır.

 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisi kaldırıldığında özel görev bölmesi tarafından kullanılan kaynakları otomatik olarak temizler. <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.RemoveAt%2A> Projenizdeki olay işleyicisinde veya yöntemlerini çağırmayın `ThisAddIn_Shutdown` . <xref:System.ObjectDisposedException>Daha [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] önce nesne tarafından kullanılan kaynakları temizleyerek, bu yöntemler bir oluşturur <xref:Microsoft.Office.Tools.CustomTaskPane> `ThisAddIn_Shutdown` . hakkında daha fazla bilgi için `ThisAddIn_Shutdown` bkz. [Office projelerindeki olaylar](../vsto/events-in-office-projects.md).

## <a name="manage-custom-task-panes-in-multiple-application-windows"></a><a name="Managing"></a> Birden çok uygulama penceresinde özel görev bölmelerini yönetme
 Belgeleri ve diğer öğeleri göstermek için birden çok pencere kullanan bir uygulamada özel bir görev bölmesi oluşturduğunuzda, Kullanıcı onu beklediğinde görev bölmesinin görünebildiğinden emin olmak için ek adımlar gerçekleştirmeniz gerekir.

 Tüm uygulamalardaki özel görev bölmeleri, kullanıcıya bir belge veya öğe görünümü sunan bir belge çerçevesi penceresiyle ilişkilendirilir. Görev bölmesi yalnızca ilişkili pencere görünür olduğunda görülebilir. Ancak, tüm uygulamalar belge çerçevesi pencerelerini aynı şekilde kullanmaz.

 Aşağıdaki uygulama grupları farklı geliştirme gereksinimlerine sahiptir:

- [Outlook](#Outlook)

- [Word, InfoPath ve PowerPoint](#WordAndInfoPath)

## <a name="outlook"></a><a name="Outlook"></a>Outlook
 Özel görev bölmesi oluşturmak için özel Outlook, özel görev bölmesi belirli bir Gezgin veya Denetçi penceresiyle ilişkilendirildi. Gezginler, bir klasörün içeriğinin görüntül olduğu pencerelerdir ve Denetçiler ise e-posta iletisi veya görev gibi bir öğeyi içeren pencerelerdir.

 Birden çok Gezgin veya Denetçi penceresi olan bir özel görev bölmesi görüntülemek için, bir Gezgin veya Denetçi penceresi açıldığında özel görev bölmesinin yeni bir örneğini oluşturmanız gerekir. Bunu yapmak için, Bir Gezgin veya Denetçi penceresi oluşturulduğunda oluşturulan bir olayı işleyin ve ardından olay işleyicisinde görev bölmesini oluşturun. Hangi pencerenin görünür olduğuna bağlı olarak görev bölmelerini gizlemek veya görüntülemek için Gezgin ve Denetçi olaylarını da işleyebilirsiniz.

 Görev bölmesini belirli bir Gezgin veya Denetçi ile ilişkilendirmek için, görev bölmesini oluşturmak için yöntemini kullanın ve veya nesnesini <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> <xref:Microsoft.Office.Interop.Outlook.Explorer> pencere <xref:Microsoft.Office.Interop.Outlook.Inspector> *parametresine* iletir. Özel görev bölmeleri oluşturma hakkında daha fazla bilgi için bkz. [Özel görev bölmeleri'ne genel bakış.](../vsto/custom-task-panes.md)

- <xref:Microsoft.Office.Interop.Outlook.ExplorersEvents_Event.NewExplorer>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Deactivate>

  Denetçi pencerelerinin durumunu izlemek için, Denetçi ile ilgili aşağıdaki olayları iş yapabilirsiniz:

- <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Activate>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close>

- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Deactivate>

### <a name="prevent-multiple-instances-of-a-custom-task-pane-in-outlook"></a>Bir özel görev bölmesinin birden çok örneğini Outlook
 Özel Outlook bir görev bölmesinin birden çok örneğini görüntülemesini önlemek için, her pencere kapatılan özel görev bölmesini sınıfın `CustomTaskPanes` `ThisAddIn` koleksiyonundan açıkça kaldırın. veya <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Remove%2A> gibi bir pencere kapatılan bir olayda yöntemini <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_10_Event.Close> çağırma.

 Özel görev bölmesini açıkça kaldırıyorsanız, Outlook pencereler özel görev bölmesinin birden çok örneğini görüntüleyebilirsiniz. Outlook bazen pencereleri geri dönüştürer ve geri dönüştürülmüş pencereler, onlara eklenmiş olan özel görev bölmelerine başvurularını korur.

## <a name="word-infopath-and-powerpoint"></a><a name="WordAndInfoPath"></a>Word, InfoPath ve PowerPoint
 Word, InfoPath ve PowerPoint belgeyi farklı bir belge çerçevesi penceresinde görüntüler. Bu uygulamalar için özel bir görev bölmesi ekleyebilirsiniz. Özel görev bölmesi yalnızca belirli bir belgeyle ilişkilendirilmektedir. Kullanıcı farklı bir belge açarsa, önceki belge yeniden görünür olana kadar özel görev bölmesi gizlenir.

 Birden çok belge içeren bir özel görev bölmesi görüntülemek için, kullanıcı yeni bir belge oluşturduğunda veya mevcut bir belgeyi açtığında özel görev bölmesinin yeni bir örneğini oluşturun. Bunu yapmak için, bir belge oluşturulduğunda veya açıldığında oluşturulan olayları işleyebilirsiniz ve ardından olay işleyicileri içinde görev bölmesini oluşturun. Ayrıca, hangi belgenin görünür olduğuna bağlı olarak görev bölmelerini gizlemek veya görüntülemek için belge olaylarını işleyebilirsiniz.

 Görev bölmesini belirli bir belge penceresiyle ilişkilendirmek için, görev bölmesini oluşturmak için yöntemini kullanın ve pencere parametresine <xref:Microsoft.Office.Tools.CustomTaskPaneCollection.Add%2A> <xref:Microsoft.Office.Interop.Word.Window> bir (Word için), <xref:Microsoft.Office.Interop.InfoPath.WindowObject> (InfoPath için) veya [DocumentWindow](/previous-versions/office/developer/office-2010/ff762047(v=office.14)) (PowerPoint için) ekleyin. 

### <a name="word-events"></a>Sözcük olayları
 Word'de belge pencerelerinin durumunu izlemek için aşağıdaki olayları işebilirsiniz:

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeClose>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.NewDocument>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.WindowDeactivate>

### <a name="infopath-events"></a>InfoPath olayları
 InfoPath'te belge pencerelerinin durumunu izlemek için aşağıdaki olayları işebilirsiniz:

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.NewXDocument>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowActivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.WindowDeactivate>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentBeforeClose>

- <xref:Microsoft.Office.Interop.InfoPath._ApplicationEvents_Event.XDocumentOpen>

### <a name="powerpoint-events"></a>PowerPoint olayları
 Belge pencerelerinin durumunu bir PowerPoint için aşağıdaki olayları işebilirsiniz:

- [Microsoft. Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.AfterNewPresentation](/previous-versions/office/developer/office-2010/ff761105(v%3doffice.14))

- [Microsoft. Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v%3doffice.14))

- [Microsoft. Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.NewPresentation](/previous-versions/office/developer/office-2010/ff761498(v%3doffice.14))

- [Microsoft. Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.PresentationOpen](/previous-versions/office/developer/office-2010/ff760423(v=office.14))

- [Microsoft. Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.WindowActivate](/previous-versions/office/developer/office-2010/ff761153(v=office.14))

- [Microsoft. Office. Birlikte çalış -abilir -lik. PowerPoint. EApplication_Event.WindowDeactivate](/previous-versions/office/developer/office-2010/ff763093(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl ekleyebilirsiniz: Uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Adım adım kılavuz: Özel görev bölmesinden uygulamayı otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Adım adım kılavuz: Özel görev bölmesini Şerit düğmesiyle eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Adım adım kılavuz: Özel görev bölmelerini e-posta iletileriyle birlikte Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
