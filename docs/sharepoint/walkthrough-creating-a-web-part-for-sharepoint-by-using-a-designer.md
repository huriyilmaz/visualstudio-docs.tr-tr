---
title: Tasarımcı kullanarak web SharePoint bölümü oluşturma
description: Bu kılavuzda, SharePoint Visual Web Bölümü proje şablonunu kullanarak görsel olarak bir web Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2a00ea5c8720c02b9dbdbd8a6fad7fa7657efeb5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130799"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Adım adım kılavuz: Tasarımcı kullanarak SharePoint web bölümü oluşturma

Bir web sitesi için web SharePoint, kullanıcılarınız bir tarayıcı kullanarak bu sitenin içeriğini, görünümünü ve davranışını doğrudan değiştirebilir. Bu kılavuzda, SharePoint **Visual Web** Bölümü proje şablonunu kullanarak görsel olarak web bölümü oluşturma Visual Studio.

Oluşturacakları web bölümü, sitenin her takvim listesi için aylık takvim görünümünü ve onay kutusunu görüntüler. Kullanıcılar, onay kutularını seçerek aylık takvim görünümüne hangi takvim listelerinin dahil olduğunu belirtebilirsiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Görsel Web Bölümü proje şablonunu **kullanarak bir web bölümü** oluşturma.
- Web bölümünü web'de Visual Web Geliştirici tasarımcısını kullanarak Visual Studio.
- Web bölümünde denetimlerin olaylarını işlemek için kod ekleme.
- Web bölümünü SharePoint.

    > [!NOTE]
    > Bilgisayarınız aşağıdaki yönergelerde, kullanıcı arabiriminin bazı öğeleri için farklı adlar Visual Studio konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz. [IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint.

## <a name="create-a-web-part-project"></a>Web bölümü projesi oluşturma

İlk olarak, Görsel Web Bölümü proje şablonunu **kullanarak bir web bölümü** projesi oluşturun.

1. Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] olarak Yönetici Olarak Çalıştır **seçeneğini** kullanın.

2. Menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >  
::: moniker range="=vs-2017"

3. Yeni **Project** iletişim **kutusunda, Visual C#** veya **Visual Basic** altında **Office/SharePoint** seçeneğini genişletin ve SharePoint **Çözümleri kategorisini** seçin.

4. Şablon listesinde SharePoint **2013 - Visual Web Bölümü** şablonunu ve ardından Tamam **düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir. Bu sihirbazı kullanarak projede hata ayıklamak için kullanabileceğiniz siteyi ve çözümün güven düzeyini belirtebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
3. Yeni **Sürüm Oluştur Project** iletişim kutusunda, *SharePoint sürümünün SharePoint* boş Project * SharePoint seçin. Örneğin, 2019 yüklemesi SharePoint **2019 - Boş** SharePoint şablonunu Project seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. Ad **kutusuna** **TestProject1 yazın** ve oluştur **düğmesini** seçin.

::: moniker-end
5. Bu **çözüm için güven düzeyi SharePoint** grup çözümü olarak dağıt **seçeneğini** belirleyin.

6. Varsayılan yerel **siteyi** kabul etmek için Son SharePoint seçin.

## <a name="designing-the-web-part"></a>Web bölümünü tasarlama

Araç Kutusundan Visual Web Geliştirici **tasarımcısının yüzeyine** denetimler ekleyerek web bölümünü tasarlar.

1. Visual Web Geliştirici tasarımcısında Tasarım sekmesini **seç** seçen Tasarım görünümü.

2. Menü çubuğunda Görünüm Araç **Kutusu'nı**  >  **seçin.**

3. Araç **Kutusunun Standart** **düğümünde** **CheckBoxList denetimi** seçin ve ardından aşağıdaki adımlardan birini gerçekleştirin:

    - **CheckBoxList** denetimi için kısayol menüsünü açın, Kopyala'yı **seçin,** tasarımcıda ilk satırın kısayol menüsünü açın ve yapıştır'ı **seçin.**

    - **CheckBoxList denetimi** araç **kutusundan sürükleyin** ve denetimi tasarımcının ilk satırına bağlama.

4. Önceki adımı yinele, ancak düğmeyi tasarımcının sonraki satırına taşı.

5. Tasarımcıda **Düğme1 düğmesini** seçin.

6. Menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >  **seçin.**

     Özellikler  penceresi açılır.

7. Düğmenin **Text** özelliğine Update **girin.**

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Web bölümünde denetimlerin olaylarını işleme

Kullanıcının ana takvim görünümüne takvim eklemesi için kod ekleyin.

