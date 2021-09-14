---
title: Sorun SharePoint Çözümleri | Microsoft Docs
description: Hata ayıklayıcının hata ayıklayıcısını kullanarak SharePoint hangi sorunların veya uyarıların Visual Studio bakın.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f4c69d5464d23fdeacbb77fb5af7b178a70d2fa5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636814"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint sorunlarını giderme
  Hata ayıklayıcıyı kullanarak çözümlerde hata SharePoint aşağıdaki sorunlar veya [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] uyarılar oluşabilir. Daha fazla bilgi için bkz. [Hata Ayıklama SharePoint 2007 İş Akışı Çözümleri.](/previous-versions/bb386166(v=vs.100))

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Korumalı alan görsel web parçalarında belirteç kısıtlamaları
 Korumalı alanlı çözümlerde görsel web bölümleri, $SPUrl çalışma zamanının desteklediği SharePoint belirteçleri işleyemektedir. Sonuç olarak URL çözümlenmezse ve görsel web Tasarım görünümü tasarımcısında doğrudan aşağıdaki örnekte olduğu gibi bir betik öğesinde başvurursanız içeriğin önizlemesini görüntülenemiyor:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Bu sınırlamaya bir çözüm olarak belirteci çözmek için değişmez sabitleri kullanarak bu belirteci bakın:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Proje ve proje öğeleri adlarında karakter kısıtlamaları
 Proje ve proje öğelerinin adları yalnızca 2010'daki bir dağıtım yolunda geçerli SharePoint içerebilir. Başka hiçbir karaktere izin verilmez.

### <a name="error-message"></a>Hata iletisi
 "Geçersiz karakterler" hata iletisi.

### <a name="resolution"></a>Çözüm
 Proje ve proje SharePoint adları için yalnızca aşağıdaki karakterleri kullanın:

- Alfasayısal ASCII karakterleri

- Alan

- Nokta (.)

- Virgül (,)

- Alt çizgi (_)

- Tire (-)

- Ters eğik çizgi ( \\ )

  Bir proje paketlenenin doğrulama kuralı, dağıtıyorsanız her dosya için dağıtım yolu özelliğinin yalnızca bu geçerli karakterleri içerdiğini doğrular.

## <a name="errors-when-creating-custom-fields"></a>Özel alanlar oluşturulurken hatalar
 içinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özel alanlar XML'de tanımlanır. Bir alan tanımlanmamışsa veya belirli bir biçim kullanılarak başvurulmasa hatalar oluşabilir.

### <a name="error-message"></a>Hata iletisi
 Paketleme zamanında "Geçersiz karakterler" hata iletisi.

