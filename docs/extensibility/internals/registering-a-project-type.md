---
title: Project Türü | Microsoft Docs
description: Kullanıcıların yeni proje türünü tanımasını ve Visual Studio kayıt defteri girdileri oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0d20db232bc340e241f2fc4ab05927c59660741b5b0bc5e77e4280a6a1498d41
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401277"
---
# <a name="registering-a-project-type"></a>Proje Türü Kaydetme
Yeni bir proje türü oluşturdukta, proje türünü tanımayı ve bu türle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çalışmanızı sağlayan kayıt defteri girdileri oluşturmanız gerekir. Bu kayıt defteri girdilerini genellikle bir kayıt defteri betiği (.rgs) dosyası kullanarak oluşturabilirsiniz.

 Aşağıdaki örnekte, kayıt defterindeki deyimler, varsa varsayılan yolları ve verileri sağlar ve ardından her deyimi için kayıt defteri betiğinden girdileri içeren bir tabloyu içerir. Tablolar betik girişlerini ve deyimler hakkında ek bilgileri sağlar.

> [!NOTE]
> Aşağıdaki kayıt defteri bilgileri, proje türlerinizi kaydetmek için yazacakları kayıt defteri betikleri girişlerinin türüne ve amaçlarına bir örnek olarak tasarlanmıştır. Gerçek girişleriniz ve kullanımları, proje türüne özgü gereksinimlere göre değişiklik gösterebilir. Geliştirmekte olduğunu proje türüne yakından benzeyen bir tane bulmak için kullanılabilir örnekleri gözden geçirmeniz ve ardından bu örneğin kayıt defteri betiklerini gözden geçirmeniz gerekir.

 Aşağıdaki örnekler, HKEY_CLASSES_ROOT.

## <a name="example-1"></a>Örnek 1

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

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|.chromep uzantısına sahip proje türü dosyalarının adı ve açıklaması.|
|`Content Type`|REG_SZ|`Text/plain`|Proje dosyaları için içerik türü.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Bu tür bir proje için kullanılan varsayılan simge. %MODULE% deyimi, kayıt defterinde proje türü DLL'nin varsayılan konumu olarak tamamlanır.|
|`@`|REG_SZ|`&Open in Visual Studio`|Bu proje türünün aç olduğu varsayılan uygulama.|
|`@`|REG_SZ|`devenv.exe "%1"`|Bu tür bir proje açıldığında çalıştıracak varsayılan komut.|

 Aşağıdaki örnekler, HKEY_LOCAL_MACHINE ve [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] anahtarının altında kayıt defterinde bulunur.

