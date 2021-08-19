---
title: SharePoint çözümlerinde sorun giderme | Microsoft Docs
description: Visual Studio hata ayıklayıcısını kullanarak SharePoint çözümlerinde hata ayıkladığınızda oluşabilecek sorun veya uyarıların neler olabileceğini görün.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156246"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint çözümlerinde sorun giderme
  hata ayıklayıcıyı kullanarak SharePoint çözümlerinde hata ayıkladığınızda aşağıdaki sorunlar veya uyarılar oluşabilir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . daha fazla bilgi için bkz. [SharePoint 2007 iş akışı çözümlerinde hata ayıklama](/previous-versions/bb386166(v=vs.100)).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Korumalı görsel Web bölümlerinde belirteç kısıtlamaları
 korumalı çözümlerin Visual web bölümleri, SharePoint çalışma zamanının desteklediği $SPUrl gibi standart belirteçleri işleyemez. Sonuç olarak, URL çözümlenmez ve Visual Web Bölümü Tasarımcısında Tasarım görünümü içeriği, aşağıdaki örnekte olduğu gibi doğrudan bir betik öğesinde ifade ederseniz önizleyemezsiniz:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Bu sınırlamaya geçici bir çözüm bulmak ve belirteci çözmek için, değişmez değerleri kullanarak buna başvurun:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Projelerin ve proje öğelerinin adlarındaki karakter kısıtlamaları
 projelerin ve proje öğelerinin adları yalnızca SharePoint 2010 ' deki bir dağıtım yolunda geçerli olan karakterleri içerebilir. Başka hiçbir karaktere izin verilmez.

### <a name="error-message"></a>Hata iletisi
 "Geçersiz karakterler" hata iletisi.

### <a name="resolution"></a>Çözüm
 SharePoint projelerinin ve proje öğelerinin adları için yalnızca aşağıdaki karakterleri kullanın:

- Alfasayısal ASCII karakterleri

- Alan

- Nokta (.)

- Virgül (,)

- Alt çizgi (_)

- Kısa çizgi (-)

- Ters eğik çizgi ( \\ )

  Bir proje paketlendiğinde, bir doğrulama kuralı, dağıttığınız her bir dosyanın dağıtım yolu özelliğinin yalnızca bu geçerli karakterleri içerdiğini doğrular.

## <a name="errors-when-creating-custom-fields"></a>Özel alanlar oluşturulurken hatalar oluştu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]' De, özel alanlar xml içinde tanımlanmıştır. Bir alan, belirli bir biçim kullanılarak tanımlanmamışsa veya başvurulmuyorsa hatalar oluşabilir.

### <a name="error-message"></a>Hata iletisi
 Paketleme zamanında "geçersiz karakterler" hata iletisi.

