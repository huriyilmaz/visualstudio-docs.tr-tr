---
title: İş & çözümü SharePoint hata ayıklaması oluşturma
description: Bu kılavuzda, bir iş akışı çözümü SharePoint ve hata ayıklaması oluşturun. Temel bir sıralı iş akışı şablonu oluşturun. İş akışı etkinlikleri oluşturma ve olayları işleme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e96987734a3414f0e55f75fb221124de79573acd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115492"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Adım adım kılavuz: İş akışı çözümü SharePoint oluşturma ve hata ayıklama
  Bu kılavuzda, temel bir sıralı iş akışı şablonunun nasıl oluşturularak ilgili bilgiler ve bilgiler yer almaktadır. İş akışı, bir belgenin gözden geçirip gözden geçiril olmadığını belirlemek için paylaşılan belge kitaplığının özelliğini denetler. Belge gözden geçirildi ise iş akışı tamamlar.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- içinde bir SharePoint listesi tanımı sıralı iş akışı projesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] oluşturma.

- İş akışı etkinlikleri oluşturma.

- İş akışı etkinlik olaylarını işleme.

> [!NOTE]
> Bu kılavuz sıralı bir iş akışı projesi kullanıyor olsa da, işlem bir durum makinesi iş akışı projesi için aynıdır.
>
> Ayrıca, bilgisayarınız aşağıdaki yönergelerde bazı kullanıcı arabirimi öğeleri için Visual Studio adları veya konumları gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows ve SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Paylaşılan belgeler kitaplığına SharePoint ekleme
 Paylaşılan Belgeler kitaplığında belgelerin gözden geçirme **durumunu** izlemek için, SharePoint sitesinde paylaşılan belgeler için üç yeni `Status` özellik `Assignee` oluşturuz: , ve `Review Comments` . Bu özellikleri Paylaşılan Belgeler **kitaplığında tanımlariz.**

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Paylaşılan belgeler kitaplığına SharePoint eklemek için

1. Web SharePoint /SitePages/Home.aspx gibi http:// bir site \<system name> açın.

2. QuickLaunch çubuğunda **SharedDocuments'ı seçin.**

3. Kitaplık **Araçları** **şeridinde Kitaplık'ı** seçin ve ardından **şeritteki** Sütun Oluştur düğmesini seçerek yeni bir sütun oluşturun.

4. Sütuna **Belge Durumu adını** girin, türünü **Seçim (seçilen menü)** olarak ayarlayın, aşağıdaki üç seçeneği belirtin ve ardından Tamam **düğmesini** seçin:

    - **Gözden Geçirme Gerekli**

    - **Gözden Geçirme Tamamlandı**

    - **İstenen Değişiklikler**

5. İki sütun daha oluşturun ve bunları **Assignee ve** **Review Comments olarak adlandırabilirsiniz.** Assignee sütun türünü tek bir metin satırı olarak, Yorumları Gözden Geçir sütun türünü ise birden çok metin satırı olarak ayarlayın.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Belgelerin teslim almadan düzenlensin mi?
 Belgeleri kontrol etmek zorunda kalmadan düzenleyemezken iş akışı şablonunu test etmek daha kolaydır. Sonraki yordamda, bunu etkinleştirmek için SharePoint siteyi yapılandırabilirsiniz.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Belgeleri denetlemeden düzenlemek için

1. QuickLaunch çubuğunda Paylaşılan Belgeler **bağlantısını** seçin.

2. Kitaplık **Araçları şeridinde,** Kitaplık sekmesini **seçin** ve ardından Kitaplık Ayarlar **düğmesini** seçerek Belge Kitaplığı Ayarlar **görüntüleyin.**

3. Genel **Ayarlar** bölümünde Sürüm **Ayarlar'ı** seçerek **Sürüm Ayarlar** sayfasını görüntüleyebilirsiniz.

4. Belgelerin düzenlenmeden önce kullanıma alınmış olması **gerektir ayarının Hayır olduğunu** **doğrulayın.** Doğru değilse Hayır'ı **ve** ardından Tamam **düğmesini** seçin.

