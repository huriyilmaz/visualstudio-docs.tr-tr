---
title: SharePoint için OData görüntüleyen Silverlight Web Bölümü oluşturma
titleSuffix: ''
description: SharePoint için OData görüntüleyen bir Silverlight Web bölümü oluşturun. Silverlight uygulamasını özelleştirin ve Silverlight Web bölümünü değiştirin ve test edin.
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
ms.workload:
- office
ms.openlocfilehash: ee35ecc9cfa49f445e93677df9d2917150bc1e74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847836"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>İzlenecek yol: SharePoint için OData görüntüleyen bir Silverlight Web Bölümü oluşturma
  SharePoint 2010, liste verilerini OData aracılığıyla gösterir. SharePoint 'te OData hizmeti, Reststaservıce ListData. svc tarafından uygulanır. Bu izlenecek yol, bir Silverlight uygulaması barındıran SharePoint Web Bölümü oluşturmayı gösterir. Silverlight uygulaması, ListData. svc kullanarak SharePoint duyuru listesi bilgilerini görüntüler. Daha fazla bilgi için bkz. [SharePoint FOUNDATION Rest arabirimi](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) ve [Açık Veri Protokolü](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Microsoft Windows ve SharePoint sürümleri.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight uygulaması ve Silverlight Web Bölümü oluşturma
 İlk olarak, Visual Studio 'da bir Silverlight uygulaması oluşturun. Silverlight uygulaması, ListData. svc hizmetini kullanarak SharePoint Duyurular listesinden veri alır.

> [!NOTE]
> 4,0 ' dan önceki Silverlight sürümü, SharePoint listesi verilerine başvurmak için gereken arabirimleri desteklemez.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight uygulaması ve Silverlight Web bölümü oluşturmak için

1.   >    >  **Yeni proje** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Proje** ' yi seçin.

2. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Şablonlar bölmesinde, **SharePoint 2010 Silverlight Web Bölümü** şablonunu seçin.

4. **Ad** kutusuna **SLWebPartTest** girin ve **Tamam** düğmesini seçin.

    **SharePoint Özelleştirme Sihirbazı** iletişim kutusu görüntülenir.

5. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımında hata ayıklamak istediğiniz SharePoint Server sitesinin URL 'sini girin veya varsayılan konumu (http://<em>sistem adı</em>/) kullanın.

6. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, **Grup çözümü olarak dağıt** seçenek düğmesini seçin.

    Bu örnek, bir Grup çözümü kullanıyor olsa da, Silverlight Web Bölümü projeleri grup veya Korumalı çözüm olarak dağıtılabilir. Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Silverlight Yapılandırma bilgilerini belirtin** sayfasının **Silverlight Web bölümünü nasıl ilişkilendirmek** istiyorsunuz sayfasında, **Yeni bir Silverlight projesi oluştur ve bunu Web Bölümü ile ilişkilendir** seçenek düğmesini seçin.

8. **Adı** **SLApplication** olarak değiştirin, **dili** **Visual Basic** veya **Visual C#** olarak ayarlayın ve ardından **Silverlight sürümünü** **Silverlight 4,0** olarak ayarlayın.

9. **Son** düğmesini seçin. Projeler **Çözüm Gezgini** görüntülenir.

     Çözüm iki proje içerir: bir Silverlight uygulaması ve bir Silverlight Web bölümü. Silverlight uygulaması SharePoint 'ten liste verilerini alır ve görüntüler ve Silverlight Web Bölümü Silverlight uygulamasını barındırır ve bu sayede SharePoint 'te görüntülemenize olanak sağlar.

## <a name="customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirme
 Silverlight uygulamasına kod ve tasarım öğeleri ekleyin.

#### <a name="to-customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirmek için

1. Silverlight uygulamasındaki System. Windows. Data öğesine bir derleme başvurusu ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](/previous-versions/wkze6zky(v=vs.140)).

2. **Çözüm Gezgini**' de, **Başvurular** için kısayol menüsünü açın ve **hizmet başvurusu Ekle** öğesini seçin.

    > [!NOTE]
    > Visual Basic kullanıyorsanız, **Başvurular** düğümünü görüntülemek için **Çözüm Gezgini** en üstündeki **tüm dosyaları göster** simgesini seçmeniz gerekir.