## <a name="example-2"></a>Örnek 2

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
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

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@` (Varsayılan)|REG_SZ|`FigPrj Project VSPackage`|Bu kayıtlı VSPackage'ın yerelleştirilebilir adı (proje türü).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Proje türü DLL'nin yolu. IDE bu DLL'i yükler ve nesnesini oluşturmak için VSPackage `DllGetClassObject` CLSID'lerini <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> 'ye <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> iletir.|
|`CompanyName`|REG_SZ|`Microsoft`|Proje türünü geliştiren şirketin adı.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Proje türünün adı.|
|`ProductVersion`|REG_SZ|`9.0`|Proje türü sürümünün sürüm numarası.|
|`MinEdition`|REG_SZ|`professional`|Kaydedilen VSPackage sürümü.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|VSPackage projesinin paket yükleme anahtarı. Anahtar, ortam başlatıldıktan sonra proje yüklendiğinde doğrulanır.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Proje türü için yerelleştirilmiş kaynakları içeren uydu DLL'nin dosya adı.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Uydu DLL'nin yolu.|
|`FigProjectsEvents`|REG_SZ|Değer için bkz. deyimi.|Bu otomasyon olayı için döndürülen metin dizesini belirler.|
|`FigProjectItemsEvents`|REG_SZ|Değer için bkz. deyimi.|Bu otomasyon olayı için döndürülen metin dizesini belirler.|

 Aşağıdaki örneklerin hepsi kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarının altında bulunur.

## <a name="example-3"></a>Örnek 3

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Bu tür projelerin varsayılan adı.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Paketler altında kayıtlı uydu DLL'den alınarak alınan adın kaynak kimliği.|
|`Package`|REG_SZ|`%CLSID_Package%`|Paketler altında kayıtlı VSPackage'ın sınıf kimliği.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Şablon dosyalarının Project yolu. Bunlar New Project şablonu tarafından görüntülenen dosyalardır.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Öğe Şablonu Project varsayılan yolu. Bunlar, Yeni Öğe Ekle şablonu tarafından görüntülenen dosyalardır.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|IDE'nin Aç iletişim kutusunu **uygulamasına** olanak sağlar.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE tarafından, açılan projenin bu proje türü (proje fabrikası) tarafından iş olup olmadığını belirlemek için kullanılır. Birden fazla girişin biçimi noktalı virgülle ayrılmış bir listedir. Örneğin, "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE tarafından Farklı Kaydet işlemi için varsayılan dosya adı uzantısı olarak kullanılır.|
|`Filter Settings`|REG_DWORD|Çeşitli, aşağıdaki tabloda yer alan deyimlere ve açıklamalara bakın.|Bu ayarlar, kullanıcı arabirimi iletişim kutularında dosyaları görüntülemeye ilişkin çeşitli filtreleri ayarlamak için kullanılır.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Öğe Ekle şablonları için Kaynak Kimliği.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Yeni Öğe Ekle şablonunun iletişim kutusunda görüntülenen **proje öğelerinin** yolu.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Yeni Öğe Ekle iletişim kutusunda görüntülenen dosyaların ağaç düğümünde **sıralama sıralamayı** belirler.|

 Aşağıdaki tabloda, önceki kod segmentinde kullanılabilen Filtreler seçenekleri yer alır.

|Filtre seçeneği|Açıklama|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Filtrenin Dosyalarda Bul iletişim kutusundaki yaygın **filtrelerden biri olduğunu** gösterir. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|`CommonOpenFilesFilter`|Filtrenin **Dosya Aç** iletişim kutusundaki ortak filtrelerden biri olduğunu gösterir. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|`FindInFilesFilter`|Filtrenin **dosyalarda bul** iletişim kutusunda filtrelerden biri olacağını ve ortak filtrelerden sonra listelenmeyeceğini gösterir.|
|`NotOpenFileFilter`|Filtrenin **Dosya Aç** iletişim kutusunda kullanılmayacağını gösterir.|
|`NotAddExistingItemFilter`|Filtrenin **Varolan öğe** Ekle iletişim kutusunda kullanılmayacağını gösterir.|

 Varsayılan olarak, bir filtre bu bayrak kümesinden bir veya daha fazla yoksa, filtre **Varolan öğe Ekle** iletişim kutusunda ve **Dosya Aç** iletişim kutusunda ortak filtreler listelendikten sonra kullanılır. Filtre, **dosyalarda bul** iletişim kutusunda kullanılmaz.

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarı altında bulunur.

## <a name="example-4"></a>Örnek 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|yeni Project şablonları için kaynak kimliği.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Kayıtlı proje türünün projeleri için varsayılan yol.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Yeni projeler Sihirbazı iletişim kutusunda görünen projelerin sıralama sırasını ayarlar.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 bu türdeki projelerin yalnızca yeni Project iletişim kutusunda görüntülendiğini belirtir.|

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarı altında bulunur.

## <a name="example-5"></a>Örnek 5

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Hiçbiri|Diğer dosyalar proje girdileri için aşağıdaki girdilerin olduğunu gösteren varsayılan değer.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Yeni öğe Ekle şablon dosyaları için kaynak KIMLIĞI değeri.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**Yeni öğe Ekle** iletişim kutusunda görüntülenecek olan öğelerin varsayılan yolu.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**Yeni öğe Ekle** iletişim kutusunun ağaç düğümünde görüntülenmek üzere sıralama düzeni oluşturur.|

 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] anahtarı altında bulunur.

## <a name="example-6"></a>Örnek 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Menü girişi, IDE 'yi menü bilgilerini almak için kullanılan kaynağa yönlendirir. Bu veriler menü veritabanıyla birleştirildiğinde, kayıt defterinin MenusMerged bölümüne aynı anahtar eklenecektir. VSPackage, MenusMerged bölümünün altındaki herhangi bir şeyi doğrudan değiştirmemelidir. Aşağıdaki tabloda yer alan veri alanında, virgülle ayrılmış üç alan vardır. İlk alan, bir menü kaynak dosyasının tam yolunu tanımlar:

- İlk alan atlanırsa, menü kaynağı VSPackage GUID 'i tarafından tanımlanan uydu DLL 'den yüklenir.

  İkinci alan, CTMENU türünde bir menü kaynak KIMLIĞI tanımlar:

- Kaynak KIMLIĞI belirtilmişse ve dosya yolu ilk parametre tarafından sağlandıysa, tam dosya yolundan bir menü kaynağı yüklenir.

- Kaynak KIMLIĞI sağlanmışsa ancak dosya yolu yoksa, menü kaynağı uydu DLL 'sinden yüklenir.

- Tam dosya yolu sağlanmışsa ve kaynak KIMLIĞI atlanırsa, yüklenecek dosyanın bir CTO dosyası olması beklenir.

  Son alan, CTMENU kaynağı için sürüm numarasını tanımlar. Sürüm numarasını değiştirerek menüyü bir kez daha birleştirebilirsiniz.

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|% CLSID_Package%|REG_SZ|`,1000,1`|Menü bilgilerini almak için kaynak.|

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] anahtarı altında bulunur.

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|rakamların kaynak kimliği değeri yeni Project şablonları Project.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Yeni projeler dizininin varsayılan yolu. bu dizindeki öğeler, **yeni Project sihirbazı** iletişim kutusunda görüntülenecektir.|
|`SortPriority`|REG_DWORD|`41 (x29)`|**yeni Project** iletişim kutusunun ağaç düğümünde projelerin gösterileceği sırayı belirler.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 bu türdeki projelerin yalnızca **yeni Project** iletişim kutusunda görüntülendiğini belirtir.|

 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] anahtarı altında bulunur.

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Ad|Tür|Veriler|Açıklama|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Kayıtlı VSPackage sınıf KIMLIĞI.|
|`UseInterface`|REG_DWORD|`1`|1 Kullanıcı arabiriminin bu proje ile etkileşim kurmak için kullanılacağını gösterir. 0, UI arabirimi olmadığını gösterir.|

 Yeni proje türlerini denetleyen. vsz dosyaları sıklıkla bir RELATIVE_PATH girişi içerir. Bu yol, aşağıdaki kurulum anahtarında proje türünün \ProductDir girişinde belirtilen yola göredir:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 örneğin, Enterprise çerçeveleri proje şablonları aşağıdaki kayıt defteri girdilerini ekler:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files \ Microsoft Visual Studio \enterpriseframeworks\

 Yani,. vsz dosyasına bir PROJECT_TYPE = EF girişi eklerseniz, ortam daha önce belirtilen ProductDir dizininde. vsz dosyalarınızı bulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
