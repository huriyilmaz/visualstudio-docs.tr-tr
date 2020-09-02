---
title: Seçenekler sayfası, ortam düğümü özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b45716db44dcc316ec60604aa0411e6498797ae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595039"
---
# <a name="options-page-environment-node-properties"></a>Seçenekler Sayfası, Ortam Düğümü Özellikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belgede, **Environment** `DTE.Properties("Environment", <Property Page>)` **Seçenekler** iletişim kutusunun ortam kategorisiyle ilişkili sayfalar (veya özellikler koleksiyonlar) açıklanmaktadır. Her alt bölümünün başlığı, özellikler koleksiyonuna erişmek için kullanılan çağrıdır ve her alt bölüm içindeki tablo koleksiyondaki özellikleri listeler.

## <a name="general"></a>Genel
 `DTE.Properties("Environment", "General")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|ShowStatusBar|Get/Set (Boole)|Durum çubuğunun görünür olup olmadığını belirler.|
|WindowMenuContainsNItems|Al/ayarla (kısa)|Belge pencerelerinin Windows menüsünün en altında nasıl dahil olduğunu belirler.|
|MRUListContainsNItems|Al/ayarla (kısa)|"En son kullanılan" alt menüsünde kaç dosya görüntüleneceğini belirler.|
|Animasyonlar|Get/Set (Boole)|Tümleşik geliştirme ortamının (IDE) durum çubuğunda animasyon kullanıp kullanmadığını belirler.|
|AnimationSpeed|Al/ayarla (kısa)||
|Oto ayarlan, Texperience|Get/Set (Boole)|İstemci performansına bağlı olarak görsel deneyimi otomatik olarak ayarlar.|
|RichClientExperienceOptions|Get/Set (Enum)|İçindeki değerlerle zengin istemci görsel deneyimini sunar <xref:EnvDTE100.vsRichClientExperienceOptions> .|
|Yalnızca CloseButtonActiveTabOnly|Get/Set (Boole)|**Kapat** düğmesinin yalnızca etkin sekmede gösterilip gösterilmeyeceğini belirler.|
|Yalnızca oto hidepınactivetab|Get/Set (Boole)|**Otomatik gizleme** düğmesinin yalnızca etkin sekmeyi etkileyip etkilemeyeceğini belirler.|

## <a name="add-inmacros-security"></a>Eklenti/makro güvenliği
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|Makrosenabled|Get/Set (Boole)|Makroların çalışmasına izin verir.|
|Addınsenabled|Get/Set (Boole)|Eklentilerin yüklenmesine izin verir.|
|Loadaddinsfromweb|Get/Set (Boole)|Web 'deki bir URL 'den yüklenecek eklentilerin yüklenmesine izin verir.|

## <a name="documents"></a>Belgeler
 `DTE.Properties("Environment", "Documents")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (Boole)|Geçerli belge kaydedilmişse yeni bir dosyanın açılmasını geçerli belge penceresini yeniden kullanıp kullanmayacağını belirler. `false` her zaman açık her belge için yeni bir belge penceresi açar demektir.|
|DetectFileChangesOutsideIDE|Get/Set (Boole)|İşletim sistemi IDE 'ye dosyaların diskte değiştirildiğini bildirir, ortamın IDE 'de açılan dosyaları otomatik olarak yeniden yükleyemeyeceğini belirler.|
|Oto Loadexternalchanges|Get/Set (Boole)|Açık belge değiştirilmediyse, belgeleri açmak için algılanan dış değişikliklerin değiştirilen dosyayı otomatik olarak yeniden yükleyip yükleyemeyeceğini belirler. Açık belge değiştirilirse ve bu özellik ise `true` IDE, bu özellik gibi istemde bulunur `false` .|
|InitializeOpenFileFromCurrentDocument|Get/Set (Boole)|<xref:EnvDTE.DTEClass.OpenFile%2A>Komutun, son etkin belgeden veya bir dosyayı açtığınız son konumdan dizin ve dosya adı olup olmadığını belirler.|
|MiscFilesProjectSavesLastNItems|Al/ayarla (kısa)|Çeşitli dosyalar projesinin kaç dosya için kayıt olduğunu belirler. Sonuç olarak, IDE 'yi bir dahaki kullandığınızda diskte en son ne kadar çok dosya olarak açık olduğunu görebilirsiniz.|
|Showmiscfilesprojesi|Get/Set (Boole)|Çeşitli dosyalar projesinin gösterilip gösterilmeyeceğini belirler.|
|CheckFor, Entlinesonları|Get/Set (Boole)|Dosya yüklerinde tutarlı satır sonları olup olmadığını denetler.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (Boole)|Veriler kod sayfasına kaydedilemediğinde belgeleri Unicode olarak kaydeder.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (Boole)|Genel geri alma, diğer düzenlenmiş dosyaları değiştirecek olduğunda bir uyarı görüntüler.|
|AllowEditingReadOnlyFiles|Get/Set (Boole)|Salt okuma dosyalarının düzenlenmesine izin verir, ancak bunları kaydetme girişimi olduğunda bir uyarı verir.|
|DocumentDockPreference|Get/Set (Enum)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Açılan belgeyi eklemek için sekme kutusu içinde konumlandırın.|

