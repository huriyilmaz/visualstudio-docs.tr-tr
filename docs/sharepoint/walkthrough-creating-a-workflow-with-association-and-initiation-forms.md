---
title: İlişki ve başlatma formları ile iş akışı oluşturma
description: Bu SharePoint, ilişkilendirme ve başlatma formlarının kullanımını içeren temel bir sıralı iş akışı oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2f3852452d163f14e93b73e7fd894759f7aa0197
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625088"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Adım adım kılavuz: İlişki ve başlatma formları ile iş akışı oluşturma
  Bu kılavuzda, ilişkilendirme ve başlatma formlarının kullanımını içeren temel bir sıralı iş akışının nasıl oluşturularak ilgili bilgiler ve bilgiler yer almaktadır. Bunlar, bir iş akışına parametrelerin SharePoint yöneticisi (ilişkilendirme formu) tarafından ilk kez ilişkilendirilirken ve iş akışı kullanıcı tarafından (başlatma formu) başlatılana kadar eklenebilecek ASPX formlarıdır.

 Bu kılavuzda, bir kullanıcının aşağıdaki gereksinimlere sahip gider raporları için onay iş akışı oluşturmak istediği bir senaryo özetlemektedir:

- İş akışı bir listeyle ilişkilendirildiğinde, yöneticiden gider raporları için dolar sınırı girmeleri için bir ilişkilendirme formu istenir.

- Çalışanlar gider raporlarını Paylaşılan Belgeler listesine yükler, iş akışını başlatarak iş akışı başlatma formuna gider toplamı girer.

- Bir çalışan gider raporu toplamı yöneticinin önceden tanımlanmış sınırını aşarsa, çalışanın yöneticisinin gider raporunu onaylaması için bir görev oluşturulur. Ancak, bir çalışanın gider raporu toplamı gider limitine eşit veya daha küçükse, iş akışının geçmiş listesine otomatik olarak onaylanan bir ileti yazılır.

  Bu izlenecek yol aşağıdaki görevleri gösterir:

- içinde bir SharePoint listesi tanımı sıralı iş akışı projesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturma.

- İş akışı zamanlaması oluşturma.

- İş akışı etkinlik olaylarını işleme.

- İş akışı ilişkilendirme ve başlatma formları oluşturma.

- İş akışının irdeleni.

- İş akışını el ile başlatma.

> [!NOTE]
> Bu kılavuz sıralı bir iş akışı projesi kullanıyor olsa da, işlem durum makinesi iş akışları için aynıdır.
>
> Ayrıca, bilgisayarınız aşağıdaki yönergelerde bazı kullanıcı arabirimi öğeleri için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] farklı adlar veya konumlar gösterebilir. Sahip [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] olduğunuz sürüm ve bu öğeleri kullanmak ayarları belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen ve sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Sıralı iş SharePoint projesi oluşturma
 İlk olarak, içinde sıralı bir iş akışı projesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturun. Sıralı iş akışı, son etkinlik sona e kadar sırayla yürütülen bir dizi adımdır. Bu yordamda, SharePoint'daki Paylaşılan Belgeler listesine uygulanan sıralı bir iş SharePoint. İş akışının sihirbazı, iş akışını site veya liste tanımıyla ilişkilendirmenizi sağlar ve iş akışının ne zaman başlayacağını belirlemenizi sağlar.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Sıralı iş akışı SharePoint oluşturmak için

1. Menü çubuğunda, Yeni dosya **iletişim**  >  **kutusunu**  >  **Project** Dosya Yeni **Dosya'Project** seçin.

2. Visual **C# SharePoint** altındaki  Visual Basic düğümünü **genişletin** ve **ardından 2010 düğümünü** seçin.

3. Şablonlar **bölmesinde,** **2010** SharePoint proje şablonunu Project seçin.

4. Ad **kutusuna** **ExpenseReport yazın ve** Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

5. Hata **ayıklama için siteyi** ve güvenlik düzeyini  belirtin sayfasında Grup çözümü olarak dağıt  seçeneğini belirleyin ve ardından Son düğmesini seçerek güven düzeyini ve varsayılan siteyi kabul edin.

     Bu adım ayrıca çözümün güven düzeyini, iş akışı projeleri için kullanılabilen tek seçenek olan grup çözümü olarak ayarlar.

