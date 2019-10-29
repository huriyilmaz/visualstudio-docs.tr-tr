---
title: IntelliTrace kullanarak SharePoint uygulamasında hata ayıklama
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fe1130880db42e920e656d5efef1ea6a5af4d2d0
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984150"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>İzlenecek yol: IntelliTrace kullanarak bir SharePoint uygulamasında hata ayıklama

IntelliTrace 'i kullanarak SharePoint Çözümlerinde daha kolay hata ayıklama yapabilirsiniz. Geleneksel hata ayıklayıcıları, size geçerli anda yalnızca bir çözümün anlık görüntüsünü verir. Ancak, çözümünüzde oluşan geçmiş olayları ve bunların oluştuğu bağlamı gözden geçirmek için IntelliTrace 'i kullanabilir ve koda gidebilirsiniz.

 Bu izlenecek yolda, dağıtılan uygulamalardan IntelliTrace verilerini toplamak için Microsoft Monitoring Agent kullanarak Visual Studio 'da SharePoint 2010 veya SharePoint 2013 projesinde hata ayıklama yapılacağını gösterilmektedir. Bu verileri çözümlemek için Visual Studio Enterprise kullanmanız gerekir. Bu proje, özellik etkinleştirildiğinde, görev listesine bir görev ve Duyurular listesine bir duyuru ekleyen bir özellik alıcısı içerir. Özellik devre dışı bırakıldığında, görev tamamlandı olarak işaretlenir ve Duyurular listesine ikinci bir duyuru eklenir. Ancak yordam, projenin düzgün çalışmasını engelleyen bir mantıksal hata içeriyor. IntelliTrace 'i kullanarak hatayı bulacak ve düzelteceksiniz.

 **Uygulama hedefi:** Bu konudaki bilgiler SharePoint 2010 ve Visual Studio 'da oluşturulan SharePoint 2013 çözümleri için geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Özellik alıcısı oluşturma](#create-a-feature-receiver)

