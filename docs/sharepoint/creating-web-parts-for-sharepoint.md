---
title: SharePoint için Web Bölümleri oluşturuluyor | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3825ef7d2c1c90f63a90f5028063c74332543841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015053"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint için Web bölümleri oluşturma
  Web bölümleri 'ni kullanarak bir SharePoint sitesinin sayfalarının içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak değiştirebilirsiniz. Web bölümleri, bir Web Bölümü sayfası içinde çalışan sunucu tarafı denetimleridir: bir SharePoint sitesinde görünen sayfaların yapı taşlarıdır. Bkz. [Yapı bloğu: Web bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Visual Studio 'daki şablonları kullanarak bir SharePoint sitesinde Web bölümleri oluşturabilir ve hata ayıklayabilirsiniz.

## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio 'da Web Bölümü oluşturma
 Herhangi bir SharePoint projesine **Web Bölümü** öğesi ekleyerek bir Web bölümü oluşturun. Bir korumalı çözüm veya grup çözümünde bir **Web Bölümü** öğesi kullanabilirsiniz.

 Tasarımcı kullanarak bir Web bölümünü görsel olarak tasarlamak istiyorsanız, bir **Visual Web Bölümü** projesi oluşturun veya herhangi bir SharePoint projesine **Visual Web Bölümü** öğesi ekleyin. Yalnızca bir grup çözümünde bir **görsel web bölümü** öğesini kullanabilirsiniz.

### <a name="web-part-item"></a>Web Bölümü öğesi
 **Web Bölümü** öğesi, bir SharePoint sitesi için bir Web Bölümü tasarlamak üzere kullanabileceğiniz dosyalar sağlar. Bir **Web Bölümü** öğesi eklediğinizde, Visual Studio projenizde bir klasör oluşturur ve sonra klasöre birkaç dosya ekler. Aşağıdaki tabloda her bir dosya açıklanmaktadır.

