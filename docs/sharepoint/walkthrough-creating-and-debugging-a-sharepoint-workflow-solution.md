---
title: '& hata ayıklama SharePoint iş akışı çözümü oluştur'
description: bu kılavuzda bir SharePoint iş akışı çözümü oluşturun ve hata ayıklayın. Temel sıralı bir iş akışı şablonu oluşturun. İş akışı etkinlikleri oluşturun ve olayları işleyin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726747"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>izlenecek yol: SharePoint iş akışı çözümü oluşturma ve hatalarını ayıklama
  Bu izlenecek yol, temel sıralı bir iş akışı şablonunun nasıl oluşturulacağını göstermektedir. İş akışı, bir belgenin gözden geçirilip geçirilmediğini anlamak için paylaşılan belge kitaplığının bir özelliğini denetler. Belge incelenip iş akışı tamamlanır.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- içinde SharePoint liste tanımı sıralı iş akışı projesi oluşturuluyor [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- İş akışı etkinlikleri oluşturuluyor.

- İş akışı etkinlik olaylarını işleme.

> [!NOTE]
> Bu kılavuzda sıralı bir iş akışı projesi kullanılıyorsa, işlem durum makinesi iş akışı projesi için de aynıdır.
>
> ayrıca bilgisayarınız, aşağıdaki yönergelerde Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri ve SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint paylaşılan belgeler kitaplığına özellikler ekleme
 **paylaşılan belgeler** kitaplığındaki belgelerin gözden geçirme durumunu izlemek için, SharePoint sitemizdeki paylaşılan belgeler için üç yeni özellik oluşturacağız: `Status` , `Assignee` , ve `Review Comments` . Bu özellikleri **paylaşılan belgeler** kitaplığında tanımladık.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint paylaşılan belgeler kitaplığına özellikler eklemek için

1. http:// \<system name> /sitepages/home.aspx gibi bir SharePoint sitesini bir Web tarayıcısında açın.

2. Hızlı Başlat çubuğunda **Shareddocuments**' i seçin.

3. **Kitaplık araçları** şeridinde **kitaplık** ' ı seçin ve ardından Şeritteki **sütun oluştur** düğmesini seçerek yeni bir sütun oluşturun.

4. Sütun **belgesi durumunu** adlandırın, türünü seçenek olarak ayarlayın **(arasından seçim yapmak için menü)**, aşağıdaki üç seçeneği belirtin ve ardından **Tamam** düğmesini seçin:

    - **Gözden geçirme gerekiyor**

    - **İnceleme Tamam**

    - **Değişiklikler Istendi**

5. İki sütun daha oluşturun ve bunları **atanan** şekilde adlandırın ve **açıklamaları gözden geçirin**. Atanan sütun türünü tek satırlık metin olarak ayarlayın ve yorumları gözden geçir sütunu birden çok satırlık metin olarak yazın.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Kullanıma alma gerekmeden belgelerin düzenlenmesini etkinleştir
 Belgeleri kullanıma almak zorunda kalmadan düzenleyebilmeniz için iş akışı şablonunu test etmek daha kolaydır. sonraki yordamda, bunu etkinleştirmek için SharePoint sitesini yapılandırırsınız.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Belgelerin kullanıma almadan düzenlenmesini sağlamak için

1. Hızlı Başlat çubuğunda, **paylaşılan belgeler** bağlantısını seçin.

2. **kitaplık araçları** şeridinde **kitaplık** sekmesini seçin ve sonra **belge kitaplığı Ayarlar** sayfasını göstermek için **kitaplık Ayarlar** düğmesini seçin.

3. **genel Ayarlar** bölümünde, **sürüm oluşturma Ayarlar** sayfasını göstermek için **sürüm oluşturma Ayarlar** bağlantısını seçin.

4. **Belgelerin düzenlenmeden önce kullanıma alınmasını iste** seçeneğinin **Hayır** olduğunu doğrulayın. Değilse, **Hayır** olarak değiştirin ve **Tamam** düğmesini seçin.

5. Tarayıcıyı kapatın.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı iş akışı projesi oluşturma
 Sıralı bir iş akışı, son etkinlik bitene kadar sırayla yürütülen bir adım kümesidir. Bu yordamda, paylaşılan belgeler listemize uygulanacak sıralı bir iş akışı oluşturacağız. İş akışı Sihirbazı, iş akışını site tanımı veya liste tanımıyla ilişkilendirmenize olanak tanır ve iş akışının ne zaman başlatılacağını belirlemenizi sağlar.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint sıralı bir iş akışı projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2.   >    >  **yeni Project** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Project** öğesini seçin.

3. **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. **şablonlar** bölmesinde **SharePoint 2010 Project** şablonunu seçin.

5. **Ad** kutusuna **MySharePointWorkflow** yazın ve **Tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

6. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından güven düzeyini ve varsayılan siteyi kabul etmek için **son** düğmesini seçin.

     Bu adım, iş akışı projeleri için kullanılabilir tek seçenek olan çözüm için güven düzeyini Grup çözümü olarak ayarlar. Daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, **Project**  >  **yeni öğe ekle**' yi seçin.

8. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

9. **Şablonlar** bölmesinde, **sıralı iş akışı (yalnızca Grup çözümü)** şablonunu seçin ve ardından **Ekle** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** görüntülenir.

10. **Hata ayıklama için iş akışı adını belirtin** sayfasında, varsayılan adı (**MySharePointWorkflow-Workflow1**) kabul edin. Varsayılan iş akışı şablonu tür değerini tutun, **Iş akışını listeleyin** ve sonra **İleri** düğmesini seçin.

11. **bir hata ayıklama oturumunda iş akışını otomatik olarak ilişkilendirmek Visual Studio ister misiniz?** sayfasında, tüm varsayılan ayarları kabul etmek için **ileri** düğmesini seçin.

     Bu adım iş akışını paylaşılan belgeler kitaplığıyla otomatik olarak ilişkilendirir.

12. **İş akışınızın başlatılma koşullarını belirtin** sayfasında, **Iş akışının başlamasını nasıl başlatmak istiyorsunuz?** bölümünde varsayılan seçenekleri seçili bırakın ve **son** düğmesini seçin.

     Bu sayfa, iş akışınızın ne zaman başlayacağını belirtmenizi sağlar. varsayılan olarak, iş akışı, bir kullanıcı SharePoint içinde el ile başlatıldığında veya iş akışının ilişkilendirildiği bir öğe oluşturulduğunda başlatılır.

## <a name="create-workflow-activities"></a>İş akışı etkinlikleri oluşturma
 İş akışları gerçekleştirilecek eylemleri temsil eden bir veya daha fazla *etkinlik* içerir. İş akışı için etkinlikleri düzenlemek üzere iş akışı tasarımcısını kullanın. Bu yordamda, iş akışına iki etkinlik ekleyeceğiz: Handleexternaliventactivity ve Onworkflowwitemchanged. Bu etkinlikler, **paylaşılan belgeler** listesindeki belgelerin gözden geçirme durumunu izler

#### <a name="to-create-workflow-activities"></a>İş akışı etkinlikleri oluşturmak için

1. İş akışı, iş akışı Tasarımcısı 'nda görüntülenmelidir. Değilse, **Çözüm Gezgini** içinde **Workflow1. cs** veya **Workflow1. vb** dosyasını açın.

2. Tasarımcıda **onWorkflowActivated1** etkinliğini seçin.

3. **Özellikler** penceresinde, **çağrılan** özelliğin yanına **onWorkflowActivated** yazın ve ardından Enter tuşunu seçin.

     Kod Düzenleyicisi açılır ve Workflow1 kod dosyasına onWorkflowActivated adlı bir olay işleyicisi yöntemi eklenir.

4. iş akışı tasarımcısına geri dönün, araç kutusunu açın ve ardından **Windows workflow v 3.0** düğümünü genişletin.

5. **araç kutusunun** **Windows Workflow v 3.0** düğümünde aşağıdaki adım kümelerinden birini gerçekleştirin:

    1. **While** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **onWorkflowActivated1** etkinliğinin altındaki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    2. **While** etkinliğini **araç kutusundan** iş akışı tasarımcısına sürükleyin ve etkinliği **onWorkflowActivated1** etkinliğinin altındaki satıra bağlayın.

6. **WhileActivity1** etkinliğini seçin.

7. **Özellikler** penceresinde **koşulu** kod koşulu olarak ayarlayın.

8. **Koşul** özelliğini genişletin, alt **koşul** özelliğinin yanına **ısworkflowpending** yazın ve Enter tuşunu seçin.

     Kod Düzenleyicisi açılır ve Workflow1 kod dosyasına ıworkflowpending adlı bir yöntem eklenir.

9. iş akışı tasarımcısına geri dönün, araç kutusunu açın ve sonra **SharePoint iş akışı** düğümünü genişletin.

10. **araç kutusunun** **SharePoint iş akışı** düğümünde aşağıdaki adım kümelerinden birini gerçekleştirin:

    - **Onworkflowwitemchanged** etkinliğinin kısayol menüsünü açın ve **Kopyala**' yı seçin. İş akışı tasarımcısında, **whileActivity1** etkinliğinin içindeki satır için kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    - **Onworkflowwitemchanged** etkinliğini **araç kutusundan** iş akışı tasarımcısına sürükleyin ve etkinliği **whileActivity1** etkinliğinin içindeki satıra bağlayın.

11. **OnWorkflowItemChanged1** etkinliğini seçin.

12. **Özellikler** penceresinde, aşağıdaki tabloda gösterildiği gibi özellikleri ayarlayın.

    |Özellik|Değer|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Tanımladığınızda**|**Onworkflowwitemchanged**|

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

3. yöntemini çağıran ve `onWorkflowActivated` `onWorkflowItemChanged` yöntemlerine aşağıdaki kodu `checkStatus` ekleyin. İş akışı başlatıldığında yöntemi, belgenin zaten gözden geçirip gözden geçiril olmadığını `onWorkflowActivated` belirlemek için yöntemini `checkStatus` çağırmış olur. Gözden geçiriLmse, iş akışı devam eder. Belge kaydedilirken yöntemi, `onWorkflowItemChanged` belgenin gözden `checkStatus` geçirip gözden geçiril olmadığını belirlemek için yöntemini yeniden arar. alanı `workflowPending` true olarak ayarlanmış **olsa da** iş akışı çalıştırmaya devam eder.

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

4. Özelliğinin durumunu kontrol `isWorkflowPending` etmek için yöntemine aşağıdaki kodu `workflowPending` ekleyin. Belge her kaydedilebilirken **WhileActivity1** etkinliği yöntemini `isWorkflowPending` çağırmaktadır. Bu yöntem, WhileActivity1 etkinliğinin devam mı yoksa bitip bitip bit mi gerektiğini belirlemek <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> <xref:System.Workflow.Activities.ConditionalEventArgs> için nesnesinin özelliğini inceler.  özelliği true olarak **ayarlanırsa** etkinlik devam eder. Aksi takdirde etkinlik biter ve iş akışı biter.

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

5. Belge **Upload kutusunda** Gözat düğmesini seçin,  herhangi bir belge dosyasını seçin, Aç **düğmesini** ve ardından Tamam **düğmesini** seçin.

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
 Aşağıdaki konulardan iş akışı şablonları oluşturma hakkında daha fazla bilgi edinmek için:

- İş akışı etkinlikleri hakkında daha SharePoint için bkz. SharePoint Foundation için [İş Akışı Etkinlikleri.](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))

- Workflow Foundation etkinlikleri hakkında daha Windows için bkz. [System.Workflow.Activities Ad Alanı.](/dotnet/api/system.windows.media.color)

## <a name="see-also"></a>Ayrıca bkz.
- [İş SharePoint çözümleri oluşturma](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint proje ve proje öğesi şablonlarını kullanma](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Çözüm oluşturma ve SharePoint ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