### <a name="resolution"></a>Çözüm
 Bir alan tanımının kimliği, aşağıdaki örnekte de olduğu gibi küme ayraçları ile çevreli bir GUID olması gerekir:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Aşağıdaki örnekte de olduğu gibi, içerik türünde bir alan başvurusu, başlangıç/bitiş öğeleri ( ) kullanılarak değil boş öğe biçimi () kullanılarak \<FieldRef /> \<FieldRef> \</FieldRef> tanımlanmalıdır:

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Alanın kaynak XML'i yanlış biçimlendirilmişse, geçerli bir XML dosyası değilse veya başka bir sorun sergileniyorsa, "Dosya ayrıştırılaamıyor" hatası oluşur.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Yeni İngilizce olmayan site tanımları, dağıtımdan sonra site oluşturma sayfasında görünmüyor
 İngilizce olmayan bir sürümünü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] (1033   dışında bir yerel ayarları olan bir sürüm) kullanarak bir site tanımı oluşturduktan ve dağıtın, SharePoint Özelleştirmeler sekmesi Şablon Seçimi kutusunda görünmez  ve yeni site şablonu Yeni SharePoint Sitesi sayfasında görünmez.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorun, webtemp site tanımı yapılandırma dosyasının **Path** özelliğinde bulunan yanlış bir değerden (örneğin, *webtemp_SiteDefinitionProject1.xml.* Dağıtım Konumu altında bulunan webtemp dosyasının  **Path** özelliğinde, 1033'ü uygun yerel değeriyle [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] değiştirir. Örneğin, Bir Japonca yerel ayarlarını kullanmak için değeri 1041 olarak değiştirebilirsiniz. Daha fazla bilgi için [bkz. Microsoft tarafından Atanan Yerel Kimlikler.](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Temiz bir sistemde bir iş akışı projesi dağıtıldığında hata görünüyor
 Temiz bir sistemde içinde bir iş akışı projesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dağıtırsanız bu sorun oluşur. Temiz bir sistem, yeni yüklemesi ve yüklemesi olan ancak SharePoint iş akışı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projesine sahip bir bilgisayardır.

### <a name="error-message"></a>Hata iletisi
 İş Akışı SharePoint listesi bulunamaz.

### <a name="resolution"></a>Çözüm
 Bu hata, eksik bir İş Akışı Geçmişi listesi nedeniyle oluşur. Geliştirme ortamı temiz bir sistem olduğundan, hiçbir iş akışı dağıtlanmadı ve İş Akışı Geçmişi listesi henüz yok. Bu sorunu çözmek için, İş Akışı Geçmişi listesinin oluşturularak iş akışı sihirbazını yeniden açın.

##### <a name="to-reenter-the-workflow-wizard"></a>İş akışı sihirbazını yeniden girmeden önce

1. Bu **Çözüm Gezgini** iş akışı düğümünü seçin.

2. Özellikler **penceresinde,** üç nokta düğmesi olan herhangi bir özellikte üç nokta (...) düğmesini seçin.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Güncelleştirilmiş görüntüyü görüntülemek için kullanıcının hata ayıklama sırasında tarayıcıda uygulama sayfasını yenilemesi gerekir
 Görüntü denetimi gibi bir görüntü görüntüleyen denetime sahip bir uygulama sayfası içeren bir SharePoint çözümünde hata ayıklarsanız, görüntüde yapılan değişiklikleri görüntülemek için tarayıcıda sayfayı [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] yenilemeniz gerekir.

## <a name="error-the-site-location-is-not-valid"></a>Hata: Site konumu geçerli değil
 Yüklü değilse bu [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] sorun oluşabilir. Ayrıca, Özelleştirme Sihirbazı'nda belirtilen SharePoint Web sitesine yönetici erişiminiz SharePoint **oluşabilir.**

### <a name="error-message"></a>Hata iletisi

- SharePoint konumu geçerli değil.

### <a name="resolution"></a>Çözüm

- [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]yükleyin.

- Web sitesine yönetici erişimine sahip SharePoint emin olmak. Daha fazla bilgi için, SharePoint Server'da hizmet uygulamalarının yöneticilerini [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] atama veya kaldırma çevrimiçi [makalesine bakın.](/sharepoint/administration/assign-or-remove-administrators-of-service-applications)

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Olay alıcı projesinde site silme web olayı oluşmaz
 Bir olay alıcı projesi oluşturma ve "site siliniyor" gibi belirli Web olaylarını seçmeniz durumunda olay hiçbir zaman oluşmaz.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Site düzeyindeki olayları işlemek için özellik kapsamının "Site" olması, ancak olay alıcısı projeleri için varsayılan özellik kapsamı "Web" olduğu için bu sorun oluşur. Etkilenen Web olayları:

- Bir site siliniyor (WebDeleting)

- Bir site silindi (WebDeleted)

- Bir site taşınıyor (WebMoving)

- Bir site taşındı (WebMoved)

  Sorunu çözmek için olay alıcısının özellik kapsamını aşağıdaki gibi değiştirin.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Olay alıcısının özellik kapsamını değiştirmek için

1. Bu **Çözüm Gezgini,** dosyaya çift tıklayarak veya kısayol menüsünü  açıp Aç'ı seçerek olay alıcısının *.feature* dosyasını Özellik Tasarımcısı'nda **açın.**

2. Kapsam'ın yanındaki **oku seçin** ve sonra görüntülenen listeden **Site'yi** seçin.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>İş verileri bağlantı modeli projesinde tanımlayıcının adı değiştirildikten sonra dağıtım hatası görüntülenir
 Bu sorun, bir İş Verileri Bağlantısı (BDC) modelinde bir varlığın tanımlayıcı adını değiştirir ve ardından çözümü dağıtmayı denersiniz.

### <a name="error-messages"></a>Hata iletileri

- \<*model name*> aşağıdaki Dış İçerik Türü etkinleştirme hatalarına sahip ...

- Adı ' olan IMetadataObject, Alan 'name' içinde yinelenen bir \<*model name*> değere sahip...

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için modeli el ile silin ve çözümü yeniden dağıtın.  Aşağıdaki araçlardan birini kullanarak modeli silebilirsiniz:

- SharePoint 2010 Merkezi Yönetimi. Daha fazla bilgi için Bkz. Microsoft TechNet Web Model Yönetimi [BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) kimlik bilgileri.

- Windows PowerShell. Modeli silmek için komut istemine şu komutu yazabilirsiniz: **Remove-SPBusinessDataCatalogModel**. Daha fazla bilgi için Microsoft TechNet Web sitesinde [genel cmdlet'ler (SharePoint Server 2010)](/powershell/module/sharepoint-server) makalesini ziyaret edin.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Web'de görsel bir web bölümünü görüntülemeye çalışsanız hata SharePoint
 Kullanıcı denetimi path **özelliği** "CONTROLTEMPLATES" dizesiyle başlamazsa bu sorun \\ oluşur.

### <a name="error-messages"></a>Hata iletileri

- '/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* .ascx' dosyası yok.

- '/' Uygulamasında Sunucu Hatası.

### <a name="resolution"></a>Çözüm

##### <a name="to-resolve-this-issue"></a>Bu sorunu çözmek için

1. **Çözüm Gezgini**, dosya adı uzantısı *. ascx* olan kullanıcı denetim dosyasını seçin.

2. Menü çubuğunda   >  **Özellikler penceresini** görüntüle ' yi seçin.

3. **Özellikler** penceresinde **dağıtım konumu** düğümünü genişletin.

4. **Path** özelliğinin DEĞERININ "ControlTemplates" dizesiyle başladığı emin olun \\ .

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Bir görev formu alanı içeren içeri aktarılmış bir yeniden kullanılabilir iş akışı çalıştırıldığında hata görüntülenir
 Bu sorun, bir alan içeren bir görev formu içeren bir iş akışını içeri aktarırsanız ve ardından yeni iş akışını içeri aktardığınız aynı sistemde çalıştırırsanız oluşur.

### <a name="error-message"></a>Hata iletisi
 ' Etkinleştirme özellikleri ' dağıtım adımında hata oluştu: [*GUID*] özelliğinde tanımlanan [*GUID] kimliğine* sahip alan, geçerli site koleksiyonunda veya bir alt sitede bulundu.

### <a name="resolution"></a>Çözüm
 Bu hata, içinde yeniden kullanılabilir yeniden kullanılabilir Iş akışı projesi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] görev formu alan kimliklerini değiştirmediğinden oluşan alan kimliği çakışmalarının sonucudur. İçeri aktarılan bir iş akışını orijinal iş akışını içeren aynı sunucuya dağıtırsanız, alan KIMLIĞI çakışmaları oluşur.

 Bu sorunu çözmek için bul ve Değiştir özelliğini kullanarak içeri aktarılan tüm iş akışı dosyalarındaki alan KIMLIĞI özniteliğinin değerini değiştirin.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Yeniden adlandırılmış bir içeri aktarılan liste örneği çalıştırıldığında hata görüntülenir
 Bu sorun, içeri aktarılan bir liste örneğini yeniden adlandırırsanız ve sonra ' de çalıştırırsanız oluşur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

### <a name="error-message"></a>Hata iletisi
 Derleme hatası: dağıtım adımı ' etkinleştirme özellikleri ' sırasında hata oluştu: dosya Template\Features \\ [*Import Project*<em>Feature</em>*Name*] \files\lists \\ [*eski*<em>liste Name</em>] \Schema.xml yok.

### <a name="resolution"></a>Çözüm
 Bir liste örneğini içeri aktardığınızda, liste örneğinin Elements.xml dosyasına CustomSchema adlı bir öznitelik eklenir. Elements.xml, liste örneği için özel bir schema.xml yolunu içerir. İçindeki liste örneğini yeniden adlandırdığınızda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , özel schema.xml için dağıtım yolu değişir, ancak CustomSchema özniteliğinin yol değeri güncellenmez. Sonuç olarak, liste örneği, özellik etkinleştirildiğinde CustomSchema özniteliği tarafından belirtilen eski yoldaki *schema.xml* dosyasını bulamaz.

 Bu sorunu çözmek için, CustomSchema özniteliğinde *schema.xml* dosyasının Dağıtım konumunun yolunu güncelleştirin.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint hata ayıklama oturumu ııs tarafından sonlandırıldı
 bu sorun, bir SharePoint çözümünde bir kesme noktası ayarlarsanız [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , çalıştırmak için **F5** tuşunu ve ardından 90 saniyeden daha uzun bir kesme noktasında kalmasını sağlayabilirsiniz.

### <a name="error-message"></a>Hata iletisi
 hata ayıklanan Web sunucusu işlemi Internet Information Services (ııs) tarafından sonlandırıldı. IIS 'deki uygulama havuzu ping ayarlarını yapılandırarak bu sorundan kaçınabilirsiniz. Daha fazla ayrıntı için yardıma bakın.

### <a name="resolution"></a>Çözüm
 Varsayılan olarak, IIS uygulama havuzu uygulamayı kapatmadan önce bir uygulamanın yanıt vermesi 90 saniye bekler. Bu işlem, uygulamanın "ping" olarak bilinir. Bu sorunu çözmek için, bekleme süresini artırabilir ya da uygulama için ping komutunu tamamen devre dışı bırakabilirsiniz.

##### <a name="to-access-the-iis-app-pool-settings"></a>IIS uygulama havuzu ayarlarına erişmek için

1. IIS Yöneticisi'ni açın.

2. **bağlantılar** bölmesinde SharePoint sunucusu düğümünü genişletin ve ardından **uygulama havuzları** düğümünü seçin.

3. **uygulama havuzları** sayfasında, uygulama havuzunu SharePoint (genellikle "SharePoint-80") seçin ve ardından **eylemler** bölmesinde **gelişmiş Ayarlar** bağlantısını seçin.

4. IIS zaman aşımından önceki bekleme süresini artırmak için, **ping en yüksek yanıt süresi (saniye)** değerini 90 saniyeden daha büyük bir değere değiştirin.

5. IIS ping komutunu devre dışı bırakmak için **ping etkin** ayarını **false** olarak ayarlayın.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Otomatik geri çekme, SharePoint yalnız bırakılmış liste örneğini bırakır
 Aşağıdaki adımları uygulamanız durumunda bu sorun oluşur.

1. İçinde liste örneği olan bir liste tanımı oluşturun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Çözümü çalıştırmak için **F5** tuşunu seçin.

3. hata ayıklamayı durdurun veya SharePoint sitesini kapatın.

4. SharePoint sitesini yeniden açın ve liste örneğini açın.

### <a name="error-message"></a>Hata iletisi
 '/' Uygulamasında sunucu hatası.

### <a name="resolution"></a>Çözüm
 bu durum, bir SharePoint çözümünün hata ayıklama oturumunu kapattıktan sonra otomatik olarak geri çekin özelliğinin çözümü geri çeker. geri çekme, liste tanımını SharePoint siler, ancak listenin örneğini silmez. Liste örneği için temel alınan liste tanımı gereklidir.

 Bu sorunu çözmek için, menü çubuğunda **Yapı** dağıtımı ' nı seçerek çözümü dağıtın  >  . ( **F5** tuşunu seçerek çözümde hata ayıklamayın.) Ardından SharePoint içindeki liste örneğini silin.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>özgün SharePoint çözümü, dışarıya aktarılmış bir sürümle değiştirilmiştir
 bir SharePoint çözümü dışarı aktarırsanız, çözümü içine aktarın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve ardından, yeniden dışarı aktarılan siteye geri dağıtırsanız, özgün SharePoint çözümü değiştirilmiştir. Çözümü, üzerinde etkin bir çözüm etkinleştirilmemiş bir sunucuya dağıtırsanız bu sorun oluşmaz.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bir çözümün verildiği sitede üzerine yazılmasını önlemek için, SolutionId 'nin GUID 'Lerini ve projedeki tüm içeri aktarılan özelliklerin özellik kimliklerini değiştirin [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

## <a name="error-appears-when-debugging-starts"></a>Hata ayıklama başladığında hata görüntülenir
 Visual Studio bir SharePoint çözümünde hata ayıklamaya başladığınızda, bir hata Visual Studio, belirtilen anahtarın sözlükte olmadığı için Web.config dosyayı yükleyemediğini belirtir.

### <a name="error-message"></a>Hata iletisi
 Web.config yapılandırma dosyası yüklenemedi. Hatalı biçimlendirilmiş XML öğeleri için dosyayı denetleyin ve yeniden deneyin. Şu hata oluştu: belirtilen anahtar sözlükte yoktu.

### <a name="resolution"></a>Çözüm
 bu sorunu çözmek için, Visual Studio SharePoint projesinin Site URL 'si özellik değerinin, web uygulamasının alternatif erişim eşlemeleri için varsayılan bölgeye atanan url ile eşleştiğinden emin olun. URL için Intranet gibi başka bir bölge kullanarak hatayı çözümlenemez. Projenin site URL 'SI ve varsayılan bölgedeki URL eşleşmelidir. alternatif erişim eşlemelerine erişmek için SharePoint 2010 merkezi yönetim yardımcı programını açın, **uygulama yönetimi** bağlantısını seçin ve ardından **Web uygulamaları** altında, **alternatif erişim eşlemelerini yapılandır** bağlantısını seçin. Daha fazla bilgi için bkz. [Web uygulamaları için bölge oluşturma](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Ayrıca bkz.

- [paketleme ve dağıtım SharePoint sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [SharePoint çözümleri oluşturun ve hata ayıklayın](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Visual Studio'da Hata Ayıklama](../debugger/debugger-feature-tour.md)