---
title: SharePoint Çözümlerinde Sorun giderme | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 046f3bbca7b66d14e9b6a3eae96b613492292be0
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189194"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint Çözümlerinde Sorun giderme
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklayıcısını kullanarak SharePoint Çözümlerinde hata ayıkladığınızda aşağıdaki sorunlar veya uyarılar oluşabilir. Daha fazla bilgi için bkz. [SharePoint 2007 Iş akışı çözümlerinde hata ayıklama](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Korumalı görsel Web bölümlerinde belirteç kısıtlamaları
 Korumalı çözümlerin Visual Web bölümleri, SharePoint çalışma zamanının desteklediği $SPUrl gibi standart belirteçleri işleyemez. Sonuç olarak, URL çözümlenmez ve Visual Web Bölümü Tasarımcısında Tasarım görünümü içeriği, aşağıdaki örnekte olduğu gibi doğrudan bir betik öğesinde ifade ederseniz önizleyemezsiniz:

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
 Projelerin ve proje öğelerinin adları yalnızca SharePoint 2010 ' deki bir dağıtım yolunda geçerli olan karakterleri içerebilir. Başka hiçbir karaktere izin verilmez.

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

- Ters eğik çizgi (\\)

  Bir proje paketlendiğinde, bir doğrulama kuralı, dağıttığınız her bir dosyanın dağıtım yolu özelliğinin yalnızca bu geçerli karakterleri içerdiğini doğrular.

## <a name="errors-when-creating-custom-fields"></a>Özel alanlar oluşturulurken hatalar oluştu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], özel alanlar XML içinde tanımlanmıştır. Bir alan, belirli bir biçim kullanılarak tanımlanmamışsa veya başvurulmuyorsa hatalar oluşabilir.

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

 Aşağıdaki örnekte gösterildiği gibi, içerik türündeki bir alan başvurusu, başlangıç/bitiş öğeleri (\<FieldRef >\</FieldRef >) kullanılarak değil, boş öğe biçimi (\<FieldRef/>) kullanılarak tanımlanmalıdır:

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Alan için kaynak XML hatalı biçimlendirilmişse, geçerli bir XML dosyası veya başka bir sorun ortaya çıkarsa, "dosya ayrıştırılamıyor" hatası oluşur.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Yeni Ingilizce olmayan site tanımları dağıtımdan sonra site oluşturma sayfasında görünmez
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ingilizce olmayan bir sürümünü (yani 1033 dışında bir yerel ayar [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] sahip bir sürümü) kullanarak bir site tanımı oluşturup dağıttıktan sonra, **SharePoint özelleştirmeler** sekmesi **şablon seçim** kutusunda ve yeni sitede görünmez Şablon **Yeni SharePoint sitesi** sayfasında görünmez.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bu sorun, *webtemp_SiteDefinitionProject1. xml*gibi WebTemp site tanımı yapılandırma dosyasının **Path** özelliğindeki yanlış bir değer nedeniyle oluşur. Web geçici dosyasının **yol** özelliğinde, **dağıtım konumu**altında bulunan 1033 değerini uygun yerel ayara [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]değiştirin. Örneğin, Japonca yerel ayarı kullanmak için değeri 1041 olarak değiştirin. Daha fazla bilgi için bkz. [Microsoft tarafından atanan yerel kimlikler](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Bir iş akışı projesi temiz bir sisteme dağıtıldığında hata görüntülenir
 Bu sorun, bir iş akışı projesini temiz bir sistemde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dağıtırsanız oluşur. Temiz bir sistem, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve SharePoint 'in yeni yüklemesi olan ancak dağıtılmış iş akışı projelerinin olmadığı bir bilgisayardır.

### <a name="error-message"></a>Hata iletisi
 SharePoint listesi bulunamıyor: İş akışı geçmişi.

### <a name="resolution"></a>Çözüm
 Bu hata, eksik bir Iş akışı geçmiş listesi nedeniyle oluşur. Geliştirme ortamı temiz bir sistem olduğundan, hiçbir iş akışı dağıtılmaz ve Iş akışı geçmiş listesi henüz yok. Bu sorunu çözmek için, iş akışı geçmiş listesinin oluşturulmasına neden olan iş akışı Sihirbazı 'nı yeniden açın.

##### <a name="to-reenter-the-workflow-wizard"></a>İş akışı Sihirbazı 'nı yeniden girmek için

1. **Çözüm Gezgini**, iş akışı düğümünü seçin.

2. **Özellikler** penceresinde, üç nokta düğmesi olan herhangi bir özellikte üç nokta (...) düğmesini seçin.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Kullanıcı, güncelleştirilmiş görüntüyü görüntülemek için hata ayıklarken tarayıcıda uygulama sayfasını yenilemelidir
 [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] resim denetimi gibi bir görüntü görüntüleyen bir uygulama sayfası içeren bir SharePoint çözümünde hata ayıklaması yapıyorsanız, görüntüde yapılan tüm değişiklikleri göstermek için tarayıcıda sayfayı yenilemeniz gerekir.

## <a name="error-the-site-location-is-not-valid"></a>Hata: Site konumu geçerli değil
 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] yüklenmemişse bu sorun oluşabilir. **SharePoint Özelleştirme sihirbazında**belirtilen SharePoint Web sitesine yönetici erişiminiz yoksa da bu durum oluşabilir.

### <a name="error-message"></a>Hata iletisi

- SharePoint sitesi konumu geçerli değil.

### <a name="resolution"></a>Çözüm

- [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]yükleyin.

- SharePoint Web sitesine yönetici erişimi olduğundan emin olun. Daha fazla bilgi için bkz. çevrimiçi [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)], [SharePoint Server 'daki hizmet uygulamalarının yöneticilerini atama veya kaldırma](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

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

- \<*model adı*> şu dış içerik türü etkinleştirme hatalarına sahip...

- '\<*model adı*> ' adlı IMetadataObject, ' name ' alanında yinelenen bir değer içeriyor...

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için modeli el ile silin ve ardından çözümü yeniden dağıtın.  Modeli aşağıdaki araçlardan birini kullanarak silebilirsiniz:

- SharePoint 2010 merkezi yönetimi. Daha fazla bilgi için bkz. Microsoft TechNet Web sitesindeki [BDC model yönetimi](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#deleteamodel) .

- Windows PowerShell. Bu komutu komut istemine yazarak modeli silebilirsiniz: **Remove-SPBusinessDataCatalogModel**. Daha fazla bilgi için bkz. Microsoft TechNet Web sitesindeki [genel cmdlet 'ler (SharePoint Server 2010)](/powershell/module/sharepoint-server/&view=sharepoint-ps) .

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>SharePoint 'te bir görsel web bölümünü görüntülemeye çalıştığınızda bir hata görüntüleniyor
 Bu sorun, Kullanıcı denetiminin **Path** ÖZELLIĞI "controltemplates\\" dizesiyle başlamamasından oluşur.

### <a name="error-messages"></a>Hata iletileri

- '/_CONTROLTEMPLATES/ *\<proje adı >* / *\<Web bölümü adı* >/\<*Kullanıcı denetimi adı >* . ascx ' yok.

- '/' Uygulamasında Sunucu Hatası.

### <a name="resolution"></a>Çözüm

##### <a name="to-resolve-this-issue"></a>Bu sorunu çözmek için

1. **Çözüm Gezgini**, dosya adı uzantısı *. ascx*olan kullanıcı denetim dosyasını seçin.

2. Menü çubuğunda > **Özellikler penceresini** **görüntüle** ' yi seçin.

3. **Özellikler** penceresinde **dağıtım konumu** düğümünü genişletin.

4. **Path** özelliğinin DEĞERININ "controltemplates\\" dizesiyle başladığı emin olun.

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Bir görev formu alanı içeren içeri aktarılmış bir yeniden kullanılabilir iş akışı çalıştırıldığında hata görüntülenir
 Bu sorun, bir alan içeren bir görev formu içeren bir iş akışını içeri aktarırsanız ve ardından yeni iş akışını içeri aktardığınız aynı sistemde çalıştırırsanız oluşur.

### <a name="error-message"></a>Hata iletisi
 ' Etkinleştirme özellikleri ' dağıtım adımında hata oluştu: [*GUID*] özelliğinde tanımlanan [*GUID] kimliğine*sahip alan, geçerli site koleksiyonunda veya bir alt sitede bulundu.

### <a name="resolution"></a>Çözüm
 Bu hata, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ' deki yeniden kullanılabilir Iş akışı projesi görev formu alan kimliklerini değiştirmediğinden oluşan alan KIMLIĞI çakışmalarının sonucudur. İçeri aktarılan bir iş akışını orijinal iş akışını içeren aynı sunucuya dağıtırsanız, alan KIMLIĞI çakışmaları oluşur.

 Bu sorunu çözmek için bul ve Değiştir özelliğini kullanarak içeri aktarılan tüm iş akışı dosyalarındaki alan KIMLIĞI özniteliğinin değerini değiştirin.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Yeniden adlandırılmış bir içeri aktarılan liste örneği çalıştırıldığında hata görüntülenir
 Bu sorun, içeri aktarılan bir liste örneğini yeniden adlandırıp [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]sonra çalıştırırsanız oluşur.

### <a name="error-message"></a>Hata iletisi
 Derleme hatası: ' Etkinleştirme özellikleri ' dağıtım adımında hata oluştu: Dosya Template\Features\\[*içeri aktarma projesi*<em>özellik</em>*adı*] \files\lists\\[*eski*<em>liste adı</em>] \Schema.xml yok.

### <a name="resolution"></a>Çözüm
 Bir liste örneğini içeri aktardığınızda, CustomSchema adlı bir öznitelik liste örneğinin Elements. xml dosyasına eklenir. Elements. xml, liste örneği için özel bir Schema. XML yolu içerir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]' de liste örneğini yeniden adlandırdığınızda, özel Schema. xml ' in dağıtım yolu değişir, ancak CustomSchema özniteliğinin yol değeri güncellenmez. Sonuç olarak, liste örneği, özellik etkinleştirildiğinde CustomSchema özniteliği tarafından belirtilen eski yolda *Schema. xml* dosyasını bulamaz.

 Bu sorunu çözmek için, CustomSchema özniteliğinde *Schema. xml* dosyasının Dağıtım konumunun yolunu güncelleştirin.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint hata ayıklama oturumu IIS tarafından sonlandırıldı
 Bu sorun, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir SharePoint çözümünde bir kesme noktası ayarlarsanız, çalıştırmak için **F5** tuşunu ve ardından 90 saniyeden daha uzun bir kesme noktasında kalmasını sağlamak için oluşur.

### <a name="error-message"></a>Hata iletisi
 Hata ayıklanan Web sunucusu işlemi Internet Information Services (IIS) tarafından sonlandırıldı. IIS 'deki uygulama havuzu ping ayarlarını yapılandırarak bu sorundan kaçınabilirsiniz. Daha fazla ayrıntı için yardıma bakın.

### <a name="resolution"></a>Çözüm
 Varsayılan olarak, IIS uygulama havuzu uygulamayı kapatmadan önce bir uygulamanın yanıt vermesi 90 saniye bekler. Bu işlem, uygulamanın "ping" olarak bilinir. Bu sorunu çözmek için, bekleme süresini artırabilir ya da uygulama için ping komutunu tamamen devre dışı bırakabilirsiniz.

##### <a name="to-access-the-iis-app-pool-settings"></a>IIS uygulama havuzu ayarlarına erişmek için

1. IIS Yöneticisi'ni açın.

2. **Bağlantılar** bölmesinde, SharePoint sunucusu düğümünü genişletin ve ardından **uygulama havuzları** düğümünü seçin.

3. **Uygulama havuzları** sayfasında, SharePoint uygulama havuzunu (genellikle "SharePoint-80") seçin ve ardından **Eylemler** bölmesinde **Gelişmiş ayarlar** bağlantısını seçin.

4. IIS zaman aşımından önceki bekleme süresini artırmak için, **ping en yüksek yanıt süresi (saniye)** değerini 90 saniyeden daha büyük bir değere değiştirin.

5. IIS ping komutunu devre dışı bırakmak için **ping etkin** ayarını **false**olarak ayarlayın.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Otomatik geri çekme, SharePoint 'te yalnız bırakılmış liste örneğini bırakır
 Aşağıdaki adımları uygulamanız durumunda bu sorun oluşur.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]bir liste örneği olan bir liste tanımı oluşturun.

2. Çözümü çalıştırmak için **F5** tuşunu seçin.

3. Hata ayıklamayı durdurun veya SharePoint sitesini kapatın.

4. SharePoint sitesini yeniden açın ve liste örneğini açın.

### <a name="error-message"></a>Hata iletisi
 '/' Uygulamasında Sunucu Hatası.

### <a name="resolution"></a>Çözüm
 Bu durum, bir SharePoint çözümünün hata ayıklama oturumunu kapattıktan sonra otomatik olarak geri çekin özelliğinin çözümü geri çeker. Geri çekme, liste tanımını SharePoint 'ten siler, ancak listenin örneğini silmez. Liste örneği için temel alınan liste tanımı gereklidir.

 Bu sorunu çözmek için, menü çubuğunda **yapı** > **Dağıt**' ı seçerek çözümü dağıtın. ( **F5** tuşunu seçerek çözümde hata ayıklamayın.) Ardından, SharePoint 'teki liste örneğini silin.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Özgün SharePoint çözümü, dışarıya aktarılmış bir sürümle değiştirilmiştir
 Bir SharePoint çözümünü dışarı aktarırsanız, çözümü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]içe aktarın ve ardından, yeniden dışarı aktarıldığı siteye geri dağıtırsanız, özgün SharePoint çözümü değiştirilmiştir. Çözümü, üzerinde etkin bir çözüm etkinleştirilmemiş bir sunucuya dağıtırsanız bu sorun oluşmaz.

