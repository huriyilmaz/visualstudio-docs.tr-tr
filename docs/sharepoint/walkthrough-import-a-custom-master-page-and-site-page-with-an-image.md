---
title: Özel Ana sayfa & site sayfasını görüntüyle al
description: bu izlenecek yolda, bir SharePoint özel ana sayfa ve bir Visual Studio SharePoint projesine görüntü içeren bir site sayfası içeri aktarın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7694c80d47e7dd16c603eaedd0527ac4ec4d9031
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135838"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>İzlenecek yol: bir görüntü ile özel ana sayfa ve site sayfasını Içeri aktarma
  bu izlenecek yolda, bir SharePoint özel ana sayfanın ve bir SharePoint projesine görüntü içeren bir site sayfasının nasıl içeri aktarılacağı gösterilmektedir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Bu izlenecek yol, aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:

- SharePoint tasarımcısında bir görüntü kullanarak özel bir ana sayfa ve site sayfası oluşturun.

- özel bir ana sayfa, resim ve site sayfasını bir SharePoint çözümü (*. wsp*) dosyasına aktarın.

- *. wsp* dosyasını içeri aktar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint çözüm paketi projesini kullanarak. wsp dosyasını bir SharePoint projesine aktarın ve dağıtın.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere sahip olmanız gerekir:

- [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]Ve SharePoint desteklenen sürümleri.

- Visual Studio.

- SharePoint Tasarımcı 2010.

## <a name="create-items-in-sharepoint-designer"></a>SharePoint tasarımcısında öğe oluşturma
 bu örnek, dışarı aktarma için SharePoint tasarımcısında üç öğenin nasıl oluşturulacağını gösterir: özel ana sayfa, özel ana sayfaya başvuran bir site sayfası ve site sayfasında görünecek bir görüntü dosyası. Görüntü, SharePoint ' deki/images/klasörüne eklenir.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>SharePoint tasarımcısında özel ana sayfa oluşturmak için

1. SharePoint tasarımcısı ' nda, gezinti bölmesinde, **ana sayfalar** site nesnesini seçin.

2. **Ana sayfalar** şeridinde **boş ana sayfa**' yı seçin.

3. Yeni ana sayfayı seçin, sonra **ana sayfalar** şeridinde **dosyayı Düzenle**' yi seçin.

4. SharePoint tasarımcısı ' nın altında **kod** sekmesini seçin.

5. Varolan biçimlendirmeyi aşağıdaki biçimlendirme ile değiştirin.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6. Sayfayı kaydedin, **ana sayfalar** sekmesini seçin ve ana sayfayı **mybasic1. Master** olarak yeniden adlandırın.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint tasarımcısında içerik veritabanına resim ekleme
 Artık site sayfasında görüntülenecek bir resim ekleyebilirsiniz. görüntü, SharePoint içerik veritabanına dağıtılır.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint tasarımcısında içerik veritabanına görüntü eklemek için

1. Gezinti bölmesinde, **tüm dosyalar** site nesnesini seçin ve ardından ağaç görünümünde **görüntüler** klasörünü seçin.

2. **Tüm dosyalar** şeridinde **dosyaları içeri aktar**' ı seçin, Istediğiniz dosyayı seçin ve **Tamam** düğmesini seçin. Bu örnekte, dosya **myimg1.png** olarak adlandırılır.

     İsteğe bağlı olarak, görüntülerin düzenlenmesine yardımcı olması için bir alt klasör oluşturabilirsiniz.

3. **Içeri aktar** iletişim kutusunu kapatın.

## <a name="create-a-site-page"></a>Site sayfası oluştur
 Bu temel site sayfası özel ana sayfayı kullanır ve önceki adımda eklediğiniz görüntüyü görüntüler.

#### <a name="to-create-a-site-page"></a>Site sayfası oluşturmak için

1. Gezinti bölmesinde, **site sayfaları** nesnesini seçin.

2. **Sayfalar** şeridinde, **sayfa** düğmesini seçin, **aspx** sayfası türünü seçin ve ardından yeni dosyayı **MyContentPage1. aspx** olarak adlandırın.

     İsteğe bağlı olarak, site sayfalarını düzenlemeye yardımcı olması için bir alt klasör oluşturabilirsiniz.

3. Site sayfaları listesinde, Özellikler sayfasını açmak için **MyContentPage1. aspx** ' i seçin ve ardından sayfanın alt kısmında **Dosya Düzenle** bağlantısını seçin.

     Bir ileti görünürse ve bu sayfanın güvenli modda düzenlenebilir bir bölge içermediğini ve bu sayfayı Gelişmiş modda açmak isteyip istemediğinizi sorduğunda **Evet** düğmesini seçin.

