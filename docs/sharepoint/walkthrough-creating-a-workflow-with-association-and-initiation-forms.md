---
title: İlişkilendirme ve başlatma formları ile iş akışı oluşturma
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7946e48502ea4fd8e9e9382a20de3c8ce25987b3
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984689"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>İzlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma
  Bu izlenecek yol, ilişkilendirme ve başlatma formlarının kullanımını içeren temel sıralı bir iş akışının nasıl oluşturulacağını gösterir. Bunlar, SharePoint Yöneticisi (ilişkilendirme formu) tarafından ilk kez ilişkilendirildiğinde ve iş akışı Kullanıcı tarafından başlatıldığında (başlatma formu) parametrelerin bir iş akışına eklenmesini sağlayan ASPX formlarıdır.

 Bu izlenecek yol, kullanıcının aşağıdaki gereksinimlere sahip olan gider raporları için onay iş akışı oluşturmak istediği bir senaryoyu özetler:

- İş akışı bir listeyle ilişkilendirildiğinde, yöneticiye, harcama raporları için dolar sınırı girdikleri bir ilişkilendirme formu istenir.

- Çalışanlar, harcama raporlarını paylaşılan belgeler listesine yükler, iş akışını başlatır ve sonra iş akışı başlatma formunda gider toplamı ' nu girer.

- Bir çalışan gider raporu toplamı, yöneticinin önceden tanımlı limitini aşarsa, çalışan yöneticisinin gider raporunu onaylaması için bir görev oluşturulur. Ancak, bir çalışanın gider raporu toplamı, gider limitinden küçükse veya buna eşitse, iş akışının geçmiş listesine bir otomatik onaylı ileti yazılır.

  Bu izlenecek yol aşağıdaki görevleri gösterir:

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]' de bir SharePoint liste tanımı sıralı iş akışı projesi oluşturuluyor.

- İş akışı zamanlaması oluşturuluyor.

- İş akışı etkinlik olaylarını işleme.

- İş akışı ilişkilendirmesi ve başlatma formları oluşturuluyor.

- İş akışını ilişkilendirme.

- İş akışını el ile başlatma.

> [!NOTE]
> Bu kılavuzda sıralı bir iş akışı projesi kullanılıyorsa, işlem durum makinesi iş akışlarıyla aynı olur.
>
> Ayrıca bilgisayarınız, aşağıdaki yönergelerde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sürümü ve kullandığınız ayarlar bu öğeleri tespit. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint 'in desteklenen sürümleri.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı iş akışı projesi oluşturma
 İlk olarak, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]içinde sıralı bir iş akışı projesi oluşturun. Sıralı bir iş akışı, son etkinlik bitene kadar sırayla yürütülen bir dizi adımdan oluşur. Bu yordamda, SharePoint 'te paylaşılan belgeler listesi için geçerli olan sıralı bir iş akışı oluşturacaksınız. İş akışının Sihirbazı, iş akışını siteyle veya liste tanımıyla ilişkilendirmenize olanak tanır ve iş akışının ne zaman başlatılacağını belirlemenizi sağlar.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı iş akışı projesi oluşturmak için

1. **Yeni proje** iletişim kutusunu göstermek için menü çubuğunda **dosya**  > **Yeni**  > **Proje** ' yi seçin.

2. **Visual C#**  veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **Şablonlar** bölmesinde, **SharePoint 2010 proje** projesi şablonunu seçin.

4. **Ad** kutusuna **ExpenseReport** girin ve sonra **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından güven düzeyini ve varsayılan siteyi kabul etmek için **son** düğmesini seçin.

     Bu adım Ayrıca, iş akışı projeleri için kullanılabilir tek seçenek olan çözüm için güven düzeyini Grup çözümü olarak ayarlar.

6. **Çözüm Gezgini**, proje düğümünü seçin.

7. Menü çubuğunda, **proje**  > **Yeni öğe Ekle**' yi seçin.

8. **Görsel C#**  veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

9. **Şablonlar** bölmesinde, **sıralı iş akışı (yalnızca Grup çözümü)** şablonunu seçin ve ardından **Ekle** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir.

10. **Hata ayıklama için iş akışı adını belirtin** sayfasında, varsayılan adı (**ExpenseReport-Workflow1**) kabul edin. Varsayılan iş akışı şablonu tür değerini tut (**liste Iş akışı)** . **İleri** düğmesini seçin.

11. **Visual Studio 'nun bir hata ayıklama oturumunda iş akışını otomatik olarak ilişkilendirmesini ister misiniz?** sayfasında, iş akışı şablonunuzu denetlediyseniz otomatik olarak ilişkilendiren kutuyu temizleyin.

     Bu adım, iş akışını daha sonra ilişki formunu görüntüleyen paylaşılan belgeler listesiyle el ile ilişkilendirmenize olanak tanır.

