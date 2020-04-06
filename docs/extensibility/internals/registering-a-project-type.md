---
title: Proje Türünü Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705880"
---
# <a name="registering-a-project-type"></a>Proje Türü Kaydetme
Yeni bir proje türü oluşturduğunuzda, proje türünü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tanımayı ve onlarla çalışmayı sağlayan kayıt defteri girişleri oluşturmanız gerekir. Genellikle bir kayıt defteri komut dosyası (.rgs) dosyakullanarak bu kayıt defteri girişleri oluşturun.

 Aşağıdaki örnekte, kayıt defterindeki ifadeler, varsa varsayılan yollar ve veriler ve ardından her bir bildirim için kayıt defteri komut dosyasından girişleri içeren bir tablo sağlar. Tablolar komut dosyası girişlerini ve deyimler hakkında ek bilgiler sağlar.

> [!NOTE]
> Aşağıdaki kayıt defteri bilgileri, proje türünüzü kaydetmek için yazacağınız kayıt defteri komut dosyasındaki girişlerin türü ne ve amaçlarına örnek olacak şekilde tasarlanmıştır. Gerçek girişleriniz ve bunların kullanımları proje türünün belirli gereksinimlerine bağlı olarak değişebilir. Geliştirmekte olduğunuz proje türüne yakından benzeyen bir örnek bulmak için kullanılabilir örnekleri gözden geçirmeniz ve ardından bu örnek için kayıt defteri komut dosyasını gözden geçirmelisiniz.

 Aşağıdaki örnekler HKEY_CLASSES_ROOT.

## <a name="example"></a>Örnek

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|.figp uzantılı proje türü dosyalarının adı ve açıklaması.|
|`Content Type`|REG_SZ|`Text/plain`|Proje dosyaları için içerik türü.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Varsayılan simge bu tür proje için kullanılır. %MODULE% deyimi, proje türü DLL'nin varsayılan konumuna kayıt defterinde tamamlanır.|
|`@`|REG_SZ|`&Open in Visual Studio`|Bu proje türünün açılacağı varsayılan uygulama.|
|`@`|REG_SZ|`devenv.exe "%1"`|Bu tür bir proje açıldığında çalıştırılacak varsayılan komut.|

 Aşağıdaki örnekler HKEY_LOCAL_MACHINE ve kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] anahtarının altında yer almaktadır.

