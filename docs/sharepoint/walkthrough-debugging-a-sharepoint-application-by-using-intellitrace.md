---
title: IntelliTrace SharePoint uygulamanın hata ayıklaması
description: IntelliTrace kullanarak uygulamalarda daha kolay hata ayıklama ve SharePoint düzeltin. Özellik alıcısına kod oluşturma ve ekleme. Projeyi test etmek. IntelliTrace verilerini toplama.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123248"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Kılavuz: IntelliTrace kullanarak SharePoint uygulamanın hata ayıklaması

IntelliTrace kullanarak, çözümlerin hata ayıklama SharePoint yapabilirsiniz. Geleneksel hata ayıklayıcılar, geçerli anda yalnızca bir çözümün anlık görüntüsünü sağlar. Ancak IntelliTrace'i kullanarak çözümünüzde meydana gelen geçmiş olayları ve bunların hangi bağlamda olduğunu gözden geçirebilirsiniz ve koda gidin.

 Bu kılavuzda, dağıtılan uygulamalardan IntelliTrace verilerini toplamak Visual Studio Microsoft Monitoring Agent bir SharePoint projesinde hata ayıklamayı gösteren bir adım adım kılavuz. Bu verileri analiz etmek için bu verileri Visual Studio Enterprise. Bu proje, özellik etkinleştirildiğinde Görev listesine bir görev ve Duyurular listesine bir duyuru ekleyen bir özellik alıcısı içerir. Özellik devre dışı bırakıldığında görev tamamlandı olarak işaretlenir ve Duyurular listesine ikinci bir duyuru eklenir. Ancak, yordam projenin doğru şekilde çalışmasını engelleyen bir mantıksal hata içerir. IntelliTrace kullanarak hatayı bulup düzeltin.

 **Aşağıdakiler için geçerlidir:** Bu konu başlığı altında yer alan bilgiler, SharePoint çözümler için Visual Studio.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Özellik Alıcısı Oluşturma](#create-a-feature-receiver)

- [Özellik Alıcısına Kod Ekleme](#add-code-to-the-feature-receiver)

- [Test Project](#test-the-project)

- [IntelliTrace Verilerini Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [SharePoint Çözümde Hata Ayıklama ve Düzeltme](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Özellik alıcısı oluşturma

İlk olarak, özellik alıcısı SharePoint boş bir proje oluşturun.

1. Yüklemiş SharePoint sürümünü hedef alan bir SharePoint çözüm projesi oluşturun ve **IntelliTraceTest olarak anın.**

     Projeniz **SharePoint** siteyi ve çözümün güven düzeyini belirtebilirsiniz SharePoint.

2. Grup **çözümü olarak dağıt seçeneğini belirleyin** ve ardından Son **düğmesini** seçin.

     IntelliTrace yalnızca grup çözümlerinde çalışır.

3. Bu **Çözüm Gezgini** Özellikler düğümü için kısayol menüsünü **açın ve Özellik** Ekle'yi **seçin.**

     *Feature1.feature* görüntülenir.

4. Feature1.feature kısayol menüsünü açın ve ardından Olay **Alıcısı** Ekle'yi seçarak özelliğe bir kod modülü ekleyin.

## <a name="add-code-to-the-feature-receiver"></a>Özellik alıcısına kod ekleme

Ardından, özellik alıcısı içinde iki yönteme kod ekleyin: `FeatureActivated` ve `FeatureDeactivating` . Bu yöntemler, bir özellik sırasıyla bir özellik her etkinleştirildiğinde veya SharePoint tetiklenir.

1. sınıfının en üstüne aşağıdaki kodu ekleyin. Bu kod, sitenin ve `Feature1EventReceiver` alt sitenin SharePoint değişkenleri belirtir:

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

Artık kod özellik alıcısına eklenmiştir ve veri toplayıcı çalışır, doğru şekilde çalıştığını test etmek için SharePoint çözümü dağıtın ve çalıştırın.

> [!IMPORTANT]
> Bu örnekte, FeatureDeactivating olay işleyicisinde bir hata oluştu. Bu kılavuzda daha sonra, veri toplayıcının oluşturduğu .iTrace dosyasını kullanarak bu hatayı bulun.

1. Çözümü SharePoint dağıtın ve SharePoint tarayıcıda açın.

     Özellik otomatik olarak etkin hale geliyor ve bu da özellik alıcısının bir duyuru ve görev eklemesini sağlar.

2. Duyurular ve Görevler listelerinin içeriğini görüntüler.

     Duyurular listesinde Etkin özellik adlı yeni bir duyuru olması **gerekir: IntelliTraceTest_Feature1** ve Görevler listesinde Devre dışı bırakma **özelliği:** IntelliTraceTest_Feature1. Bu öğelerden biri eksikse özelliğin etkinleştirildiğinden emin olun. Etkinleştirilmezse etkinleştirin.

3. Aşağıdaki adımları gerçekleştirerek özelliği devre dışı bırakma:

   1. **SharePoint'daki** Site Eylemleri menüsünde Site **Eylemleri'Ayarlar.**

   2. **Site Eylemleri'nin** altında Site **özelliklerini yönet bağlantısını** seçin.

   3. **IntelliTraceTest Feature1'in yanındaki** Devre Dışı Bırak **düğmesini** seçin.

   4. Uyarı sayfasında Bu özelliği devre dışı **bırak bağlantısını** seçin.

      FeatureDeactivating() olay işleyicisi bir hata döndürür.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>IntelliTrace verilerini Microsoft Monitoring Agent

Microsoft Monitoring Agent çalıştıran sisteme SharePoint, IntelliTrace tarafından döndüren genel bilgilerden daha özel olan verileri kullanarak SharePoint çözümlerinin hata ayıklaması oluşturabilirsiniz. Aracı, çözüm Visual Studio hata ayıklama bilgilerini yakalamak için PowerShell cmdlet'lerini kullanarak SharePoint çalışır.

> [!NOTE]
> Bu bölümdeki yapılandırma bilgileri bu örnekteki özeldir. Diğer yapılandırma seçenekleri hakkında daha fazla bilgi için [bkz. IntelliTrace tek başına toplayıcıyı kullanma.](../debugger/using-the-intellitrace-stand-alone-collector.md)

1. SharePoint çalıştıran bilgisayarda, [Microsoft Monitoring Agent'i ayarlayın ve çözümlerinizi izlemeye başlatın.](../debugger/using-the-intellitrace-stand-alone-collector.md)

2. Özelliği devre dışı bırakma:

   1. **SharePoint'daki** Site Eylemleri menüsünde Site **Eylemleri'Ayarlar.**

   2. **Site Eylemleri'nin** altında Site **özelliklerini yönet bağlantısını** seçin.

   3. **IntelliTraceTest Feature1'in yanındaki** Devre Dışı Bırak **düğmesini** seçin.

   4. Uyarı sayfasında Bu özelliği devre dışı **bırak bağlantısını** seçin.

      Bir hata oluşur (bu durumda, FeatureDeactivating() olay işleyicisinde oluşan hata nedeniyle).

3. PowerShell penceresinde [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) komutunu çalıştırarak .iTrace dosyasını oluşturun, izlemeyi durdurun ve SharePoint başlatın.

     **Stop-WebApplicationMonitoring***"<\<SharePointSite> \\ SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Çözümde hata ayıklama SharePoint düzeltme

Artık IntelliTrace günlük dosyasını Visual Studio çözümde hatayı bulup düzeltmek için SharePoint görüntüebilirsiniz.

1. \IntelliTraceLogs klasöründeki .iTrace dosyasını Visual Studio.

     **IntelliTrace Özeti** sayfası görüntülenir. Hata işlendiğinden Analiz bölümünün SharePoint özel durum alanında bir bağıntı kimliği (GUID) **görüntülenir.** Hatanın **meydana** geldiği çağrı yığınını görüntülemek için Çağrı Yığını düğmesini seçin.

2. Hata Ayıklama **Özel Durumu düğmesini** seçin.

     İstendiğinde sembol dosyalarını yükle. **IntelliTrace penceresinde** özel durum "Oluştu: Ciddi hata oluştu!" olarak vurgulanır.

     IntelliTrace penceresinde başarısız olan kodu görüntülemek için özel durumu seçin.

3. SharePoint çözümünü açarak ve sonra açıklama ekleme veya FeatureDeactivating() yordamının üst kısmında **throw** deyimini kaldırarak hatayı düzeltin.

4. Çözümü Visual Studio yeniden SharePoint.

5. Aşağıdaki adımları gerçekleştirerek özelliği devre dışı bırakma:

    1. **SharePoint'daki** Site Eylemleri menüsünde Site **Eylemleri'Ayarlar.**

    2. **Site Eylemleri'nin** altında Site **özelliklerini yönet bağlantısını** seçin.

    3. **IntelliTraceTest Feature1'in yanındaki** Devre Dışı Bırak **düğmesini** seçin.

    4. Uyarı sayfasında Bu özelliği devre dışı **bırak bağlantısını** seçin.

6. Görev listesini açın ve Devre Dışı Bırak görevinin **Durum** değerinin "Tamamlandı" ve **Tamamlanma %** değerinin %100 olduğunu doğrulayın.

     Kod artık düzgün çalışıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu doğrulama ve SharePoint ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [adım adım kılavuz: SharePoint Testlerini Kullanarak Kodu Doğrulama](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