5. Tarayıcıyı kapatın.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Sıralı iş SharePoint projesi oluşturma
 Sıralı iş akışı, son etkinlik sona e kadar sırayla yürütülen bir adım kümesidir. Bu yordamda, Paylaşılan Belgeler listemize uygulanacak sıralı bir iş akışı oluşturuz. İş akışı sihirbazı, iş akışını site tanımı veya liste tanımıyla ilişkilendirmenizi sağlar ve iş akışının ne zaman başlayacağını belirlemenizi sağlar.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Sıralı iş akışı SharePoint oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Yeni dosya iletişim kutusunu görüntülemek **için**  >    >  **menü çubuğunda Dosya** **Project'Project** seçin.

3. **Visual C#** **SharePoint** veya Visual Basic altındaki Visual Basic düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

4. Şablonlar **bölmesinde,** SharePoint **2010** Project seçin.

5. Ad **kutusuna** **MySharePointWorkflow yazın** ve Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

6. Hata **ayıklama için siteyi** ve güvenlik düzeyini  belirtin sayfasında Grup çözümü olarak dağıt  seçeneğini belirleyin ve ardından son düğmesini seçerek güven düzeyini ve varsayılan siteyi kabul edin.

     Bu adım, iş akışı projeleri için kullanılabilen tek seçenek olan grup çözümü olarak çözümün güven düzeyini ayarlar. Daha fazla bilgi için [bkz. Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

7. Bu **Çözüm Gezgini** proje düğümünü seçin ve ardından menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

8. Visual **C# veya** **Visual Basic** altında, SharePoint **düğümünü** genişletin ve ardından **2010 düğümünü** seçin.

9. Şablonlar **bölmesinde Sıralı** İş Akışı (yalnızca Grup **Çözümü)** şablonunu ve ardından Ekle **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir.

10. Hata ayıklama **için iş akışı adını belirtin sayfasında** varsayılan adı kabul edin (**MySharePointWorkflow - Workflow1**). Varsayılan iş akışı şablon türü değerini (İş Akışını **Listele) tutun** ve ardından Sonraki **düğmesini** seçin.

11. Hata **ayıklama oturumunda Visual Studio** otomatik olarak ilişkilendirmek mi istediğiniz? sayfasında,  tüm varsayılan ayarları kabul etmek için Sonraki düğmesini seçin.

     Bu adım, iş akışını paylaşılan belgeler kitaplığıyla otomatik olarak ilişkilendirmektedir.

12. İş **akışınızı başlatma** koşulları belirtin sayfasında, iş akışının nasıl başlamalarını **istiyorsunuz?** bölümünde varsayılan seçenekleri seçili bırakın ve Son **düğmesini** seçin.

     Bu sayfa, iş akışınız ne zaman başlar? Varsayılan olarak, iş akışı bir kullanıcı iş akışında el ile SharePoint veya iş akışının ilişkili olduğu bir öğe oluşturulduğunda başlar.

## <a name="create-workflow-activities"></a>İş akışı etkinlikleri oluşturma
 İş akışları, gerçekleştirecek eylemleri *temsil eden* bir veya daha fazla etkinlik içerir. bir iş akışına yönelik etkinlikleri düzenlemek için iş akışı tasarımcısını kullanın. Bu yordamda iş akışına iki etkinlik ekleyeğiz: HandleExternalEventActivity ve OnWorkFlowItemChanged. Bu etkinlikler, Paylaşılan Belgeler listesinde belgelerin gözden **geçirme durumunu** takip ediyor

#### <a name="to-create-workflow-activities"></a>İş akışı etkinlikleri oluşturmak için

1. İş akışı, iş akışı tasarımcısında görüntüleniyor olması gerekir. Açılmazsa, **workflow1.cs** veya **Workflow1.vb'yi** **Çözüm Gezgini.**

2. Tasarımcıda **OnWorkflowActivated1 etkinliğini** seçin.

3. Özellikler **penceresinde** **Invoked** özelliğinin yanına **onWorkflowActivated** girin ve Enter tuşuna basın.

     Kod Düzenleyicisi açılır ve Workflow1 kod dosyasına onWorkflowActivated adlı bir olay işleyici yöntemi eklenir.

4. İş akışı tasarımcısına geri dönüp araç kutusunu açın ve Windows **Workflow v3.0 düğümünü** genişletin.

5. Araç **Windows İş Akışı v3.0** düğümünde, aşağıdaki adım kümelerinden birini gerçekleştirin:

    1. While etkinliğinin kısayol **menüsünü açın** ve Kopyala'yı **seçin.** İş akışı tasarımcısında **onWorkflowActivated1** etkinliğinin altındaki satırın kısayol menüsünü açın ve Yapıştır'ı **seçin.**

    2. Araç **Kutusundan While** etkinliğini **iş** akışı tasarımcısına sürükleyin ve etkinliği **onWorkflowActivated1** etkinliğinin altındaki satıra bağlama.

6. **WhileActivity1 etkinliğini** seçin.

7. Özellikler penceresinde **Koşul'i** **Kod Koşulu** olarak ayarlayın.

8. Koşul **özelliğini** genişletin, alt Koşul özelliğinin yanına **isWorkflowPending** **girin** ve Enter tuşuna basın.

     Kod Düzenleyicisi açılır ve Workflow1 kod dosyasına isWorkflowPending adlı bir yöntem eklenir.

9. İş akışı tasarımcısına geri dönüp araç kutusunu açın ve İş Akışı SharePoint **genişletin.**

10. Araç **SharePoint İş** Akışı **düğümünde** aşağıdaki adım kümelerinden birini gerçekleştirin:

    - **OnWorkflowItemChanged etkinliğinin** kısayol menüsünü açın ve Kopyala'yı **seçin.** İş akışı tasarımcısında **whileActivity1** etkinliğinin içindeki satırın kısayol menüsünü açın ve Yapıştır'ı **seçin.**

    - Araç **Kutusundan OnWorkflowItemChanged** etkinliğini iş akışı tasarımcısına sürükleyin ve etkinliği **whileActivity1** etkinliğinin içindeki satıra bağlama. 

11. **onWorkflowItemChanged1 etkinliğini** seçin.

12. Özellikler **penceresinde,** özellikleri aşağıdaki tabloda gösterildiği gibi ayarlayın.

    |Özellik|Değer|
    |--------------|-----------|
    |**Correlationtoken**|**workflowToken**|
    |**Çağrılan**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Etkinlik olaylarını işleme
 Son olarak, her etkinlikten belgenin durumunu kontrol edin. Belge gözden geçirildi ise iş akışı tamam demektir.

#### <a name="to-handle-activity-events"></a>Etkinlik olaylarını işlemek için

1. *Workflow1.cs veya* *Workflow1.vb* içinde sınıfının en üstüne aşağıdaki alanı `Workflow1` ekleyin. Bu alan, iş akışının tamam olup olmadığını belirlemek için bir etkinlikte kullanılır.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Sınıfına aşağıdaki yöntemi `Workflow1` ekleyin. Bu yöntem, belgenin gözden `Document Status` geçirip gözden geçiril olmadığını belirlemek için Belgeler listesinin özelliğinin değerini denetler. özelliği `Document Status` olarak ayarlanırsa yöntemi, iş akışının bitmaya hazır olduğunu `Review Complete` belirtmek için alanı false `checkStatus` olarak `workflowPending` ayarlar. 

    ```vb
    Private Sub checkStatus()
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then
            workflowPending = False
        End If
    End Sub
    ```

    ```csharp
    private void checkStatus()
    {
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")
        workflowPending = false;
    }
    ```

3. yöntemini çağıran ve `onWorkflowActivated` `onWorkflowItemChanged` yöntemlerine aşağıdaki kodu `checkStatus` ekleyin. İş akışı başlatıldığında yöntemi, `onWorkflowActivated` belgenin zaten `checkStatus` gözden geçirip gözden geçiril olmadığını belirlemek için yöntemini çağırmış olur. Gözden geçiriLmse, iş akışı devam eder. Belge kaydedilirken yöntemi, `onWorkflowItemChanged` belgenin gözden `checkStatus` geçirip gözden geçiril olmadığını belirlemek için yöntemini yeniden arar. alanı `workflowPending` true olarak ayarlanmış **olsa da** iş akışı çalıştırmaya devam eder.

    ```vb
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub

    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub
    ```

    ```csharp
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }

    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }
    ```

4. Özelliğinin durumunu kontrol `isWorkflowPending` etmek için yöntemine aşağıdaki kodu `workflowPending` ekleyin. Belge her kaydedilebilirken **WhileActivity1** etkinliği yöntemini `isWorkflowPending` çağırmaktadır. Bu yöntem, WhileActivity1 etkinliğinin devam edip edip edeceğini veya bitip bit edeceğini <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> <xref:System.Workflow.Activities.ConditionalEventArgs> **belirlemek** için nesnesinin özelliğini inceler. özelliği true olarak **ayarlanırsa** etkinlik devam eder. Aksi takdirde etkinlik biter ve iş akışı biter.

    ```vb
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)
        e.Result = workflowPending
    End Sub
    ```

    ```csharp
    private void isWorkflowPending(object sender, ConditionalEventArgs e)
    {
        e.Result = workflowPending;
    }
    ```

5. Projeyi kaydedin.

## <a name="test-the-sharepoint-workflow-template"></a>İş akışı SharePoint test etmek
 Hata ayıklayıcıyı başlatarak iş akışı şablonunu SharePoint sunucusuna dağıtır ve iş akışını Paylaşılan Belgeler [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **listesiyle** ilişkilendirin. İş akışını test etmek için Paylaşılan Belgeler listesinde bir belgeden iş akışının **bir örneğini** başlatabilirsiniz.

#### <a name="to-test-the-sharepoint-workflow-template"></a>İş akışı SharePoint test etmek için

1. *Workflow1.cs veya* *Workflow1.vb içinde* **onWorkflowActivated** yönteminin yanında bir kesme noktası ayarlayın.

2. Çözümü **derlemek ve** çalıştırmak için F5 anahtarını seçin.

     SharePoint sitesi görüntülenir.

3. SharePoint'daki gezinti bölmesinde Paylaşılan Belgeler **bağlantısını** seçin.

4. Paylaşılan **Belgeler sayfasında,** Kitaplık **Araçları** sekmesinde belgeler bağlantısını **seçin** ve sonra belgeyi Upload **seçin.**

5. Belge **Upload kutusunda** Gözat düğmesini seçin, herhangi bir belge dosyasını seçin, Aç **düğmesini** ve ardından Tamam **düğmesini** seçin. 

     Bu, seçilen belgeyi Paylaşılan Belgeler **listesine yükler** ve iş akışını başlatır.

6. içinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcının yönteminin yanındaki kesme noktası içinde durarak olduğunu `onWorkflowActivated` doğrulayın.

7. Yürütmeye **devam etmek için F5** anahtarını seçin.

8. Belge ayarlarını burada değiştirebilirsiniz, ancak Kaydet düğmesini seçerek şimdilik varsayılan değerde **bırakın.**

     Bu, sizi varsayılan **Web sitesi** için paylaşılan SharePoint döndürür.

9. Paylaşılan **Belgeler sayfasında,** **MySharePointWorkflow - Workflow1** sütunlarının altındaki değerin Devam Ediyor olarak ayar **olduğunu doğrulayın.** Bu, iş akışının devam ediyor olduğunu ve belgenin gözden geçirmeyi beklediğini gösterir.

10. Paylaşılan **Belgeler sayfasında** belgeyi seçin, görüntülenen oku seçin ve ardından Özellikleri Düzenle **menü** öğesini seçin.

11. Belge **Durumu olarak** **Tamamla'nın Gözden** Geçir'i ayarlayın ve kaydet **düğmesini** seçin.

     Bu, sizi varsayılan **Web sitesi** için paylaşılan SharePoint döndürür.

12. Paylaşılan **Belgeler sayfasında,** Belge Durumu sütununu altındaki değerin Tamamla'nın Gözden Geçir olarak ayar **olduğunu doğrulayın.**  Paylaşılan Belgeler **sayfasını yenileyin** ve **MySharePointWorkflow - Workflow1** sütunlarının altındaki değerin Tamamlandı olarak ayarlandıktan **emin olun.** Bu, iş akışının tamam olduğunu ve belgenin incelenmiş olduğunu gösterir.

## <a name="next-steps"></a>Sonraki adımlar
 Bu konulardan iş akışı şablonları oluşturma hakkında daha fazla bilgi edinmek için:

- İş akışı etkinlikleri hakkında SharePoint fazla bilgi edinmek için bkz. [SharePoint Foundation için İş Akışı Etkinlikleri.](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))

- Workflow Foundation etkinlikleri hakkında daha Windows için bkz. [System.Workflow.Activities Ad Alanı.](/dotnet/api/system.windows.media.color)

## <a name="see-also"></a>Ayrıca bkz.
- [İş SharePoint çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint proje ve proje öğesi şablonlarını kullanma](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Çözüm oluşturma ve SharePoint ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