## <a name="example"></a>Örnek

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`(Varsayılan)|REG_SZ|`FigPrj Project VSPackage`|Bu kayıtlı VSPackage'ın (proje türü) yerelleştirilebilir adı.|
|`InprocServer32`|REG_SZ|`%MODULE%`|Proje türü DLL yolu. IDE bu DLL yükler ve `DllGetClassObject` <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> nesne oluşturmak için almak için VSPackage CLSID geçer.|
|`CompanyName`|REG_SZ|`Microsoft`|Proje türünü geliştiren şirketin adı.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Proje türü için ad.|
|`ProductVersion`|REG_SZ|`9.0`|Proje türü sürümü sürüm numarası.|
|`MinEdition`|REG_SZ|`professional`|VSPackage sürümü kayıtlı ediliyor.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Proje VSPackage için paket yük anahtarı. Ortam başladıktan sonra bir proje yüklendiğinde anahtar doğrulanır.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Proje türü için yerelleştirilmiş kaynaklar içeren uydu DLL'sinin dosya adı.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Uydunun yolu DLL.|
|`FigProjectsEvents`|REG_SZ|Değer ifadesine bakın.|Bu otomasyon olayı için döndürülen metin dizesini belirler.|
|`FigProjectItemsEvents`|REG_SZ|Değer ifadesine bakın.|Bu otomasyon olayı için döndürülen metin dizesini belirler.|

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarının altında yer almaktadır.

## <a name="example"></a>Örnek

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Bu tür projelerin varsayılan adı.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Paketler altında kayıtlı dll uydudan alınacak adın kaynak kimliği.|
|`Package`|REG_SZ|`%CLSID_Package%`|Paketler altında kayıtlı VSPackage sınıf kimliği.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Project Template dosyalarının varsayılan yolu. Bunlar Yeni Proje şablonu tarafından görüntülenen dosyalardır.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Project Item Template dosyalarının varsayılan yolu. Bunlar Yeni Öğe Ekle şablonu tarafından görüntülenen dosyalardır.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|IDE'nin **Aç** iletişim kutusunu uygulamasını sağlar.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Açılan projenin bu proje türü (proje fabrikası) tarafından işlenip işlenmediğini belirlemek için IDE tarafından kullanılır. Birden fazla giriş için biçim yarı sütunlu sınırlı bir listedir. Örneğin "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE tarafından, Farklı Kaydet işlemi için varsayılan dosya adı uzantısı olarak kullanılır.|
|`Filter Settings`|REG_DWORD|Çeşitli, aşağıdaki tabloya bakın ifadeler ve yorumlar.|Bu ayarlar, Dosyaları Ara Bilgi Kutusu iletişim kutularında görüntülemek için çeşitli filtreleri ayarlamak için kullanılır.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Madde Ekle şablonları için kaynak kimliği.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**Yeni Öğe Ekle** şablonu için iletişim kutusunda görüntülenen proje öğelerinin yolu.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**Yeni Öğe Ekle** iletişim kutusunda görüntülenen dosyaların ağaç düğümündeki sıralama sırasını belirler.|

 Aşağıdaki tablo, önceki kod segmentinde kullanılabilen Filtreler seçeneklerini gösterir.

|Filtre seçeneği|Açıklama|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Filtrenin **Dosyalarda Bul** iletişim kutusundaki yaygın filtrelerden biri olduğunu gösterir. Yaygın filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|`CommonOpenFilesFilter`|Filtrenin **Dosya Aç** iletişim kutusundaki yaygın filtrelerden biri olduğunu gösterir. Yaygın filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|`FindInFilesFilter`|Filtrenin **Dosyalarda Bul** iletişim kutusundaki filtrelerden biri olacağını ve ortak filtrelerden sonra listelenemeyeceğini gösterir.|
|`NotOpenFileFilter`|**Dosya aç** iletişim kutusunda filtrenin kullanılmayacağını gösterir.|
|`NotAddExistingItemFilter`|**Varolan Öğe** Ekle iletişim kutusunda filtrenin kullanılmayacağını gösterir.|

 Varsayılan olarak, bir filtrede bu bayraklardan biri veya daha fazlası ayarlı değilse, filtre **Varolan Öğe Ekle** iletişim kutusunda ve ortak filtreler listelendikten sonra **Dosyaaç** iletişim kutusunda kullanılır. Filtre, **Dosyalarda Bul** iletişim kutusunda kullanılmaz.

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarının altında yer almaktadır.

## <a name="example"></a>Örnek

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Yeni Proje şablonları için kaynak kimliği.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Kayıtlı proje türündeki projeler için varsayılan yol.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Yeni Projeler sihirbazı iletişim kutusunda görüntülenen projelerin sıralama sırasını ayarlar.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu tür projelerin yalnızca Yeni Proje iletişim kutusunda görüntülendiğini gösterir.|

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarının altında yer almaktadır.

## <a name="example"></a>Örnek

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|None|Aşağıdaki girişlerin Çeşitli Dosyalar projeleri girişleri için olduğunu belirten varsayılan değer.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Yeni Öğeler Ekle şablon dosyaları için kaynak kimliği değeri.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**Yeni Öğe Ekle** iletişim kutusunda görüntülenecek öğelerin varsayılan yolu.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**Yeni Öğe Ekle** iletişim kutusunun ağaç düğümünde görüntülenmek için sıralama sırası kurar.|

 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] anahtarının altında yer alır.

## <a name="example"></a>Örnek

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Menü girişi, Menü bilgilerini almak için kullanılan kaynağa IDE'yi işaret etmektedir. Bu veriler menü veritabanında birleştirildiğinde, aynı anahtar kayıt defterinin MenusMerged bölümüne eklenir. VSPackage doğrudan MenusMerged bölümü altında hiçbir şeyi değiştirmemelidir. Aşağıdaki tablodaki Veri alanında üç virgülle ayrılmış alan vardır. İlk alan, bir menü kaynak dosyasının tam yolunu tanımlar:

- İlk alan atlanırsa, menü kaynağı VSPackage GUID tarafından tanımlanan DLL uydudan yüklenir.

  İkinci alan, CTMENU türünün bir menü kaynak kimliğini tanımlar:

- Kaynak kimliği belirtilirse ve dosya yolu ilk parametre tarafından sağlanırsa, tam dosya yolundan bir menü kaynağı yüklenir.

- Kaynak kimliği sağlanmışsa, ancak dosya yolu sağlanmışsa, menü kaynağı uydu DLL'den yüklenir.

- Tam dosya yolu sağlanır ve kaynak kimliği atlanırsa, yüklenecek dosyanın bir CTO dosyası olması beklenir.

  Son alan, CTMENU kaynağının sürüm numarasını tanımlar. Sürüm numarasını değiştirerek menüyü yeniden birleştirebilirsiniz.

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|Menü bilgilerini almak için kaynak.|

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] anahtarının altında yer almaktadır.

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Şekiller Projesi Yeni Proje şablonları için kaynak kimliği değeri.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Yeni Projeler dizininin varsayılan yolu. Bu dizindeki öğeler **Yeni Proje sihirbazı** iletişim kutusunda görüntülenir.|
|`SortPriority`|REG_DWORD|`41 (x29)`|**Projelerin Yeni Proje** iletişim kutusunun ağaç düğümünde görüntülenme sırasını belirler.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu tür projelerin yalnızca **Yeni Proje** iletişim kutusunda görüntülendiğini gösterir.|

 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] anahtarının altında yer alır.

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Adı|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Kayıtlı VSPackage sınıf kimliği.|
|`UseInterface`|REG_DWORD|`1`|1, UI'nin bu projeyle etkileşim de kullanılacağını gösterir. 0, Ara Birimi arabirimi olmadığını gösterir.|

 Yeni proje türlerini denetleyen The.vsz dosyaları sık sık RELATIVE_PATH girişi içerir. Bu yol, aşağıdaki Kurulum anahtarında proje türünün \ProductDir girişi altında belirtilen yola göreli:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Örneğin, Kurumsal Çerçeveler proje şablonları aşağıdaki kayıt defteri girişlerini ekler:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 Yani .vsz dosyasına bir PROJECT_TYPE=EF girişi eklerseniz, ortam .vsz dosyalarınızı daha önce belirtilen ProductDir dizininde bulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