6. Bu **Çözüm Gezgini** proje düğümünü seçin.

7. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

8. Visual **C# veya** **Visual Basic** altında, SharePoint **düğümünü** genişletin ve **ardından 2010 düğümünü** seçin.

9. Şablonlar **bölmesinde Sıralı** İş Akışı (yalnızca Grup **Çözümü)** şablonunu ve ardından Ekle **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

10. Hata ayıklama **için iş akışı adını belirtin sayfasında** varsayılan adı kabul edin (**ExpenseReport - Workflow1**). Varsayılan iş akışı şablon türü değerini (İş Akışını **Listele) kullanın.** Sonraki **düğmesini** seçin.

11. İş **akışını bir hata Visual Studio** otomatik olarak ilişkilendirmek mi istediğiniz? sayfasında, iş akışı şablonunuz denetlenirse otomatik olarak ilişkilendiren kutuyu temizleyin.

     Bu adım, iş akışını daha sonra ilişkilendirme formunu görüntüleyen Paylaşılan Belgeler listesiyle el ile ilişkilendirmenizi sağlar.

12. Son **düğmesini** seçin.

## <a name="add-an-association-form-to-the-workflow"></a>İş akışına ilişkilendirme formu ekleme
 Ardından bir oluşturun. SharePoint yöneticisi iş akışını bir gider raporu belgesiyle ilişkilendirse görüntülenen ASPX ilişkilendirme formu.

#### <a name="to-add-an-association-form-to-the-workflow"></a>İş akışına bir ilişkilendirme formu eklemek için

1. içinde **Workflow1 düğümünü** **Çözüm Gezgini.**

2. Yeni Öğe Ekle iletişim **kutusunu Project**  >  **menü çubuğunda** Yeni Öğe **Ekle'yi** seçin.

3. İletişim kutusu ağaç görünümünde **Visual C#** **veya Visual Basic** (proje dilinize bağlı olarak) genişletin, SharePoint **düğümünü** genişletin ve **ardından 2010 düğümünü** seçin.

4. Şablon listesinde İş Akışı İlişkisi Formu **şablonunu** seçin.

5. Ad **metin kutusuna** **ExpenseReportAssocForm.aspx yazın.**

6. Formu **projeye** eklemek için Ekle düğmesini seçin.

## <a name="designing-and-coding-the-association-form"></a>İlişki formunu tasarlama ve kodlama
 Bu yordamda, buna denetimler ve kod ekleyerek ilişkilendirme formuna işlevsellik eklersiniz.

#### <a name="to-design-and-code-the-association-form"></a>İlişki formunu tasarlamak ve kod oluşturmak için

1. İlişkilendirilen formda (ExpenseReportAssocForm.aspx), `asp:Content` olan öğesini `ID="Main"` bulun.

