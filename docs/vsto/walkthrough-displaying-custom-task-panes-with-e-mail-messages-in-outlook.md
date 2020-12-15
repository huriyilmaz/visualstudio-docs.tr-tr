---
title: Outlook 'ta e-posta iletileriyle özel görev bölmelerini görüntüleme
description: Oluşturulan veya açılan Microsoft Outlook 'taki her bir e-posta iletisiyle özel bir görev bölmesinin benzersiz bir örneğini görüntülemeyi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac14eff05c6f776181c20acde4cff4e2ed7a87b6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522709"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>İzlenecek yol: Outlook 'ta e-posta iletileriyle özel görev bölmelerini görüntüleme
  Bu izlenecek yol, oluşturulan veya açılan her bir e-posta iletisiyle özel bir görev bölmesinin benzersiz bir örneğinin nasıl görüntüleneceğini gösterir. Kullanıcılar, her bir e-posta iletisinin şeridinde bir düğme kullanarak özel görev bölmesini görüntüleyebilir veya gizleyebilir.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Birden çok gezgin veya Inspector penceresi içeren özel bir görev bölmesini göstermek için, açılan her pencere için özel görev bölmesinin bir örneğini oluşturmanız gerekir. Outlook Windows 'daki özel görev bölmelerinin davranışı hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

> [!NOTE]
> Bu izlenecek yol, kodun arkasındaki mantığın daha kolay bir şekilde açıklanbilmesini sağlamak için VSTO eklenti kodunu küçük bölümler halinde gösterir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel görev bölmesinin kullanıcı arabirimini (UI) tasarlama.

- Özel şerit kullanıcı arabirimi oluşturma.

- Özel şerit kullanıcı arabirimini e-posta iletileriyle görüntüleme.

- Inspector pencerelerini ve özel görev bölmelerini yönetmek için bir sınıf oluşturma.

- VSTO eklentisi tarafından kullanılan kaynakları başlatma ve temizleme.

- Şerit geçiş düğmesini özel görev bölmesiyle eşitleme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya Microsoft Outlook 2010.

## <a name="create-the-project"></a>Proje oluşturma
 Özel görev bölmeleri VSTO eklentilerinde uygulanır. Outlook için bir VSTO eklentisi projesi oluşturarak başlayın.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **OutlookMailItemTaskPane** adlı bir **Outlook eklenti** projesi oluşturun. **Outlook eklentisi** proje şablonunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]*ThisAddIn.cs* veya *ThisAddIn. vb* kod dosyasını açar ve **outlookmailıtemtaskpane** projesini **Çözüm Gezgini** ekler.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlama
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz kullanıcı ARABIRIMINI kullanarak bir kullanıcı denetimi tasarlayabilirsiniz. Bu VSTO eklentisinin özel görev bölmesinde bir denetim içeren basit bir UI vardır <xref:System.Windows.Forms.TextBox> . Bu izlenecek yolda daha sonra Kullanıcı denetimini özel görev bölmesine ekleyeceksiniz.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlamak için

1. **Çözüm Gezgini**, **OutlookMailItemTaskPane** projesine tıklayın.

2. **Proje** menüsünde **Kullanıcı denetimi Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** iletişim kutusunda, Kullanıcı denetiminin adını **TaskPaneControl** olarak değiştirin ve ardından **Ekle**' ye tıklayın.

     Kullanıcı denetimi tasarımcıda açılır.

4. **Araç kutusunun** **ortak denetimler** sekmesinden kullanıcı denetimine bir **TextBox** denetimi sürükleyin.

## <a name="design-the-user-interface-of-the-ribbon"></a>Şeridin Kullanıcı arabirimini tasarlama
 Bu VSTO eklentisinin amaçlarından biri, kullanıcılara her bir e-posta iletisinin şeritlerinden özel görev bölmesini gizleme veya görüntüleme yöntemi vermektir. Kullanıcı arabirimini sağlamak için, kullanıcıların özel görev bölmesini göstermek veya gizlemek için tıklacılarını gösteren bir iki durumlu düğme görüntüleyen özel bir şerit kullanıcı arabirimi oluşturun.

### <a name="to-create-a-custom-ribbon-ui"></a>Özel bir şerit kullanıcı arabirimi oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şeridin adını **ManageTaskPaneRibbon** olarak değiştirin ve **Ekle**' ye tıklayın.

     *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon. vb* dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit tasarımcısında, **grup1**' e tıklayın.

5. **Özellikler** penceresinde, **etiket** özelliğini **görev bölmesi Yöneticisi** olarak ayarlayın.

6. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden bir ToggleButton denetimini **görev bölmesi Yöneticisi** grubuna sürükleyin.

7. **ToggleButton1** tıklayın.

8. **Özellikler** penceresinde, **etiket** özelliğini **görev bölmesini göster** olarak ayarlayın.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>E-posta iletileriyle özel şerit kullanıcı arabirimini görüntüleme
 Bu kılavuzda oluşturduğunuz özel görev bölmesi, yalnızca e-posta iletileri içeren Inspector pencereleri ile görüntülenecek şekilde tasarlanmıştır. Bu nedenle, özellikleri özel şerit Kullanıcı arabiriminizi yalnızca bu pencereler ile görüntüleyecek şekilde ayarlayın.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Özel şerit kullanıcı arabirimini e-posta iletileriyle birlikte görüntüleme

1. Şerit tasarımcısında, **ManageTaskPaneRibbon** Şeritine tıklayın.

2. **Özellikler** penceresinde, **RibbonType**' ın yanındaki açılan listeye tıklayın ve **Microsoft. Outlook. mail. Compose** ve **Microsoft. Outlook. mail. Read**' i seçin.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Inspector pencerelerini ve özel görev bölmelerini yönetmek için bir sınıf oluşturma
 VSTO eklentisinin belirli bir e-posta iletisiyle ilişkili olan özel görev bölmesini tanımlaması gereken birkaç durum vardır. Bu durumlar şunları içerir:

- Kullanıcı bir e-posta iletisini kapattığında. Bu durumda, VSTO eklentisi tarafından kullanılan kaynakların doğru şekilde temizlendiğinden emin olmak için VSTO eklentisinin karşılık gelen özel görev bölmesini kaldırması gerekir.

- Kullanıcı özel görev bölmesini kapattığında. Bu durumda, VSTO eklentisi e-posta iletisinin şeridinde iki durumlu düğmenin durumunu güncelleştirmelidir.

- Kullanıcı Şeritteki iki durumlu düğmeye tıkladığında. Bu durumda, VSTO eklentisinin ilgili görev bölmesini gizlemeniz veya görüntülemesi gerekir.

  Tüm açık e-posta iletileri ile hangi özel görev bölmesinin ilişkilendirildiğini izlemeye devam etmek için VSTO eklentisini etkinleştirmek üzere, ve nesnelerinin çiftlerini sarmalayan özel bir sınıf oluşturun <xref:Microsoft.Office.Interop.Outlook.Inspector> <xref:Microsoft.Office.Tools.CustomTaskPane> . Bu sınıf her e-posta iletisi için yeni bir özel görev bölmesi nesnesi oluşturur ve ilgili e-posta iletisi kapatıldığında özel görev bölmesini siler.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Inspector pencerelerini ve özel görev bölmelerini yönetmek üzere bir sınıf oluşturmak için

1. **Çözüm Gezgini**, *ThisAddIn.cs* veya *ThisAddIn. vb* dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. Aşağıdaki deyimlerini dosyanın en üstüne ekleyin.

     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]

3. Aşağıdaki kodu, sınıfının dışında (  Visual C# için, bu kodu ad alanı içine ekleyin) ThisAddIn.cs veya *ThisAddIn. vb* dosyasına ekleyin `ThisAddIn` `OutlookMailItemTaskPane` . `InspectorWrapper`Sınıfı, <xref:Microsoft.Office.Interop.Outlook.Inspector> ve nesnelerini yönetir <xref:Microsoft.Office.Tools.CustomTaskPane> . Aşağıdaki adımlarda bu sınıfın tanımını tamamlayacaksınız.

     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]

4. Önceki adımda eklediğiniz koddan sonra aşağıdaki oluşturucuyu ekleyin. Bu Oluşturucu, geçirilen nesneyle ilişkili yeni bir özel görev bölmesi oluşturur ve başlatır <xref:Microsoft.Office.Interop.Outlook.Inspector> . C# ' de, Oluşturucu olay işleyicilerini <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> <xref:Microsoft.Office.Interop.Outlook.Inspector> nesnenin olayına ve nesnenin olayına de ekler <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> <xref:Microsoft.Office.Tools.CustomTaskPane> .

     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]

5. Önceki adımda eklediğiniz koddan sonra aşağıdaki yöntemi ekleyin. Bu yöntem, <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> sınıfında bulunan nesnesinin olayı için bir olay işleyicisidir <xref:Microsoft.Office.Tools.CustomTaskPane> `InspectorWrapper` . Bu kod, Kullanıcı özel görev bölmesini her açtığında veya kapattığında iki durumlu düğmenin durumunu güncelleştirir.

     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]

