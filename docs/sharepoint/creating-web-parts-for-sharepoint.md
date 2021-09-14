---
title: Web Bölümleri için SharePoint | Microsoft Docs
description: Web bölümleri oluşturma SharePoint. Web bölümlerini kullanarak, bir tarayıcı kullanarak bir sitenin SharePoint, görünümünü ve davranışını değiştirebilirsiniz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635609"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint için web bölümleri oluşturma
  Web bölümlerini kullanarak, bir tarayıcı kullanarak bir sitenin SharePoint, görünümünü ve davranışını değiştirebilirsiniz. Web bölümleri, bir web bölümü sayfasında çalıştıran sunucu tarafı denetimlerdir. Bunlar, web bölümü sayfasında görünen sayfaların yapı SharePoint dır. Bkz. [Building Block: Web Bölümleri](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Bir web sitesinde web bölümleri oluşturabilir ve SharePoint şablonlarını kullanarak Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio'de web bölümü oluşturma
 Herhangi bir web projesine Web **Bölümü öğesi** ekleyerek bir web SharePoint oluşturun. Korumalı alanlı bir **çözümde veya** grup çözümünde Bir Web Bölümü öğesini kullanabilirsiniz.

 Tasarımcı kullanarak bir web bölümü tasarlamak için bir Görsel **Web** Bölümü projesi oluşturun veya herhangi bir web projesine Görsel **Web** Bölümü SharePoint ekleyin. Görsel Web Bölümü **öğesini yalnızca bir** grup çözümünde kullanabilirsiniz.

### <a name="web-part-item"></a>Web bölümü öğesi
 Web **Bölümü öğesi,** bir web sitesi için web bölümü tasarlamak üzere kullanabileceğiniz SharePoint sağlar. Bir Web Bölümü **öğesi eklerken,** Visual Studio projeniz içinde bir klasör oluşturur ve ardından klasöre birkaç dosya ekler. Aşağıdaki tabloda her dosya açık almaktadır.

|Dosya|Description|
|----------|-----------------|
|*Elements.xml*|Projenizin Özellik tanımı dosyasının web bölümünü dağıtmak için kullandığı bilgileri içerir.|
|.webpart dosyası|Web bölümü SharePoint görüntülemek için gereken bilgileri sağlar.|
|Kod Dosyası|Web parçasına denetimler ek eden ve web bölümü içinde özel içerik oluşturan yöntemleri içerir.|

 Daha fazla bilgi için [bkz. Nasıl SharePoint web bölümü oluşturma.](../sharepoint/how-to-create-a-sharepoint-web-part.md)

### <a name="visual-web-part-item"></a>Görsel web bölümü öğesi
 Görsel web bölümü, web'de Visual Web Geliştirici tasarımcısını kullanarak Visual Studio. Görsel web bölümü, diğer web bölümüyle aynı şekilde işlev gösterir. Web parçasına düğmeler ve metin kutuları gibi denetimler eklemek için XML dosyasına kod eklersiniz. Ancak, denetimler görsel web parçasına, araç kutusundan web parçasına sürükleyerek veya kopya Visual Studio **eklersiniz.** Tasarımcı daha sonra XML dosyasında gerekli kodu üretir. Bkz. [Tasarımcı kullanarak SharePoint web bölümü oluşturma.](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)

## <a name="sharepoint-controls"></a>SharePoint denetimler
 Visual Studio, uygulama sayfaları gibi SharePoint oluşturmak için bazı denetimler sağlar. Bu denetimler, **Denetimler altındaki** Araç **kutusunda SharePoint görünür.** Bu denetimlerin işlevselliği [Microsoft.SharePoint. Site ve](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) liste sayfalarında ASP.NET sunucu denetimlerini içeren WebControls SharePoint alanı.

|Denetim Adı|Description|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Asp menüsü ekler. Daha fazla bilgi için bkz. [Menü Denetimine Genel Bakış.](/previous-versions/ecs0x9w5(v=vs.140))|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|*.aspx* **sayfasına bir LINK** öğesi ekler ve **CssRegistration** tarafından tanımlanan bir veya daha fazla dış stil sayfası uygular.|
|[Datetimecontrol](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|*.aspx* sayfasına bir DateTime denetimi ekler.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|*.aspx* sayfasına bir güvenlik doğrulaması ekler|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Belirtilen bir listenin özelliğini döndürür.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Geçerli web sitesinin genel bir özelliğini döndürür.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|.aspx sayfasına RSS akışına *bir bağlantı* ekler.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Sayfa işlenirken istenebilir olması için bir sayfaya betikler gibi kaynakları kaydetmek için özellikler ve yöntemler sağlar.|
|[Tema](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|.aspx sayfasına *bir tema* uygular.|

## <a name="debug-a-web-part"></a>Web bölümünde hata ayıklama
 Web bölümü içeren bir SharePoint projesinde diğer projelerde olduğu gibi hata Visual Studio ayıklarsiniz. Hata ayıklayıcısını Visual Studio, Visual Studio siteyi SharePoint açar.

 Kodda hata ayıklamaya başlamak için web bölümünü bir web bölümü sayfasına ekleyin ve SharePoint.

 Projelerde hata ayıklama hakkında daha fazla bilgi SharePoint [bkz. SharePoint giderme.](../sharepoint/troubleshooting-sharepoint-solutions.md)

## <a name="visual-web-part-limitations"></a>Görsel web bölümü sınırlamaları
 Bu Visual Studio, korumalı alanlı sanal ağ çözümlerine ve grup çözümlerine SharePoint web bölümleri eklemeye devam edebilirsiniz. Ancak görsel web bölümleri aşağıdaki sınırlamalara sahiptir:

- Görsel web bölümleri Değiştirilebilir parametreleri desteklemez. Daha fazla bilgi için [bkz. Değiştirilebilir parametreler.](../sharepoint/replaceable-parameters.md)

- Kullanıcı denetimleri veya görsel web bölümleri görsel web bölümlerine sürüklenip bırakılır veya kopyalanamaz. Bu eylem derleme hatasına neden olur.

- Görsel web bölümleri, SharePoint gibi sunucu belirteçlerini doğrudan $SPUrl. Daha fazla bilgi için, sorun giderme ve çözüm sorunlarını giderme konusunun "Korumalı Web Bölümleri GörselDe Belirteç [Kısıtlamaları" SharePoint bakın.](../sharepoint/troubleshooting-sharepoint-solutions.md)

- Korumalı alan çözümünde görsel web bölümleri bazen şu hatayı alır: "Korumalı Alan Kod Ana Bilgisayar Hizmeti isteği işlemek için çok meşgul olduğundan korumalı alan kod yürütme isteği reddedildi." Bu hata hakkında daha fazla bilgi için, SharePoint [Geliştirici Ekibi Blogu'SharePoint bu gönderiye bakın.](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157)

- Sunucu tarafı JavaScript hata ayıklaması Visual Studio, ancak istemci tarafı JavaScript hata ayıklaması de destekler.

   Sunucu tarafı işaretleme dosyasına satır içi JavaScript ekleyebilirsiniz ancak işaretlemeye eklenen kesme noktaları için hata ayıklama desteklenmiyor. JavaScript'te hata ayıklamak için işaretleme dosyasındaki bir dış JavaScript dosyasına bakın ve ardından JavaScript dosyasında kesme noktaları ayarlayın.

- Satır içi kodun [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] hata ayıklaması, işaretleme dosyası yerine oluşturulan kod dosyasında yapılmalı.

- Görsel web bölümleri yönergenin kullanımını `<@ Assembly Src=` desteklemez.

- SharePoint web denetimleri [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ve bazı denetimler, korumalı alanlı ortamda SharePoint desteklenmiyor. Korumalı alan çözümünde bir görsel web bölümünde desteklenmeyen denetimler kullanılıyorsa şu hata oluşur: "'Tema' türü veya ad alanı adı 'Microsoft' ad alanı içinde yok. SharePoint. WebControls'" görüntülenir.

  Korumalı alan çözümleri hakkında daha fazla bilgi için [bkz. Korumalı alan ve grup çözümleri arasındaki farklar.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)

## <a name="create-older-style-sharepoint-based-web-parts"></a>Eski stil ve SharePoint tabanlı web bölümleri oluşturma
 Web siteniz için özel web Visual Studio oluşturmak üzere [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] şablonlarını SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] web bölümleri web bölümü altyapısı üzerine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] inşa edilmiştir ve yeni projeler için önerilen türlerdir.

 Çok az durumda, eski stil tabanlı web bölümünü kullanarak bir web SharePoint oluşturmanız gerekmektedir. Bu tür Visual Studio web bölümü oluşturmak için Visual Studio kullanabilirsiniz, ancak Visual Studio oluşturmanıza yardımcı olmak için özel olarak tasarlanmış herhangi bir şablon sağlamaz.

 Tabanlı web bölümü için daha eski bir stil SharePoint daha fazla bilgi için bkz. [Windows SharePoint Services.](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)) Eski stil tabanlı web bölümünü kullanarak bir web bölümü oluşturma hakkında daha fazla bilgi SharePoint için, bkz. [Walkthrough Creating a Basic SharePoint Web Part](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Sayfalarda web bölümleri oluşturma SharePoint gösterir.|
|[Nasıl kullanılır: Tasarımcı SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Görsel tasarım yüzeyi kullanarak web bölümleri SharePoint web bölümleri oluşturma hakkında bilgi sağlar.|
|[Nasıl SharePoint uygulama sayfası veya web bölümü için kullanıcı denetimi oluşturma](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Uygulama sayfaları ve web bölümleri tarafından uygulama içinde çalıştırılabilir özel, yeniden kullanılabilir denetimlerin nasıl oluşturul SharePoint.|
|[Adım adım kılavuz: SharePoint için web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Web bölümü için web bölümü tasarlamayı SharePoint.|
|[Adım adım kılavuz: Tasarımcı kullanarak SharePoint web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Denetimleri görsel tasarım yüzeyine sürükleyerek SharePoint web bölümü tasarlamayı açıklar.|
|[Adım adım kılavuz: SharePoint için OData görüntüleyen Silverlight web SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Bir Silverlight uygulamasını barındıran ve SharePoint listelerden veri görüntüleyen web bölümü SharePoint açıklar.|