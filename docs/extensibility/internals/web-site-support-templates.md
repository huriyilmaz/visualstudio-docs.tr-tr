---
title: Web sitesi destek şablonları | Microsoft Docs
description: Web sitesi destek şablonları hakkında bilgi edinin. Visual Studio web sitesi projesi ve öğe şablonları, yeniden kullanılabilir ve özelleştirilebilir web sitesi projesi ve öğe saplamalarını sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6480b21cc4907e45b174b69418f1d10177f36440597949fd8a1806246016dc27
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414161"
---
# <a name="web-site-support-templates"></a>Web Sitesi Destek Şablonları
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web sitesi projesi ve öğe şablonları, yeni Web sitesi projeleri ve öğeleri sıfırdan oluşturma gereksinimini ortadan kaldırarak geliştirme sürecini hızlandıran, yeniden kullanılabilir ve özelleştirilebilir Web sitesi projesi ve öğe saplamaları sağlar. şablonlar hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bkz. [Project ve öğe şablonları oluşturma](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Project Şablon klasörü
 web projesi şablonları genellikle, web programlama dilinden sonra adlandırılmış bir alt klasörde bulunan [*Visual Studio yükleme yolu*] \Common7\IDE\ProjectTemplates\Web üzerine yüklenir \\ .

## <a name="project-file"></a>Proje Dosyası
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE), bir şablonu doğru proje türüyle eşlemek için bir proje dosyası uzantısı gerektirir. Web projelerinin bir proje dosyası olmadığından, şablonu proje türüyle eşlemek için. webproj sözde proje dosyası uzantısı kaydedilir.

 İsteğe bağlı olarak, Web projesi sisteminin şablona dayalı öğeler için **Yeni öğe Ekle** iletişim kutusunda varsayılan dil ayarlaması için bir dil adı dizesi şablona eklenebilir. Dize dosyanın ilk satırı olmalıdır. ıntellisense altyapısı kaydında AddItemLanguageName altında kayıtlı ad ve Project alt türü (vstemplate) altında kayıtlı ad ile eşleşmelidir. Daha fazla bilgi için bkz. [Web sitesi destek öznitelikleri](../../extensibility/internals/web-site-support-attributes.md).

 dize yoksa, web proje sistemi, Project şablonu tarafından web projesine eklenen sayfaların dil özniteliği ve dosya uzantılarına göre varsayılan dili saptamaya çalışır.

## <a name="project-templates"></a>Project Şablondan
 Web sitesi proje şablonları, **Dosya** menüsündeki **Yeni Web sitesi** komutuna yanıt olarak yeni Web siteleri oluşturmak için kullanılır. Üç Web sitesi proje türü şu anda destekleniyor:

- Boş Web sitesi projeleri

- Web sitesi projeleri

- Web hizmeti projeleri

### <a name="empty-web-site-projects"></a>Boş Web sitesi projeleri
 Bu dosyalar, **Dosya** yeni Web sitesi ' ni seçtikten sonra kullanılabilen **boş Web sitesi** komutuna yanıt olarak yeni bir boş Web sitesi oluşturur  >  :

- EmptyWeb. vstemplate

     Yeni boş Web sitesinin oluşturulmasını yönlendiren şablon dosyası.

- EmptyWeb. webproj

     Bu dosya, proje şablonu sisteminin yapıtıdır. EmptyWeb. vstemplate dosyasındaki proje dosyası başvurusunu karşılar.

### <a name="web-site-projects"></a>Web sitesi projeleri
 bu dosyalar, **dosya** yeni web sitesi ' ni seçtikten sonra kullanılabilir olan **ASP.NET web sitesi** komutuna yanıt olarak yeni bir web sitesi oluşturur  >  :

- Default.aspx

     Yeni Web sitesi için varsayılan giriş sayfası. Language özniteliği codebehind dilini belirtir ve CodeFile özniteliği bu sayfayla ilişkili olan codebehind kodunu içeren bağımlı dosyayı belirtir.

- Default. aspx. *uzantı*

     Varsayılan giriş sayfası için codebehind kodunu içeren bağımlı dosya. CodeBehind dili bu dosyanın *uzantısını* belirler.

- web.config

     Kök web.site yapılandırma dosyası.

- WebApplication. vstemplate

     Web sitesi çözümünün içeriğini belirleyen ve App_Data klasörünün oluşturulmasını zorlayan şablon dosyası.

- WebApplication. webproj

     Bu dosya, proje şablonu sisteminin yapıtıdır. WebApplication. vstemplate dosyasındaki proje dosyası başvurusunu karşılar.

### <a name="web-service-projects"></a>Web hizmeti projeleri
 bu dosyalar, **dosya** yeni web sitesi ' ni seçtikten sonra kullanılabilir olan **ASP.NET web hizmeti** komutuna yanıt olarak yeni bir web sitesi oluşturur  >  :

- Service. asmx

     Yeni Web hizmeti için HTML sayfası. Language özniteliği codebehind dilini belirtir ve CodeBehind Özniteliği bu hizmetle ilişkili olan codebehind kodunu içeren bağımlı dosyayı belirtir.

- Hizmetle. *uzantının*

     Hizmet sınıfını uygulayan bağımlı dosya. CodeBehind dili bu dosyanın *uzantısını* belirler.