6. Önceki adımda eklediğiniz koddan sonra aşağıdaki yöntemi ekleyin. Bu yöntem, <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> <xref:Microsoft.Office.Interop.Outlook.Inspector> geçerli e-posta iletisini içeren nesnenin olayına yönelik bir olay işleyicisidir. Olay işleyicisi, e-posta iletisi kapatıldığında kaynakları serbest bırakır. Olay işleyicisi aynı zamanda geçerli özel görev bölmesini `CustomTaskPanes` koleksiyondan kaldırır. Bu, sonraki e-posta iletisi açıldığında özel görev bölmesinin birden çok örneğinin engellenmesine yardımcı olur.

     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]

7. Önceki adımda eklediğiniz koddan sonra aşağıdaki kodu ekleyin. Bu kılavuzda daha sonra, özel görev bölmesini göstermek veya gizlemek için özel şerit Kullanıcı arabirimindeki bir yöntemden bu özelliği çağıracaksınız.

     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Eklenti tarafından kullanılan kaynakları başlatma ve Temizleme
 `ThisAddIn`YÜKLENDIĞINDE VSTO eklentisini başlatmak ve bu eklentinin KALDıRıLDıĞıNDA VSTO eklentisi tarafından kullanılan kaynakları temizlemek için sınıfa kod ekleyin. Etkinlik için bir olay işleyicisi ayarlayarak <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> ve var olan tüm e-posta iletilerini bu olay işleyicisine GEÇIREREK VSTO eklentisini başlatırsınız. VSTO eklentisi kaldırıldığında, olay işleyicisini ayırın ve VSTO eklentisi tarafından kullanılan nesneleri temizleyin.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>VSTO eklentisi tarafından kullanılan kaynakları başlatmak ve temizlemek için

1. *ThisAddIn.cs* veya *ThisAddIn. vb* dosyasında, sınıfının tanımını bulun `ThisAddIn` .

2. Sınıfına aşağıdaki bildirimleri ekleyin `ThisAddIn` :

   - `inspectorWrappersValue`Alan, <xref:Microsoft.Office.Interop.Outlook.Inspector> `InspectorWrapper` VSTO eklentisi tarafından yönetilen tüm ve nesnelerini içerir.

   - Bu `inspectors` alan, geçerli Outlook örneğindeki Inspector pencerelerinin koleksiyonuna bir başvuru tutar. Bu başvuru, çöp toplayıcısının bir <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> sonraki adımda bildirdiğiniz olay işleyicisini içeren belleği boşaltmasını önler.

     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]

3. `ThisAddIn_Startup` yöntemini aşağıdaki kodla değiştirin. Bu kod, olaya bir olay işleyicisi ekler <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> ve tüm mevcut <xref:Microsoft.Office.Interop.Outlook.Inspector> nesneleri olay işleyicisine geçirir. Kullanıcı, Outlook zaten çalıştıktan sonra VSTO eklentisini yüklerse, VSTO eklentisi zaten açık olan tüm e-posta iletileri için özel görev bölmeleri oluşturmak üzere bu bilgileri kullanır.

    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]

4. `ThisAddIn_ShutDown` yöntemini aşağıdaki kodla değiştirin. Bu kod, <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay işleyicisini ayırır ve VSTO eklentisi tarafından kullanılan nesneleri temizler.

    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]

5. Aşağıdaki <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> olay işleyicisini `ThisAddIn` sınıfına ekleyin. Yeni bir <xref:Microsoft.Office.Interop.Outlook.Inspector> e-posta iletisi içeriyorsa, yöntemi `InspectorWrapper` e-posta iletisi ile buna karşılık gelen görev bölmesi arasındaki ilişkiyi yönetmek için yeni bir nesne örneği oluşturur.

    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]

6. Sınıfına aşağıdaki özelliği ekleyin `ThisAddIn` . Bu özellik özel `inspectorWrappersValue` alanını sınıfının dışında kodla gösterir `ThisAddIn` .

    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]

## <a name="checkpoint"></a>Checkpoint
 Hata olmadan derlendiğinden emin olmak için projenizi derleyin.

### <a name="to-build-your-project"></a>Projenizi derlemek için

