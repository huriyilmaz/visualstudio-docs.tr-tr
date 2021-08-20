---
title: 'Adım adım kılavuz: SharePoint Application | Microsoft Docs'
description: Bu kılavuzda, bir Visual Studio uygulamasının performansını iyileştirmek için SharePoint kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 555f805203e7f0f4097d97d0950d85be859b1c1e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148707"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Adım adım kılavuz: SharePoint profili oluşturma
  Bu kılavuz, bir uygulamanın performansını iyileştirmek için Visual Studio profil oluşturma araçlarının nasıl SharePoint gösterir. Örnek uygulama, SharePoint olay alıcısının performansını düşüren bir boşta döngü içeren bir özellik olayı alıcısıdır. Profil Visual Studio, projenin sık kullanılan yol olarak da bilinen en pahalı (en yavaş performans gösteren) bölümünü bulup ortadan *kaldırmaya olanak sağlar.*

 Bu kılavuz aşağıdaki görevleri gösterir:

- [Özellik ve özellik olay alıcısı ekleyin.](#add-a-feature-and-feature-event-receiver)

- [SharePoint uygulamasını yapılandırma ve dağıtma.](#configure-and-deploy-the-sharepoint-application)

- [SharePoint uygulamasını çalıştırın.](#run-the-sharepoint-application)

- [Profil sonuçlarını görüntüleme ve yorumlama.](#view-and-interpret-the-profile-results)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows ve SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>SharePoint oluşturma
 İlk olarak bir SharePoint oluşturun.

### <a name="to-create-a-sharepoint-project"></a>Bir SharePoint oluşturmak için

1. Yeni dosya iletişim kutusunu görüntülemek **için**  >    >  **Project** Yeni Dosya'Project seçin. 

2. Visual **C# SharePoint** altındaki  Visual Basic düğümünü **genişletin** ve **ardından 2010 düğümünü** seçin.

3. Şablonlar bölmesinde, SharePoint **2010** Project seçin.

4. Ad **kutusuna** **ProfileTest yazın ve** tamam **düğmesini** seçin.

    SharePoint **Özelleştirme Sihirbazı** görüntülenir.

5. Hata **ayıklama için site** ve güvenlik düzeyini belirtin sayfasında, site tanımında hata ayıklamak istediğiniz SharePoint sunucusu sitesinin URL'sini girin veya varsayılan konumu (http://<em>sistem adı</em>/) kullanın.

6. Bu **çözüm için güven düzeyi nedir SharePoint** grup çözümü olarak dağıt **seçeneğini** belirleyin.

    Şu anda yalnızca grup çözümlerinin profilini ebilirsiniz. Korumalı alanlı çözümler ve grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

7. Son **düğmesini** seçin. Proje, içinde **Çözüm Gezgini.**

## <a name="add-a-feature-and-feature-event-receiver"></a>Özellik ve özellik olay alıcısı ekleme
 Ardından, projeye özellik için bir olay alıcısı ile birlikte bir özellik ekleyin. Bu olay alıcısı profili oluşturmak için gereken kodu içerir.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Özellik ve özellik olay alıcısı eklemek için

1. Bu **Çözüm Gezgini** Özellikler düğümünün kısayol menüsünü  açın, Özellik Ekle'yi **seçin** ve adı varsayılan değer olan **Özellik1'de bırakın.**

2. Bu **Çözüm Gezgini** **Özellik1** kısayol menüsünü açın ve Olay Alıcısı **Ekle'yi seçin.**

     Bu, çeşitli açıklamalı olay işleyicileriyle özelliğe bir kod dosyası ekler ve dosyayı düzenlemek için açar.

3. Olay alıcısı sınıfında aşağıdaki değişken bildirimlerini ekleyin.

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

4. yordamını `FeatureActivated` aşağıdaki kodla değiştirin.

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

5. Yordamın altına aşağıdaki yordamı `FeatureActivated` ekleyin.

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

6. Bu **Çözüm Gezgini** proje kısayol menüsünü açın (**ProfileTest**) ve ardından Özellikler'i **seçin.**

7. Özellikler **iletişim** kutusunda, SharePoint **seçin.**

8. Etkin Dağıtım **Yapılandırması listesinde Etkinleştirme** **Yok'a tıklayın.**

     Bu dağıtım yapılandırmasının seçerek özelliği daha sonra el ile etkinleştirmenizi SharePoint.

9. Projeyi kaydedin.

## <a name="configure-and-deploy-the-sharepoint-application"></a>SharePoint uygulamasını yapılandırma ve dağıtma
 Artık SharePoint hazır olduğunu, yapılandırarak SharePoint dağıtın.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>SharePoint uygulamasını yapılandırmak ve dağıtmak için

1. Analiz menüsünde **Performans** Başlatma **Sihirbazı'nı seçin.**

2. Performans Sihirbazı'nın **ilk sayfasında,** profil oluşturma yöntemini CPU örneklemesi **olarak bırakın ve** Sonraki **düğmesini** seçin.

     Diğer profil oluşturma yöntemleri daha gelişmiş profil oluşturma durumlarında kullanılabilir. Daha fazla bilgi için [bkz. Performans Toplama Yöntemlerini Anlama.](../profiling/understanding-performance-collection-methods.md)

3. Performans Sihirbazı'nın iki **sayfasında** profil hedefini **ProfilTest** olarak bırakın ve Sonraki **düğmesini** seçin.

     Bir çözümde birden çok proje varsa, bunlar bu listede görünür.

4. Performans Sihirbazı'nın üçüncü **sayfasında** Katman Etkileşimi **Profili Oluşturmayı** Etkinleştir onay kutusunun işaretini kaldırın ve ardından Sonraki **düğmesini** seçin.

     Katman Etkileşim Profili Oluşturma (TIP) özelliği, veritabanlarını sorgulatan uygulamaların performansını ölçmek ve bir web sayfasının kaç kez istenebilir olduğunu göstermek için yararlıdır. Bu örnek için bu veriler gerekli değildir, bu özelliği etkinleştirmeziz.

5. Performans Sihirbazı'nın dördüncü **sayfasında,** Sihirbaz tamam olduktan sonra **profil** oluşturmayı başlat onay kutusunu seçili bırakın ve ardından Son **düğmesini** seçin.

     Sihirbaz, sunucuda uygulama profili oluşturmayı sağlar, Performans Gezgini **penceresini** görüntüler ve ardından uygulamanın SharePoint çalıştırır.

## <a name="run-the-sharepoint-application"></a>SharePoint çalıştırma
 SharePoint özelliğini etkinleştirerek çalıştıracak olay `FeatureActivation` kodunu tetikler.

### <a name="to-run-the-sharepoint-application"></a>SharePoint çalıştırmak için

1. Bu SharePoint Site Eylemleri menüsünü **açın ve Site** Eylemleri'Ayarlar. 

2. Site **Eylemleri listesinde** Site özelliklerini yönet **bağlantısını** seçin.

3. Özellikler **listesinde ProfilTest** **Özelliği1'in** yanındaki **Etkinleştir düğmesini seçin.**

     Bunu yapmak için işlevde boştaki döngü çağrıldıktan sonra bir duraklama `FeatureActivated` olur.

4. Yeni **Hızlı Başlat** Listeler'i **ve** ardından Listeler listesinde **Duyurular'ı** **seçin.**

     Özelliğin etkinleştirildikten sonra listeye yeni bir duyuru eklenmiştir.

5. SharePoint kapatın.

     Profil oluşturma SharePoint profil oluşturma raporu oluşturur, görüntüler ve **ProfileTest** projesinin klasörüne bir .vsp dosyası olarak kaydeder.

## <a name="view-and-interpret-the-profile-results"></a>Profil sonuçlarını görüntüleme ve yorumlama
 Artık uygulamanın profilini çalıştırdı ve SharePoint test sonuçlarını görüntüle.

### <a name="to-view-and-interpret-the-profile-results"></a>Profil sonuçlarını görüntülemek ve yorumlamak için

1. Örnek **Profil Oluşturma Raporunun En Bireysel** İş Yapan İşlevler bölümünde listenin en üstüne `TimeCounter` yakın olduğunu fark edin.

     Bu konum, en fazla örnek sayısına sahip işlevlerden biri olduğunu, yani uygulamadaki en büyük performans sorunlarından `TimeCounter` biri olduğunu gösterir. Ancak bu durum şaşırtıcı değildir çünkü tanıtım amacıyla bu şekilde tasarlanmıştır.

2. İşlevlerin **En Bireysel İş Yapıyor bölümünde,** `ProcessRequest` işlevin maliyet dağılımını görüntülemek için bağlantıyı `ProcessRequest` seçin.

     için **Çağrılan işlevler** bölümünde `ProcessRequest` **FeatureActiviated işlevinin** en pahalı çağrılan işlev olarak listelenmiş olduğunu fark edin.

3. Çağrılı **işlevler bölümünde** **FeatureActivated düğmesini** seçin.

     **FeatureActivated** **işlevinin** Çağrılan işlevler bölümünde `TimeCounter` işlev, çağrılan en pahalı işlev olarak listelenir. İşlev **Kodu Görünümü bölmesinde** vurgulanan kod ( ) etkin noktadır ve `TimeCounter` düzeltmenin nerede gerekli olduğunu gösterir.

4. Örnek Profil Oluşturma Raporu'na kapatın.

     Raporu istediğiniz zaman yeniden görüntülemek için . vsp dosyasını Performans Gezgini **açın.**

## <a name="fix-the-code-and-reprofile-the-application"></a>Kodu düzeltme ve uygulamayı yeniden dosyala
 Artık SharePoint etkin nokta işlevi tanımlandı.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Kodu düzeltmek ve uygulamayı yeniden dosyala

1. Özellik olay alıcı kodunda, çağrılması `TimeCounter` önlemek için içinde `FeatureActivated` yönteminin çağrısını açıklama olarak girin.

2. Projeyi kaydedin.

3. Bu **Performans Gezgini,** Hedefler klasörünü açın ve ardından **ProfileTest düğümünü** seçin.

4. Yeni **Performans Gezgini** çubuğundaki **Eylemler** sekmesinde Profil Oluşturmayı Başlat **düğmesini** seçin.

     Uygulamayı yeniden oluşturmadan önce profil oluşturma özelliklerinden herhangi birini değiştirmek için Bunun yerine Performans Başlatma **Sihirbazı düğmesini** seçin.

5. Bu konu başlığında daha **önce SharePoint** Uygulama Çalıştırma bölümündeki yönergeleri izleyin.

     Boşta döngüye yapılan çağrı ortadan kaldırılmış olduktan sonra özelliğin çok daha hızlı bir şekilde etkinleştirmesi gerekir. Örnek Profil Oluşturma Raporu bunu yansıtacak.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Oturumuna Genel Bakış](../profiling/performance-session-overview.md)
- [Performans Profili Oluşturma için Yeni Başlayanlar Kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)
- [Visual Studio Profiler ile Uygulama Performans Sorunlarını Bulma](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler)