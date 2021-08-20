---
title: SharePoint için Web Bölümleri oluşturuluyor | Microsoft Docs
description: SharePoint için Web bölümleri oluşturun. web bölümleri 'ni kullanarak bir SharePoint sitesinin sayfalarının içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak değiştirebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a21ec422677dfa0a2de03f8822046000b06a0293
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149292"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint için Web bölümleri oluşturma
  web bölümleri 'ni kullanarak bir SharePoint sitesinin sayfalarının içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak değiştirebilirsiniz. web bölümleri, bir web bölümü sayfasında çalışan sunucu tarafı denetimleridir: bir SharePoint sitesinde görünen sayfaların yapı taşlarıdır. bkz. [yapı bloğu: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Visual Studio şablonları kullanarak SharePoint bir sitede web bölümleri oluşturabilir ve hata ayıklayabilirsiniz.

## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio bir Web bölümü oluşturun
 herhangi bir SharePoint projesine **web bölümü** öğesi ekleyerek bir web bölümü oluşturun. Bir korumalı çözüm veya grup çözümünde bir **Web Bölümü** öğesi kullanabilirsiniz.

 tasarımcı kullanarak bir web bölümünü görsel olarak tasarlamak istiyorsanız, bir **visual web bölümü** projesi oluşturun veya herhangi bir SharePoint projesine **görsel web bölümü** öğesi ekleyin. Yalnızca bir grup çözümünde bir **görsel web bölümü** öğesini kullanabilirsiniz.

### <a name="web-part-item"></a>Web Bölümü öğesi
 bir **web bölümü** öğesi, bir SharePoint sitesi için bir Web bölümü tasarlamak üzere kullanabileceğiniz dosyalar sağlar. bir **Web bölümü** öğesi eklediğinizde, Visual Studio projenizde bir klasör oluşturur ve sonra klasöre birkaç dosya ekler. Aşağıdaki tabloda her bir dosya açıklanmaktadır.

