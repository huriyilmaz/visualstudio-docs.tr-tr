---
title: İlişkilendirme ve başlatma formları ile iş akışı oluşturma
description: bu SharePoint izlenecek yol, ilişkilendirme ve başlatma formlarının kullanımını içeren temel bir sıralı iş akışı oluşturun.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148824"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>İzlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma
  Bu izlenecek yol, ilişkilendirme ve başlatma formlarının kullanımını içeren temel sıralı bir iş akışının nasıl oluşturulacağını gösterir. bunlar, SharePoint yöneticisi (ilişkilendirme formu) tarafından ilk kez ilişkilendirildiğinde ve iş akışı kullanıcı tarafından başlatıldığında (başlatma formu) parametrelerin bir iş akışına eklenmesini sağlayan ASPX formlarıdır.

 Bu izlenecek yol, kullanıcının aşağıdaki gereksinimlere sahip olan gider raporları için onay iş akışı oluşturmak istediği bir senaryoyu özetler:

- İş akışı bir listeyle ilişkilendirildiğinde, yöneticiye, harcama raporları için dolar sınırı girdikleri bir ilişkilendirme formu istenir.

- Çalışanlar, harcama raporlarını paylaşılan belgeler listesine yükler, iş akışını başlatır ve sonra iş akışı başlatma formunda gider toplamı ' nu girer.

- Bir çalışan gider raporu toplamı, yöneticinin önceden tanımlı limitini aşarsa, çalışan yöneticisinin gider raporunu onaylaması için bir görev oluşturulur. Ancak, bir çalışanın gider raporu toplamı, gider limitinden küçükse veya buna eşitse, iş akışının geçmiş listesine bir otomatik onaylı ileti yazılır.

  Bu izlenecek yol aşağıdaki görevleri gösterir:

- içinde SharePoint liste tanımı sıralı iş akışı projesi oluşturuluyor [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- İş akışı zamanlaması oluşturuluyor.

- İş akışı etkinlik olaylarını işleme.

- İş akışı ilişkilendirmesi ve başlatma formları oluşturuluyor.

- İş akışını ilişkilendirme.

- İş akışını el ile başlatma.

> [!NOTE]
> Bu kılavuzda sıralı bir iş akışı projesi kullanılıyorsa, işlem durum makinesi iş akışlarıyla aynı olur.
>
> Ayrıca bilgisayarınız, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Aşağıdaki yönergelerde bazı Kullanıcı arabirimi öğeleri için farklı adlar veya konumlar gösterebilir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Sahip olduğunuz sürüm ve kullandığınız ayarlar bu öğeleri tespit. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]Ve SharePoint desteklenen sürümleri.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı iş akışı projesi oluşturma
 İlk olarak, içinde sıralı bir iş akışı projesi oluşturun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sıralı bir iş akışı, son etkinlik bitene kadar sırayla yürütülen bir dizi adımdan oluşur. Bu yordamda, SharePoint içindeki paylaşılan belgeler listesi için geçerli olan sıralı bir iş akışı oluşturacaksınız. İş akışının Sihirbazı, iş akışını siteyle veya liste tanımıyla ilişkilendirmenize olanak tanır ve iş akışının ne zaman başlatılacağını belirlemenizi sağlar.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı bir iş akışı projesi oluşturmak için

1.   >    >  **yeni Project** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Project** öğesini seçin.

2. **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **şablonlar** bölmesinde **SharePoint 2010 Project** proje şablonu ' nu seçin.

4. **Ad** kutusuna **ExpenseReport** girin ve sonra **Tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından güven düzeyini ve varsayılan siteyi kabul etmek için **son** düğmesini seçin.

     Bu adım Ayrıca, iş akışı projeleri için kullanılabilir tek seçenek olan çözüm için güven düzeyini Grup çözümü olarak ayarlar.

6. **Çözüm Gezgini**, proje düğümünü seçin.

7. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

8. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

9. **Şablonlar** bölmesinde, **sıralı iş akışı (yalnızca Grup çözümü)** şablonunu seçin ve ardından **Ekle** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