12. **Son** düğmesini seçin.

## <a name="add-an-association-form-to-the-workflow"></a>İş akışına ilişkilendirme formu ekleme
 Sonra, oluşturun. SharePoint Yöneticisi ilk olarak iş akışını bir harcama raporu belgesiyle ilişkilendirdiğinde görüntülenen ASPX ilişkilendirme formu.

#### <a name="to-add-an-association-form-to-the-workflow"></a>İş akışına bir ilişkilendirme formu eklemek için

1. **Çözüm Gezgini**içinde **Workflow1** düğümünü seçin.

2. **Yeni öğe** Ekle iletişim kutusunu göstermek için menü çubuğunda **Proje** > **Yeni öğe Ekle** ' yi seçin.

3. İletişim kutusu ağacı görünümünde, **görsel C#**  veya **Visual Basic** (Proje dilinize bağlı olarak) öğesini genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. Şablon listesinde **Iş akışı Ilişkilendirmesi form** şablonunu seçin.

5. **Ad** metin kutusuna **ExpenseReportAssocForm. aspx**girin.

6. Formu projeye eklemek için **Ekle** düğmesini seçin.

## <a name="designing-and-coding-the-association-form"></a>İlişkilendirme formunu tasarlama ve kodlama
 Bu yordamda, bu işleve denetimler ve kod ekleyerek, işlevselliği ilişkilendirme formuna tanıtmaktadır.

#### <a name="to-design-and-code-the-association-form"></a>İlişkilendirme formunu tasarlamak ve kodlayın

1. İlişkilendirme formunda (ExpenseReportAssocForm. aspx), `ID="Main"`olan `asp:Content` öğesini bulun.

2. Bu içerik öğesinin ilk satırından hemen sonra, gider onay limiti için istemde bulunan bir etiket ve metin kutusu oluşturmak için aşağıdaki kodu ekleyin (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Bağımlı dosyalarını göstermek için **Çözüm Gezgini** içindeki **ExpenseReportAssocForm. aspx** dosyasını genişletin.

    > [!NOTE]
    > Projeniz [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]ise, bu adımı gerçekleştirmek için **tüm dosyaları görüntüle** düğmesini seçmeniz gerekir.

4. ExpenseReportAssocForm. aspx dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

5. `GetAssociationData` yöntemini ile değiştirin:

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

1. **Çözüm Gezgini**içinde **Workflow1** düğümünü seçin.

2. Menü çubuğunda **proje** > **Yeni öğe Ekle** ' yi seçerek **Yeni öğe Ekle** iletişim kutusunu görüntüleyin.

3. İletişim kutusu ağacı görünümünde, **görsel C#**  veya **Visual Basic** (Proje dilinize bağlı olarak) öğesini genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. Şablon listesinde, **Iş akışı başlatma formu** şablonunu seçin.

5. **Ad** metin kutusuna **ExpenseReportInitForm. aspx**girin.

6. Formu projeye eklemek için **Ekle** düğmesini seçin.

## <a name="designing-and-coding-the-initiation-form"></a>Başlatma formunu tasarlama ve kodlama
 Daha sonra, denetim ve kod ekleyerek başlatma formunu işlevselliği tanıtın.

#### <a name="to-code-the-initiation-form"></a>Başlatma formunu kodlayın

1. Başlatma formunda (ExpenseReportInitForm. aspx), `ID="Main"`içeren `asp:Content` öğesini bulun.

2. Bu içerik öğesindeki ilk satırdan sonra doğrudan bir etiket ve metin kutusu oluşturmak için aşağıdaki kodu ekleyin. ilişki formuna girilen gider onay limiti (*AutoApproveLimit*) ve Toplam harcama (*ExpenseTotal*):

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

5. `Page_Load` yöntemini aşağıdaki örnekle değiştirin:

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

6. `GetInitiationData` yöntemini aşağıdaki örnekle değiştirin:

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

2. **Araç kutusunda** **Windows Workflow v 3.0** düğümünü genişletin ve **IfElse** etkinliğini bulun.

3. Aşağıdaki adımlardan birini gerçekleştirerek iş akışına bu etkinliği ekleyin:

    - **IfElse** etkinliği için kısayol menüsünü açın, **Kopyala**' yı seçin, iş akışı tasarımcısında **onWorkflowActivated1** etkinliğinin altındaki satır Için kısayol menüsünü açın ve ardından **Yapıştır**' ı seçin.

    - **Araç kutusundan** **ifelse** etkinliğini sürükleyin ve iş akışı tasarımcısında **onWorkflowActiviated1** etkinliğinin altındaki satıra bağlayın.

4. Araç kutusunda **SharePoint Iş akışı** düğümünü genişletin ve **CreateTask** etkinliğini bulun.

5. Aşağıdaki adımlardan birini gerçekleştirerek iş akışına bu etkinliği ekleyin:

    - **CreateTask** etkinliğinin kısayol menüsünü açın, **Kopyala**' yı seçin, iş akışı tasarımcısında **IfElseActivity1** içinde yer alan iki **bırakma etkinliği** alanının kısayol menüsünü açın ve ardından **Yapıştır**' ı seçin.

    - **CreateTask** etkinliğini **araç kutusundan** **IfElseActivity1**içinde yer alan iki **bırakma etkinliği** alanından birine sürükleyin.

6. **Özellikler** penceresinde, **CorrelationToken** özelliği için *taskToken* özellik değerini girin.

7. Yanındaki artı işaretini (![TreeView Plus](../sharepoint/media/plus.gif "TreeView Plus")) seçerek **CorrelationToken** özelliğini genişletin.

8. **OwnerActivityName** Sub özelliğindeki açılan oku seçin ve *Workflow1* değerini ayarlayın.

9. **TaskID** özelliğini seçin ve sonra **bağlama özelliği** iletişim kutusunu göstermek için üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

10. **Yeni bir üyeye bağla** sekmesini seçin, **alan oluştur** seçenek düğmesini seçin ve sonra **Tamam** düğmesini seçin.

11. **TaskProperties** özelliğini seçin ve sonra **bağlama özelliği** iletişim kutusunu göstermek için üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) düğmesini seçin.