|Dosya|Description|
|----------|-----------------|
|*Elements.xml*|Projenizdeki Özellik tanım dosyasının Web bölümünü dağıtmak için kullandığı bilgileri içerir.|
|. WebPart dosyası|Web Bölümü galerisinde, SharePoint 'in Web bölümünü görüntülemesi için gereken bilgileri sağlar.|
|Kod dosyası|Web bölümüne denetimler ekleyen ve Web Bölümü içinde özel içerik üreten yöntemleri içerir.|

 Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Görsel web bölümü öğesi
 Görsel web bölümü, Visual Studio 'da Visual Web Developer Designer kullanarak oluşturduğunuz bir Web bölümüdür. Görsel web bölümü, diğer Web bölümleri ile aynı şekilde çalışır. Bir Web bölümüne düğmeler ve metin kutuları gibi denetimler eklemek için bir XML dosyasına kod eklersiniz. Ancak, Visual Studio **araç kutusu**'ndan web bölümüne sürükleyip yapıştırarak bir görsel web bölümüne denetimler eklersiniz. Tasarımcı daha sonra gerekli kodu XML dosyasında oluşturur. Bkz. [nasıl yapılır: tasarımcı kullanarak SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>SharePoint denetimleri
 Visual Studio, uygulama sayfaları gibi SharePoint sayfaları oluşturmaya yönelik bazı denetimler sağlar. Bu denetimler, **SharePoint denetimleri**altındaki **araç kutusunda** görünür. Bu denetimlerin işlevselliği, SharePoint sitesinde ve liste sayfalarında kullanılan ASP.NET sunucu denetimlerini içeren [Microsoft. SharePoint. WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) ad alanından türetilir.

|Denetim adı|Description|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Bir ASP menüsü ekler. Daha fazla bilgi için bkz. [menü denetimine genel bakış](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|*. Aspx* sayfasına bir **bağlantı** öğesi ekler ve **CssRegistration**tarafından tanımlanan bir veya daha fazla dış stil sayfası uygular.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|*. Aspx* sayfasına bir tarih saat denetimi ekler.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|*. Aspx* sayfasına bir güvenlik doğrulaması ekler|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Belirtilen listenin bir özelliğini döndürür.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Geçerli Web sitesinin genel bir özelliğini döndürür.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|*. Aspx* sayfasına RSS akışına bir bağlantı ekler.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Sayfa işlendiğinde istenmeleri için komut dosyaları gibi kaynakları bir sayfaya kaydetmek için özellikler ve yöntemler sağlar.|
|[Tema](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|*. Aspx* sayfasına bir tema uygular.|

## <a name="debug-a-web-part"></a>Web bölümünde hata ayıklama
 Web bölümünü içeren bir SharePoint projesinde, diğer Visual Studio projelerinde hata ayıklaması yaptığınız gibi hata ayıklayabilirsiniz. Visual Studio hata ayıklayıcısını başlattığınızda, Visual Studio SharePoint sitesini açar.

 Kodunuzda hata ayıklamaya başlamak için Web bölümünü SharePoint 'teki bir Web Bölümü sayfasına ekleyin.

 SharePoint projelerinde hata ayıklama hakkında daha fazla bilgi için bkz. [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Görsel web bölümü sınırlamaları
 Visual Studio 'dan başlayarak, korumalı SharePoint çözümlerine ve grup çözümlerine görsel Web bölümleri ekleyebilirsiniz. Ancak, Visual Web bölümleri aşağıdaki sınırlamalara sahiptir:

- Görsel Web bölümleri değiştirilebilir parametreleri desteklemez. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

- Kullanıcı denetimleri veya görsel Web bölümleri, görsel Web bölümlerine sürüklenemez ve bırakılamaz veya kopyalanamaz. Bu eylem, derleme hatasına neden olur.

- Görsel Web bölümleri $SPUrl gibi SharePoint Server belirteçlerini doğrudan desteklemez. Daha fazla bilgi için [SharePoint çözümlerinin sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-solutions.md)konusundaki "korumalı Visual Web bölümleri 'Da belirteç kısıtlamaları" konusuna bakın.

- Bir korumalı çözüm içindeki Visual Web bölümleri bazen hata alır, "korumalı kod ana bilgisayar hizmeti isteği işleyemeyecek kadar meşgul olduğu için korumalı kod yürütme isteği reddedildi." Bu hata hakkında daha fazla bilgi için [SharePoint Geliştirici ekibi bloguna](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157)bu gönderisine bakın.

- Sunucu tarafı JavaScript hata ayıklaması Visual Studio 'da desteklenmez, ancak istemci tarafı JavaScript hata ayıklaması desteklenir.

   Bir sunucu tarafı biçimlendirme dosyasına satır içi JavaScript ekleyebilseniz de, İşaretlemede eklenen kesme noktaları için hata ayıklama desteklenmez. JavaScript hata ayıklaması yapmak için, biçimlendirme dosyasında bir dış JavaScript dosyasına başvurun ve sonra JavaScript dosyasındaki kesme noktalarını ayarlayın.

- Satır içi kodun hata ayıklaması, [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] biçimlendirme dosyası yerine oluşturulan kod dosyasında yapılmalıdır.

- Görsel Web bölümleri, yönergesinin kullanımını desteklemez `<@ Assembly Src=` .

- SharePoint Web denetimleri ve bazı [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] denetimler, SharePoint korumalı ortamında desteklenmez. Korumalı bir çözümde Visual Web bölümü üzerinde desteklenmeyen denetimler kullanılıyorsa, "' Microsoft. SharePoint. WebControls '" ad alanında "tür veya ad alanı adı ' teması ' yok" hatası görüntülenir.

  Korumalı çözümler hakkında daha fazla bilgi için bkz. [korumalı ve Grup çözümleri arasındaki farklılıklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Eski stil SharePoint tabanlı Web bölümleri oluşturma
 SharePoint için özel Web bölümleri oluşturmak üzere Visual Studio 'daki şablonları kullanabilirsiniz [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] . [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web bölümleri, [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web Bölümü altyapısının üzerine kurulmuştur ve yeni projeler için önerilen türdür.

 Çok az durumda, daha eski stil SharePoint tabanlı Web bölümünü kullanarak bir Web bölümü oluşturmanız gerekebilir. Bu Web bölümleri türlerini oluşturmak için Visual Studio 'Yu kullanabilirsiniz, ancak Visual Studio, özel olarak bunları oluşturmanıza yardımcı olmak için tasarlanan herhangi bir şablon sağlamaz.

 Eski stil bir SharePoint tabanlı Web bölümü oluşturmak isteyebileceğiniz zaman hakkında daha fazla bilgi için bkz. [Windows SharePoint Services 'de Web Bölümü altyapısı](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Eski stil SharePoint tabanlı Web bölümünü kullanarak bir Web Bölümü oluşturma hakkında daha fazla bilgi için bkz. [temel bir SharePoint Web Bölümü oluşturma Izlenecek yol](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint sayfaları için nasıl Web bölümleri oluşturacağınız gösterilir.|
|[Nasıl yapılır: tasarımcı kullanarak SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Görsel tasarım yüzeyi kullanarak SharePoint için nasıl Web bölümleri oluşturacağınız gösterilir.|
|[Nasıl yapılır: SharePoint uygulama sayfası veya Web bölümü için Kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint 'te çalışan uygulama sayfaları ve Web bölümleri tarafından tüketilen özel, yeniden kullanılabilir denetimler oluşturmayı gösterir.|
|[İzlenecek yol: SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint için bir Web bölümünün nasıl tasarlanacağını açıklar.|
|[İzlenecek yol: tasarımcı kullanarak SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Denetimleri görsel tasarım yüzeyine sürükleyerek SharePoint için bir Web bölümünün nasıl tasarlanacağını açıklar.|
|[İzlenecek yol: SharePoint için OData görüntüleyen Silverlight Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Bir Silverlight uygulaması barındıran ve SharePoint listelerindeki verileri görüntüleyen SharePoint için bir Web bölümünün nasıl tasarlanacağını açıklar.|