|Dosya|Açıklama|
|----------|-----------------|
|*Elements.xml*|Projenizdeki Özellik tanım dosyasının Web bölümünü dağıtmak için kullandığı bilgileri içerir.|
|. WebPart dosyası|web bölümü galerisinde SharePoint web bölümünü görüntülemesi gereken bilgileri sağlar.|
|Kod dosyası|Web bölümüne denetimler ekleyen ve Web Bölümü içinde özel içerik üreten yöntemleri içerir.|

 daha fazla bilgi için bkz. [nasıl yapılır: SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Görsel web bölümü öğesi
 Görsel web bölümü, Visual Studio ' de Visual Web geliştirici Tasarımcısı 'nı kullanarak oluşturduğunuz bir Web bölümüdür. Görsel web bölümü, diğer Web bölümleri ile aynı şekilde çalışır. Bir Web bölümüne düğmeler ve metin kutuları gibi denetimler eklemek için bir XML dosyasına kod eklersiniz. ancak, Visual Studio **araç kutusundan** web bölümüne sürükleyip yapıştırarak bir görsel web bölümüne denetimler eklersiniz. Tasarımcı daha sonra gerekli kodu XML dosyasında oluşturur. bkz. [nasıl yapılır: tasarımcı kullanarak SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>SharePoint denetimleri
 Visual Studio, uygulama sayfaları gibi SharePoint sayfaları oluşturmaya yönelik bazı denetimler sağlar. bu denetimler **araç kutusunda** **SharePoint denetimleri** altında görüntülenir. Bu denetimlerin işlevleri [Microsoft. SharePoint türetilir. ](/previous-versions/office/sharepoint-server/ms413880(v=office.15))SharePoint site ve liste sayfalarında kullanılan ASP.NET sunucu denetimlerini içeren WebControls ad alanı.

|Denetim adı|Açıklama|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Bir ASP menüsü ekler. Daha fazla bilgi için bkz. [menü denetimine genel bakış](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|*. Aspx* sayfasına bir **bağlantı** öğesi ekler ve **CssRegistration** tarafından tanımlanan bir veya daha fazla dış stil sayfası uygular.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|*. Aspx* sayfasına bir tarih saat denetimi ekler.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|*. Aspx* sayfasına bir güvenlik doğrulaması ekler|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Belirtilen listenin bir özelliğini döndürür.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Geçerli Web sitesinin genel bir özelliğini döndürür.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|*. Aspx* sayfasına RSS akışına bir bağlantı ekler.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Sayfa işlendiğinde istenmeleri için komut dosyaları gibi kaynakları bir sayfaya kaydetmek için özellikler ve yöntemler sağlar.|
|[Tema](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|*. Aspx* sayfasına bir tema uygular.|

## <a name="debug-a-web-part"></a>Web bölümünde hata ayıklama
 web bölümünü içeren SharePoint bir projede, diğer Visual Studio projelerinde hata ayıkladığınız gibi hata ayıklayabilirsiniz. Visual Studio hata ayıklayıcıyı başlattığınızda Visual Studio SharePoint sitesini açar.

 Kodunuzda hata ayıklamaya başlamak için, Web bölümünü SharePoint bir Web Bölümü sayfasına ekleyin.

 SharePoint projelerinin hatalarını ayıklama hakkında daha fazla bilgi için bkz. [SharePoint çözümlerinde sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Görsel web bölümü sınırlamaları
 Visual Studio başlayarak, korumalı SharePoint çözümlere ve grup çözümlerine görsel web bölümleri ekleyebilirsiniz. Ancak, Visual Web bölümleri aşağıdaki sınırlamalara sahiptir:

- Görsel Web bölümleri değiştirilebilir parametreleri desteklemez. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

- Kullanıcı denetimleri veya görsel Web bölümleri, görsel Web bölümlerine sürüklenemez ve bırakılamaz veya kopyalanamaz. Bu eylem, derleme hatasına neden olur.

- görsel web bölümleri, $SPUrl gibi SharePoint sunucu belirteçlerini doğrudan desteklemez. daha fazla bilgi için, [SharePoint çözüm sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-solutions.md)konusundaki "korumalı Visual Web Bölümleri 'da belirteç kısıtlamaları" konusuna bakın.

- Bir korumalı çözüm içindeki Visual Web bölümleri bazen hata alır, "korumalı kod ana bilgisayar hizmeti isteği işleyemeyecek kadar meşgul olduğu için korumalı kod yürütme isteği reddedildi." bu hata hakkında daha fazla bilgi için [SharePoint geliştirici ekibi blogu](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157)' nda bu gönderi bölümüne bakın.

- sunucu tarafı javascript hata ayıklaması Visual Studio desteklenmez, ancak istemci tarafı javascript hata ayıklaması desteklenir.

   Bir sunucu tarafı biçimlendirme dosyasına satır içi JavaScript ekleyebilseniz de, İşaretlemede eklenen kesme noktaları için hata ayıklama desteklenmez. JavaScript hata ayıklaması yapmak için, biçimlendirme dosyasında bir dış JavaScript dosyasına başvurun ve sonra JavaScript dosyasındaki kesme noktalarını ayarlayın.

- Satır içi kodun hata ayıklaması, [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] biçimlendirme dosyası yerine oluşturulan kod dosyasında yapılmalıdır.

- Görsel Web bölümleri, yönergesinin kullanımını desteklemez `<@ Assembly Src=` .

- SharePoint web denetimleri ve bazı [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] denetimler SharePoint korumalı ortamda desteklenmez. Korumalı bir çözümde Visual Web bölümü üzerinde desteklenmeyen denetimler kullanılıyorsa, "tür veya ad alanı adı ' teması ', ' Microsoft ' ad alanında yok. SharePoint. ' "WebControls '" görünür.

  Korumalı çözümler hakkında daha fazla bilgi için bkz. [korumalı ve Grup çözümleri arasındaki farklılıklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>daha eski stil SharePoint tabanlı web bölümleri oluşturma
 SharePoint için özel web bölümleri oluşturmak üzere Visual Studio şablonlarını kullanabilirsiniz [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] . [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] Web bölümleri, [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Web Bölümü altyapısının üzerine kurulmuştur ve yeni projeler için önerilen türdür.

 çoğu durumda, daha eski stil SharePoint tabanlı web bölümünü kullanarak bir web bölümü oluşturmanız gerekebilir. bu tür web bölümleri oluşturmak için Visual Studio kullanabilirsiniz, ancak Visual Studio, bunları oluşturmanıza yardımcı olmak için özel olarak tasarlanan herhangi bir şablon sağlamaz.

 daha eski bir stil SharePoint tabanlı web bölümü oluşturmak isteyebileceğiniz hakkında daha fazla bilgi için, bkz. [Windows SharePoint Services web bölümü altyapısı](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). eski stil SharePoint tabanlı web bölümünü kullanarak bir web bölümü oluşturma hakkında daha fazla bilgi için, bkz. [izlenecek yol temel SharePoint web bölümü oluşturma](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[nasıl yapılır: SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint sayfaları için nasıl web bölümleri oluşturacağınız gösterilir.|
|[nasıl yapılır: tasarımcı kullanarak SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|görsel tasarım yüzeyi kullanarak SharePoint için web bölümleri oluşturmayı gösterir.|
|[nasıl yapılır: SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint ' de çalışan uygulama sayfaları ve Web bölümleri tarafından tüketilen özel, yeniden kullanılabilir denetimler oluşturmayı gösterir.|
|[İzlenecek yol: SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint için bir Web bölümünün nasıl tasarlanacağını açıklar.|
|[izlenecek yol: tasarımcı kullanarak SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|denetimleri görsel tasarım yüzeyine sürükleyerek SharePoint için bir web bölümünün nasıl tasarlanacağını açıklar.|
|[İzlenecek yol: SharePoint için OData görüntüleyen Silverlight Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|bir Silverlight uygulaması barındıran SharePoint için bir web bölümünün nasıl tasarlanacağını ve SharePoint listelerden verilerin nasıl görüntüleneceğini açıklar.|