---
title: Project türünü kaydetme | Microsoft Docs
description: Visual Studio, yeni proje türünü tanımasını ve ile çalışmasını sağlayan kayıt defteri girişlerini oluşturma hakkında bilgi edinin.
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
ms.openlocfilehash: 8b3966b807f87fd6767727e66b6f5b035cfc1510
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725021"
---
# <a name="registering-a-project-type"></a>Proje Türü Kaydetme
Yeni bir proje türü oluşturduğunuzda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje türü tanımak ve bunlarla çalışmak için etkinleştirilecek kayıt defteri girişleri oluşturmanız gerekir. Genellikle bu kayıt defteri girdilerini bir kayıt defteri betiği (. RGS) dosyası kullanarak oluşturursunuz.

 Aşağıdaki örnekte, kayıt defterindeki deyimler varsayılan yolları ve verileri sağlar ve ardından her deyimin kayıt defteri betiğinin girdilerini içeren bir tablo gelir. Tablolar, komut dosyası girişlerini ve deyimleriyle ilgili ek bilgileri sağlar.

> [!NOTE]
> Aşağıdaki kayıt defteri bilgileri, proje türünü kaydetmek için yazmakta olduğunuz kayıt defteri betiklerinde bulunan girişlerin türüne ve amaçlarına bir örnek olarak tasarlanmıştır. Gerçek girdlarınız ve kullanımları, proje türünün belirli gereksinimlerine göre değişiklik gösterebilir. Geliştirmekte olduğunuz projenin türüne yakından benzeyen bir tane bulmak için mevcut örnekleri gözden geçirmeniz ve ardından bu örneğe ait kayıt defteri betiğini gözden geçirmeniz gerekir.

 Aşağıdaki örnekler HKEY_CLASSES_ROOT.

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

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|. Figp uzantısına sahip proje türü dosyalarının adı ve açıklaması.|
|`Content Type`|REG_SZ|`Text/plain`|Proje dosyaları için içerik türü.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Bu türün projesi için varsayılan simge kullanıldı. % MODULE% deyimleri kayıt defterinde proje türü DLL 'sinin varsayılan konumuna tamamlanır.|
|`@`|REG_SZ|`&Open in Visual Studio`|Bu proje türünün açıldığı varsayılan uygulama.|
|`@`|REG_SZ|`devenv.exe "%1"`|Bu türden bir proje açıldığında çalıştırılacak varsayılan komut.|

 Aşağıdaki örnekler HKEY_LOCAL_MACHINE ve [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] anahtarı altındaki kayıt defterinde bulunur.

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

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`@` Varsayılanını|REG_SZ|`FigPrj Project VSPackage`|Bu kayıtlı VSPackage 'ın yerelleştirilebilir adı (proje türü).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Proje türü DLL dosyasının yolu. IDE bu DLL 'yi yükler ve nesneyi oluşturmaya ulaşmak için VSPackage CLSID değerini geçirir `DllGetClassObject` <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .|
|`CompanyName`|REG_SZ|`Microsoft`|Proje türünü geliştiren şirketin adı.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Proje türünün adı.|
|`ProductVersion`|REG_SZ|`9.0`|Proje türü sürümünün sürüm numarası.|
|`MinEdition`|REG_SZ|`professional`|Kaydedilen VSPackage sürümü.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Proje VSPackage için paket yükleme anahtarı. Bu anahtar, bir proje, ortam başladıktan sonra yüklendiğinde onaylanır.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Proje türü için yerelleştirilmiş kaynakları içeren uydu DLL dosyasının adı.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Uydu DLL yolu.|
|`FigProjectsEvents`|REG_SZ|Değer için bkz..|Bu Otomasyon olayı için döndürülen metin dizesini belirler.|
|`FigProjectItemsEvents`|REG_SZ|Değer için bkz..|Bu Otomasyon olayı için döndürülen metin dizesini belirler.|

 Aşağıdaki örneklerin tümü kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarı altında bulunur.

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

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Bu türdeki projelerin varsayılan adı.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Paketler altında kayıtlı olan uydu DLL 'sinden alınacak adın kaynak KIMLIĞI.|
|`Package`|REG_SZ|`%CLSID_Package%`|Paketler altına kaydedilen VSPackage sınıf KIMLIĞI.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Project şablon dosyalarının varsayılan yolu. bunlar, yeni Project şablonu tarafından görüntülenen dosyalardır.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Project öğesi şablon dosyalarının varsayılan yolu. Bunlar, yeni öğe Ekle şablonu tarafından görüntülenen dosyalardır.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|IDE 'nin **Aç** iletişim kutusunu uygulamasına olanak sağlar.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE tarafından, açılmakta olan projenin bu proje türü (proje fabrikası) tarafından işlenip işlenmediğini tespit etmek için kullanılır. Birden fazla girdinin biçimi noktalı virgülle ayrılmış bir liste. Örneğin, "VDPROJ; VDP".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Farklı Kaydet işlemi için varsayılan dosya adı uzantısı olarak IDE tarafından kullanılır.|
|`Filter Settings`|REG_DWORD|Çeşitli, bkz. tablolar ve Yorumlar aşağıdaki tablo.|Bu ayarlar, Kullanıcı arabirimi iletişim kutularında dosya görüntülemek için çeşitli filtreleri ayarlamak üzere kullanılır.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Öğe şablonları eklemek için kaynak KIMLIĞI.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**Yeni öğe Ekle** şablonu için iletişim kutusunda görünen proje öğelerinin yolu.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**Yeni öğe Ekle** iletişim kutusunda gösterilecek dosyaların ağaç düğümündeki sıralama düzenini belirler.|

 Aşağıdaki tabloda, önceki kod segmentinde bulunan filtre seçenekleri gösterilmektedir.