12. **Yeni bir üyeye bağla** sekmesini seçin, **alan oluştur** seçenek düğmesini seçin ve sonra **Tamam** düğmesini seçin.

13. **Araç kutusunda** **SharePoint iş akışı** düğümünü genişletin ve **LogToHistoryListActivity** etkinliğini bulun.

14. Aşağıdaki adımlardan birini gerçekleştirerek iş akışına bu etkinliği ekleyin:

    - **LogToHistoryListActivity** etkinliğinin kısayol menüsünü açın, **Kopyala**' yı seçin, iş akışı tasarımcısında **IfElseActivity1** içindeki diğer **bırakma etkinlikleri** için kısayol menüsünü açın ve ardından Yapıştır ' ı seçin..

    - **LogToHistoryListActivity** etkinliğini **araç kutusundan**sürükleyin ve **IfElseActivity1**içindeki diğer **bırakma etkinlikleri** alanına bırakın.

## <a name="add-code-to-the-workflow"></a>İş akışına kod ekleme
 Sonra, BT işlevselliği sağlamak için iş akışına kod ekleyin.

#### <a name="to-add-code-to-the-workflow"></a>İş akışına kod eklemek için

1. İş akışı tasarımcısında **createTask1** etkinliğinin kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

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
    > Kodda, `somedomain\\someuser`, "`Office\\JoeSch`" gibi bir görevin oluşturulacağı bir etki alanı ve Kullanıcı adıyla değiştirin. Test etmek için, geliştirmekte olduğunuz hesabın kullanımı en kolay yoldur.

3. `MethodInvoking` yönteminin altında aşağıdaki örneği ekleyin:

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

4. İş akışı tasarımcısında **ifElseBranchActivity1** etkinliğini seçin.

5. **Özellikler** penceresinde **koşul** özelliğinin aşağı açılan okunu seçin ve ardından *Kod koşulu* değerini ayarlayın.

6. **Koşul** özelliğini genişleterek yanındaki artı Işaretini (![TreeView Plus](../sharepoint/media/plus.gif "TreeView Plus")) seçip değerini *checkApprovalNeeded*olarak ayarlayın.

7. İş akışı tasarımcısında, **logToHistoryListActivity1** etkinliğinin kısayol menüsünü açın ve ardından `MethodInvoking` olayı için boş bir yöntem oluşturmak üzere **işleyicileri oluştur** ' u seçin.

8. `MethodInvoking` kodunu aşağıdaki kodla değiştirin:

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

9. Programda hata ayıklamak için **F5** tuşunu seçin.

     Bu, uygulamayı derler, paketler, dağıtır, özelliklerini etkinleştirir, [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] uygulama havuzunu geri dönüştürür ve ardından tarayıcıyı **site URL** özelliğinde belirtilen konumda başlatır.

## <a name="associating-the-workflow-to-the-documents-list"></a>İş akışını belgeler listesiyle ilişkilendirme
 Daha sonra, iş akışını SharePoint sitesindeki **Shareddocuments** listesiyle ilişkilendirerek iş akışı ilişkilendirme formunu görüntüleyin.

