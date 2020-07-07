---
title: Tasarımcı kullanarak SharePoint için Web Bölümü oluşturma
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 732bd9fe3d34a768e0c6f71315f212c49bdf02af
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016392"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>İzlenecek yol: tasarımcı kullanarak SharePoint için bir Web Bölümü oluşturma

Bir SharePoint sitesi için Web bölümleri oluşturursanız, kullanıcılarınız bu sitedeki sayfaların içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak doğrudan değiştirebilir. Bu izlenecek yol, Visual Studio 'da SharePoint **Visual Web Bölümü** proje şablonunu kullanarak nasıl bir Web Bölümü oluşturulacağını gösterir.

Oluşturacağınız web bölümü bir aylık takvim görünümü ve sitedeki her takvim listesi için bir onay kutusu görüntüler. Kullanıcılar, onay kutularını seçerek aylık Takvim görünümüne hangi takvim listelerinin ekleneceğini belirtebilir.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- **Visual Web Bölümü** proje şablonunu kullanarak bir Web Bölümü oluşturma.
- Visual Studio 'da Visual Web Developer Designer kullanarak Web bölümünü tasarlama.
- Web bölümünde denetimlerin olaylarını işlemek için kod ekleme.
- SharePoint 'te Web bölümünü test etme.

    > [!NOTE]
    > Bilgisayarınız, aşağıdaki yönergelerde Visual Studio için Kullanıcı arabiriminin bazı öğeleri için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint sürümleri.

## <a name="create-a-web-part-project"></a>Web Bölümü projesi oluşturma

İlk olarak, **Visual Web Bölümü** proje şablonunu kullanarak bir Web Bölümü projesi oluşturun.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Yönetici olarak çalıştır** seçeneğini kullanarak başlayın.

2. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

     **Yeni Proje** iletişim kutusu görünür.

3. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic**altında **Office/SharePoint**' i genişletin ve **SharePoint çözümleri** kategorisini seçin.

4. Şablonlar listesinde, **SharePoint 2013-Visual Web Bölümü** şablonunu seçin ve ardından **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir. Bu Sihirbazı kullanarak, projede hata ayıklamak için kullanacağınız siteyi ve çözümün güven düzeyini belirtebilirsiniz.

5. **Bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, **Grup çözümü olarak dağıt** seçenek düğmesini seçin.

6. Varsayılan yerel SharePoint sitesini kabul etmek için **son** düğmesini seçin.

## <a name="designing-the-web-part"></a>Web bölümünü tasarlama

**Araç kutusundan** Visual Web Developer Designer 'ın yüzeyine denetimler ekleyerek Web bölümünü tasarlayın.

1. Görsel web geliştirici tasarımcısında, Tasarım görünümü geçiş yapmak için **Tasarım** sekmesini seçin.

2. Menü çubuğunda **Görünüm**  >  **araç kutusunu**seçin.

3. **Araç kutusunun** **Standart** düğümünde **CheckBoxList** denetimini seçin ve ardından aşağıdaki adımlardan birini gerçekleştirin:

    - **CheckBoxList** denetimi için kısayol menüsünü açın, **Kopyala**' yı seçin, tasarımcıda ilk satır için kısayol menüsünü açın ve ardından **Yapıştır**' ı seçin.

    - **Araç kutusundan** **CheckBoxList** denetimini sürükleyin ve denetimi tasarımcıda ilk satıra bağlayın.

4. Önceki adımı tekrarlayın, ancak bir düğmeyi tasarımcının sonraki satırına taşıyın.

5. Tasarımcıda **button1** düğmesini seçin.

6. Menü çubuğunda **View**  >  **Özellikler penceresini**görüntüle ' yi seçin.

     **Özellikler** penceresi açılır.

7. Düğmenin **metin** özelliğinde **Güncelleştir**' i girin.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Web bölümünde denetimlerin olaylarını işleme

Kullanıcının Ana Takvim görünümüne takvim eklemesini sağlayan kodu ekleyin.

1. Aşağıdaki adım kümelerinden birini uygulayın:

   - Tasarımcıda **Güncelleştir** düğmesine çift tıklayın.

   - **Güncelleştirme** düğmesinin **Özellikler** penceresinde, **Olaylar** düğmesini seçin. **Tıklama** özelliğinde **Button1_Click**girin ve Enter tuşunu seçin.

     Kullanıcı denetimi kod dosyası Kod Düzenleyicisi 'nde açılır ve `Button1_Click` olay işleyicisi görünür. Daha sonra bu olay işleyicisine kod ekleyeceksiniz.