- web.config

- Kök web.site yapılandırma dosyası.

- WebService. vstemplate

     Web sitesi çözümünün içeriğini belirleyen ve App_Data ve App_Code klasörlerinin oluşturulmasına zorlayan şablon dosyası. Hizmet. *uzantı* dosyası App_Code klasörüne kopyalanır.

- WebService. webproj

     Bu dosya, proje şablonu sisteminin yapıtıdır. WebService. vstemplate dosyasındaki proje dosyası başvurusunu karşılar.

## <a name="project-item-template-folder"></a>Project Öğe şablonu klasörü
 web projesi-öğe şablonları genellikle, web programlama dilinden sonra adlandırılmış bir alt klasörde bulunan [*Visual Studio yükleme yolu*] \Common7\IDE\ItemTemplates\Web \\ ' a yüklenir.

## <a name="project-item-templates"></a>Project Öğe şablonları
 Web sitesi proje öğesi şablonları, **var olan öğe Ekle** komutuna yanıt olarak bir Web sitesine yeni Web sayfaları eklemek için kullanılır. Şu anda bu tür web sayfaları desteklenmektedir:

- Yeni sınıf

- Yeni HTML sayfası

- Yeni Web formu

- Yeni Ana sayfa

### <a name="new-class"></a>Yeni sınıf
 Bu şablon, **Yeni sınıf Ekle** komutuna yanıt olarak boş bir sınıfı tanımlayan yeni bir kaynak dosyası oluşturur.

- Sınıfı. *uzantının*

     Boş sınıfı uygulayan kaynak dosya. CodeBehind dili bu dosyanın *uzantısını* belirler.

- Class. vstemplate

     Kaynak dosyayı oluşturan ve içeriğini belirleyen şablon dosyası.

### <a name="new-html-page"></a>Yeni HTML sayfası
 Bu şablon **yenı HTML sayfası ekle** komutuna yanıt olarak yeni bir Web sayfası oluşturur.

- HTMLPage.htm

     Web sayfasının başlangıç içeriği. Bu Web sayfasına genellikle ilişkili bir codebehind bağımlı dosyası yok. İlişkili bir codebehind dosyası ile akıllı sayfa oluşturmak için, bunun yerine Web formu şablonunu kullanın.

- HTMLPage. vstemplate

     Web sayfasını oluşturan ve içeriğini belirleyen şablon dosyası.

### <a name="new-webform"></a>Yeni WebForm
 Bu şablon yeni **Web formu Ekle** komutuna yanıt olarak yeni bir akıllı Web sayfası oluşturur.

 Bağımlı bir codebehind kaynak dosyası oluşturmak için **kodu ayrı dosyaya yerleştir**' i seçin. Aksi halde, boş bir betik bloğu olan ve \<% Page %> bağımlı bir dosyayı bağlama yönergesi olmayan tek bir Web sayfası oluşturulur.

 Seçili ana sayfa için bir içerik sayfası oluşturmak için **Ana sayfa seç**' i seçin.

- WebForm. aspx

     Web sayfasının başlangıç içeriği. Bu Web sayfasına ilişkili bir codebehind bağımlı dosyası yok.

- WebForm_cb. aspx

     Web sayfasının başlangıç içeriği. Bu Web sayfasında ilişkili bir codebehind bağımlı dosyası bulunur.

- CodeBehind. *uzantının*

     WebForm sınıfını uygulayan bağımlı dosya. CodeBehind dili bu dosyanın *uzantısını* belirler.

- ContentPage. aspx

     Web sayfasının içerik sayfası olarak başlangıç içeriği. Bu Web sayfasına ilişkili bir codebehind bağımlı dosyası yok.

- ContentPage_cb. aspx

     Web sayfasının içerik sayfası olarak başlangıç içeriği. Bu Web sayfasında ilişkili bir codebehind bağımlı dosyası bulunur.

- WebForm. vstemplate

     Varsa, yeni Web sayfasının ve bağımlı dosyanın içeriğini belirleyen şablon dosyası.

### <a name="new-master-page"></a>Yeni Ana sayfa
 Bu şablon **Yeni Ana sayfa ekle** komutuna yanıt olarak yeni bir ana sayfa oluşturur.

 Bağımlı bir codebehind kaynak dosyası oluşturmak için **kodu ayrı dosyaya yerleştir**' i seçin. Aksi halde, boş bir betik bloğu olan ve \<% Page %> bağımlı bir dosyayı bağlama yönergesi olmayan tek bir Web sayfası oluşturulur.

- MasterPage. Master

     Ana sayfanın başlangıç içeriği. Bu ana sayfaya ilişkili bir codebehind bağımlı dosyası yok.

- MasterPage_cb. Master

     Ana sayfanın başlangıç içeriği. Bu ana sayfada, ilişkili bir codebehind bağımlı dosyası var.

- CodeBehind. *uzantı*

     Ana sayfa sınıfını uygulayan bağımlı dosya. CodeBehind dili bu dosyanın *uzantısını* belirler.

- MasterPage. vstemplate

     Varsa, yeni ana sayfanın ve bağımlı dosyanın içeriğini belirleyen şablon dosyası.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Sitesi Desteği](../../extensibility/internals/web-site-support.md)