2. Bu içerik öğesinde ilk satırın hemen sonra, gider onay sınırını *(AutoApproveLimit)* istenecek bir etiket ve metin kutusu oluşturmak için aşağıdaki kodu ekleyin:

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Bağımlı dosyalarını **görüntülemek için Çözüm Gezgini ExpenseReportAssocForm.aspx** dosyasını genişletin. 

    > [!NOTE]
    > Projeniz içinde [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ise, bu adımı gerçekleştirmek için **Tüm Dosyaları** Görüntüle düğmesini seçmeniz gerekir.

4. ExpenseReportAssocForm.aspx dosyasının kısayol menüsünü açın ve Kodu **Görüntüle'yi seçin.**

5. yöntemini `GetAssociationData` şu şekilde değiştirin:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>İş akışına bir başlatma formu ekleme
 Ardından, kullanıcılar iş akışını gider raporlarına göre çalıştıracakları zaman görünen başlatma formunu oluşturun.

#### <a name="to-create-an-initiation-form"></a>Bir başlat formu oluşturmak için

1. içinde **Workflow1 düğümünü** **Çözüm Gezgini.**

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **Ekle iletişim** kutusunu **görüntüle'yi** seçin.

3. İletişim kutusu ağaç görünümünde **Visual C#** **veya** Visual Basic (proje dilinize bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

4. Şablon listesinde İş Akışı Başlatma **Formu şablonunu** seçin.

5. Ad **metin kutusuna** **ExpenseReportInitForm.aspx yazın.**

6. Formu **projeye** eklemek için Ekle düğmesini seçin.

## <a name="designing-and-coding-the-initiation-form"></a>Başlat formunu tasarlama ve kodlama
 Ardından, buna denetimler ve kod ekleyerek başlat formuna işlevsellik katabilirsiniz.

#### <a name="to-code-the-initiation-form"></a>Başlat formuna kod oluşturmak için

1. Başlat formu (ExpenseReportInitForm.aspx) içinde öğesini `asp:Content` `ID="Main"` bulun.

2. Bu içerik öğesinde ilk satırın hemen ardından, ilişkilendirme formunda girilen gider onay sınırını (*AutoApproveLimit*) ve gider toplamını *(ExpenseTotal)* istenecek başka bir etiket ve metin kutusu görüntüleyen bir etiket ve metin kutusu oluşturmak için aşağıdaki kodu ekleyin:

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Bağımlı dosyalarını görüntülemek için Çözüm Gezgini **ExpenseReportInitForm.aspx** dosyasını genişletin. 

4. ExpenseReportInitForm.aspx dosyasının kısayol menüsünü açın ve Kodu **Görüntüle'yi seçin.**

5. yöntemini `Page_Load` aşağıdaki örnekle değiştirin:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. yöntemini `GetInitiationData` aşağıdaki örnekle değiştirin:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>İş akışını kesin olarak seçin
 Ardından iş akışını özelleştirin. Daha sonra iki formu iş akışıyla ilişkilendirilecek.

#### <a name="to-customize-the-workflow"></a>İş akışını özelleştirmek için

1. projede Workflow1'i açarak iş akışı tasarımcısında iş akışını görüntüler.

2. Araç Kutusunda **İş Akışı** **v3.0 Windows** genişletin ve **IfElse etkinliğini** bulun.

3. Aşağıdaki adımlardan birini gerçekleştirerek bu etkinliği iş akışına ekleyin:

    - **IfElse** etkinliğinin kısayol menüsünü açın, Kopyala'yı **seçin,** iş akışı tasarımcısında **onWorkflowActivated1** etkinliğinin altındaki satırın kısayol menüsünü açın ve yapıştır'ı **seçin.**

    - **IfElse etkinliğini** Araç **Kutusundan sürükleyin** ve iş akışı tasarımcısında **onWorkflowActiviated1 etkinliğinin** altındaki satıra bağlama.

4. Araç Kutusunda İş Akışı SharePoint **genişletin** ve **CreateTask etkinliğini** bulun.

5. Aşağıdaki adımlardan birini gerçekleştirerek bu etkinliği iş akışına ekleyin:

    - **CreateTask** etkinliğinin kısayol menüsünü açın, Kopyala'yı **seçin,** iş  akışı tasarımcısında **IfElseActivity1** içindeki iki Etkinliği Buraya Bırak alanlarından biri için kısayol menüsünü açın ve yapıştır'ı **seçin.**

    - **CreateTask etkinliğini** Araç  Kutusundan  **IfElseActivity1** içindeki iki Bırakma EtkinliğiNden biri üzerine sürükleyin.

6. Özellikler **penceresinde** **CorrelationToken** özelliği için *taskToken* özellik değerini girin.

7. Yanındaki artı işareti (![TreeView](../sharepoint/media/plus.gif "TreeView artı")artı ) seçerek **CorrelationToken** özelliğini genişletin.

8. **OwnerActivityName** alt özelliği üzerinde açılan oku seçin ve *Workflow1 değerini* ayarlayın.

9. **TaskId özelliğini** seçin ve ardından Bağlama Özelliği iletişim kutusunu ![görüntülemek için üç](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")nokta ( ASP.NET Mobil Tasarımcı üç nokta ) **düğmesini** seçin.

10. Yeni **üyeye bağla sekmesini** seçin, Alan **Oluştur seçeneği** düğmesini ve ardından Tamam **düğmesini** seçin.

11. **TaskProperties özelliğini** seçin ve ardından Bağlama Özelliği iletişim kutusunu ![görüntülemek için üç](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı üç nokta")nokta ( ASP.NET Mobil Tasarımcı üç nokta ) düğmesini seçin. 

12. Yeni **üyeye bağla sekmesini** seçin, Alan **Oluştur seçeneği** düğmesini ve ardından Tamam **düğmesini** seçin.

13. Araç **Kutusunda,** İş Akışı SharePoint **genişletin** ve **LogToHistoryListActivity etkinliğini** bulun.

14. Aşağıdaki adımlardan birini gerçekleştirerek bu etkinliği iş akışına ekleyin:

    - **LogToHistoryListActivity** etkinliğinin kısayol menüsünü açın, Kopyala'yı **seçin,**  iş akışı tasarımcısında **IfElseActivity1** içindeki Diğer Etkinlikler Buraya Bırak alanına yönelik kısayol menüsünü açın ve yapıştır'ı **seçin.**

    - **LogToHistoryListActivity etkinliğini** **Araç** Kutusundan sürükleyin ve **IfElseActivity1** içindeki diğer Etkinlikleri Buraya Bırak alanına bırakın. 

## <a name="add-code-to-the-workflow"></a>İş akışına kod ekleme
 Ardından, iş akışına işlev sağlamak için kod ekleyin.

#### <a name="to-add-code-to-the-workflow"></a>İş akışına kod eklemek için

1. İş akışı tasarımcısında **createTask1 etkinliğinin** kısayol menüsünü açın ve ardından Kodu Görüntüle'yi **seçin.**

2. Aşağıdaki yöntemi ekleyin:

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > Kodda yerine bir görev oluşturulacak olan etki alanı ve kullanıcı adını `somedomain\\someuser` yazın; örneğin, " `Office\\JoeSch` ". Test etmek için, geliştirmekte olduğunu hesabı kullanmak en kolay yöntemdir.

3. yönteminin `MethodInvoking` altına aşağıdaki örneği ekleyin:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. İş akışı tasarımcısında **ifElseBranchActivity1 etkinliğini** seçin.

5. Özellikler **penceresinde** Koşul özelliğinin aşağı açılan okunu **seçin** ve ardından Kod Koşulu *değerini* ayarlayın.

6. Yanındaki **artı işaretini** (![TreeView artı](../sharepoint/media/plus.gif "TreeView artı")) seçerek Condition özelliğini genişletin ve değerini *checkApprovalNeeded olarak ayarlayın.*

7. İş akışı tasarımcısında **logToHistoryListActivity1** etkinliğinin kısayol menüsünü açın  ve ardından olay için boş bir yöntem oluşturmak için İşleyiciLer Oluştur'a `MethodInvoking` tıklayın.

8. Kodu `MethodInvoking` aşağıdakiyle değiştirin:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Programda **hata ayıklamak** için F5 anahtarını seçin.

     Bu, uygulamayı derler, paketler, dağıtır, özelliklerini etkinleştirir, uygulama havuzunu geri dönüştürer ve ardından [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] **tarayıcıyı Site Url'si** özelliğinde belirtilen konumda başlatır.

## <a name="associating-the-workflow-to-the-documents-list"></a>İş akışını belgeler listesiyle ekleme
 Ardından, iş akışını SharePoint sitenin **SharedDocuments** listesiyle birleştirerek iş akışı ilişkilendirme formunu görüntüler.

#### <a name="to-associate-the-workflow"></a>İş akışını ilişkilendirmek için

1. QuickLaunch **çubuğunda** Paylaşılan Belgeler bağlantısını seçin.

2. Kitaplık **Araçları sekmesinde** Kitaplık **bağlantısını ve** ardından Kitaplık Kitaplığı şerit **Ayarlar** seçin.

3. İzinler **ve Yönetim bölümünde** İş Akışı Ayarlar bağlantısını ve  ardından İş Akışları sayfasındaki İş akışı ekle **bağlantısını** seçin. 

4. İş akışı ayarları sayfasının üst listesinde **ExpenseReport - Workflow1 şablonunu** seçin.

5. Sonraki alana **ExpenseReportWorkflow girin** ve ardından Sonraki **düğmesini** seçin.

     Bu, iş akışını Paylaşılan Belgeler **listesiyle** ilişkilendirin ve iş akışı ilişkilendirme formunu görüntüler.

6. Otomatik Onay **Sınırı metin** kutusuna **1200 yazın** ve ardından İş Akışını İş Akışını İşLe **düğmesini** seçin.

## <a name="start-the-workflow"></a>İş akışını başlatma
 Ardından, iş akışı başlatma formunu görüntülemek için iş akışını **Paylaşılan** Belgeler listesinde yer alan belgelerden biri ile ilişkilendiril.

#### <a name="to-start-the-workflow"></a>İş akışını başlatmak için

1. Giriş SharePoint Giriş **düğmesini** seçin.

2. Paylaşılan **Belgeler listesini** görüntülemek için QuickLaunch çubuğunda Paylaşılan Belgeler **bağlantısını** seçin.

3. Sayfanın **üst kısmında**  kitaplık araçları sekmesinde belgeler bağlantısını seçin ve ardından şeritteki **Upload** Belge düğmesini seçerek Paylaşılan Belgeler listesine yeni bir **belge** yükleyin.

4. Belge **Upload kutusunda** Gözat düğmesini seçin,  herhangi bir belge dosyasını seçin, Aç **düğmesini** ve ardından Tamam **düğmesini** seçin.

     Bu iletişim kutusunda belgenin ayarlarını değiştirebilirsiniz, ancak Kaydet düğmesini seçerek varsayılan değerlerde **bırakın.**

5. Karşıya yüklenen belgeyi seçin, görüntülenen açılan oku seçin ve ardından İş Akışları **öğesini** seçin.

6. ExpenseReportWorkflow'un yanındaki görüntüyü seçin.

     Bu, iş akışı başlatma formunu görüntüler. (Otomatik Onay Sınırı kutusunda görüntülenen **değerin,** ilişkilendirme formuna girilirken salt okunur olduğunu unutmayın.)

7. Expense **Total metin** kutusuna **1600 yazın** ve ardından İş Akışını Başlat **düğmesini** seçin.

     Paylaşılan Belgeler **listesi yeniden** görüntülenir. yeni başlatan iş akışının öğeye **Tamamlandı** değerini içeren **ExpenseReportWorkflow** adlı yeni bir sütun eklenir.

8. Karşıya yüklenen belgenin yanındaki açılan oku seçin ve ardından iş akışı durum sayfasını **görüntülemek** için İş akışları öğesini seçin. Tamamlandı İş **Akışları** altında **Tamamlandı değerini seçin.** Görev, Görevler bölümünde **listelenir.**

9. Görev ayrıntılarını görüntülemek için görevin başlığını seçin.

10. Geri dön paylaşılan belgeler **listesine** ekleyin ve aynı belgeyi veya farklı bir belgeyi kullanarak iş akışını yeniden başlatın.

11. Giriş sayfasında ilişkilendirme sayfasına girilen miktardan küçük veya buna eşit bir miktar girin (**1200**).

     Bu durum oluştuğunda, görev yerine geçmiş listesinde bir giriş oluşturulur. Girdi, iş akışı **durum sayfasının** İş Akışı Geçmişi bölümünde görüntülenir. Geçmiş olayı sonuç **sütunundaki** iletiyi not alır. Olayda girilen ve `logToHistoryListActivity1.MethodInvoking` otomatik olarak onaylanan miktarı içeren metni içerir.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan iş akışı şablonları oluşturma hakkında daha fazla bilgi edinmek için:

- İş akışlarını kullanma hakkında daha SharePoint için [bkz.](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14))Windows SharePoint Services.

## <a name="see-also"></a>Ayrıca bkz.
- [İş SharePoint çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Adım adım kılavuz: İş akışına uygulama sayfası ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
