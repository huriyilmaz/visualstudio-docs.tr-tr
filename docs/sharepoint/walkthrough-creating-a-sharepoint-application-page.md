---
title: 'İzlenecek yol: SharePoint uygulama sayfası oluşturma | Microsoft Docs'
description: Bu kılavuzda, bir uygulama sayfası (bir ASP.NET sayfasının özelleştirilmiş formu) oluşturun ve ardından yerel bir SharePoint sitesi kullanarak hata ayıklayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6640373dac6d08144f1ef7fd230afa172540afe6
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217768"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>İzlenecek yol: SharePoint uygulama sayfası oluşturma

Uygulama sayfası, ASP.NET sayfasının özelleşmiş bir biçimidir. Uygulama sayfaları bir SharePoint ana sayfasıyla birleştirilmiş içerik içerir. Daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

Bu izlenecek yol, bir uygulama sayfasının nasıl oluşturulduğunu ve sonra yerel bir SharePoint sitesi kullanarak nasıl hata ayıklaması yapılacağını gösterir. Bu sayfa, her kullanıcının sunucu grubundaki tüm sitelerde oluşturduğu veya değiştirdiği tüm öğeleri gösterir.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- SharePoint projesi oluşturma.
- SharePoint projesine bir uygulama sayfası ekleniyor.
- Uygulama sayfasına ASP.NET denetimleri ekleme.
- ASP.NET denetimlerinin arkasına kod ekleme.
- Uygulama sayfasını test etme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

- Desteklenen Windows ve SharePoint sürümleri.

## <a name="create-a-sharepoint-project"></a>SharePoint projesi oluşturma

İlk olarak, **boş bir SharePoint projesi** oluşturun. Daha sonra, bu projeye bir **uygulama sayfası** öğesi eklersiniz.

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Yeni proje** iletişim kutusunu açın, kullanmak istediğiniz dilin altındaki **Office/SharePoint** düğümünü genişletin ve **SharePoint çözümleri** düğümünü seçin.

3. **Visual Studio yüklü şablonlar** bölmesinde, **SharePoint 2010-boş proje** şablonunu seçin. Projeyi **MySharePointProject** olarak adlandırın ve ardından **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir. Bu sihirbaz, projenin hatalarını ayıklamak için kullanacağınız siteyi ve çözümün güven düzeyini seçmenizi sağlar.

4. **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından varsayılan yerel SharePoint sitesini kabul etmek için **son** düğmesini seçin.

## <a name="create-an-application-page"></a>Uygulama sayfası oluşturma

Bir uygulama sayfası oluşturmak için projeye bir **Uygulama sayfa** öğesi ekleyin.

1. **Çözüm Gezgini**, **MySharePointProject** projesini seçin.

2. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

3. **Yeni öğe Ekle** iletişim kutusunda, **uygulama sayfasını (yalnızca Grup çözümü** şablonu) seçin.

4. Sayfayı **SearchItems** olarak adlandırın ve ardından **Ekle** düğmesini seçin.

     Visual Web Developer Designer, sayfanın HTML öğelerini görebileceğiniz **kaynak** görünümündeki uygulama sayfasını görüntüler. Tasarımcı, birkaç denetim için biçimlendirmeyi görüntüler <xref:System.Web.UI.WebControls.Content> . Her denetim <xref:System.Web.UI.WebControls.ContentPlaceHolder> , varsayılan uygulama ana sayfasında tanımlanan bir denetimle eşlenir.

## <a name="design-the-layout-of-the-application-page"></a>Uygulama sayfasının yerleşimini tasarlama

Uygulama sayfası öğesi, uygulama sayfasına ASP.NET denetimleri eklemek için bir tasarımcı kullanmanıza olanak sağlar. Bu tasarımcı, Visual Web Developer 'da kullanılan tasarlayıcıdır. Tasarımcı **kaynak** görünümüne bir etiket, radyo düğmesi listesi ve tablo ekleyin ve ardından, herhangi bir standart ASP.NET sayfası tasarlarken yaptığınız gibi özellikleri ayarlayın.

