---
title: SharePoint için OData'nın görüntüleniyor Silverlight web SharePoint
titleSuffix: ''
description: SharePoint için OData görüntüleyen bir Silverlight web SharePoint. Silverlight uygulamasını özelleştirin ve Silverlight web bölümünü değiştirerek test edin.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 03c4089706d15178425c193f9dcabd4a592db2b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148811"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Adım adım kılavuz: SharePoint için OData görüntüleyen bir Silverlight web SharePoint
  SharePoint 2010, liste verilerini OData ile ortaya çıkarır. Bu SharePoint, OData hizmeti RESTful hizmeti ListData.svc tarafından uygulanır. Bu kılavuzda, Silverlight uygulamasını barındıran SharePoint web bölümü oluşturma adımlarını gösterir. Silverlight uygulaması, ListData.svc SharePoint Duyuru listesi bilgilerini görüntüler. Daha fazla bilgi için [bkz. SharePoint Foundation REST Arabirimi](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) ve Açık Veri [Protokolü.](https://www.odata.org/)

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows ve SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight uygulaması ve Silverlight web bölümü oluşturma
 İlk olarak, Visual Studio'da bir Silverlight uygulaması oluşturun. Silverlight uygulaması, ListData.svc SharePoint Duyurular listesinden verileri alıyor.

> [!NOTE]
> 4.0'dan önceki Silverlight sürümleri, liste verilerine başvurmak için SharePoint arabirimleri desteklemez.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight uygulaması ve Silverlight web bölümü oluşturmak için

1. Yeni dosya iletişim kutusunu görüntülemek **için**  >    >  **menü Project** Dosya **Yeni Dosya'Project** seçin.

2. **Visual C#** **SharePoint** altındaki Visual Basic düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

3. Şablonlar bölmesinde, **SharePoint 2010 Silverlight Web Bölümü şablonunu** seçin.

4. Ad **kutusuna** **SLWebPartTest yazın** ve Tamam **düğmesini** seçin.

    SharePoint **Özelleştirme Sihirbazı** iletişim kutusu görüntülenir.

5. Hata **ayıklama için site** ve güvenlik düzeyini belirtin sayfasında, site tanımında hata ayıklamak istediğiniz SharePoint sunucusu sitesinin URL'sini girin veya varsayılan konumu (http://<em>sistem adı</em>/) kullanın.

6. Bu **çözüm için güven düzeyi SharePoint** grup çözümü olarak **dağıt seçeneğini** belirleyin.

    Bu örnek bir grup çözümü kullanıyor olsa da Silverlight web bölümü projeleri grup veya korumalı alan çözümleri olarak dağıtılabilir. Korumalı alanlı çözümler ve grup çözümleri hakkında daha fazla bilgi için [bkz. Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

7. Silverlight **Yapılandırma Bilgilerini Belirtin** sayfasının **Silverlight** Web Bölümü'sini nasıl ilişkilendirmek istediğiniz bölümünde Yeni Silverlight projesi oluştur'a tıklayın ve web bölümü **seçeneği düğmesiyle** ilişkilendirmek için tıklayın.

8. **Ad'ı** **SLApplication** olarak, **Dil'i** **Visual Basic** **veya Visual C#** olarak ayarlayın ve **Silverlight** Sürümü'ü **Silverlight 4.0 olarak ayarlayın.**

9. Son **düğmesini** seçin. Projeler, içinde **Çözüm Gezgini.**

     Çözüm iki proje içerir: Silverlight uygulaması ve Silverlight web bölümü. Silverlight uygulaması, SharePoint'den liste verilerini alın ve görüntüler ve Silverlight web bölümü Silverlight uygulamasını barındırarak bu uygulamayı SharePoint.

## <a name="customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirme
 Silverlight uygulamasına kod ve tasarım öğeleri ekleyin.

#### <a name="to-customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirmek için

1. System'e bir derleme başvurusu ekleyin. Windows. Silverlight uygulamasındaki veriler. Daha fazla bilgi için, [bkz. How to: Add References By Using References (Başvuru](/previous-versions/wkze6zky(v=vs.140))Ekle İletişim Kutusunu Kullanarak Başvuru Ekleme veya Kaldırma).

2. Bu **Çözüm Gezgini,** Başvurular kısayol menüsünü **açın ve** sonra Datele'Hizmet Başvurusu Ekle. 

    > [!NOTE]
    > Visual Basic kullanıyorsanız, Başvurular düğümünü görüntülemek  için tüm dosyaların üst **Çözüm Gezgini** **simgesini seçmeniz** gerekir.

3. Hizmet Başvurusu Ekle iletişim **kutusunun** Adres kutusuna SharePoint sitenizin URL'sini girin ve ardından Git **http://MySPSite** **düğmesini** seçin.

     Silverlight, OData SharePoint ListData.svc'yi bularak adresi tam hizmet URL'si ile değiştirir. Bu örnekte http://myserver http://myserver/_vti_bin/ListData.svc olur.

4. Projeye **hizmet başvurusu** eklemek için Tamam düğmesini seçin ve varsayılan hizmet adı olan ServiceReference1'i kullanın.

5. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

6. SharePoint hizmetine göre projeye yeni bir veri SharePoint ekleyin. Bunu yapmak için menü çubuğunda Diğer Verileri **Görüntüle'yi**  >  **Windows**  >  **seçin.**

     Veri **Kaynakları penceresinde** Görevler, Duyurular ve SharePoint gibi tüm kullanılabilir veri listesi verileri gösterilir.

7. Duyurular listesi verilerini Silverlight uygulamasına ekleyin. "Duyurular"ı Veri Kaynakları **penceresinden** Silverlight tasarımcısına sürükleyebilirsiniz.

     Bu, sitenin Duyurular listesine SharePoint bir kılavuz denetimi oluşturur.

8. Kılavuz denetimi, Silverlight sayfasına sığacak şekilde yeniden boyutlandırılır.

9. MainPage.xaml kod dosyasında ( Visual C# için *MainPage.xaml.cs* veya Visual Basic için *MainPage.xaml.vb),* aşağıdaki ad alanı başvurularını ekleyin.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Sınıfının en üstüne aşağıdaki değişken bildirimlerini ekleyin.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. yordamını `UserControl_Loaded` aşağıdakiyle değiştirin.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     *ServerName* yer tutucusunu, sunucuyu çalıştıran sunucunun adıyla SharePoint.

12. Aşağıdaki hata işleme yordamını ekleyin.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Silverlight web bölümünü değiştirme
 Silverlight hata ayıklamayı etkinleştirmek için Silverlight web bölümü projesinde bir özelliği değiştirme.

#### <a name="to-modify-the-silverlight-web-part"></a>Silverlight web bölümünü değiştirmek için

1. Silverlight web bölümü projesinin kısayol menüsünü açın (**SLWebPartTest**) ve ardından Özellikler'i **seçin.**

2. Özellikler **penceresinde** SharePoint **seçin.**

3. Henüz seçilmemişse Silverlight hata ayıklamasını etkinleştir **(Betik hata ayıklaması yerine) onay** kutusunu işaretleyin.

4. Projeyi kaydedin.

## <a name="test-the-silverlight-web-part"></a>Silverlight web bölümünü test edin
 Yeni Silverlight web bölümünü SharePoint liste verilerini düzgün bir şekilde SharePoint test edin.

#### <a name="to-test-the-silverlight-web-part"></a>Silverlight web bölümünü test etmek için

1. Yeni **çözüm oluşturmak ve** çalıştırmak için F5 SharePoint seçin.

2. Bu SharePoint Site Eylemleri menüsünde **Yeni** Sayfa'ya **tıklayın.**

3. Yeni **Sayfa iletişim** kutusunda **SL Web** Bölümü Testi gibi bir başlık girin ve oluştur **düğmesini** seçin.

4. Sayfa tasarımcısının Düzenleme Araçları sekmesinde **Ekle'yi** **seçin.**

5. Sekme şeridinin Web **Bölümü'sini seçin.**

6. Kategoriler **kutusunda** Özel **klasörünü** seçin.

7. Web **Web Bölümleri** Silverlight web bölümünü seçin ve ardından Ekle  düğmesini seçarak web bölümünü tasarımcıya ekleyin.

8. Web sayfasına istediğiniz tüm eklemeleri yaptıktan sonra Sayfa sekmesini  seçin ve araç çubuğundaki Kaydet **& Kapat** düğmesini seçin.

     Silverlight web bölümü artık web sitesinden Duyuru verilerini SharePoint gerekir. Varsayılan olarak sayfa, sitenin Site Sayfaları listesinde SharePoint.

    > [!NOTE]
    > Silverlight'ta etki alanları arasında verilere erişirken Silverlight, web uygulamalarından yararlanmak için kullanılan güvenlik açıklarına karşı koruma sağlar. Silverlight'ta uzak verilere erişirken sorunlarla karşılaşırsanız, bkz. Bir Hizmeti [Etki Alanı Sınırları Arasında Kullanılabilir Yapma.](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95))

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Çözüm paketlerini dağıtma, SharePoint ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)