---
title: E-posta iletileri içeren özel görev bölmelerini Outlook
description: Microsoft'ta oluşturulan veya açılan her e-posta iletisiyle özel bir görev bölmesinin Outlook örneğini görüntülemeyi öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9fb3d933bd661a4a00a3998d9199b3cd469f7dbc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075599"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Adım adım kılavuz: Özel görev bölmelerini e-posta iletileriyle birlikte Outlook
  Bu kılavuzda, oluşturulan veya açılan her e-posta iletisiyle özel görev bölmesinin benzersiz bir örneğini görüntüleme gösterilir. Kullanıcılar her e-posta iletisinin Şeridinde bir düğme kullanarak özel görev bölmesini görüntüleyebilirsiniz veya gizleyebilirsiniz.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Birden çok Gezgin veya Denetçi penceresi olan bir özel görev bölmesini görüntülemek için, açılan her pencere için özel görev bölmesinin bir örneğini oluşturmanız gerekir. Windows'da özel görev bölmelerinin davranışı hakkında daha fazla Outlook [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

> [!NOTE]
> Bu kılavuzda, VSTO mantığı daha kolay tartışabilirsiniz.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Özel görev bölmesinin kullanıcı arabirimini (UI) tasarlama.

- Özel şerit kullanıcı arabirimi oluşturma.

- E-posta iletileriyle özel Şerit kullanıcı arabirimini görüntüleme.

- Denetçi pencerelerini ve özel görev bölmelerini yönetmek için bir sınıf oluşturma.

- VSTO Eklenti tarafından kullanılan kaynakları başlatma ve temizleme.

- Şerit iki durumlu düğmesini özel görev bölmesiyle eşitleme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya Microsoft Outlook 2010.

## <a name="create-the-project"></a>Proje oluşturma
 Özel görev bölmeleri, VSTO uygulanır. Başlangıç olarak, VSTO için bir Eklenti projesi Outlook.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. **OutlookMailItemTaskPane** **Outlook** bir eklenti projesi oluşturun. Outlook **Eklenti proje şablonunu** kullanın. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]*ThisAddIn.cs* veya *ThisAddIn.vb* kod dosyasını açar ve **OutlookMailItemTaskPane** projesini **Çözüm Gezgini.**

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlama
 Özel görev bölmeleri için görsel tasarımcı yoktur, ancak istediğiniz kullanıcı arabirimiyle bir kullanıcı denetimi tasarleyebilirsiniz. Bu bölmede özel görev VSTO denetimi içeren basit bir kullanıcı arabirimi <xref:System.Windows.Forms.TextBox> vardır. Bu kılavuzda daha sonra kullanıcı denetimi özel görev bölmesine eklenecektir.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Özel görev bölmesinin kullanıcı arabirimini tasarlamak için

1. Bu **Çözüm Gezgini** **OutlookMailItemTaskPane projesine** tıklayın.

2. Uygulama menüsünde **Project** Denetimi **Ekle'ye tıklayın.**

3. Yeni Öğe **Ekle iletişim kutusunda,** kullanıcı denetimi adını **TaskPaneControl** olarak değiştirin ve ekle'ye **tıklayın.**

     Kullanıcı denetimi tasarımcıda açılır.

4. Araç **Kutusunun Ortak** Denetimler **sekmesinden,** bir **TextBox denetimi** kullanıcı denetimine sürükleyin.

## <a name="design-the-user-interface-of-the-ribbon"></a>Şeridin kullanıcı arabirimini tasarlama
 Bu eklentinin hedeflerinden biri VSTO kullanıcılara her e-posta iletisi şeridinde özel görev bölmesini gizleme veya görüntüleme yolu vermektir. Kullanıcı arabirimini sağlamak için, kullanıcıların özel görev bölmesini görüntülemek veya gizlemek için tıklayabilirsiniz bir iki durumlu düğme görüntüleyen özel bir Şerit kullanıcı arabirimi oluşturun.

### <a name="to-create-a-custom-ribbon-ui"></a>Özel şerit kullanıcı arabirimi oluşturmak için

1. Yeni **Project** Ekle'ye **tıklayın.**

2. Yeni Öğe **Ekle iletişim kutusunda** Şerit **(Görsel Tasarımcı) öğesini seçin.**

3. Yeni Şeridin adını **ManageTaskPaneRibbon olarak değiştirerek** Ekle'ye **tıklayın.**

     *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon.vb* dosyası Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit Tasarımcısı'nda **group1'e tıklayın.**

5. Özellikler **penceresinde Etiket** özelliğini **Görev** Bölmesi Yöneticisi **olarak ayarlayın.**

6. Araç **kutusunun Office Şerit** Denetimleri **sekmesinden,** bir ToggleButton denetimlerini Görev Bölmesi **Yöneticisi grubuna** sürükleyin.

7. **toggleButton1 'e tıklayın.**

8. Özellikler **penceresinde** Etiket özelliğini Görev **Bölmesini** Göster **olarak ayarlayın.**

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Özel Şerit kullanıcı arabirimini e-posta iletileriyle görüntüleme
 Bu kılavuzda oluştursanız özel görev bölmesi yalnızca e-posta iletileri içeren Denetçi pencereleriyle görünecek şekilde tasarlanmıştır. Bu nedenle, özel Şerit kullanıcı arabiriminizi yalnızca bu pencerelerle görüntülemek için özellikleri ayarlayın.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Özel Şerit kullanıcı arabirimini e-posta iletileriyle görüntülemek için

1. Şerit Tasarımcısı'nda **ManageTaskPaneRibbon Şeridi'ne** tıklayın.

2. Özellikler **penceresinde** **RibbonType** öğesinin yanındaki açılan listeye tıklayın ve **Microsoft.Outlook.Mail.Compose** ve **Microsoft.Outlook. Mail.Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Denetçi pencerelerini ve özel görev bölmelerini yönetmek için bir sınıf oluşturma
 Eklentinin belirli bir e-VSTO özel görev bölmesini tanımlaması gereken birkaç durum vardır. Bu durumlar aşağıdakileri içerir:

- Kullanıcı bir e-posta iletisi kapatıyor. Bu durumda, VSTO eklenti tarafından kullanılan kaynakların doğru şekilde temizlenmesini sağlamak için VSTO özel görev bölmesini kaldırması gerekir.

- Kullanıcı özel görev bölmesini kapatıyor. Bu durumda, VSTO Ekle'nin e-posta iletisi şeridinde iki durumlu düğmenin durumunu güncelleştirmesi gerekir.

- Kullanıcı şeritteki iki durumlu düğmeyi tıkladığında. Bu durumda, VSTO ilgili görev bölmesini gizlemesi veya görüntülemesi gerekir.

  Eklentinin, VSTO görev bölmesinin her bir açık e-posta iletisiyle ilişkili olduğunu izlemesi için ve nesneleri çiftlerini sarmalar özel bir <xref:Microsoft.Office.Interop.Outlook.Inspector> sınıf <xref:Microsoft.Office.Tools.CustomTaskPane> oluşturun. Bu sınıf, her e-posta iletisi için yeni bir özel görev bölmesi nesnesi oluşturur ve karşılık gelen e-posta iletisi kapatılan özel görev bölmesini siler.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Denetçi pencerelerini ve özel görev bölmelerini yönetmek için bir sınıf oluşturmak için

1. Bu **Çözüm Gezgini** *ThisAddIn.cs* veya *ThisAddIn.vb* dosyasına sağ tıklayın ve ardından Kodu **Görüntüle'ye tıklayın.**

2. Aşağıdaki deyimlerini dosyanın en üstüne ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet2":::