4. Sayfanın alt kısmındaki **kod** düğmesini seçin.

5. Varolan biçimlendirmeyi aşağıdaki biçimlendirme ile değiştirin.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6. Güncelleştirilmiş site sayfasını kaydedin.

## <a name="export-the-items-from-sharepoint"></a>Öğeleri SharePoint dışarı aktarma
 öğeleri SharePoint SharePoint çözüm (*. wsp*) dosyasına dışarı aktarın.

#### <a name="to-export-items-from-sharepoint-designer"></a>öğeleri SharePoint tasarımcıdan dışarı aktarmak için

1. SharePoint tasarımcısı ' nda, gezinti bölmesinde, **ekip sitesi** nesnesini seçin ve ardından **site** şeridinde, **şablon olarak kaydet**' i seçin.

2. **Şablon olarak kaydet** iletişim kutusunda bir dosya adı ve şablon adı girin, **İçerik Ekle** onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

     Bu, sitenin içeriğini *. wsp* dosyasına kaydeder.

3. Çözüm dışarı aktardıktan sonra, kullanılabilir çözüm dosyalarının listesini göstermek için **Çözüm Galerisi** bağlantısını seçin.

4. Yeni *. wsp* dosyası için kısayol menüsünü açın ve ardından sisteme kaydetmek için **hedefi farklı kaydet** ' i seçin.

## <a name="import-the-items-into-visual-studio"></a>Öğeleri Visual Studio içeri aktar
 *. Wsp* dosyasını içine aktarın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . İçerik içeri aktarıldıktan sonra, onu özelleştirebilir, daha fazla öğe ekleyebilir ve dağıtabilirsiniz.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Öğeleri. wsp dosyasından Visual Studio içine aktarmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir **içeri aktarma SharePoint 2010 çözüm paketi** projesi oluşturun.

2. **İçeri aktarılacak öğeleri seçin** sayfasında, **tür** sütunundaki **Modül** altında, içeri aktarma için yalnızca aşağıdaki tablodaki dosyalar için onay kutularını seçin.

   | Dosya Adı | Açıklama |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Özel Ana sayfa. |
   | images_ | SharePoint dosya sistemindeki görüntü dosyası. |
   | SitePages_ | Site sayfası. |

3. Seçilen öğeleri içe aktarmak için **son** düğmesini seçin.

4. **Çözüm Gezgini**, \_ catalogsmasterpage \_ düğümünü seçin ve **dağıtım çakışma çözümü** özelliğinin değerini **Otomatik** olarak ayarlayın.

    Bu, tüm dağıtım çakışmalarının otomatik olarak çözümlendiğinden emin olmanıza yardımcı olur.

5. yeni ana sayfanız varolan bir sayfayla aynı ada sahipse, mevcut sayfanın bir varsayılan ana sayfa veya SharePoint tasarımcısında özel ana sayfa olarak işaretlenmemiş olduğundan emin olun.

    Varolan bir ana sayfa varsayılan ana sayfa veya özel ana sayfa olarak işaretlenmişse, ana sayfanın silinemediğini belirten bir dağıtım hatası alırsınız. Bu sorundan kaçınmak için şunları yapın:

   - Varolan ana sayfa varsayılan ana sayfa olarak ayarlandıysa, geçici olarak başka bir ana sayfayı varsayılan ana sayfa olarak ayarlayın. dosyaları SharePoint ' a dağıttıktan sonra, yeni ana sayfanızı varsayılan ana sayfa olarak ayarlayın.

   - Mevcut ana sayfa özel ana sayfa olarak ayarlandıysa, geçici olarak başka bir ana sayfayı özel ana sayfa olarak ayarlayın. dosyaları SharePoint ' a dağıttıktan sonra, yeni ana sayfanızı özel ana sayfa olarak ayarlayın.

6. Menü çubuğunda **Yapı**  >  **dağıtım çözümü**' ni seçin.

7. dağıtılan öğeleri görüntülemek için SharePoint sitesini açın.

   dosyaları içine aktarmak ve SharePoint dağıtmak için alternatif bir yol da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosyaları ' de modüllere eklemektir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Nasıl yapılır: bir ana sayfa veya temayı Içeri aktarma](../sharepoint/how-to-import-a-master-page-or-theme.md) ve [çözümdeki dosyaları dahil etmek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