10. **Hata ayıklama için iş akışı adını belirtin** sayfasında, varsayılan adı (**ExpenseReport-Workflow1**) kabul edin. Varsayılan iş akışı şablonu tür değerini tut (**liste Iş akışı)**. **İleri** düğmesini seçin.

11. **bir hata ayıklama oturumunda iş akışını otomatik olarak ilişkilendirmek Visual Studio ister misiniz?** sayfasında, iş akışı şablonunuzu işaretliyse otomatik olarak ilişkilendiren kutuyu temizleyin.

     Bu adım, iş akışını daha sonra ilişki formunu görüntüleyen paylaşılan belgeler listesiyle el ile ilişkilendirmenize olanak tanır.

12. **Son** düğmesini seçin.

## <a name="add-an-association-form-to-the-workflow"></a>İş akışına ilişkilendirme formu ekleme
 Sonra, oluşturun. SharePoint yöneticisi ilk olarak iş akışını bir harcama raporu belgesiyle ilişkilendirdiğinde görüntülenen ASPX ilişkilendirme formu.

#### <a name="to-add-an-association-form-to-the-workflow"></a>İş akışına bir ilişkilendirme formu eklemek için

1. **Çözüm Gezgini** içinde **Workflow1** düğümünü seçin.

2. menü çubuğunda, yeni   >  **öğe** ekle iletişim kutusunu göstermek için Project **yeni öğe ekle** ' yi seçin.

3. iletişim kutusu ağacı görünümünde, **Visual C#** veya **Visual Basic** (proje dilinize bağlı olarak) öğesini genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. Şablon listesinde **Iş akışı Ilişkilendirmesi form** şablonunu seçin.

5. **Ad** metin kutusuna **ExpenseReportAssocForm. aspx** girin.

6. Formu projeye eklemek için **Ekle** düğmesini seçin.

## <a name="designing-and-coding-the-association-form"></a>İlişkilendirme formunu tasarlama ve kodlama
 Bu yordamda, bu işleve denetimler ve kod ekleyerek, işlevselliği ilişkilendirme formuna tanıtmaktadır.

#### <a name="to-design-and-code-the-association-form"></a>İlişkilendirme formunu tasarlamak ve kodlayın

1. İlişkilendirme formunda (ExpenseReportAssocForm. aspx), `asp:Content` olan öğesini bulun `ID="Main"` .