2. Aşağıdaki deyimlerini Kullanıcı denetim kodu dosyasının en üstüne ekleyin.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Aşağıdaki kod satırını `VisualWebPart1` sınıfına ekleyin. Bu kod, bir aylık takvim görünümü denetimi bildirir.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. `Page_Load` `VisualWebPart1` Sınıfının yöntemini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Kullanıcı denetimine aylık takvim görünümü ekler.

   - Sitedeki her takvim listesi için bir onay kutusu ekler.

   - Takvim görünümünde görüntülenen her öğe türü için bir şablon belirtir.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. `Button1_Click` `VisualWebPart1` Sınıfının yöntemini aşağıdaki kodla değiştirin. Bu kod, seçili her takvimden öğeleri Ana Takvim görünümüne ekler.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Web bölümünü test etme

Projeyi çalıştırdığınızda, SharePoint sitesi açılır. Web Bölümü, SharePoint 'teki Web Bölümü galerisine otomatik olarak eklenir. Bu projeyi test etmek için aşağıdaki görevleri yerine getirmeniz gerekir:

- İki ayrı takvim listesindeki her birine bir olay ekleyin.
- Web bölümünü bir Web Bölümü sayfasına ekleyin.
- Aylık Takvim görünümüne dahil edilecek listeleri belirtin.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Sitedeki takvim listelerine olay eklemek için

1. Visual Studio 'da **F5** tuşunu seçin.

     SharePoint sitesi açılır ve [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] sayfada Hızlı Başlat çubuğu görünür.

2. Hızlı Başlat çubuğunda, **listeler**altında **Takvim** bağlantısını seçin.

     **Takvim** sayfası görüntülenir.

     Hızlı başlatma çubuğunda takvim bağlantısı yoksa, **site içeriği** bağlantısını seçin. Site Içeriği sayfasında bir **Takvim** öğesi gösterilmezse, bir tane oluşturun.

3. Takvim sayfasında bir gün seçin ve ardından bir olay eklemek için seçili gündeki **Ekle** bağlantısını seçin.

4. **Başlık** kutusuna **varsayılan takvime Olay**yazın ve ardından **Kaydet** düğmesini seçin.

5. **Site içeriği** bağlantısını seçin ve ardından **Uygulama Ekle** kutucuğunu seçin.

6. **Oluştur** sayfasında **Takvim** türünü seçin, takvimi adlandırın ve **Oluştur** düğmesini seçin.

7. Yeni takvime bir olay ekleyin, olay **olayını özel takvime**adlandırın ve **Kaydet** düğmesini seçin.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Web bölümünü bir Web Bölümü sayfasına eklemek için

1. **Site içeriği** sayfasında, **site sayfaları** klasörünü açın.

2. Şeritte, **dosyalar** sekmesini seçin, **Yeni belge** menüsünü açın ve ardından **Web Bölümü sayfası** komutunu seçin.

3. **Yeni Web Bölümü sayfası** sayfasında **SampleWebPartPage. aspx**sayfasını adlandırın ve **Oluştur** düğmesini seçin.

     Web Bölümü sayfası görüntülenir.

4. Web Bölümü sayfasının en üst bölgesinde **Ekle** sekmesini seçin ve ardından **Web Bölümü** düğmesini seçin.

5. **Özel** klasörü seçin, **VisualWebPart1** Web bölümünü seçin ve sonra **Ekle** düğmesini seçin.

     Web Bölümü sayfada görüntülenir. Aşağıdaki denetimler Web bölümünde görünür:

    - Aylık takvim görünümü.

    - Bir **güncelleştirme** düğmesi.

    - **Takvim** onay kutusu.

    - **Özel bir takvim** onay kutusu.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aylık Takvim görünümüne dahil edilecek listeleri belirtmek için

Web bölümünde, aylık Takvim görünümüne eklemek istediğiniz takvimleri belirtin ve ardından **Güncelleştir** düğmesini seçin.

Belirttiğiniz tüm takvimlerdeki olaylar aylık Takvim görünümünde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

SharePoint için Web [bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Nasıl yapılır: SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Izlenecek yol: SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
