---
title: SharePoint iş akışı çözümü oluştur & hata ayıkla
description: Bu kılavuzda bir SharePoint iş akışı çözümü oluşturun ve hata ayıklayın. Temel sıralı bir iş akışı şablonu oluşturun. İş akışı etkinlikleri oluşturun ve olayları işleyin.
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
ms.workload:
- office
ms.openlocfilehash: 637d46eaa9ac9306d63befed1c011c278b46af24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952726"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>İzlenecek yol: SharePoint iş akışı çözümü oluşturma ve hatalarını ayıklama
  Bu izlenecek yol, temel sıralı bir iş akışı şablonunun nasıl oluşturulacağını göstermektedir. İş akışı, bir belgenin gözden geçirilip geçirilmediğini anlamak için paylaşılan belge kitaplığının bir özelliğini denetler. Belge incelenip iş akışı tamamlanır.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- İçinde bir SharePoint liste tanımı sıralı iş akışı projesi oluşturuluyor [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- İş akışı etkinlikleri oluşturuluyor.

- İş akışı etkinlik olaylarını işleme.

> [!NOTE]
> Bu kılavuzda sıralı bir iş akışı projesi kullanılıyorsa, işlem durum makinesi iş akışı projesi için de aynıdır.
>
> Ayrıca bilgisayarınız, aşağıdaki yönergelerde yer alarak Visual Studio Kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Microsoft Windows ve SharePoint sürümleri.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint paylaşılan belgeler kitaplığına özellikler ekleme
 **Paylaşılan belgeler** kitaplığındaki belgelerin gözden geçirme durumunu izlemek Için, SharePoint sitemizdeki paylaşılan belgeler için üç yeni özellik oluşturacağız: `Status` , `Assignee` ve `Review Comments` . Bu özellikleri **paylaşılan belgeler** kitaplığında tanımladık.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint paylaşılan belgeler kitaplığına özellikler eklemek için

1. \<system name>Bir Web tarayıcısında http:///SitePages/Home.aspx gibi bir SharePoint sitesi açın.

2. Hızlı Başlat çubuğunda **Shareddocuments**' i seçin.

3. **Kitaplık araçları** şeridinde **kitaplık** ' ı seçin ve ardından Şeritteki **sütun oluştur** düğmesini seçerek yeni bir sütun oluşturun.

4. Sütun **belgesi durumunu** adlandırın, türünü seçenek olarak ayarlayın **(arasından seçim yapmak için menü)**, aşağıdaki üç seçeneği belirtin ve ardından **Tamam** düğmesini seçin:

    - **Gözden geçirme gerekiyor**

    - **İnceleme Tamam**

    - **Değişiklikler Istendi**

5. İki sütun daha oluşturun ve bunları **atanan** şekilde adlandırın ve **açıklamaları gözden geçirin**. Atanan sütun türünü tek satırlık metin olarak ayarlayın ve yorumları gözden geçir sütunu birden çok satırlık metin olarak yazın.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Kullanıma alma gerekmeden belgelerin düzenlenmesini etkinleştir
 Belgeleri kullanıma almak zorunda kalmadan düzenleyebilmeniz için iş akışı şablonunu test etmek daha kolaydır. Bir sonraki yordamda, SharePoint sitesini bunu etkinleştirecek şekilde yapılandırırsınız.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Belgelerin kullanıma almadan düzenlenmesini sağlamak için

1. Hızlı Başlat çubuğunda, **paylaşılan belgeler** bağlantısını seçin.

2. **Kitaplık araçları** şeridinde **kitaplık** sekmesini seçin ve ardından **kitaplık ayarları** düğmesini seçerek **belge kitaplığı ayarları** sayfasını görüntüleyin.

3. **Genel ayarlar** bölümünde **sürüm oluşturma ayarları bağlantısını seçerek** **sürüm oluşturma ayarları** sayfasını görüntüleyin.

4. **Belgelerin düzenlenmeden önce kullanıma alınmasını iste** seçeneğinin **Hayır** olduğunu doğrulayın. Değilse, **Hayır** olarak değiştirin ve **Tamam** düğmesini seçin.

5. Tarayıcıyı kapatın.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı iş akışı projesi oluşturma
 Sıralı bir iş akışı, son etkinlik bitene kadar sırayla yürütülen bir adım kümesidir. Bu yordamda, paylaşılan belgeler listemize uygulanacak sıralı bir iş akışı oluşturacağız. İş akışı Sihirbazı, iş akışını site tanımı veya liste tanımıyla ilişkilendirmenize olanak tanır ve iş akışının ne zaman başlatılacağını belirlemenizi sağlar.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı iş akışı projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2.   >    >  **Yeni proje** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Proje** ' yi seçin.

3. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. **Şablonlar** bölmesinde, **SharePoint 2010 proje** şablonunu seçin.

5. **Ad** kutusuna **MySharePointWorkflow** yazın ve **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir.

6. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından güven düzeyini ve varsayılan siteyi kabul etmek için **son** düğmesini seçin.

     Bu adım, iş akışı projeleri için kullanılabilir tek seçenek olan çözüm için güven düzeyini Grup çözümü olarak ayarlar. Daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda **Proje**  >  **Ekle yeni öğe**' yi seçin.

8. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

9. **Şablonlar** bölmesinde, **sıralı iş akışı (yalnızca Grup çözümü)** şablonunu seçin ve ardından **Ekle** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir.

10. **Hata ayıklama için iş akışı adını belirtin** sayfasında, varsayılan adı (**MySharePointWorkflow-Workflow1**) kabul edin. Varsayılan iş akışı şablonu tür değerini tutun, **Iş akışını listeleyin** ve sonra **İleri** düğmesini seçin.

11. **Visual Studio 'nun bir hata ayıklama oturumunda iş akışını otomatik olarak ilişkilendirilmesini ister misiniz?** sayfasında, tüm varsayılan ayarları kabul etmek için **İleri** düğmesini seçin.

     Bu adım iş akışını paylaşılan belgeler kitaplığıyla otomatik olarak ilişkilendirir.

12. **İş akışınızın başlatılma koşullarını belirtin** sayfasında, **Iş akışının başlamasını nasıl başlatmak istiyorsunuz?** bölümünde varsayılan seçenekleri seçili bırakın ve **son** düğmesini seçin.

     Bu sayfa, iş akışınızın ne zaman başlayacağını belirtmenizi sağlar. Varsayılan olarak, iş akışı, bir kullanıcı SharePoint 'te el ile başlatıldığında veya iş akışının ilişkilendirildiği bir öğe oluşturulduğunda başlatılır.

## <a name="create-workflow-activities"></a>İş akışı etkinlikleri oluşturma
 İş akışları gerçekleştirilecek eylemleri temsil eden bir veya daha fazla *etkinlik* içerir. İş akışı için etkinlikleri düzenlemek üzere iş akışı tasarımcısını kullanın. Bu yordamda, iş akışına iki etkinlik ekleyeceğiz: Handleexternaliventactivity ve Onworkflowwitemchanged. Bu etkinlikler, **paylaşılan belgeler** listesindeki belgelerin gözden geçirme durumunu izler

#### <a name="to-create-workflow-activities"></a>İş akışı etkinlikleri oluşturmak için

1. İş akışı, iş akışı Tasarımcısı 'nda görüntülenmelidir. Değilse, **Çözüm Gezgini** içinde **Workflow1.cs** veya **Workflow1. vb** dosyasını açın.

2. Tasarımcıda **onWorkflowActivated1** etkinliğini seçin.

3. **Özellikler** penceresinde, **çağrılan** özelliğin yanına **onWorkflowActivated** yazın ve ardından Enter tuşunu seçin.

     Kod Düzenleyicisi açılır ve Workflow1 kod dosyasına onWorkflowActivated adlı bir olay işleyicisi yöntemi eklenir.

4. İş akışı tasarımcısına geri dönün, araç kutusunu açın ve ardından **Windows Workflow v 3.0** düğümünü genişletin.

5. **Araç kutusunun** **Windows Workflow v 3.0** düğümünde aşağıdaki adım kümelerinden birini gerçekleştirin:

    1. **While** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **onWorkflowActivated1** etkinliğinin altındaki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    2. **While** etkinliğini **araç kutusundan** iş akışı tasarımcısına sürükleyin ve etkinliği **onWorkflowActivated1** etkinliğinin altındaki satıra bağlayın.

6. **WhileActivity1** etkinliğini seçin.

7. **Özellikler** penceresinde **koşulu** kod koşulu olarak ayarlayın.

8. **Koşul** özelliğini genişletin, alt **koşul** özelliğinin yanına **ısworkflowpending** yazın ve Enter tuşunu seçin.

     Kod Düzenleyicisi açılır ve Workflow1 kod dosyasına ıworkflowpending adlı bir yöntem eklenir.

9. İş akışı tasarımcısına geri dönün, araç kutusunu açın ve ardından **SharePoint Iş akışı** düğümünü genişletin.

10. **Araç kutusunun** **SharePoint iş akışı** düğümünde aşağıdaki adım kümelerinden birini gerçekleştirin:

    - **Onworkflowwitemchanged** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **whileActivity1** etkinliğinin içindeki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    - **Onworkflowwitemchanged** etkinliğini **araç kutusundan** iş akışı tasarımcısına sürükleyin ve etkinliği **whileActivity1** etkinliğinin içindeki satıra bağlayın.

11. **OnWorkflowItemChanged1** etkinliğini seçin.

12. **Özellikler** penceresinde, aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.

    |Özellik|Değer|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Tanımladığınızda**|**Onworkflowwitemchanged**|

## <a name="handle-activity-events"></a>Etkinlik olaylarını işle
 Son olarak, her etkinlikten belgenin durumunu kontrol edin. Belge incelenip, iş akışı tamamlanmıştır.

#### <a name="to-handle-activity-events"></a>Etkinlik olaylarını işlemek için

1. *Workflow1.cs* veya *Workflow1. vb*' de, sınıfının en üstüne aşağıdaki alanı ekleyin `Workflow1` . Bu alan, iş akışının tamamlanıp bitmediğini tespit etmek için bir etkinlikte kullanılır.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Sınıfına aşağıdaki yöntemi ekleyin `Workflow1` . Bu yöntem, `Document Status` belgenin gözden geçirilip geçirilmediğini anlamak Için belgeler listesi özelliğinin değerini denetler. `Document Status`Özelliği olarak ayarlandıysa `Review Complete` , `checkStatus` yöntemi `workflowPending` iş akışının bitmek üzere hazırlandığını göstermek için alanı **false** olarak ayarlar.

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

3. `onWorkflowActivated` `onWorkflowItemChanged` Yöntemini çağırmak için ve yöntemlerine aşağıdaki kodu ekleyin `checkStatus` . İş akışı başladığında `onWorkflowActivated` yöntemi, `checkStatus` belgenin zaten gözden geçirilip geçirilmediğini anlamak için yöntemini çağırır. Gözden geçirilmeyen iş akışı devam eder. Belge kaydedildiğinde `onWorkflowItemChanged` yöntemi, `checkStatus` belgenin gözden geçirilip geçirilmediğini anlamak için yöntemini yeniden çağırır. `workflowPending`Alan **true** olarak ayarlandığında iş akışı çalışmaya devam eder.

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

4. `isWorkflowPending`Özelliğin durumunu denetlemek için yöntemine aşağıdaki kodu ekleyin `workflowPending` . Belge her kaydedildiğinde, **whileActivity1** etkinliği `isWorkflowPending` yöntemini çağırır. Bu yöntem, <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> <xref:System.Workflow.Activities.ConditionalEventArgs> **whileActivity1** etkinliğinin devam edip etmeyeceğini veya bitmeyeceğini anlamak için nesnesinin özelliğini inceler. Özelliği **true** olarak ayarlanırsa etkinlik devam eder. Aksi takdirde, etkinlik sonlanır ve iş akışı sonlanır.

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

## <a name="test-the-sharepoint-workflow-template"></a>SharePoint iş akışı şablonunu test etme
 Hata ayıklayıcıyı başlattığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı şablonunu SharePoint sunucusuna dağıtır ve iş akışını **paylaşılan belgeler** listesiyle ilişkilendirir. İş akışını test etmek için, **paylaşılan belgeler** listesindeki bir belgeden iş akışının bir örneğini başlatın.

#### <a name="to-test-the-sharepoint-workflow-template"></a>SharePoint iş akışı şablonunu test etmek için

1. *Workflow1.cs* veya *Workflow1. vb*' de, **onWorkflowActivated** yönteminin yanında bir kesme noktası ayarlayın.

2. Çözümü derlemek ve çalıştırmak için **F5** tuşunu seçin.

     SharePoint sitesi görüntülenir.

3. SharePoint 'teki gezinti bölmesinde, **paylaşılan belgeler** bağlantısını seçin.

4. **Paylaşılan belgeler** sayfasında, **kitaplık araçları** sekmesindeki **Belgeler** bağlantısını seçin ve ardından **belgeyi karşıya yükle** düğmesini seçin.

5. **Belgeyi karşıya yükle** iletişim kutusunda, **Gözden** geçirme düğmesini seçin, herhangi bir belge dosyasını seçin, **Aç** düğmesini seçin ve **Tamam** düğmesini seçin.

     Bu, Seçili belgeyi **paylaşılan belgeler** listesine yükler ve iş akışını başlatır.

6. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , hata ayıklayıcının yöntemin yanındaki kesme noktasında durduğunu doğrulayın `onWorkflowActivated` .

7. Yürütmeye devam etmek için **F5** tuşunu seçin.

8. Burada belge için ayarları değiştirebilirsiniz, ancak **Kaydet** düğmesini seçerek bunları varsayılan değerlerde bırakabilirsiniz.

     Bu, sizi varsayılan SharePoint Web sitesinin **paylaşılan belgeler** sayfasına döndürür.

9. **Paylaşılan belgeler** sayfasında, **MySharePointWorkflow-Workflow1** sütununun altındaki değerin **devam ediyor** olarak ayarlandığını doğrulayın. Bu, iş akışının devam ettiğini ve belgenin gözden geçirme beklediğini gösterir.

10. **Paylaşılan belgeler** sayfasında belgeyi seçin, görüntülenen oku seçin ve ardından **Özellikleri Düzenle** menü öğesini seçin.

11. **Belge durumunu** **Gözden geçirme Tamam** olarak ayarlayın ve ardından **Kaydet** düğmesini seçin.

     Bu, sizi varsayılan SharePoint Web sitesinin **paylaşılan belgeler** sayfasına döndürür.

12. **Paylaşılan belgeler** sayfasında, **belge durumu** sütununun altındaki değerin **İnceleme Tamam** olarak ayarlandığını doğrulayın. **Paylaşılan belgeler** sayfasını yenileyin ve **MySharePointWorkflow-Workflow1** sütununun altındaki değerin **tamamlandı** olarak ayarlandığını doğrulayın. Bu, iş akışının tamamlandığını ve belgenin incelendiğini gösterir.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan iş akışı şablonlarının nasıl oluşturulacağı hakkında daha fazla bilgi edinebilirsiniz:

- SharePoint iş akışı etkinlikleri hakkında daha fazla bilgi edinmek için bkz. [SharePoint Foundation Için Iş akışı etkinlikleri](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Windows Workflow Foundation etkinlikleri hakkında daha fazla bilgi edinmek için bkz. [System. Workflow. Activities ad alanı](/dotnet/api/system.windows.media.color).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint iş akışı çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
