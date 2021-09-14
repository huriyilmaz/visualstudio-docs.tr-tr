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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 03c4089706d15178425c193f9dcabd4a592db2b0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726752"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>İzlenecek yol: SharePoint için OData görüntüleyen bir Silverlight Web Bölümü oluşturma
  SharePoint 2010, liste verilerini OData aracılığıyla gösterir. SharePoint, OData hizmeti, reststaservıce listdata. svc tarafından uygulanır. bu izlenecek yol, bir Silverlight uygulaması barındıran SharePoint web bölümünün nasıl oluşturulacağını gösterir. Silverlight uygulaması, listdata. svc kullanarak SharePoint duyuru listesi bilgilerini görüntüler. daha fazla bilgi için bkz. [SharePoint Foundation REST arabirimi](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) ve [açık veri protokolü](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri ve SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight uygulaması ve Silverlight Web Bölümü oluşturma
 İlk olarak, Visual Studio bir Silverlight uygulaması oluşturun. Silverlight uygulaması, listdata. svc hizmetini kullanarak SharePoint duyurular listesinden veri alır.

> [!NOTE]
> 4,0 ' dan önceki Silverlight sürümü, SharePoint listesi verilerine başvurmak için gereken arabirimleri desteklemez.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight uygulaması ve Silverlight Web bölümü oluşturmak için

1.   >    >  **yeni Project** iletişim kutusunu göstermek için menü çubuğunda dosya yeni **Project** öğesini seçin.

2. **Visual C#** veya **Visual Basic** altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. şablonlar bölmesinde **SharePoint 2010 Silverlight Web bölümü** şablonunu seçin.

4. **Ad** kutusuna **SLWebPartTest** girin ve **Tamam** düğmesini seçin.

    **SharePoint özelleştirme sihirbazı** iletişim kutusu görüntülenir.

5. **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımında hata ayıklamak istediğiniz SharePoint sunucusu sitesinin URL 'sini girin veya varsayılan konumu (http://<em>sistem adı</em>/) kullanın.

6. **bu SharePoint çözümü için güven düzeyi nedir?** bölümünde, **grup çözümü olarak dağıt** seçenek düğmesini seçin.

    Bu örnek, bir Grup çözümü kullanıyor olsa da, Silverlight Web Bölümü projeleri grup veya Korumalı çözüm olarak dağıtılabilir. Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Silverlight Yapılandırma bilgilerini belirtin** sayfasının **Silverlight Web bölümünü nasıl ilişkilendirmek** istiyorsunuz sayfasında, **Yeni bir Silverlight projesi oluştur ve bunu Web Bölümü ile ilişkilendir** seçenek düğmesini seçin.

8. **adı** **slapplication** olarak değiştirin, **dili** **Visual Basic** veya **Visual C#** olarak ayarlayın ve ardından **silverlight sürümünü** **silverlight 4,0** olarak ayarlayın.

9. **Son** düğmesini seçin. Projeler **Çözüm Gezgini** görüntülenir.

     Çözüm iki proje içerir: bir Silverlight uygulaması ve bir Silverlight Web bölümü. silverlight uygulaması SharePoint verileri alır ve görüntüler ve silverlight web bölümü silverlight uygulamasını barındırır ve bunu SharePoint görüntülemenize olanak sağlar.

## <a name="customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirme
 Silverlight uygulamasına kod ve tasarım öğeleri ekleyin.

#### <a name="to-customize-the-silverlight-application"></a>Silverlight uygulamasını özelleştirmek için

1. Sisteme bir derleme başvurusu ekleyin. Windows. Silverlight uygulamasındaki veriler. Daha fazla bilgi için bkz. [nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](/previous-versions/wkze6zky(v=vs.140)).

2. **Çözüm Gezgini**' de, **Başvurular** için kısayol menüsünü açın ve **hizmet başvurusu Ekle** öğesini seçin.

    > [!NOTE]
    > Visual Basic kullanıyorsanız, **başvurular** düğümünü görüntülemek için **Çözüm Gezgini** en üstündeki **tüm dosyaları göster** simgesini seçmeniz gerekir.

3. **Hizmet Başvurusu Ekle** iletişim kutusunun adres kutusuna SharePoint sitenizin URL 'sini girin (gibi) **http://MySPSite** ve sonra **git** düğmesini seçin.

     Silverlight, SharePoint OData hizmeti listdata. svc ' yi bulduktan sonra adresi tam hizmet URL 'si ile değiştirir. Bu örnek için http://myserver olur http://myserver/_vti_bin/ListData.svc .

4. Hizmet başvurusunu projeye eklemek için **Tamam** düğmesini seçin ve varsayılan hizmet adı olan ServiceReference1 ' ı kullanın.

5. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

6. SharePoint hizmetine göre projeye yeni bir veri kaynağı ekleyin. bunu yapmak için, menü çubuğunda   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçin.

     **veri kaynakları** penceresi, görevler, duyurular ve takvim gibi tüm kullanılabilir SharePoint listesi verilerini gösterir.

7. Duyurular listesi verilerini Silverlight uygulamasına ekleyin. "Duyurular" öğesini **veri kaynakları** penceresinden Silverlight Tasarımcısı üzerine sürükleyebilirsiniz.

     bu, SharePoint sitesinin duyurular listesine dayalı bir kılavuz denetimi oluşturur.

8. Kılavuz denetimini Silverlight sayfasına sığacak şekilde yeniden boyutlandırın.

9. mainpage. xaml kod dosyasında (Visual C# için *mainpage. xaml. cs* veya Visual Basic için *mainpage. xaml. vb* ), aşağıdaki ad alanı başvurularını ekleyin.

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

     *ServerName* yer tutucusunu SharePoint çalıştıran sunucunuzun adı ile değiştirdiğinizden emin olun.

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

2. **özellikler** penceresinde **SharePoint** sekmesini seçin.

3. Henüz seçili değilse, **Silverlight hata ayıklamasını etkinleştir (betik hata ayıklaması yerine)** onay kutusunu seçin.

4. Projeyi kaydedin.

## <a name="test-the-silverlight-web-part"></a>Silverlight Web bölümünü test etme
 SharePoint liste verilerini düzgün bir şekilde görüntülediğinden emin olmak için SharePoint yeni Silverlight web bölümünü Test edin.

#### <a name="to-test-the-silverlight-web-part"></a>Silverlight Web bölümünü test etmek için

1. SharePoint çözümünü derlemek ve çalıştırmak için **F5** tuşunu seçin.

2. SharePoint, **Site eylemleri** menüsünde **yeni sayfa**' yı seçin.

3. **Yeni sayfa** Iletişim kutusunda **SL Web Bölümü testi** gibi bir başlık girin ve **Oluştur** düğmesini seçin.

4. Sayfa Tasarımcısı ' nda, **Düzen araçları** sekmesinde, **Ekle**' yi seçin.

5. Sekme şeridinde **Web Bölümü**' nu seçin.

6. **Kategoriler** kutusunda **özel** klasörü seçin.

7. **Web Bölümleri** listesinde, Silverlight web bölümünü seçin ve sonra web bölümünü tasarımcıya eklemek için **ekle** düğmesini seçin.

8. İstediğiniz Web sayfasına yapılan eklemeleri tamamladıktan sonra, **sayfa** sekmesini seçin ve ardından araç çubuğundaki **& kapat** düğmesini seçin.

     Silverlight web bölümü artık SharePoint sitesinden bildiri verileri görüntülüyor olmalıdır. Varsayılan olarak, sayfa SharePoint site sayfaları listesinde depolanır.

    > [!NOTE]
    > Etki alanları arasında Silverlight 'taki verilere erişirken, Web uygulamalarından yararlanmak için kullanılabilecek güvenlik açıklarına karşı Silverlight koruyucuları. Silverlight 'taki uzak verilere erişirken sorunlarla karşılaşırsanız bkz. [bir hizmeti etki alanı sınırları genelinde kullanılabilir hale getirme](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)