1. **Çözüm Gezgini**, **OutlookMailItemTaskPane** projesine sağ tıklayın ve ardından **Oluştur**' a tıklayın. Projenin hata olmadan derlendiğini doğrulayın.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Şerit geçiş düğmesini özel görev bölmesiyle eşitler
 Görev bölmesi görünür olduğunda iki durumlu düğme basıldığında görünür ve görev bölmesi gizli olduğunda basılı olarak görünür. Düğmenin durumunu özel görev bölmesiyle senkronize etmek için <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olay işleyicisini değiştirin.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Özel görev bölmesini iki durumlu düğmeyle eşleştirmek için

1. Şerit tasarımcısında **görev bölmesini göster** iki durumlu düğmesine çift tıklayın.

     Visual Studio, `toggleButton1_Click` <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olayını işleyen adlı bir olay işleyicisini otomatik olarak oluşturur. Visual Studio Ayrıca kod düzenleyicisinde *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon. vb* dosyasını açar.

2. Aşağıdaki deyimlerini *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon. vb* dosyasının en üstüne ekleyin.

     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]

3. `toggleButton1_Click`Olay işleyicisini aşağıdaki kodla değiştirin. Kullanıcı iki durumlu düğmeye tıkladığında, bu yöntem geçerli Inspector penceresiyle ilişkili özel görev bölmesini gizler veya görüntüler.

     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]

## <a name="test-the-project"></a>Projeyi test etme
 Projenin hata ayıklamasını başlattığınızda Outlook açılır ve VSTO eklentisi yüklenir. VSTO eklentisi, açılan her bir e-posta iletisiyle özel görev bölmesinin benzersiz bir örneğini görüntüler. Kodu test etmek için birkaç yeni e-posta iletisi oluşturun.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisini test etmek için

1. **F5** tuşuna basın.

2. Outlook 'ta yeni bir e-posta iletisi oluşturmak için **Yeni** ' ye tıklayın.

3. E-posta iletisinin şeridinde, **Eklentiler** sekmesine tıklayın ve ardından **görev bölmesini göster** düğmesine tıklayın.

    **Görev Bölmesimin** bulunduğu bir görev bölmesinin e-posta iletisiyle görüntülendiğini doğrulayın.

4. Görev bölmesinde, metin kutusuna **ilk görev bölmesini** yazın.

5. Görev bölmesini kapatın.

    **Görev bölmesini göster** düğmesinin durumunun artık basılmayacak şekilde değiştiğini doğrulayın.

6. **Görev bölmesini göster** düğmesine tekrar tıklayın.

    Görev bölmesinin açıldığını ve metin kutusunun hala dize **ilk görev bölmesini** içerdiğini doğrulayın.

7. Outlook 'ta, ikinci bir e-posta iletisi oluşturmak için **Yeni** ' ye tıklayın.

8. E-posta iletisinin şeridinde, **Eklentiler** sekmesine tıklayın ve ardından **görev bölmesini göster** düğmesine tıklayın.

    **Görev Bölmesimin** bulunduğu görev bölmesinin e-posta iletisiyle görüntülendiğini ve bu görev bölmesindeki metin kutusunu boş olduğunu doğrulayın.

9. Görev bölmesinde, metin kutusuna **ikinci görev bölmesini** yazın.

10. Odağı ilk e-posta iletisiyle değiştirin.

     Bu e-posta iletisiyle ilişkili görev bölmesinin, hala metin kutusunda **ilk görev bölmesini** görüntülediğini doğrulayın.

    Bu VSTO eklentisi, deneyebileceğiniz daha gelişmiş senaryolar da işler. Örneğin, bir **sonraki öğeyi** ve **önceki öğe** düğmelerini kullanarak e-postaları görüntülerken davranışı test edebilirsiniz. Ayrıca, VSTO eklentisini kaldırdığınızda davranışı test edebilir, birkaç e-posta iletisi açıp VSTO eklentisini yeniden yükleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan özel görev bölmeleri oluşturma hakkında daha fazla bilgi edinebilirsiniz:

- Farklı bir uygulama için VSTO eklentisi içinde özel bir görev bölmesi oluşturun. Özel görev bölmelerini destekleyen uygulamalar hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

- Bir Microsoft Office uygulamasını özel bir görev bölmesi kullanarak otomatikleştirin. Daha fazla bilgi için bkz. [Izlenecek yol: uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Excel 'de, özel bir görev bölmesini gizlemek veya göstermek için kullanılabilecek bir Şerit düğmesi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: özel görev bölmesini Şerit düğmesi Ile senkronize](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)etme.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [İzlenecek yol: özel görev bölmesini Şerit düğmesi ile senkronize etme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