3. **Hizmet başvurusu Ekle** Iletişim kutusunun Adres kutusuna SHAREPOINT sitenizin URL 'sini girin (gibi) **http://MySPSite** ve sonra **Git** düğmesini seçin.

     Silverlight, SharePoint OData hizmeti ListData. svc ' yi bulduktan sonra adresi tam hizmet URL 'SI ile değiştirir. Bu örnek için http://myserver olur http://myserver/_vti_bin/ListData.svc .

4. Hizmet başvurusunu projeye eklemek için **Tamam** düğmesini seçin ve varsayılan hizmet adı olan ServiceReference1 ' ı kullanın.

5. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

6. SharePoint hizmetine göre projeye yeni bir veri kaynağı ekleyin. Bunu yapmak için, menü çubuğunda   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçin.

     **Veri kaynakları** penceresi, görevler, Duyurular ve takvim gibi tüm kullanılabilir SharePoint listesi verilerini gösterir.

7. Duyurular listesi verilerini Silverlight uygulamasına ekleyin. "Duyurular" öğesini **veri kaynakları** penceresinden Silverlight Tasarımcısı üzerine sürükleyebilirsiniz.

     Bu, SharePoint sitesinin Duyurular listesine dayalı bir kılavuz denetimi oluşturur.

8. Kılavuz denetimini Silverlight sayfasına sığacak şekilde yeniden boyutlandırın.

9. MainPage. xaml kod dosyasında (*MainPage.xaml.cs* for Visual C# veya *MainPage. xaml. vb* için Visual Basic), aşağıdaki ad alanı başvurularını ekleyin.

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

10. Aşağıdaki değişken bildirimlerini sınıfının üst kısmına ekleyin.

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

11. `UserControl_Loaded`Yordamı aşağıdaki ile değiştirin.

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

     *ServerName* yer tutucusunu SharePoint çalıştıran sunucunuzun adıyla değiştirdiğinizden emin olun.

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

## <a name="modify-the-silverlight-web-part"></a>Silverlight Web bölümünü değiştirme
 Silverlight hata ayıklamasını etkinleştirmek için Silverlight Web Bölümü projesindeki bir özelliği değiştirin.

#### <a name="to-modify-the-silverlight-web-part"></a>Silverlight Web bölümünü değiştirmek için

1. Silverlight Web Bölümü projesi (**SLWebPartTest**) için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **Özellikler** penceresinde **SharePoint** sekmesini seçin.

3. Henüz seçili değilse, **Silverlight hata ayıklamasını etkinleştir (betik hata ayıklaması yerine)** onay kutusunu seçin.

4. Projeyi kaydedin.

## <a name="test-the-silverlight-web-part"></a>Silverlight Web bölümünü test etme
 SharePoint liste verilerini düzgün bir şekilde görüntülediğinden emin olmak için SharePoint 'te yeni Silverlight Web bölümünü sınayın.

#### <a name="to-test-the-silverlight-web-part"></a>Silverlight Web bölümünü test etmek için

1. SharePoint çözümünü derlemek ve çalıştırmak için **F5** tuşunu seçin.

2. SharePoint 'te, **Site eylemleri** menüsünde **Yeni sayfa**' yı seçin.

3. **Yeni sayfa** Iletişim kutusunda **SL Web Bölümü testi** gibi bir başlık girin ve **Oluştur** düğmesini seçin.

4. Sayfa Tasarımcısı ' nda, **Düzen araçları** sekmesinde, **Ekle**' yi seçin.

5. Sekme şeridinde **Web Bölümü**' nu seçin.

6. **Kategoriler** kutusunda **özel** klasörü seçin.

7. **Web bölümleri** listesinde, Silverlight Web bölümünü seçin ve sonra Web bölümünü tasarımcıya eklemek için **Ekle** düğmesini seçin.

8. İstediğiniz Web sayfasına yapılan eklemeleri tamamladıktan sonra, **sayfa** sekmesini seçin ve ardından araç çubuğundaki **& kapat** düğmesini seçin.

     Silverlight Web Bölümü artık SharePoint sitesinden bildiri verileri görüntülüyor olmalıdır. Varsayılan olarak, sayfa SharePoint 'teki site sayfaları listesinde depolanır.

    > [!NOTE]
    > Etki alanları arasında Silverlight 'taki verilere erişirken, Web uygulamalarından yararlanmak için kullanılabilecek güvenlik açıklarına karşı Silverlight koruyucuları. Silverlight 'taki uzak verilere erişirken sorunlarla karşılaşırsanız bkz. [bir hizmeti etki alanı sınırları genelinde kullanılabilir hale getirme](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)