1. Menü çubuğunda **Görünüm**  >  **araç kutusunu** seçin.

2. **Araç kutusunun** standart düğümünde aşağıdaki adımlardan birini gerçekleştirin:

    - **Etiket** öğesi için kısayol menüsünü açın, **Kopyala**' yı seçin, tasarımcıda **PlaceHolderMain** içerik denetiminin altındaki satır Için kısayol menüsünü açın ve ardından **Yapıştır**' ı seçin.

    - **Araç kutusundan** **etiket** öğesini, **PlaceHolderMain** içerik denetiminin gövdesine sürükleyin.

3. **PlaceHolderMain** içerik denetimine bir **DropDownList** öğesi ve **tablo** öğesi eklemek için önceki adımı tekrarlayın.

4. Tasarımcıda `Text` etiket denetiminin özniteliğinin değerini **tüm öğeleri gösterecek** şekilde değiştirin.

5. Tasarımcıda `<asp:DropDownList>` öğesini AŞAĞıDAKI XML ile değiştirin.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Sayfadaki denetimlerin olaylarını işleyin

Bir uygulama sayfasındaki denetimleri herhangi bir ASP.NET sayfasında olduğu gibi işleyin. Bu yordamda, `SelectedIndexChanged` açılan listenin olayını işleyirsiniz.

1. **Görünüm** menüsünde **kod**' u seçin.

     Uygulama sayfası kod dosyası kod düzenleyicisinde açılır.

2. Sınıfına aşağıdaki yöntemi ekleyin `SearchItems` . Bu kod <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> , <xref:System.Web.UI.WebControls.DropDownList> Bu izlenecek yolda daha sonra oluşturacağınız bir yöntemi çağırarak olayını işler.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet5":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet5":::

3. Aşağıdaki deyimlerini uygulama sayfası kod dosyasının en üstüne ekleyin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet1":::

4. Sınıfına aşağıdaki yöntemi ekleyin `SearchItems` . Bu yöntem, sunucu grubundaki tüm sitelerde yinelenir ve geçerli kullanıcı tarafından oluşturulan veya değiştirilen öğeleri arar.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet2":::

5. Sınıfına aşağıdaki yöntemi ekleyin `SearchItems` . Bu yöntem, tablodaki geçerli kullanıcı tarafından oluşturulan veya değiştirilen öğeleri görüntüler.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs" id="Snippet3":::

## <a name="test-the-application-page"></a>Uygulama sayfasını test etme

Projeyi çalıştırdığınızda, SharePoint sitesi açılır ve uygulama sayfası görüntülenir.

1. **Çözüm Gezgini**' de, uygulama sayfası için kısayol menüsünü açın ve **Başlangıç öğesi olarak ayarla**' yı seçin.

2. **F5** tuşunu seçin.

     SharePoint sitesi açılır.

3. Uygulama sayfasında **benim tarafımdan değiştirildi** seçeneğini belirleyin.

     Uygulama sayfası yenilenir ve sunucu grubundaki tüm sitelerde değiştirdiğiniz tüm öğeleri görüntüler.

4. Uygulama sayfasında, listeden **benim** oluşturduğum öğesini seçin.

     Uygulama sayfası yenilenir ve sunucu grubundaki tüm sitelerde oluşturduğunuz tüm öğeleri görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

SharePoint uygulama sayfaları hakkında daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

Aşağıdaki konulardan Visual Web Tasarımcısı 'nı kullanarak SharePoint sayfası içeriğini tasarlama hakkında daha fazla bilgi edinebilirsiniz:

- [SharePoint için Web bölümleri oluşturun](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturun](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md) 
 [Uygulama _layouts sayfa türü](/previous-versions/office/aa979604(v=office.14))