### <a name="error-message"></a>Hata iletisi
 Yok.

### <a name="resolution"></a>Çözüm
 Bir çözümün verildiği sitede üzerine yazılmasını önlemek için, SolutionId 'nin GUID 'Lerini ve [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projesindeki tüm içeri aktarılan özelliklerin özellik kimliklerini değiştirin.

## <a name="error-appears-when-debugging-starts"></a>Hata ayıklama başladığında hata görüntülenir
 Visual Studio 'da bir SharePoint çözümünde hata ayıklamaya başladığınızda, belirtilen anahtar sözlükte olmadığı için Visual Studio 'Nun Web. config dosyasını yükleyemediğini belirten bir hata oluştu.

### <a name="error-message"></a>Hata iletisi
 Web. config yapılandırma dosyası yüklenemedi. Hatalı biçimlendirilmiş XML öğeleri için dosyayı denetleyin ve yeniden deneyin. Aşağıdaki hata oluştu: Verilen anahtar sözlükte yoktu.

### <a name="resolution"></a>Çözüm
 Bu sorunu çözmek için, Visual Studio 'daki SharePoint projesinin site URL 'SI Özellik değerinin, Web uygulamasının alternatif erişim eşlemeleri için varsayılan bölgeye atanan URL ile eşleştiğinden emin olun. URL için Intranet gibi başka bir bölge kullanarak hatayı çözümlenemez. Projenin site URL 'SI ve varsayılan bölgedeki URL eşleşmelidir. Alternatif erişim eşlemelerine erişmek için SharePoint 2010 merkezi yönetim yardımcı programını açın, **uygulama yönetimi** bağlantısını seçin ve ardından **Web uygulamaları**altında, **Alternatif erişim eşlemelerini Yapılandır** bağlantısını seçin. Daha fazla bilgi için bkz. [Web uygulamaları için bölge oluşturma](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Visual Studio’da hata ayıklama](../debugger/debugger-feature-tour.md)