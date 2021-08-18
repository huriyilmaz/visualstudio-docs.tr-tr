---
title: 'İzlenecek yol: temel bir site tanımı oluşturma Project | Microsoft Docs'
description: bu SharePoint izlenecek yolda, bazı denetimlerle görsel bir Web bölümü içeren temel bir site tanımı oluşturma bölümüne bakın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2d8de9b5da1a9bff70b8332b9b6804295996af5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130812"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>İzlenecek yol: temel bir site tanımı projesi oluşturma
  Bu izlenecek yol, üzerinde bazı denetimlerle görsel bir Web Bölümü içeren temel bir site tanımı oluşturmayı gösterir. Daha fazla açıklık için, oluşturduğunuz görsel web bölümünün yalnızca birkaç denetimi vardır. ancak, daha fazla işlevsellik içeren daha karmaşık SharePoint site tanımları oluşturabilirsiniz.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Proje şablonunu kullanarak bir site tanımı oluşturma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- SharePoint bir site tanımı kullanarak SharePoint sitesi oluşturma.

- Çözüme bir görsel Web Bölümü ekleme.

- Yeni görsel web bölümünü ekleyerek sitenin default. aspx sayfasını özelleştirme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- desteklenen Microsoft Windows sürümleri ve SharePoint. daha fazla bilgi için bkz. SharePoint çözümleri geliştirme gereksinimleri.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Site tanımı çözümü oluşturma
 İlk olarak, içinde site tanımı projesi oluşturun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Bir site tanımı projesi oluşturmak için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin. ıde 'niz Visual Basic geliştirme ayarlarını kullanacak şekilde ayarlandıysa, menü çubuğunda **dosya**  >  **yeni Project**' ni seçin.

    **Yeni Proje** iletişim kutusu görünür.

2. **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. **şablonlar** listesinde **SharePoint 2010 Project** şablonunu seçin.

4. **Ad** kutusuna **TestSiteDef** yazın ve **Tamam** düğmesini seçin.

    **SharePoint özelleştirme sihirbazı** görüntülenir.

5. **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımında hata ayıklamak istediğiniz SharePoint sitesinin URL 'sini girin veya varsayılan konumu (http://<em>sistem adı</em>/) kullanın.

6. **bu SharePoint çözümü için güven düzeyi nedir?** bölümünde, **grup çözümü olarak dağıt** seçenek düğmesini seçin.

    Tüm site tanımı projelerinin Grup çözümleri olarak dağıtılması gerekir. Korumalı çözümler ve Grup çözümleri hakkında daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

7. **Son** düğmesini seçin.

    Proje **Çözüm Gezgini** görüntülenir.

8. **Çözüm Gezgini**, proje düğümünü seçin ve ardından menü çubuğunda, **Project**  >  **yeni öğe ekle**' yi seçin.

9. **Visual C#** veya **Visual Basic** altında **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

10. **Şablonlar** bölmesinde, **site tanımı** şablonunu seçin, **adı** **SiteDefinition1** olarak bırakın ve sonra **Ekle** düğmesini seçin.

## <a name="create-a-visual-web-part"></a>Görsel web bölümü oluşturma
 Sonra, site tanımının ana sayfasında görünecek bir görsel web bölümü oluşturun.

#### <a name="to-create-a-visual-web-part"></a>Görsel bir Web bölümü oluşturmak için

1. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesini seçin.

2. **SiteDefinition1** proje düğümünü seçin ve ardından menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

3. **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. Şablonlar listesinde, **Visual Web Bölümü** şablonunu seçin, VisualWebPart1 varsayılan adını koruyun ve sonra **Ekle** düğmesini seçin.

     *VisualWebPart1. ascx* dosyası açılır.

5. *VisualWebPart1. ascx*' in en altında, forma üç denetim eklemek için aşağıdaki biçimlendirmeyi ekleyin: metin kutusu, düğme ve etiket:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. *VisualWebPart1. ascx* altında, *VisualWebPart1. ascx. cs* dosyasını (için [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) veya *VisualWebPart1. ascx. vb* (için) açın [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ve aşağıdaki kodu ekleyin:

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

     Bu kod, Web bölümünün düğme tıkla, işlevselliği ekler.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Visual Web bölümünü varsayılan ASPX sayfasına ekleme
 Ardından, Visual Web bölümünü site tanımının varsayılan ASPX sayfasına ekleyin.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Varsayılan ASPX sayfasına bir görsel web bölümü eklemek için

1. Default. aspx sayfasını açın ve etiketinin altına aşağıdaki satırı ekleyin `WebPartPages` :

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Bu satır, MyWebPartControls adını Web bölümüyle ve koduyla ilişkilendirir. *Namespace* parametresi, *VisualWebPart1. ascx* kod dosyasında kullanılan ad alanıyla eşleşir.

2. Öğesinden sonra `</asp:Content>` , tüm `ContentPlaceHolderId="PlaceHolderMain"` bölümü ve içeriğini aşağıdaki kodla değiştirin:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Bu kod, daha önce oluşturduğunuz görsel web bölümü için bir başvuru oluşturur.

3. **Çözüm Gezgini**' de, **SiteDefinition1** düğümünün kısayol menüsünü açın ve **Başlangıç öğesi olarak ayarla**' yı seçin.

## <a name="deploy-and-run-the-site-definition-solution"></a>Site tanımı çözümünü dağıtma ve çalıştırma
 Sonra, projeyi SharePoint dağıtın ve ardından projeyi çalıştırın.

#### <a name="to-deploy-and-run-the-site-definition"></a>Site tanımını dağıtmak ve çalıştırmak için

- Menü çubuğunda, **Yapı**  >  **dağıtımı TestSiteDef**' i seçin.

- **F5** tuşunu seçin.

     Visual Studio kodu derler, özelliklerini ekler, tüm dosyaları bir SharePoint çözümü (WSP) dosyasına paketler ve wsp dosyasını SharePoint sunucusuna dağıtır. SharePoint dosyaları yükleyip ardından özellikleri etkinleştirir.

## <a name="create-a-site-based-on-the-site-definition"></a>Site tanımına göre bir site oluşturun
 Sonra, yeni site tanımını kullanarak bir site oluşturun.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Site tanımını kullanarak bir site oluşturmak için

1. SharePoint sitesinde, yeni SharePoint site sayfası görüntülenir.

2. **Başlık ve açıklama** bölümünde, başlık ve sitenin açıklaması Için **Yeni Sitem** ' i girin.

3. **Web sitesi adresi** bölümünde, **URL adı** kutusuna **yenbir site** girin.

4. **şablon** bölümünde **SharePoint özelleştirmeler** sekmesini seçin.

5. **Şablon seç** listesinde **SiteDefinition1**' yi seçin.

6. Diğer ayarları varsayılan değerlerinde bırakın ve ardından **Oluştur** düğmesini seçin.

     Yeni site görünür.

## <a name="test-the-new-site"></a>Yeni siteyi test etme
 Sonra, doğru çalışıp çalışmadığını doğrulamak için yeni siteyi test edin.

#### <a name="to-test-the-new-site"></a>Yeni siteyi sınamak için

- Varsayılan ASPX sayfasında, bir metin girin ve metin kutusunun yanındaki **etiket metnini Değiştir** düğmesini seçin.

     Metin, düğmenin sağ tarafındaki etikette görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
