---
title: ıntellitrace kullanarak SharePoint uygulamada hata ayıklama
description: SharePoint uygulamalarında daha kolay hata ayıklama ve çözüm için ıntellitrace kullanın. Bir özellik alıcısına kod oluşturun ve kodu ekleyin. Projeyi test edin. IntelliTrace verilerini toplayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 60a177fec8edf3b2e201eaff63ee0ff0ed4c8d72
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726744"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>izlenecek yol: ıntellitrace kullanarak SharePoint uygulamasında hata ayıklama

ıntellitrace kullanarak SharePoint çözümlerinde daha kolay hata ayıklama yapabilirsiniz. Geleneksel hata ayıklayıcıları, size geçerli anda yalnızca bir çözümün anlık görüntüsünü verir. Ancak, çözümünüzde oluşan geçmiş olayları ve bunların oluştuğu bağlamı gözden geçirmek için IntelliTrace 'i kullanabilir ve koda gidebilirsiniz.

 bu izlenecek yol, dağıtılan uygulamalardan ıntellitrace verilerini toplamak için Microsoft Monitoring Agent kullanarak Visual Studio SharePoint projenin nasıl ayıklanacağını gösterir. Bu verileri çözümlemek için Visual Studio Enterprise kullanmanız gerekir. Bu proje, özellik etkinleştirildiğinde, görev listesine bir görev ve Duyurular listesine bir duyuru ekleyen bir özellik alıcısı içerir. Özellik devre dışı bırakıldığında, görev tamamlandı olarak işaretlenir ve Duyurular listesine ikinci bir duyuru eklenir. Ancak yordam, projenin düzgün çalışmasını engelleyen bir mantıksal hata içeriyor. IntelliTrace 'i kullanarak hatayı bulacak ve düzelteceksiniz.

 **Uygulama hedefi:** bu konudaki bilgiler, Visual Studio oluşturulan SharePoint çözümleri için geçerlidir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Özellik alıcısı oluşturma](#create-a-feature-receiver)

- [Özellik alıcısına kod ekleme](#add-code-to-the-feature-receiver)

- [Project test etme](#test-the-project)

- [Microsoft Monitoring Agent kullanarak IntelliTrace verileri toplama](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [SharePoint çözümünü hata ayıklama ve çözme](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Windows ve SharePoint desteklenen sürümleri.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Özellik alıcısı oluşturma

ilk olarak, özellik alıcısı olan boş bir SharePoint projesi oluşturursunuz.

1. yüklediğiniz SharePoint sürümünü hedefleyen SharePoint bir çözüm projesi oluşturun ve bunu **ıntellitracetest** olarak adlandırın.

     **SharePoint özelleştirme sihirbazı** görüntülenir, burada hem projeniz için SharePoint sitesini hem de çözümün güven düzeyini belirtebilirsiniz.

2. **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından **son** düğmesini seçin.

     IntelliTrace yalnızca Grup çözümlerinde çalışır.

3. **Çözüm Gezgini**, **Özellikler** düğümünün kısayol menüsünü açın ve **Özellik Ekle**' yi seçin.

     *Özellik1. feature* görüntülenir.

4. Özellik1. feature için kısayol menüsünü açın ve sonra özelliğe kod modülü eklemek için **olay alıcısı Ekle** ' yi seçin.

## <a name="add-code-to-the-feature-receiver"></a>Özellik alıcısına kod ekleme

Sonra, özellik alıcısındaki iki yönteme kod ekleyin: `FeatureActivated` ve `FeatureDeactivating` . bu yöntemler sırasıyla SharePoint her bir özellik etkinleştirildiğinde veya devre dışı bırakıldığında tetiklenir.

1. sınıfının üst kısmında `Feature1EventReceiver` , SharePoint sitesini ve alt siteyi belirten değişkenleri bildiren aşağıdaki kodu ekleyin:

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

2. `FeatureActivated` yöntemini aşağıdaki kod ile değiştirin:

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

3. `FeatureDeactivating` yöntemini aşağıdaki kod ile değiştirin:

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

artık kod, özellik alıcısına eklendiğinden ve veri toplayıcı çalışır durumda olduğuna göre, SharePoint çözümünü dağıtıp çalıştırarak düzgün çalışıp çalışmadığını test edin.

> [!IMPORTANT]
> Bu örnekte, Featureını devre dışı bırakma olay işleyicisinde bir hata oluşur. Bu izlenecek yolda, veri toplayıcısının oluşturduğu. iTrace dosyasını kullanarak bu hatayı bulabilirsiniz.

1. çözümü SharePoint dağıtın ve SharePoint sitesini bir tarayıcıda açın.

     Özelliği otomatik olarak etkinleştirilir ve özellik alıcısının bir duyuru ve bir görev eklemesine neden olur.

2. Duyurular ve görevler listelerinin içeriğini görüntüleyin.

     Duyurular listesinde, **etkinleştirilen Özellik: IntelliTraceTest_Feature1** adlı yeni bir duyuru olmalıdır ve görev listesi, **devre dışı bırakma özelliği** olarak adlandırılan yeni bir görevin olması gerekir: IntelliTraceTest_Feature1. Bu öğelerden herhangi biri eksikse, özelliğin etkinleştirilip etkinleştirilmediğini doğrulayın. Etkinleştirilmemişse, etkinleştirin.

3. Aşağıdaki adımları gerçekleştirerek özelliği devre dışı bırakın:

   1. SharePoint **site eylemleri** menüsünde **site Ayarlar**' nı seçin.

   2. **Site eylemleri** altında, **site özelliklerini yönet** bağlantısını seçin.

   3. **IntelliTraceTest özellik1**' ın yanındaki **devre dışı bırak** düğmesini seçin.

   4. Uyarı sayfasında **Bu özelliği devre dışı bırak** bağlantısını seçin.

      Featuredevre dışı bırakma () olay işleyicisi bir hata oluşturur.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Microsoft Monitoring Agent kullanarak IntelliTrace verileri toplama

SharePoint çalıştıran sisteme Microsoft Monitoring Agent yüklerseniz, ıntellitrace 'in döndürdüğü genel bilgilerden daha belirgin olan verileri kullanarak SharePoint çözümlerinde hata ayıklaması yapabilirsiniz. aracı, SharePoint çözümünüz çalışırken hata ayıklama bilgilerini yakalamak için PowerShell cmdlet 'lerini kullanarak Visual Studio dışında çalışır.

> [!NOTE]
> Bu bölümdeki yapılandırma bilgileri bu örneğe özeldir. Diğer yapılandırma seçenekleri hakkında daha fazla bilgi için bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. SharePoint çalıştıran bilgisayarda, [Microsoft Monitoring Agent ayarlayın ve çözümünüzü izlemeye başlayın](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Özelliği devre dışı bırak:

   1. SharePoint **site eylemleri** menüsünde **site Ayarlar**' nı seçin.

   2. **Site eylemleri** altında, **site özelliklerini yönet** bağlantısını seçin.

   3. **IntelliTraceTest özellik1**' ın yanındaki **devre dışı bırak** düğmesini seçin.

   4. Uyarı sayfasında **Bu özelliği devre dışı bırak** bağlantısını seçin.

      Bir hata oluşur (Bu durumda, Featuredevre dışı bırakma () olay işleyicisinde oluşan hata nedeniyle).

3. PowerShell penceresinde, [stop-webapplicationmonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) komutunu çalıştırarak. itrace dosyasını oluşturun, izlemeyi durdurun ve SharePoint çözümünüzü yeniden başlatın.

     **Stop-WebApplicationMonitoring***" \<SharePointSite> \\<sharepointappname \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>SharePoint çözümünü hata ayıklama ve çözme

artık SharePoint çözümünde hatayı bulmak ve onarmak için Visual Studio 'de ıntellitrace günlük dosyasını görüntüleyebilirsiniz.

1. \IntelliTraceLogs klasöründe. iTrace dosyasını Visual Studio açın.

     **IntelliTrace Özet** sayfası görünür. hata işlenmediği için **analiz** bölümünün işlenmeyen özel durum alanında bir SharePoint bağıntı kimliği (bir guıd) görüntülenir. Hatanın gerçekleştiği çağrı yığınını görüntülemek istiyorsanız, **çağrı yığını** düğmesini seçin.

2. **Hata ayıklama özel durumu** düğmesini seçin.

     İstenirse, sembol dosyalarını yükleyin. **IntelliTrace** penceresinde, özel durum "oluşturuldu: önemli hata oluştu!" olarak vurgulanır.

     IntelliTrace penceresinde, başarısız olan kodu göstermek için özel durum ' u seçin.

3. SharePoint çözümünü açıp sonra featuredevre dışı bırakma () yordamının en üstündeki **throw** ifadesini düzenleyerek veya kaldırarak hatayı düzeltemedi.

4. Visual Studio çözümü yeniden derleyin ve sonra SharePoint için yeniden dağıtın.

5. Aşağıdaki adımları gerçekleştirerek özelliği devre dışı bırakın:

    1. SharePoint **site eylemleri** menüsünde **site Ayarlar**' nı seçin.

    2. **Site eylemleri** altında, **site özelliklerini yönet** bağlantısını seçin.

    3. **IntelliTraceTest özellik1**' ın yanındaki **devre dışı bırak** düğmesini seçin.

    4. Uyarı sayfasında **Bu özelliği devre dışı bırak** bağlantısını seçin.

6. Görev listesini açın ve devre dışı bırakma görevinin **durum** değerinin "tamamlandı" olduğunu ve **Tamamlanma yüzdesi değerinin%** 100 olduğunu doğrulayın.

     Kod artık düzgün şekilde çalışır.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint kodu doğrulama ve hata ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [izlenecek yol: birim testlerini kullanarak SharePoint kodu doğrulama](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