### <a name="resolution"></a>Çözüm
 Aşağıdaki örnekte gösterildiği gibi, bir alan tanımının KIMLIĞI, küme ayracı içine alınmış bir GUID olmalıdır:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Aşağıdaki örnekte gösterildiği gibi, içerik türündeki bir alan başvurusu, \<FieldRef /> Start/End öğeleri () kullanılarak değil, boş öğe biçimi () kullanılarak tanımlanmalıdır \<FieldRef> \</FieldRef> :

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Alan için kaynak XML hatalı biçimlendirilmişse, geçerli bir XML dosyası veya başka bir sorun ortaya çıkarsa, "dosya ayrıştırılamıyor" hatası oluşur.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Yeni Ingilizce olmayan site tanımları dağıtımdan sonra site oluşturma sayfasında görünmez
 ingilizce olmayan bir sürümü (yani, 1033 dışında bir yerel ayar) kullanarak bir site tanımı oluşturup dağıttıktan sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] , **şablon seçim** kutusunda **SharePoint özelleştirmeler** sekmesi görünmez ve yeni site şablonu **yeni SharePoint site** sayfasında görünmez.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorun, Webtemp site tanımı yapılandırma dosyası için **yol** özelliğindeki yanlış bir değer nedeniyle oluşur, örneğin *webtemp_SiteDefinitionProject1.xml*. **Dağıtım konumu** altında bulunan webtemp dosyasının **Path** özelliğinde, 1033 değerini uygun yerel ayara değiştirin [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Örneğin, Japonca yerel ayarı kullanmak için değeri 1041 olarak değiştirin. Daha fazla bilgi için bkz. [Microsoft tarafından atanan yerel kimlikler](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Bir iş akışı projesi temiz bir sisteme dağıtıldığında hata görüntülenir
 Bu sorun, içinde bir iş akışı projesini [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] temiz bir sistemde dağıtırsanız oluşur. temiz bir sistem, yeni bir yüklemesi olan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve SharePoint ancak dağıtılmış iş akışı projeleri olmayan bir bilgisayardır.

### <a name="error-message"></a>Hata iletisi
 SharePoint listesi bulunamıyor: iş akışı geçmişi.

### <a name="resolution"></a>Çözüm
 Bu hata, eksik bir Iş akışı geçmiş listesi nedeniyle oluşur. Geliştirme ortamı temiz bir sistem olduğundan, hiçbir iş akışı dağıtılmaz ve Iş akışı geçmiş listesi henüz yok. Bu sorunu çözmek için, iş akışı geçmiş listesinin oluşturulmasına neden olan iş akışı Sihirbazı 'nı yeniden açın.

##### <a name="to-reenter-the-workflow-wizard"></a>İş akışı Sihirbazı 'nı yeniden girmek için

1. **Çözüm Gezgini**, iş akışı düğümünü seçin.

2. **Özellikler** penceresinde, üç nokta düğmesi olan herhangi bir özellikte üç nokta (...) düğmesini seçin.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Kullanıcı, güncelleştirilmiş görüntüyü görüntülemek için hata ayıklarken tarayıcıda uygulama sayfasını yenilemelidir
 görüntü denetimi gibi bir görüntü görüntüleyen bir uygulama sayfası içeren bir SharePoint çözümünde hata ayıklaması yapıyorsanız, [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] görüntüde yapılan tüm değişiklikleri göstermek için tarayıcıda sayfayı yenilemeniz gerekir.

## <a name="error-the-site-location-is-not-valid"></a>Hata: site konumu geçerli değil
 Bu sorun, [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] yüklü değilse oluşabilir. ayrıca, **SharePoint özelleştirme sihirbazında** belirtilen SharePoint Web sitesine yönetici erişiminiz yoksa da bu durum oluşabilir.

### <a name="error-message"></a>Hata iletisi

- SharePoint site konumu geçerli değil.

### <a name="resolution"></a>Çözüm

- [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]yükleyin.

- SharePoint Web sitesine yönetici erişiminiz olduğundan emin olun. daha fazla bilgi için bkz [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] . [SharePoint Server 'da hizmet uygulamalarının yöneticilerini atama veya kaldırma](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Site silme Web olayı olay alıcısı projesinde gerçekleşmez
 Bir olay alıcı projesi oluşturduğunuzda ve "bir site silinmekte" gibi belirli Web olaylarını seçtiğinizde, olay hiçbir zaman gerçekleşmez.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorun, özellik kapsamının site düzeyindeki olayları işlemek için "site" olması gerektiğinden, ancak olay alıcı projeleri için varsayılan özellik kapsamı "Web" ise oluşur. Etkilenen Web olayları şunlardır:

- Site siliniyor (WebDeleted)

- Bir site silindi (WebDeleted)

- Bir site taşınıyor (Webnakliye)

- Bir site taşındı (Webtaşınmış)

  Sorunu gidermek için, olay alıcısının Özellik kapsamını aşağıdaki şekilde değiştirin.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Olay alıcısının Özellik kapsamını değiştirmek için

1. **Çözüm Gezgini**, **özellik tasarımcısında** olay alıcısının *. feature* dosyasını açın, dosyayı çift tıklatın veya kısayol menüsünü açıp **Aç**' ı seçin.

2. **Kapsam**' ın yanındaki oku seçin ve açılan listeden **site** ' yi seçin.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>İş verileri bağlantı modeli projesindeki bir tanımlayıcının adı değiştirildikten sonra dağıtım hatası görüntülenir
 Bu sorun, bir Iş verileri bağlantısı (BDC) modelinde bir varlığın tanımlayıcı adını değiştirirseniz ve sonra çözümü dağıtmaya çalıştığınızda oluşur.

### <a name="error-messages"></a>Hata iletileri

- \<*model name*> aşağıdaki dış Içerik türü etkinleştirme hatalarına sahiptir...

- ' ' Adlı IMetadataObject, \<*model name*> ' name ' alanında yinelenen bir değer içeriyor...

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için modeli el ile silin ve ardından çözümü yeniden dağıtın.  Modeli aşağıdaki araçlardan birini kullanarak silebilirsiniz:

- SharePoint 2010 merkezi yönetimi. Daha fazla bilgi için bkz. Microsoft TechNet Web sitesindeki [BDC model yönetimi](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) .

- Windows PowerShell. Şu komutu komut istemine yazarak modeli silebilirsiniz: **Remove-SPBusinessDataCatalogModel**. daha fazla bilgi için bkz. Microsoft TechNet Web sitesindeki [genel cmdlet 'ler (SharePoint Server 2010)](/powershell/module/sharepoint-server) .

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>SharePoint ' de bir görsel web bölümünü görüntülemeye çalıştığınızda bir hata görüntüleniyor
 Bu sorun, Kullanıcı denetiminin **Path** ÖZELLIĞI "ControlTemplates" dizesiyle başlamamasından oluşur \\ .

### <a name="error-messages"></a>Hata iletileri

- '/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* . ascx ' dosyası yok.

- '/' Uygulamasında sunucu hatası.

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