|Filtre seçeneği|Description|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Filtrenin **dosyalarda bul** iletişim kutusunda ortak filtrelerden biri olduğunu gösterir. Ortak filtreler, filtreler ortak olarak işaretlenmiyor olmadan önce filtre listesinde listelenir.|
|`CommonOpenFilesFilter`|Filtrenin Dosya Aç iletişim kutusundaki yaygın filtrelerden **biri olduğunu** gösterir. Ortak filtreler, filtreler ortak olarak işaretlenmiyor olmadan önce filtre listesinde listelenir.|
|`FindInFilesFilter`|Filtrenin Dosyalarda Bul iletişim kutusundaki  filtrelerden biri olacağını ve ortak filtrelerin ardından listele olacağını gösterir.|
|`NotOpenFileFilter`|Filtrenin Dosya Aç iletişim kutusunda **kullanılmay olacağını** belirtir.|
|`NotAddExistingItemFilter`|Filtrenin Var Olan Öğe Ekle iletişim **kutusunda kullanılmay olacağını** gösterir.|

 Varsayılan olarak, bir filtrede bu bayraklardan biri veya daha fazlası  ayarlanmazsa, filtre  Mevcut Öğe Ekle iletişim kutusunda ve ortak filtreler listelendikten sonra Dosya Aç iletişim kutusunda kullanılır. Filtre Dosyalarda Bul **iletişim kutusunda** kullanılamaz.

 Aşağıdaki örneklerin hepsi kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarının altında bulunur.

## <a name="example-4"></a>Örnek 4

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Yeni uygulama şablonlarının Project kimliği.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Kayıtlı proje türünde projeler için varsayılan yol.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Yeni Projeler sihirbazı iletişim kutusunda görüntülenen projelerin sıralama sıralamalarını ayarlar.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu tür projelerin yalnızca Yeni Veri Kaynağı iletişim kutusunda Project gösterir.|

 Aşağıdaki örneklerin hepsi kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarının altında bulunur.

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

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Hiçbiri|Aşağıdaki girdilerin Çeşitli Dosyalar projeleri girdileri için olduğunu gösteren varsayılan değer.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Yeni Öğe Ekle şablon dosyaları için Kaynak Kimliği değeri.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Yeni Öğe Ekle iletişim kutusunda görüntülenecek **öğelerin varsayılan** yolu.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Yeni Öğe Ekle iletişim kutusunun ağaç düğümünde **görüntülenmek için sıralama düzeni** sağlar.|

 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] anahtarının altında yer almaktadır.

## <a name="example-6"></a>Örnek 6

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Menü girişi, IDE'ye menü bilgilerini almak için kullanılan kaynağa gösterir. Bu veriler menü veritabanıyla birleştirilmiştir, aynı anahtar kayıt defterinin MenuMerged bölümüne eklenir. VSPackage, Doğrudan MenülerMerged bölümünde hiçbir şeyi değiştirmez. Aşağıdaki tabloda yer alan Veri alanında üç virgülle ayrılmış alan vardır. İlk alan, bir menü kaynak dosyasının tam yolunu tanımlar:

- İlk alan atlanırsa, menü kaynağı VSPackage GUID'si tarafından tanımlanan uydu DLL'den yüklenir.

  İkinci alan, CTMENU türünde bir menü kaynak kimliğini tanımlar:

- Kaynak kimliği belirtilirse ve dosya yolu ilk parametre tarafından sağlanırsa, tam dosya yolundan bir menü kaynağı yüklenir.

- Kaynak kimliği sağlanıyorsa ancak dosya yolu sağlanmazsa, menü kaynağı uydu DLL'den yüklenir.

- Tam dosya yolu sağlanırsa ve kaynak kimliği atlanırsa, yüklenecek dosyanın bir CTO dosyası olması beklenir.

  Son alan, CTMENU kaynağının sürüm numarasını tanımlar. Sürüm numarasını değiştirerek menüyü yeniden birleştirebilirsiniz.

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|Menü bilgilerini almak için kaynak.|

 Aşağıdaki örneklerin hepsi kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] anahtarının altında bulunur.

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Şekiller için Kaynak Kimliği değeri Project Yeni Project şablonları.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Yeni Projeler dizininin varsayılan yolu. Bu dizindeki öğeler Yeni Dizin **Sihirbazı iletişim Project görüntülenir.**|
|`SortPriority`|REG_DWORD|`41 (x29)`|Projelerin Yeni Proje Ekle iletişim kutusunun ağaç düğümünde görüntülenme **Project** belirtir.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu tür projelerin yalnızca Yeni Veri Kaynağı **iletişim kutusunda Project** gösterir.|

 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] anahtarının altında yer almaktadır.

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Ad|Tür|Veriler|Description|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Kayıtlı VSPackage'ın sınıf kimliği.|
|`UseInterface`|REG_DWORD|`1`|1, kullanıcı arabiriminin bu projeyle etkileşim kurmak için kullan olacağını gösterir. 0, kullanıcı arabirimi olmadığını gösterir.|

 Yeni proje türlerini kontrol altına alan .vsz dosyaları sıklıkla bir RELATIVE_PATH içerir. Bu yol, aşağıdaki Kurulum anahtarında proje türünün \ProductDir girdisi altında belirtilen yola göredir:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup

 Örneğin, Enterprise Frameworks proje şablonları aşağıdaki kayıt defteri girdilerini ekler:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\

 Bu, .vsz dosyasına PROJECT_TYPE=EF girişi eklersiniz, ortam daha önce belirtilen ProductDir dizininde .vsz dosyalarınızı bulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