#### <a name="to-associate-the-workflow"></a>İş akışını ilişkilendirmek için

1. Hızlı Başlat çubuğunda **paylaşılan belgeler** bağlantısını seçin.

2. **Kitaplık araçları** sekmesinde **kitaplık** bağlantısını seçin ve ardından **kitaplık ayarları** şerit düğmesini seçin.

3. **İzinler ve yönetim** bölümünde, **iş akışı ayarları** bağlantısını seçin ve sonra iş **akışları** sayfasında **iş akışı Ekle** bağlantısını seçin.

4. İş akışı ayarları sayfasındaki üst listede **ExpenseReport-Workflow1** şablonunu seçin.

5. Sonraki alana **ExpenseReportWorkflow** girin ve sonra **İleri** düğmesini seçin.

     Bu, iş akışını **paylaşılan belgeler** listesiyle ilişkilendirir ve iş akışı ilişkilendirme formunu görüntüler.

6. **Otomatik onay sınırı** metin kutusuna **1200** girin ve sonra **iş akışını ilişkilendir** düğmesini seçin.

## <a name="start-the-workflow"></a>İş akışını Başlat
 Sonra, iş akışını **paylaşılan belgeler** listesindeki belgelerden biriyle ilişkilendirin ve iş akışı başlatma formunu görüntüleyin.

#### <a name="to-start-the-workflow"></a>İş akışını başlatmak için

1. SharePoint sayfasında, **giriş** düğmesini seçin.

2. **Paylaşılan belgeler** listesini göstermek Için Hızlı Başlat çubuğundaki **paylaşılan belgeler** bağlantısını seçin.

3. Sayfanın üst kısmındaki **kitaplık araçları** sekmesinde **Belgeler** bağlantısını seçin ve ardından yeni bir belgeyi **paylaşılan belgeler** listesine yüklemek için Şeritteki **belgeyi karşıya yükle** düğmesini seçin.

4. **Belgeyi karşıya yükle** iletişim kutusunda, **Gözden** geçirme düğmesini seçin, herhangi bir belge dosyasını seçin, **Aç** düğmesini seçin ve **Tamam** düğmesini seçin.

     Belgenin ayarlarını bu iletişim kutusunda değiştirebilirsiniz, ancak **Kaydet** düğmesini seçerek bunları varsayılan değerlerde bırakabilirsiniz.

5. Karşıya yüklenen belgeyi seçin, görüntülenen aşağı açılan oku seçin ve sonra **Iş akışları** öğesini seçin.

6. ExpenseReportWorkflow ' nin yanındaki görüntüyü seçin.

     Bu, iş akışı başlatma formunu görüntüler. ( **Otomatik onay limiti** kutusunda görüntülenen değerin, ilişkilendirme formuna girildiği için salt okunurdur.)

7. **Gider toplamı** metin kutusuna **1600**girin ve sonra **iş akışını başlat** düğmesini seçin.

     Bu, **paylaşılan belgeler** listesini yeniden görüntüler. **Tamamlanan** değere sahip **ExpenseReportWorkflow** adlı yeni bir sütun, iş akışının yeni başlatıldığı öğeye eklenir.

8. Karşıya yüklenen belgenin yanındaki açılan oku seçin ve sonra iş akışı durumu sayfasını göstermek için **Iş akışları** öğesini seçin. **Tamamlanan Iş akışları**altında **Tamamlanan** değeri seçin. Görev, **Görevler** bölümünün altında listelenir.

9. Görevin ayrıntılarını göstermek için görevin başlığını seçin.

10. **Shareddocuments** listesine geri dönün ve aynı belgeyi veya farklı bir tane kullanarak iş akışını yeniden başlatın.

11. Başlangıç sayfasında, ilişkilendirme sayfasında (**1200**) girilen miktardan daha küçük veya ona eşit bir miktar girin.

     Bu gerçekleştiğinde, bir görev yerine geçmiş listesindeki bir giriş oluşturulur. Giriş, iş akışı durumu sayfasının **Iş akışı geçmişi** bölümünde görüntülenir. Geçmiş olayının **sonuç** sütunundaki iletiyi aklınızda edin. Otomatik olarak onaylanan miktarı içeren `logToHistoryListActivity1.MethodInvoking` olayına girilen metni içerir.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan iş akışı şablonlarının nasıl oluşturulacağı hakkında daha fazla bilgi edinebilirsiniz:

- SharePoint iş akışları hakkında daha fazla bilgi için bkz. [Windows SharePoint Services 'de Iş akışları](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