- [Özellik alıcısına kod ekleme](#add-code-to-the-feature-receiver)

- [Projeyi test etme](#test-the-project)

- [Microsoft Monitoring Agent kullanarak IntelliTrace verileri toplama](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [SharePoint çözümünü hata ayıklama ve çözme](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint sürümleri.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Özellik alıcısı oluşturma

İlk olarak, özellik alıcısı olan boş bir SharePoint projesi oluşturursunuz.

1. Bir SharePoint 2010 veya SharePoint 2013 çözüm projesi oluşturun ve bunu **IntelliTraceTest**olarak adlandırın.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir, burada projeniz Için hem SharePoint sitesini hem de çözümün güven düzeyini belirtebilirsiniz.

2. **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından **son** düğmesini seçin.

     IntelliTrace yalnızca Grup çözümlerinde çalışır.

3. **Çözüm Gezgini**, **Özellikler** düğümünün kısayol menüsünü açın ve **Özellik Ekle**' yi seçin.

     *Özellik1. feature* görüntülenir.

4. Özellik1. feature için kısayol menüsünü açın ve sonra özelliğe kod modülü eklemek için **olay alıcısı Ekle** ' yi seçin.

## <a name="add-code-to-the-feature-receiver"></a>Özellik alıcısına kod ekleme

Sonra, özellik alıcısındaki iki yönteme kod ekleyin: `FeatureActivated` ve `FeatureDeactivating`. Bu yöntemler sırasıyla SharePoint 'te her bir özellik etkinleştirildiğinde veya devre dışı bırakıldığında tetiklenir.

1. `Feature1EventReceiver` sınıfının üst kısmında, SharePoint sitesini ve alt siteyi belirten değişkenleri bildiren aşağıdaki kodu ekleyin:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. `FeatureActivated` yöntemini aşağıdaki kodla değiştirin:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. `FeatureDeactivating` yöntemini aşağıdaki kodla değiştirin:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Projeyi test etme

Artık kod, özellik alıcısına eklendiğinden ve veri toplayıcı çalıştırıldığına göre, doğru çalışıp çalışmadığını test etmek için SharePoint çözümünü dağıtıp çalıştırın.

> [!IMPORTANT]
> Bu örnekte, Featureını devre dışı bırakma olay işleyicisinde bir hata oluşur. Bu izlenecek yolda, veri toplayıcısının oluşturduğu. iTrace dosyasını kullanarak bu hatayı bulabilirsiniz.

1. Çözümü SharePoint 'e dağıtın ve SharePoint sitesini bir tarayıcıda açın.

     Özelliği otomatik olarak etkinleştirilir ve özellik alıcısının bir duyuru ve bir görev eklemesine neden olur.

2. Duyurular ve görevler listelerinin içeriğini görüntüleyin.

     Duyurular listesinde, **etkinleştirilen Özellik: IntelliTraceTest_Feature1**adlı yeni bir duyuru olmalıdır ve görev listesi, **devre dışı bırakma özelliği: IntelliTraceTest_Feature1**adlı yeni bir görevin olması gerekir. Bu öğelerden herhangi biri eksikse, özelliğin etkinleştirilip etkinleştirilmediğini doğrulayın. Etkinleştirilmemişse, etkinleştirin.

3. Aşağıdaki adımları gerçekleştirerek özelliği devre dışı bırakın:

   1. SharePoint 'teki **Site eylemleri** menüsünde, **site ayarları**' nı seçin.

   2. **Site eylemleri**altında, **site özelliklerini yönet** bağlantısını seçin.

   3. **IntelliTraceTest özellik1**' ın yanındaki **devre dışı bırak** düğmesini seçin.

   4. Uyarı sayfasında **Bu özelliği devre dışı bırak** bağlantısını seçin.

      Featuredevre dışı bırakma () olay işleyicisi bir hata oluşturur.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Microsoft Monitoring Agent kullanarak IntelliTrace verileri toplama

SharePoint çalıştıran sisteme Microsoft Monitoring Agent yüklerseniz, IntelliTrace 'in döndürdüğü genel bilgilerden daha belirgin olan verileri kullanarak SharePoint Çözümlerinde hata ayıklaması yapabilirsiniz. Aracı, SharePoint çözümünüz çalışırken hata ayıklama bilgilerini yakalamak için PowerShell cmdlet 'lerini kullanarak Visual Studio dışında çalışır.

> [!NOTE]
> Bu bölümdeki yapılandırma bilgileri bu örneğe özeldir. Diğer yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. SharePoint çalıştıran bilgisayarda [Microsoft Monitoring Agent ayarlayın ve çözümünüzü izlemeye başlayın](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Özelliği devre dışı bırak:

   1. SharePoint 'teki **Site eylemleri** menüsünde, **site ayarları**' nı seçin.

   2. **Site eylemleri**altında, **site özelliklerini yönet** bağlantısını seçin.

   3. **IntelliTraceTest özellik1**' ın yanındaki **devre dışı bırak** düğmesini seçin.

   4. Uyarı sayfasında **Bu özelliği devre dışı bırak** bağlantısını seçin.

      Bir hata oluşur (Bu durumda, Featuredevre dışı bırakma () olay işleyicisinde oluşan hata nedeniyle).

3. PowerShell penceresinde, [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) komutunu çalıştırarak. iTrace dosyasını oluşturun, izlemeyi durdurun ve SharePoint Çözümünüzü yeniden başlatın.

     **Stop-WebApplicationMonitoring**  *"\<sharepointsite >\\< SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>SharePoint çözümünü hata ayıklama ve çözme

Artık SharePoint çözümündeki hatayı bulmak ve onarmak için IntelliTrace günlük dosyasını Visual Studio 'da görüntüleyebilirsiniz.

1. \IntelliTraceLogs klasöründe, Visual Studio 'da. iTrace dosyasını açın.

     **IntelliTrace Özet** sayfası görünür. Hata işlenmediğinden, **analiz** bölümünün işlenmeyen özel durum alanında bir SHAREPOINT bağıntı KIMLIĞI (GUID) görüntülenir. Hatanın gerçekleştiği çağrı yığınını görüntülemek istiyorsanız, **çağrı yığını** düğmesini seçin.

2. **Hata ayıklama özel durumu** düğmesini seçin.

     İstenirse, sembol dosyalarını yükleyin. **IntelliTrace** penceresinde, özel durum "oluşturuldu: önemli hata oluştu!" olarak vurgulanır.

     IntelliTrace penceresinde, başarısız olan kodu göstermek için özel durum ' u seçin.

3. SharePoint çözümünü açıp sonra Featuredevre dışı bırakma () yordamının en üstündeki **throw** ifadesini düzenleyerek veya kaldırarak hatayı düzeltemedi.

4. Visual Studio 'da çözümü yeniden derleyin ve ardından SharePoint 'e dağıtın.

5. Aşağıdaki adımları gerçekleştirerek özelliği devre dışı bırakın:

    1. SharePoint 'teki **Site eylemleri** menüsünde, **site ayarları**' nı seçin.

    2. **Site eylemleri**altında, **site özelliklerini yönet** bağlantısını seçin.

    3. **IntelliTraceTest özellik1**' ın yanındaki **devre dışı bırak** düğmesini seçin.

    4. Uyarı sayfasında **Bu özelliği devre dışı bırak** bağlantısını seçin.

6. Görev listesini açın ve devre dışı bırakma görevinin **durum** değerinin "tamamlandı" olduğunu ve **Tamamlanma yüzdesi değerinin%** 100 olduğunu doğrulayın.

     Kod artık düzgün şekilde çalışır.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint kodunu doğrulama ve hata ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [İzlenecek yol: birim testlerini kullanarak SharePoint kodunu doğrulama](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))