## <a name="extension-manager"></a>Uzantı Yöneticisi
 `DTE.Properties("Environment", "ExtensionManager")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|EnableAdminExtensions|Get/Set (Boole)|, Visual Studio yönetici kimlik bilgileri altında çalıştırıldığında kullanıcı başına uzantıları yükler. Bu değer değiştirildikten sonra Visual Studio 'Nun yeniden başlatılması gerekir.|
|EnableOnline|Get/Set (Boole)|Visual Studio Galerisinde uzantılara erişimi sağlar.|
|AutomaticallyCheckForUpdates|Get/Set (Boole)|Yüklü uzantılara yönelik güncelleştirmeleri otomatik olarak denetler.|

## <a name="find-and-replace"></a>Bulma ve Değiştirme
 `DTE.Properties("Environment", "FindAndReplace")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|ShowWarningMessages|Get/Set (Boole)|Uyarı iletilerini görüntüler.|
|Initializefromeditor|Get/Set (Boole)|, Düzenleyiciden metni **bul** kutusunu otomatik olarak doldurur.|
|Showmessagekutularý|Get/Set (Boole)|Bilgilendirici iletileri görüntüler.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (Boole)|**Hızlı bul** veya **Hızlı Değiştir**kullanılarak bir eşleşme olduktan sonra **Bul ve Değiştir** penceresini gizler.|

## <a name="import-and-export-settings"></a>Ayarları İçeri ve Dışarı Aktarma
 `DTE.Properties("Environment", "Import and Export Settings")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|TrackTeamSettings|Get/Set (Boole)|TeamSettingsFile tarafından belirtilen dosyadaki ayarları kullanır.|
|TeamSettingsFile|Get/Set (dize)|Takım ayarlarına sahip dosyanın adı.|
|Oto SaveFile|Get/Set (dize)|Kullanıcı ayarlarının otomatik olarak kaydedildiği dosyanın adı.|

## <a name="international-settings"></a>Uluslararası Ayarlar
 `DTE.Properties("Environment", "International")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|Dil|Get/Set (dize)|Visual Studio için geçerli dilin LCıD değeri.|

