---
title: Web Sitesi Destek Şablonları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703462"
---
# <a name="web-site-support-templates"></a>Web Sitesi Destek Şablonları
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Web sitesi projesi ve madde şablonları, yeni Web sitesi projeleri ve öğelerini sıfırdan oluşturma gereksinimini ortadan kaldırarak geliştirme sürecini hızlandıran yeniden kullanılabilir ve özelleştirilebilir Web sitesi projesi ve öğe saplamaları sağlar. Şablonlar hakkında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] daha fazla bilgi için [bkz.](../../ide/creating-project-and-item-templates.md)

## <a name="project-template-folder"></a>Proje Şablon Klasörü
 Web projesi şablonları genellikle [*Visual Studio Installation Path*]\Common7\IDE\ProjectTemplates\Web\\'e yüklenir, her biri web programlama dilinden sonra adlandırılmış bir alt klasöre.

## <a name="project-file"></a>Proje Dosyası
 Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE), şablonu doğru proje türüyle eşlenebilmek için bir proje dosyası uzantısı gerektirir. Web projelerinde proje dosyası olmadığından, sahte proje dosyası uzantısı .webproj şablonu proje türüyle eşlemek için kaydedilir.

 İsteğe bağlı olarak, Web proje sisteminin şablonu temel alan öğeler için Yeni **Öğe Ekle** iletişim kutusunda ki dil varsayılanını ayarlamasını sağlamak için şablona bir dil adı dizesi eklenebilir. Dize, dosyanın ilk satırı olmalıdır. Hem IntelliSense motor kaydında AddItemLanguageName altında kayıtlı adı eşleştirmeli hem de Project Subtype (VsTemplate) altında kayıtlı adla eşleşmelidir. Daha fazla bilgi için [Web Sitesi Destek Öznitelikleri'ne](../../extensibility/internals/web-site-support-attributes.md)bakın.

 Dize yoksa, Web proje sistemi Proje Şablonu tarafından Web projesine eklenen sayfaların Dil özniteliğini ve dosya uzantılarını temel alarak varsayılan dili belirlemeye çalışır.

## <a name="project-templates"></a>Proje Şablonları
 Web sitesi proje şablonları, **Dosya** menüsündeki **Yeni Web Sitesi** komutuna yanıt olarak yeni Web siteleri oluşturmak için kullanılır. Üç Web sitesi proje türü şu anda desteklenir:

- Boş Web sitesi projeleri

- Web sitesi projeleri

- Web hizmeti projeleri

### <a name="empty-web-site-projects"></a>Boş Web Sitesi Projeleri
 Bu dosyalar, **Dosya** > **Yeni Web Sitesi**seçtikten sonra kullanılabilir Boş Web **Sitesi** komutu, yanıt olarak yeni bir boş Web sitesi oluşturmak:

- EmptyWeb.vstemplate

     Yeni boş Web sitesinin oluşturulmasına rehberlik eden şablon dosyası.

- EmptyWeb.webproj

     Bu dosya, proje şablon sisteminin bir yapıdır. EmptyWeb.vstemplate dosyasındaki proje dosyası başvurularını karşılar.

### <a name="web-site-projects"></a>Web Sitesi Projeleri
 Bu dosyalar, **Yeni Dosya** > Sitesi'ni seçtikten sonra kullanılabilen **ASP.NET Web Sitesi** komutuna yanıt olarak yeni bir Web**sitesi**oluşturur:

- Default.aspx

     Yeni Web sitesinin varsayılan giriş sayfası. Dil özniteliği dilin arkasındaki kodları belirtir ve CodeFile özniteliği bu sayfayla ilişkili kod arkasında kod içeren bağımlı dosyayı belirtir.

- Default.aspx. *uzantısı*

     Varsayılan giriş sayfasının kod arkasındaki kodu içeren bağımlı dosya. Dilin arkasındaki kodlar bu dosyanın *uzantısını* belirler.

- Config

     Root web.site yapılandırma dosyası.

- WebApplication.vstemplate

     Web sitesi çözümünün içeriğini belirleyen ve App_Data klasörünün oluşturulmasını zorlayan şablon dosyası.

- WebApplication.webproj

     Bu dosya, proje şablon sisteminin bir yapıdır. WebApplication.vstemplate dosyasındaki proje dosyası başvurusunu karşılar.

### <a name="web-service-projects"></a>Web Hizmet Projeleri
 Bu dosyalar, **Dosya** > **Yeni Web Sitesi**seçtikten sonra kullanılabilir ASP.NET Web **Hizmeti** komutu, yanıt olarak yeni bir Web sitesi oluşturmak:

- Service.asmx

     Yeni Web hizmetiiçin HTML sayfası. Dil özniteliği dilin arkasındaki kodları belirtir ve CodeBehind özniteliği bu hizmetle ilişkili kod arkasında kod içeren bağımlı dosyayı belirtir.

- Hizmet. *Uzantısı*

     Hizmet sınıfını uygulayan bağımlı dosya. Dilin arkasındaki kodlar bu dosyanın *uzantısını* belirler.

- Config

- Root web.site yapılandırma dosyası.

- WebService.vstemplate

     Web sitesi çözümünün içeriğini belirleyen ve App_Data ve App_Code klasörlerinin oluşturulmasını zorlayan şablon dosyası. Hizmet. *uzantı* dosyası App_Code klasörüne kopyalanır.

- WebService.webproj

     Bu dosya, proje şablon sisteminin bir yapıdır. WebService.vstemplate dosyasındaki proje dosyası başvurularını karşılar.

## <a name="project-item-template-folder"></a>Proje Öğesi Şablon Klasörü
 Web proje öğesi şablonları genellikle [*Visual Studio Yükleme Yolu*]\Common7\IDE\ItemTemplates\Web'de\\, her biri web programlama dilinden sonra adlandırılmış bir alt klasöre yüklenir.

## <a name="project-item-templates"></a>Proje Öğesi Şablonları
 Web sitesi proje öğesi şablonları, **Varolan Öğe Ekle** komutuna yanıt olarak bir Web sitesine yeni Web sayfaları eklemek için kullanılır. Bu tür Web sayfaları şu anda desteklenir:

- Yeni sınıf

- Yeni HTML sayfası

- Yeni Web Formu

- Yeni ana sayfa

### <a name="new-class"></a>Yeni Sınıf
 Bu şablon, **Yeni Sınıf Ekle** komutuna yanıt olarak boş bir sınıf tanımlayan yeni bir kaynak dosyası oluşturur.

- Sınıfı. *Uzantısı*

     Boş sınıfı uygulayan kaynak dosya. Dilin arkasındaki kodlar bu dosyanın *uzantısını* belirler.

- Class.vstemplate

     Kaynak dosyayı oluşturan ve içeriğini belirleyen şablon dosyası.

### <a name="new-html-page"></a>Yeni HTML Sayfası
 Bu şablon, **Yeni HTML Sayfası Ekle** komutuna yanıt olarak yeni bir Web sayfası oluşturur.

- HTMLPage.htm

     Web sayfasının başlangıç içeriği. Bu Web sayfası genellikle bağımlı dosyanın arkasında ilişkili kod yoktur. İlişkili bir kod arkasında dosya içeren akıllı bir sayfa oluşturmak için Bunun yerine Web Formu şablonu kullanın.

- HTMLPage.vstemplate

     Web sayfasını oluşturan ve içeriğini belirleyen şablon dosyası.

### <a name="new-webform"></a>Yeni WebFormu
 Bu şablon, **Yeni Web Formu Ekle** komutuna yanıt olarak yeni bir akıllı Web sayfası oluşturur.

 Kaynak dosyanın arkasında bağımlı bir kod oluşturmak için, **ayrı bir dosyada kodu yerleştir'i**seçin. Aksi takdirde, boş bir komut dosyası bloğu olan \<tek bir Web sayfası oluşturulur ve bağımlı bir dosyayı bağlamak için yönergelere % %> yoktur.

 Seçili bir ana sayfa için içerik sayfası oluşturmak için **ana sayfa yı seçin'** i seçin.

- WebForm.aspx

     Web sayfasının başlangıç içeriği. Bu Web sayfası, bağımlı dosyanın arkasında ilişkili kod yoktur.

- WebForm_cb.aspx

     Web sayfasının başlangıç içeriği. Bu Web sayfası, bağımlı dosyanın arkasında ilişkili bir koda sahiptir.

- Kod arkası. *Uzantısı*

     Webform sınıfını uygulayan bağımlı dosya. Dilin arkasındaki kodlar bu dosyanın *uzantısını* belirler.

- İçerikPage.aspx

     İçerik sayfası olarak Web sayfasının başlangıç içeriği. Bu Web sayfası, bağımlı dosyanın arkasında ilişkili kod yoktur.

- ContentPage_cb.aspx

     İçerik sayfası olarak Web sayfasının başlangıç içeriği. Bu Web sayfası, bağımlı dosyanın arkasında ilişkili bir koda sahiptir.

- WebForm.vstemplate

     Yeni web sayfasının içeriğini ve varsa bağımlı dosyasını belirleyen şablon dosyası.

### <a name="new-master-page"></a>Yeni Ana Sayfa
 Bu şablon, **Yeni Ana Sayfa Ekle** komutuna yanıt olarak yeni bir ana sayfa oluşturur.

 Kaynak dosyanın arkasında bağımlı bir kod oluşturmak için, **ayrı bir dosyada kodu yerleştir'i**seçin. Aksi takdirde, boş bir komut dosyası bloğu olan \<tek bir Web sayfası oluşturulur ve bağımlı bir dosyayı bağlamak için % Sayfa %> yönergeleri yoktur.

- MasterPage.master

     Ana sayfanın başlangıç içeriği. Bu ana sayfabağımlı dosyanın arkasında ilişkili kod yoktur.

- MasterPage_cb.usta

     Ana sayfanın başlangıç içeriği. Bu ana sayfa, bağımlı dosyanın arkasında ilişkili bir koda sahiptir.

- Kod arkası. *uzantısı*

     Ana sayfa sınıfını uygulayan bağımlı dosya. Dilin arkasındaki kodlar bu dosyanın *uzantısını* belirler.

- MasterPage.vstemplate

     Yeni ana sayfanın içeriğini ve varsa bağımlı dosyasını belirleyen şablon dosyası.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)