1. Aşağıdaki adım kümelerinden birini uygulayın:

   - Tasarımcıda Güncelleştir düğmesine **çift** tıklayın.

   - Güncelleştir **düğmesinin** Özellikler **penceresinde** Olaylar **düğmesini** seçin. Click **özelliğine** Button1_Click **girin** ve Enter tuşuna basın.

     Kullanıcı denetimi kod dosyası Kod Düzenleyicisi'nde açılır ve `Button1_Click` olay işleyicisi görüntülenir. Daha sonra bu olay işleyiciye kod eksersiniz.

2. Aşağıdaki deyimlerini kullanıcı denetim kodu dosyasının en üstüne ekleyin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. Sınıfına aşağıdaki kod satırı `VisualWebPart1` ekleyin. Bu kod, aylık takvim görünümü denetimi bildirer.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. sınıfının `Page_Load` yöntemini `VisualWebPart1` aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Kullanıcı denetimine aylık takvim görünümü ekler.

   - Sitenin her takvim listesi için bir onay kutusu ekler.

   - Takvim görünümünde görünen her öğe türü için bir şablon belirtir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. sınıfının `Button1_Click` yöntemini `VisualWebPart1` aşağıdaki kodla değiştirin. Bu kod, seçilen her takvimden ana takvim görünümüne öğe ekler.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>Web bölümünü test edin

Projeyi çalıştırdıktan sonra SharePoint açılır. Web bölümü, Web Bölümü Galerisi'ne otomatik olarak SharePoint. Bu projeyi test etmek için aşağıdaki görevleri gerçekleştirebilirsiniz:

- İki ayrı takvim listesinden her biri için bir olay ekleyin.
- Web bölümünü bir web bölümü sayfasına ekleyin.
- Aylık takvim görünümüne dahil etmek için listeleri belirtin.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Sitenin takvim listelerine olay eklemek için

1. Bu Visual Studio **F5 anahtarını** seçin.

     SharePoint sitesi açılır ve Hızlı Başlat [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] çubuğu görüntülenir.

2. Yeni Hızlı Başlat, **Listeler'in** altında Takvim **bağlantısını** seçin.

     Takvim **sayfası** görüntülenir.

     Bu çubukta Takvim bağlantısı Hızlı Başlat Site İçeriği **bağlantısını** seçin. Site İçeriği sayfasında takvim öğesi **göster** yoksa bir tane oluşturun.

3. Takvim sayfasında bir gün seçin ve ardından olay **eklemek için** seçilen günde Ekle bağlantısını seçin.

4. Başlık **kutusuna** varsayılan **takvime Olay yazın ve** kaydet **düğmesini** seçin.

5. Site İçeriği **bağlantısını** ve ardından Uygulama ekle **kutucuğunu** seçin.

6. Oluştur **sayfasında** Takvim türünü **seçin, takvimin** adını ve ardından Oluştur **düğmesini** seçin.

7. Yeni takvime bir olay ekleyin, özel **takvimde olay** Olayı olarak ad girin ve kaydet **düğmesini** seçin.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Web bölümünü bir web bölümü sayfasına eklemek için

1. Site **İçeriği sayfasında** Site Sayfaları **klasörünü** açın.

2. Şeritte Dosyalar sekmesini **seçin,** Yeni Belge **menüsünü** açın ve ardından Web Bölümü **Sayfası komutunu** seçin.

3. Yeni **Web Bölümü Sayfası sayfasında,** sayfaya **SampleWebPartPage.aspx** adını ve ardından Oluştur **düğmesini** seçin.

     Web bölümü sayfası görüntülenir.

4. Web bölümü sayfasının üst bölgesinde Ekle sekmesini **ve** ardından Web Bölümü **düğmesini** seçin.

5. Özel **klasörü** seçin, **VisualWebPart1** web bölümünü ve ardından Ekle **düğmesini** seçin.

     Web bölümü sayfada görünür. Web bölümünde aşağıdaki denetimler görünür:

    - Aylık takvim görünümü.

    - Güncelleştir **düğmesi.**

    - Takvim **onay** kutusu.

    - Özel **Takvim onay** kutusu.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aylık takvim görünümüne dahil olacak listeleri belirtmek için

Web bölümünde, aylık takvim görünümüne dahil etmek istediğiniz takvimleri belirtin ve ardından Güncelleştir **düğmesini** seçin.

Belirttiğiniz tüm takvimlerden gelen olaylar, aylık takvim görünümünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint için web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Nasıl SharePoint: SharePoint bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Adım adım kılavuz: SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