3. Aşağıdaki kodu sınıfının dışında *ThisAddIn.cs* veya *ThisAddIn.vb* dosyasına ekleyin (Visual C# için bu kodu ad `ThisAddIn` alanına `OutlookMailItemTaskPane` ekleyin). sınıfı `InspectorWrapper` ve nesnelerinin bir <xref:Microsoft.Office.Interop.Outlook.Inspector> çiftini <xref:Microsoft.Office.Tools.CustomTaskPane> yönetir. Bu sınıfın tanımını aşağıdaki adımlarda tamamlayabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet3":::

4. Önceki adımda ekley istediğiniz kodun ardından aşağıdaki oluşturucuya ekleyin. Bu oluşturucu, geçirilen nesneyle ilişkili yeni bir özel görev <xref:Microsoft.Office.Interop.Outlook.Inspector> bölmesi oluşturur ve başlatılır. C# içinde oluşturucu, olay işleyicilerini nesnenin <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> olayına <xref:Microsoft.Office.Interop.Outlook.Inspector> ve nesnesinin <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> olayına da <xref:Microsoft.Office.Tools.CustomTaskPane> iliştirer.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet4":::

5. Önceki adımda ekley istediğiniz kodun ardından aşağıdaki yöntemi ekleyin. Bu yöntem, sınıfında yer alan <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> nesnesinin <xref:Microsoft.Office.Tools.CustomTaskPane> olayı için bir olay `InspectorWrapper` işleyicidir. Bu kod, kullanıcı özel görev bölmesini her açtığında veya kapattığınızda iki durumlu düğmenin durumunu günceller.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet5":::

6. Önceki adımda ekley istediğiniz kodun ardından aşağıdaki yöntemi ekleyin. Bu yöntem, geçerli e-posta <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> iletisi içeren nesnenin olayı için bir olay <xref:Microsoft.Office.Interop.Outlook.Inspector> işleyicidir. E-posta iletisi kapatılan olay işleyicisi kaynakları serbest bıraktırıyor. Olay işleyicisi, geçerli özel görev bölmesini de koleksiyondan `CustomTaskPanes` kaldırır. Bu, sonraki e-posta iletisi açıldığında özel görev bölmesinin birden çok örneğini önlemeye yardımcı olur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet6":::

7. Önceki adımda ekley istediğiniz kodun ardından aşağıdaki kodu ekleyin. Bu kılavuzda daha sonra, özel görev bölmesini görüntülemek veya gizlemek için özel Şerit kullanıcı arabiriminde bir yöntemden bu özelliği çağıracağız.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet7":::

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Eklenti tarafından kullanılan kaynakları başlatma ve temizleme
 yüklendiğinde VSTO Eklentiyi başlatmak ve yüklemesi kaldırılan VSTO kaynakları temizlemek için sınıfına `ThisAddIn` kod ekleyin. Olay için bir VSTO işleyici ayarerek ve mevcut tüm e-posta iletilerini bu olay işleyiciye aktararak <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> eklentiyi başlatabilirsiniz. Eklenti VSTO kaldırılmışsa, olay işleyicisini ayırıp eklentinin VSTO nesneleri temizleyin.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>VSTO Eklentisinde kullanılan kaynakları başlatmak ve temizlemek için

1. *ThisAddIn.cs* veya *ThisAddIn.vb* dosyasında sınıfının tanımını `ThisAddIn` bulun.

2. Sınıfına aşağıdaki bildirimleri `ThisAddIn` ekleyin:

   - alanı, `inspectorWrappersValue` VSTO <xref:Microsoft.Office.Interop.Outlook.Inspector> `InspectorWrapper` Add-in tarafından yönetilen tüm ve nesnelerini içerir.

   - alanı, `inspectors` geçerli örnek içinde Denetçi pencerelerinin koleksiyonuna bir başvuru Outlook sağlar. Bu başvuru, atık toplayıcının olay için olay işleyicisini içeren belleği serbest bırakarak bir sonraki <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> adımda bildireceklerini önler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet8":::

3. `ThisAddIn_Startup` yöntemini aşağıdaki kodla değiştirin. Bu kod, olayına bir olay <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> işleyicisi iliştirer ve mevcut her <xref:Microsoft.Office.Interop.Outlook.Inspector> nesneyi olay işleyiciye iletir. Kullanıcı VSTO zaten Outlook sonra VSTO eklentiyi yüklerse, VSTO Eklentisi zaten açık olan tüm e-posta iletileri için özel görev bölmeleri oluşturmak üzere bu bilgileri kullanır.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet9":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet9":::

4. `ThisAddIn_ShutDown` yöntemini aşağıdaki kodla değiştirin. Bu kod, olay <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> işleyicisini ayırır ve eklentinin VSTO nesneleri temizler.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet10":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet10":::

5. Aşağıdaki olay <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> işleyicisini sınıfına `ThisAddIn` ekleyin. Yeni bir <xref:Microsoft.Office.Interop.Outlook.Inspector> e-posta iletisi içeriyorsa, yöntemi e-posta iletisi ile karşılık gelen görev bölmesi arasındaki ilişkiyi yönetmek için yeni `InspectorWrapper` bir nesne örneği oluşturur.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet11":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet11":::

6. Sınıfına aşağıdaki özelliği `ThisAddIn` ekleyin. Bu özellik, özel alanı `inspectorWrappersValue` sınıfın dışında kod olarak ortaya `ThisAddIn` çıkarır.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet12":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet12":::

## <a name="checkpoint"></a>Checkpoint
 Projenizi derlenin ve hatasız derlenin.

### <a name="to-build-your-project"></a>Projenizi derlemek için

1. Bu **Çözüm Gezgini** **OutlookMailItemTaskPane** projesine sağ tıklayın ve ardından Derle'ye **tıklayın.** Projenin hatasız derlenmiş olduğunu doğrulayın.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Şerit iki durumlu düğmesini özel görev bölmesiyle eşitle
 Görev bölmesi görünür olduğunda iki durumlu düğmede basılmış gibi görünür ve görev bölmesi gizliyken düğmede basılmış gibi görünür. Düğmenin durumunu özel görev bölmesiyle eşitlemek için iki durumlu <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> düğmenin olay işleyicisini değiştirebilirsiniz.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Özel görev bölmesini iki durumlu düğmeyle eşitlemek için

1. Şerit Tasarımcısı'nda Görev Bölmesini **Göster iki durumlu düğmesine** çift tıklayın.

     Visual Studio, iki durumlu düğmenin `toggleButton1_Click` olaylarını işleyicisi <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> olarak otomatik olarak adlı bir olay işleyicisi üretir. Visual Studio, Kod Düzenleyicisi'nde *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon.vb* dosyasını da açar.

2. *ManageTaskPaneRibbon.cs* veya *ManageTaskPaneRibbon.vb* dosyasının en üstüne aşağıdaki deyimlerini ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet14":::

3. Olay `toggleButton1_Click` işleyicisini aşağıdaki kodla değiştirin. Kullanıcı iki durumlu düğmeye tıkladığında, bu yöntem geçerli Denetçi penceresiyle ilişkili özel görev bölmesini gizler veya görüntüler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet15":::

## <a name="test-the-project"></a>Projeyi test etme
 Projede hata ayıklamaya başlarken Outlook açılır ve VSTO yüklenir. Ek VSTO, açılan her e-posta iletisiyle birlikte özel görev bölmesinin benzersiz bir örneğini görüntüler. Kodu test etmek için birkaç yeni e-posta mesajı oluşturun.

### <a name="to-test-the-vsto-add-in"></a>Eklentiyi VSTO için

1. **F5 tuşuna basın.**

2. Yeni Outlook yeni bir **e-posta** iletisi oluşturmak için Yeni'ye tıklayın.

3. E-posta iletisi şeridinde Eklentiler **sekmesine** ve ardından Görev Bölmesini Göster **düğmesine** tıklayın.

    Görev bölmesi başlığına sahip bir görev **bölmesinin e-posta** iletisiyle birlikte görüntülendiğinden emin olmak.

4. Görev bölmesinde, metin **kutusuna İlk görev** bölmesi yazın.

5. Görev bölmesini kapatın.

    Görev Bölmesini Göster **düğmesinin durumunun artık** basılameyecek şekilde değiştiklerini doğrulayın.

6. Görev Bölmesini **Göster düğmesine yeniden** tıklayın.

    Görev bölmesinin aç olduğunu ve metin kutusunun yine de İlk görev bölmesi **dizesini içerdiğini doğrulayın.**

7. İkinci Outlook **e-posta iletisi oluşturmak** için Yeni'ye tıklayın.

8. E-posta iletisi şeridinde Eklentiler **sekmesine** ve ardından Görev Bölmesini Göster **düğmesine** tıklayın.

    Görev bölmesi başlığına sahip  bir görev bölmesinin e-posta iletisiyle birlikte görüntülendiğinden ve bu görev bölmesindeki metin kutusunun boş olduğunu doğrulayın.

9. Görev bölmesinde, metin **kutusuna İkinci görev** bölmesi yazın.

10. Odağı ilk e-posta iletisiyle değiştirme.

     Bu e-posta iletisiyle ilişkili görev bölmesinin yine de metin kutusunda **İlk görev bölmesini** görüntüleyeni olduğunu doğrulayın.

    Bu VSTO Eklenti, deney deneyen daha gelişmiş senaryoları da ele almaktadır. Örneğin, Sonraki Öğe ve Önceki Öğe düğmelerini kullanarak e-postaları **görüntülerken davranışı** **test** edin. Ayrıca eklentiyi kaldırıp eklentiyi kaldırıp VSTO e-posta iletilerini açıp eklentiyi yeniden VSTO de test edin.

## <a name="next-steps"></a>Sonraki adımlar
 Özel görev bölmeleri oluşturma hakkında daha fazla bilgi edinmek için şu konu başlıklarını kullanabilirsiniz:

- Farklı bir uygulama için bir VSTO özel görev bölmesi oluşturun. Özel görev bölmelerini destekleyen uygulamalar hakkında daha fazla bilgi için [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

- Özel Microsoft Office kullanarak bir uygulamanın otomatikleştirmesi. Daha fazla bilgi için [bkz. Adım adım: Özel görev bölmesinden bir uygulamayı otomatikleştirme.](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)

- Özel bir görev bölmesini Excel veya görüntülemek için kullanılan bir şerit düğmesi oluşturun. Daha fazla bilgi için [bkz. Adım adım: Şerit düğmesiyle özel görev bölmesini eşitleme.](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Nasıl ekleyebilirsiniz: Uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Adım adım kılavuz: Özel görev bölmesinden uygulamayı otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Adım adım kılavuz: Özel görev bölmesini Şerit düğmesiyle eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Outlook modeline genel bakış](../vsto/outlook-object-model-overview.md)
- [Çalışma zamanında şerite erişme](../vsto/accessing-the-ribbon-at-run-time.md)
