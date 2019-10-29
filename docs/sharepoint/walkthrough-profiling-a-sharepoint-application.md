---
title: 'İzlenecek yol: SharePoint uygulaması profili oluşturma | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d001edcd281a0c21d244704f0a068850804b8762
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981153"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>İzlenecek yol: SharePoint uygulaması profili oluşturma
  Bu izlenecek yol, bir SharePoint uygulamasının performansını iyileştirmek için Visual Studio 'da profil oluşturma araçlarının nasıl kullanılacağını gösterir. Örnek uygulama, özellik olay alıcısının performansını düşürür bir boşta kalma döngüsü içeren bir SharePoint özellik olay alıcıdır. Visual Studio Profiler, projenin *etkin yol*olarak da bilinen en pahalı (en yavaş performanslı) kısmını bulmanıza ve ortadan kaldırmanıza olanak sağlar.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Özellik ve özellik olay alıcısını Addg](#add-a-feature-and-feature-event-receiver).

- [SharePoint uygulamasını yapılandırın ve dağıtın](#configure-and-deploy-the-sharepoint-application).

- [SharePoint uygulamasını çalıştırın](#run-the-sharepoint-application).

- [Profil sonuçlarını görüntüleyin ve yorumlayın](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Microsoft Windows ve SharePoint sürümleri.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>SharePoint projesi oluşturma
 İlk olarak, bir SharePoint projesi oluşturun.

### <a name="to-create-a-sharepoint-project"></a>SharePoint projesi oluşturmak için

1. **Yeni proje** iletişim kutusunu göstermek için menü çubuğunda **dosya**  > **Yeni**  > **Proje** ' yi seçin.

2. **Visual C#**  veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Şablonlar bölmesinde, **SharePoint 2010 proje** şablonunu seçin.

4. **Ad** kutusunda, **ProfileTest**girin ve **Tamam** düğmesini seçin.

    **SharePoint Özelleştirme Sihirbazı** görüntülenir.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımında hata ayıklamak istediğiniz SharePoint Server sitesinin URL 'sini girin veya varsayılan konumu (http://<em>sistem adı</em>/) kullanın.

6. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, **Grup çözümü olarak dağıt** seçenek düğmesini seçin.

    Şu anda yalnızca Grup çözümlerini profil oluşturabilirsiniz. Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Son** düğmesini seçin. Proje **Çözüm Gezgini**görüntülenir.

## <a name="add-a-feature-and-feature-event-receiver"></a>Özellik ve özellik olay alıcısı ekleme
 Daha sonra, özelliği için bir olay alıcısıyla birlikte projeye bir özellik ekleyin. Bu olay alıcısı, profili oluşturulacak kodu içerecektir.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Özellik ve özellik olay alıcısı eklemek için

1. **Çözüm Gezgini**, **Özellikler** düğümünün kısayol menüsünü açın, **Özellik Ekle**' yi seçin ve adı varsayılan değer olan **özellik1**olarak bırakın.

2. **Çözüm Gezgini**' de, **özellik1**için kısayol menüsünü açın ve ardından **olay alıcısı Ekle**' yi seçin.

     Bu, birkaç açıklamalı olay işleyicileriyle özelliğe bir kod dosyası ekler ve dosyayı düzenlenmek üzere açar.

3. Olay alıcısı sınıfında, aşağıdaki değişken bildirimlerini ekleyin.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. `FeatureActivated` yordamını aşağıdaki kodla değiştirin.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
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

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. Aşağıdaki yordamı `FeatureActivated`yordamının altına ekleyin.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. **Çözüm Gezgini**, projenin (**ProfileTest**) kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

7. **Özellikler** Iletişim kutusunda **SharePoint** sekmesini seçin.

8. **Etkin dağıtım yapılandırması** listesinde, **etkinleştirme yok**' u seçin.

     Bu dağıtım yapılandırmasını seçmek, özelliği SharePoint 'te daha sonra el ile etkinleştirmenizi sağlar.

9. Projeyi kaydedin.

## <a name="configure-and-deploy-the-sharepoint-application"></a>SharePoint uygulamasını yapılandırma ve dağıtma
 Artık SharePoint projesi hazır olduğuna göre, yapılandırın ve SharePoint sunucusuna dağıtın.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>SharePoint uygulamasını yapılandırmak ve dağıtmak için

1. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı seçin.

2. **Performans sihirbazından**biri sayfasında, profil oluşturma yöntemini **CPU örneklemesi** olarak bırakın ve **İleri** düğmesini seçin.

     Diğer profil oluşturma yöntemleri, daha gelişmiş profil oluşturma durumlarında kullanılabilir. Daha fazla bilgi için bkz. [performans toplama yöntemlerini anlama](/visualstudio/profiling/understanding-performance-collection-methods).

3. **Performans sihirbazının**ikinci sayfasında profil hedefini **ProfileTest** olarak bırakın ve **İleri** düğmesini seçin.

     Bir çözümde birden çok proje varsa, bu listede görünürler.

4. **Performans sihirbazının**üç sayfasında, **katman etkileşim profilini etkinleştir** onay kutusunu temizleyin ve ardından **İleri** düğmesini seçin.

     Katman etkileşimi profil oluşturma (tıp) özelliği, veritabanlarını sorgulayan uygulamaların performansını ölçmek ve bir Web sayfasının istendiği zaman sayısını göstermek için yararlıdır. Bu örnek için bu veriler gerekli olmadığından, bu özelliği etkinleştiremeyecektir.

5. **Performans Sihirbazı**'nın dört sayfasında, **Sihirbaz tamamlandıktan sonra profil oluşturmayı Başlat** onay kutusunu Işaretli bırakın ve ardından **son** düğmesini seçin.

     Sihirbaz, sunucuda uygulama profili oluşturmayı, **Performans Gezgini** penceresini görüntüler ve ardından SharePoint uygulamasını oluşturur, dağıtır ve çalıştırır.

## <a name="run-the-sharepoint-application"></a>SharePoint uygulamasını çalıştırma
 Özelliği SharePoint 'te etkinleştirin ve `FeatureActivation` olay kodunu tetikleyerek çalıştırın.

### <a name="to-run-the-sharepoint-application"></a>SharePoint uygulamasını çalıştırmak için

1. SharePoint 'te **Site eylemleri** menüsünü açın ve ardından **site ayarları**' nı seçin.

2. **Site eylemleri** listesinde, **site özelliklerini yönet** bağlantısını seçin.

3. **Özellikler** listesinde, **ProfileTest özellik1**' nin yanındaki **Etkinleştir** düğmesini seçin.

     `FeatureActivated` işlevinde çağrılan boşta döngüsü nedeniyle bunu yaptığınızda bir duraklama olur.

4. **Hızlı Başlat** çubuğunda **listeler** ' i seçin ve ardından **listeler** listesinden **Duyurular**' ı seçin.

     Özelliğin etkinleştirildiğini belirten listeye yeni bir duyuru eklendiğini unutmayın.

5. SharePoint sitesini kapatın.

     SharePoint 'i kapattıktan sonra, profil oluşturucu bir örnek profil oluşturma raporu oluşturup görüntüler ve profil **Test** projesinin klasörüne bir. vsp dosyası olarak kaydeder.

## <a name="view-and-interpret-the-profile-results"></a>Profil sonuçlarını görüntüleme ve yorumlama
 Artık SharePoint uygulamasını çalıştırıp profili oluşturup, test sonuçlarını görüntüleyin.

### <a name="to-view-and-interpret-the-profile-results"></a>Profil sonuçlarını görüntülemek ve yorumlamak için

1. Örnek profil oluşturma raporunun **en bireysel Işini yapan işlevlerde** `TimeCounter` listenin en üstüne yaklaşdığına dikkat edin.

     Bu konum, `TimeCounter` en yüksek örnek sayısı olan işlevlerden biri olduğunu gösterir, yani uygulamada en büyük performans sorunları bu kadar olur. Bu durum, özellikle de tanıtım amaçlarıyla bu şekilde tasarlandığı için ortaya çıkarmaz.

2. **En bireysel Işleri yapan işlevlerde** , `ProcessRequest` işlevine ait maliyet dağılımını göstermek için `ProcessRequest` bağlantısını seçin.

     `ProcessRequest`için **çağrılan işlevler** bölümünde, **FeatureActiviated** işlevinin en pahalı çağrılan işlev olarak listelendiğine dikkat edin.

3. **Çağrılan işlevler** bölümünde **FeatureActivated** düğmesini seçin.

     **FeatureActivated**için **çağrılan işlevler** bölümünde, `TimeCounter` işlevi en pahalı çağrılan işlev olarak listelenir. **Işlev kodu görünüm** bölmesinde, vurgulanan kod (`TimeCounter`) etkin değildir ve düzeltmenin nerede gerekli olduğunu gösterir.

4. Örnek profil oluşturma raporunu kapatın.

     Raporu dilediğiniz zaman yeniden görüntülemek için, **Performans Gezgini** penceresinde. vsp dosyasını açın.

## <a name="fix-the-code-and-reprofile-the-application"></a>Kodu düzelme ve uygulamayı yeniden profili oluşturma
 Artık SharePoint uygulamasındaki etkin nokta işlevi belirlendi, bunu düzeltemedi.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Kodu onarmak ve uygulamayı yeniden profili eklemek için

1. Özellik olay alıcısı kodunda, `FeatureActivated` `TimeCounter` yöntemi çağrısını, çağırılmasını engellemek için not edin.

2. Projeyi kaydedin.

3. **Performans Gezgini**' de, hedefler klasörünü açın ve ardından **ProfileTest** düğümünü seçin.

4. **Performans Gezgini** araç çubuğunda, **Eylemler** sekmesinde **profil oluşturmayı Başlat** düğmesini seçin.

     Uygulamanın yeniden profilini oluşturmadan önce profil oluşturma özelliklerinden herhangi birini değiştirmek istiyorsanız, bunun yerine **performansı Başlat Sihirbazı** düğmesini seçin.

5. Bu konunun önceki bölümünde yer aldığı **SharePoint uygulamasını çalıştırma** bölümündeki yönergeleri izleyin.

     Boşta döngüsü çağrısının ortadan kaldırıldığına göre özelliğin çok daha hızlı bir şekilde etkinleştirilmesi gerekir. Örnek profil oluşturma raporu bunu yansıtmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](/visualstudio/profiling/performance-explorer)
- [Performans Oturumuna Genel Bakış](/visualstudio/profiling/performance-session-overview)
- [Performans Profili Oluşturma Başlangıç Kılavuzu](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Visual Studio Profiler ile uygulama darboğazlarını bulma](https://msdn.microsoft.com/magazine/cc337887.aspx)