2. Bu içerik öğesinin ilk satırından hemen sonra, gider onay limiti için istemde bulunan bir etiket ve metin kutusu oluşturmak için aşağıdaki kodu ekleyin (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Bağımlı dosyalarını göstermek için **Çözüm Gezgini** içindeki **ExpenseReportAssocForm. aspx** dosyasını genişletin.

    > [!NOTE]
    > Projeniz ' de ise [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , bu adımı gerçekleştirmek Için **tüm dosyaları görüntüle** düğmesini seçmeniz gerekir.

4. ExpenseReportAssocForm. aspx dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

5. `GetAssociationData`Yöntemini ile değiştirin:

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

## <a name="add-an-initiation-form-to-the-workflow"></a>İş akışına başlatma formu ekleme
 Ardından, kullanıcılar iş akışını harcama raporlarında çalıştırırken görüntülenen başlatma formunu oluşturun.

#### <a name="to-create-an-initiation-form"></a>Başlatma formu oluşturmak için

1. **Çözüm Gezgini** içinde **Workflow1** düğümünü seçin.

2. menü çubuğunda **Project**  >  **yeni öğe ekle** ' yi seçerek **yeni öğe ekle** iletişim kutusunu görüntüleyin.

3. iletişim kutusu ağacı görünümünde, **Visual C#** veya **Visual Basic** (proje dilinize bağlı olarak) öğesini genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. Şablon listesinde, **Iş akışı başlatma formu** şablonunu seçin.

5. **Ad** metin kutusuna **ExpenseReportInitForm. aspx** girin.

6. Formu projeye eklemek için **Ekle** düğmesini seçin.

## <a name="designing-and-coding-the-initiation-form"></a>Başlatma formunu tasarlama ve kodlama
 Daha sonra, denetim ve kod ekleyerek başlatma formunu işlevselliği tanıtın.

#### <a name="to-code-the-initiation-form"></a>Başlatma formunu kodlayın

1. Başlatma formunda (ExpenseReportInitForm. aspx), `asp:Content` içeren öğesini bulun `ID="Main"` .

2. Bu içerik öğesindeki ilk satırdan sonra doğrudan bir etiket ve metin kutusu oluşturmak için aşağıdaki kodu ekleyin. ilişki formuna girilen gider onay limiti (*AutoApproveLimit*) ve diğer bir deyişle, gider toplamı (*ExpenseTotal*) için istemde bulunan başka bir etiket ve metin kutusu oluşturun:

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Bağımlı dosyalarını göstermek için **Çözüm Gezgini** içindeki **ExpenseReportInitForm. aspx** dosyasını genişletin.

4. ExpenseReportInitForm. aspx dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

5. `Page_Load`Yöntemini aşağıdaki örnekle değiştirin:

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

6. `GetInitiationData`Yöntemini aşağıdaki örnekle değiştirin:

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

## <a name="cutomize-the-workflow"></a>İş akışını dök
 Sonra, iş akışını özelleştirin. Daha sonra, iki formu iş akışıyla ilişkilendirirsiniz.

#### <a name="to-customize-the-workflow"></a>İş akışını özelleştirmek için

1. Projede Workflow1 ' i açarak iş akışını iş akışı tasarımcısında görüntüleyin.

2. **araç kutusunda** **Windows Workflow v 3.0** düğümünü genişletin ve **ıfelse** etkinliğini bulun.

3. Aşağıdaki adımlardan birini gerçekleştirerek iş akışına bu etkinliği ekleyin:

    - **IfElse** etkinliği için kısayol menüsünü açın, **Kopyala**' yı seçin, iş akışı tasarımcısında **onWorkflowActivated1** etkinliğinin altındaki satır Için kısayol menüsünü açın ve ardından **Yapıştır**' ı seçin.

    - **Araç kutusundan** **ifelse** etkinliğini sürükleyin ve iş akışı tasarımcısında **onWorkflowActiviated1** etkinliğinin altındaki satıra bağlayın.

4. araç kutusunda **SharePoint iş akışı** düğümünü genişletin ve **createtask** etkinliğini bulun.

5. Aşağıdaki adımlardan birini gerçekleştirerek iş akışına bu etkinliği ekleyin:

    - **CreateTask** etkinliğinin kısayol menüsünü açın, **Kopyala**' yı seçin, iş akışı tasarımcısında **IfElseActivity1** içinde yer alan iki **bırakma etkinliği** alanının kısayol menüsünü açın ve ardından **Yapıştır**' ı seçin.

    - **CreateTask** etkinliğini **araç kutusundan** **IfElseActivity1** içinde yer alan iki **bırakma etkinliği** alanından birine sürükleyin.

6. **Özellikler** penceresinde, **CorrelationToken** özelliği için *taskToken* özellik değerini girin.

7. Yanındaki artı işaretini (![TreeView Plus](../sharepoint/media/plus.gif "TreeView artı")) seçerek **CorrelationToken** özelliğini genişletin.

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
    > Kodda yerine bir görev oluşturulacak olan etki alanı ve kullanıcı adını yazın; `somedomain\\someuser` örneğin, " `Office\\JoeSch` ". Test etmek için, geliştirmekte olduğunu hesabı kullanmak en kolay yöntemdir.

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
 Ardından, iş akışını SharePoint sitenin **SharedDocuments** listesiyle ilişkilendirmek için iş akışı ilişkilendirme formunu görüntüler.

#### <a name="to-associate-the-workflow"></a>İş akışını ilişkilendirmek için

1. QuickLaunch **çubuğunda** Paylaşılan Belgeler bağlantısını seçin.

2. Kitaplık **Araçları sekmesinde** Kitaplık bağlantısını **ve** ardından Kitaplık Kitaplığı şerit **Ayarlar** seçin.

3. İzinler **ve Yönetim bölümünde** İş Akışı Ayarlar bağlantısını ve ardından İş Akışları **sayfasındaki** İş akışı ekle **bağlantısını** seçin. 

4. İş akışı ayarları sayfasının üst listesinde **ExpenseReport - Workflow1 şablonunu** seçin.

5. Sonraki alana **ExpenseReportWorkflow girin** ve ardından Sonraki **düğmesini** seçin.

     Bu, iş akışını Paylaşılan **Belgeler listesiyle** ilişkilendirin ve iş akışı ilişkilendirme formunu görüntüler.

6. Otomatik Onay **Sınırı metin** kutusuna **1200 yazın** ve ardından İş Akışını İş Akışını İşLe **düğmesini** seçin.

## <a name="start-the-workflow"></a>İş akışını başlatma
 Ardından, iş akışı başlatma formunu görüntülemek için iş akışını **Paylaşılan** Belgeler listesinde yer alan belgelerden biri ile ilişkilendirmeniz gerekir.

#### <a name="to-start-the-workflow"></a>İş akışını başlatmak için

1. Giriş SharePoint Giriş **düğmesini** seçin.

2. Paylaşılan **Belgeler listesini** görüntülemek için QuickLaunch çubuğunda Paylaşılan Belgeler **bağlantısını** seçin.

3. Sayfanın **üst kısmında**  kitaplık araçları sekmesinde belgeler bağlantısını seçin ve ardından şeritteki **Upload** belge düğmesini seçerek Paylaşılan Belgeler listesine yeni bir **belge** yükleyin.

4. Belge **Upload kutusunda** Gözat düğmesini seçin,  herhangi bir belge dosyasını seçin, Aç **düğmesini ve** ardından Tamam **düğmesini** seçin.

     Bu iletişim kutusunda belgenin ayarlarını değiştirebilirsiniz, ancak Kaydet düğmesini seçerek varsayılan değerlerde **bırakın.**

5. Karşıya yüklenen belgeyi seçin, görüntülenen açılan oku seçin ve ardından İş Akışları **öğesini** seçin.

6. ExpenseReportWorkflow'un yanındaki görüntüyü seçin.

     Bu, iş akışı başlatma formunu görüntüler. (Otomatik Onay Sınırı kutusunda görüntülenen **değerin,** ilişkilendirme formuna girilirken salt okunur olduğunu unutmayın.)

7. Expense **Total metin** kutusuna **1600 yazın** ve ardından İş Akışını Başlat **düğmesini** seçin.

     Paylaşılan Belgeler **listesi yeniden** görüntülenir. yeni başlatan iş akışının öğeye Tamamlandı değerini **içeren** **ExpenseReportWorkflow** adlı yeni bir sütun eklenir.

8. Karşıya yüklenen belgenin yanındaki açılan oku seçin ve ardından iş akışı durum sayfasını **görüntülemek** için İş akışları öğesini seçin. Tamamlandı İş **Akışları** altında **Tamamlandı değerini seçin.** Görev, Görevler bölümünde **listelenir.**

9. Görev ayrıntılarını görüntülemek için görevin başlığını seçin.

10. Geri dön **paylaşılan belgeler listesine ekleyin** ve aynı belgeyi veya farklı bir belgeyi kullanarak iş akışını yeniden başlatın.

11. Giriş sayfasında ilişkilendirme sayfasında girilen miktardan küçük veya buna eşit bir miktar girin (**1200**).

     Bu durum oluştuğunda, görev yerine geçmiş listesinde bir giriş oluşturulur. Girdi, iş akışı **durum sayfasının** İş Akışı Geçmişi bölümünde görüntülenir. Geçmiş olayı sonuç **sütunundaki** iletiyi not alır. Otomatik olarak onaylanan miktarı `logToHistoryListActivity1.MethodInvoking` içeren olayda girilen metni içerir.

## <a name="next-steps"></a>Sonraki adımlar
 Bu konulardan iş akışı şablonları oluşturma hakkında daha fazla bilgi edinmek için:

- İş akışlarını kullanma hakkında daha SharePoint için [bkz.](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14))Windows SharePoint Services.

## <a name="see-also"></a>Ayrıca bkz.
- [İş SharePoint çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Adım adım kılavuz: İş akışına uygulama sayfası ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