## <a name="keyboard"></a>Klavye
 `DTE.Properties("Environment", "Keyboard")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|Düzen|Get/Set (dize)|Yerleşik bir düzen içeren bir dize, yüklenen. vsk dosyasının tam yolunu içeren bir dize döndürür veya. vsk dosyası yüklü değilse "(varsayılan)".|

## <a name="projects-and-solution"></a>Projeler ve çözüm
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|OnRunOrPreview|Get/Set (dize)|IDE 'nin, geliştirilmiş bir projeyi önizlemeden veya çalıştırmadan önce her şeyi kaydedip etmeyeceğini belirler.|
|ProjectsLocation|Get/Set (dize)|**Proje Ekle** iletişim kutusunun yeni projeleri kaydettiği varsayılan dizini belirler.|
|ShowOutputWindowBeforeBuild|Get/Set (Boole)|Bir yapılandırmanın başlatılmasının, **Çıkış** penceresini görüntüleyip görüntülemediğini belirler.|
|ShowTaskListAfterBuild|Get/Set (Boole)|Derleme tamamlandığında, başarısız bir derleme işleminin **görev listesi** görüntüleyip görüntülemediğini belirler.|
|Trackfileselectionınexplorer|Get/Set (Boole)|Geçerli öğenin **Çözüm Gezgini**izlenip izlenmeyeceğini belirler.|
|AlwaysShowSolutionNode|Get/Set (Boole)|Çözüm düğümünün görüntülenip görüntülenmeyeceğini belirler.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (Boole)|Kaydetme işlemlerinin başlangıç projeleri ve bunların bağımlı dosyalarıyla sınırlı olup olmadığını belirler.|
|ShowAdvancedBuildConfigurations|Get/Set (Boole)|Gelişmiş derleme yapılandırmalarının görüntülenip görüntülenmeyeceğini belirler.|
|Concurrentderlemeler|Get/Set (dize)|Gerçekleşebileceğini en fazla paralel proje derlemesi sayısını belirler.|
|SaveNewProjects|Get/Set (Boole)|Yeni projelerin oluşturulduktan sonra otomatik olarak kaydedilip kaydedilmediğini belirler.|
|PromptForRenameSymbol|Get/Set (Boole)|Dosyalar yeniden adlandırıldığında sembolik yeniden adlandırma isteyip istemediğinizi belirtir.|
|OnRunWhenErrors|Get/Set (Enum)|Bir derleme hatalarla tamamlandığında çalıştırma davranışını belirtir.|
|OnRunWhenOutOfDate|Get/Set (Enum)|Bir proje güncel olmadığında çalıştırılacak davranışı belirtir.|
|ProjectTemplates konumu|Get/Set (dize)|Kullanıcı projesi şablonlarını içeren dizin.|
|Projectıtemtemplates konumu|Get/Set (dize)|Kullanıcı öğesi şablonlarını içeren dizin.|
|DefaultBehaviorForStartupProjects|Get/Set (dize)||
|MSBuildOutputVerbosity|Get/Set (dize)|Derleme çıkışı için ayrıntı düzeyini belirtir.|

## <a name="startup"></a>Başlangıç
 `DTE.Properties("Environment", "Startup")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|OnStartUp|Get/Set (Enum)|Başlangıç olarak gerçekleştirilecek eylem, <xref:EnvDTE.vsStartUp> 0 ile 5 arasında değerler içeren:<br /><br /> -0: giriş sayfasını aç<br />-1: son yüklenen çözümü yükle<br />-2: **Proje Aç** iletişim kutusunu göster<br />-3: **Yeni proje** göster iletişim kutusu<br />-4: boş ortamı göster<br />-5: başlangıç sayfasını göster|
|StartPageRSSUrl 'Si|Get/Set (dize)|Başlangıçta kullanılan RSS akışı URL 'SI.|
|StartPageRefreshDownloadedContent|Get/Set (Boole)|StartPageRefreshInterval içinde belirtilen aralığın her geçtikten sonra başlangıç sayfasını yeniler.|
|StartPageRefreshInterval|Al/ayarla (kısa)|Başlangıç sayfasını yenilemek için dakika cinsinden Aralık.|

## <a name="tasklist"></a>KILL
 `DTE.Properties("Environment", "TaskList")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (Boole)|**Görev listesi**görevler silinirken bir onay kutusunun görüntülenip görüntülenmeyeceğini belirtir.|
|WarnOnAddingHiddenItem|Get/Set (Boole)|Gösterilmeyecek bir kullanıcı görevi eklerken uyarılmak isteyip istemediğinizi belirtir.|
|DontShowFilePaths|Get/Set (Boole)|Görev Listesi tam dosya yollarının gösterilip gösterilmeyeceğini belirtir.|
|CommentTokens|Güvenli|Açıklama belirteci değerlerinin bir SafeArray değerini döndürür. Her birinin alanları, `Name` (dize) ve `Priority` ( <xref:EnvDTE.vsTaskPriority> , yüksek, orta veya düşük).|

## <a name="web-browser"></a>Web Tarayıcısı
 `DTE.Properties("Environment", "WebBrowser")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|Değiştirir|Get/Set (dize)|Giriş sayfası URL 'sini temsil eder.|
|SearchPage|Get/Set (dize)|Arama sayfası URL 'sini temsil eder.|
|ViewSourceIn|Get/Set (Enum)|<xref:EnvDTE.vsBrowserViewSource> (Kaynak, tasarım, dış).|
|ViewSourceExternalProgram|Get/Set (dize)|Dış kaynak görüntüleyicisinin yolu.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Seçenek ayarlarını denetleme](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Seçenek sayfalarındaki özellik öğelerinin adlarını belirleme](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Seçenekler Sayfası, Yazı Tipleri ve Renkler Düğümü Özellikleri](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Seçenekler Sayfası, Metin Düzenleyici Düğümü Özellikleri](../../ide/reference/options-page-text-editor-node-properties.md)
- [Ortam Seçenekleri İletişim Kutusu](../../ide/reference/environment-options-dialog-box.md)
