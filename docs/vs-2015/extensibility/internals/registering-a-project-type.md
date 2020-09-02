---
title: Proje türünü kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e0140b752adda02aba6126580ec08ee1f7536a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837596"
---
# <a name="registering-a-project-type"></a>Proje Türü Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni bir proje türü oluşturduğunuzda, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Proje türü tanımak ve bunlarla çalışmak için etkinleştirilecek kayıt defteri girişleri oluşturmanız gerekir. Genellikle bu kayıt defteri girdilerini bir kayıt defteri betiği (. RGS) dosyası kullanarak oluşturursunuz.  
  
 Aşağıdaki örnekte, kayıt defterindeki deyimler varsayılan yolları ve verileri sağlar ve ardından her deyimin kayıt defteri betiğinin girdilerini içeren bir tablo gelir. Tablolar, komut dosyası girişlerini ve deyimleriyle ilgili ek bilgileri sağlar.  
  
> [!NOTE]
> Aşağıdaki kayıt defteri bilgileri, proje türünü kaydetmek için yazmakta olduğunuz kayıt defteri betiklerinde bulunan girişlerin türüne ve amaçlarına bir örnek olarak tasarlanmıştır. Gerçek girdlarınız ve kullanımları, proje türünün belirli gereksinimlerine göre değişiklik gösterebilir. Geliştirmekte olduğunuz projenin türüne yakından benzeyen bir tane bulmak için mevcut örnekleri gözden geçirmeniz ve ardından bu örneğe ait kayıt defteri betiğini gözden geçirmeniz gerekir.  
  
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
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|. Figp uzantısına sahip proje türü dosyalarının adı ve açıklaması.|  
|`Content Type`|REG_SZ|`Text/plain`|Proje dosyaları için içerik türü.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Bu türün projesi için varsayılan simge kullanıldı. % MODULE% deyimleri kayıt defterinde proje türü DLL 'sinin varsayılan konumuna tamamlanır.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Bu proje türünün açıldığı varsayılan uygulama.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Bu türden bir proje açıldığında çalıştırılacak varsayılan komut.|  
  
 Aşağıdaki örnekler HKEY_LOCAL_MACHINE ve [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] anahtarı altındaki kayıt defterinde bulunur.  
  
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
  
 Aşağıdaki örneklerin tümü, kayıt defterinde [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarı altında bulunur.  
  
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
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Bu türdeki projelerin varsayılan adı.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Paketler altında kayıtlı olan uydu DLL 'sinden alınacak adın kaynak KIMLIĞI.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Paketler altına kaydedilen VSPackage sınıf KIMLIĞI.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Proje şablonu dosyalarının varsayılan yolu. Bunlar, yeni proje şablonu tarafından görüntülenen dosyalardır.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Proje öğesi şablon dosyalarının varsayılan yolu. Bunlar, yeni öğe Ekle şablonu tarafından görüntülenen dosyalardır.|  
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
|`CommonFindFilesFilter`|Filtrenin **dosyalarda bul** iletişim kutusunda ortak filtrelerden biri olduğunu gösterir. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|  
|`CommonOpenFilesFilter`|Filtrenin **Dosya Aç** iletişim kutusundaki ortak filtrelerden biri olduğunu gösterir. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|  
|`FindInFilesFilter`|Filtrenin **dosyalarda bul** iletişim kutusunda filtrelerden biri olacağını ve ortak filtrelerden sonra listelenmeyeceğini gösterir.|  
|`NotOpenFileFilter`|Filtrenin **Dosya Aç** iletişim kutusunda kullanılmayacağını gösterir.|  
|`NotAddExistingItemFilter`|Filtrenin **Varolan öğe** Ekle iletişim kutusunda kullanılmayacağını gösterir.|  
  
 Varsayılan olarak, bir filtre bu bayrak kümesinden bir veya daha fazla yoksa, filtre **Varolan öğe Ekle** iletişim kutusunda ve **Dosya Aç** iletişim kutusunda ortak filtreler listelendikten sonra kullanılır. Filtre, **dosyalarda bul** iletişim kutusunda kullanılmaz.  
  
 Aşağıdaki örneklerin tümü, kayıt defterinde [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarı altında bulunur.  
  
## <a name="example"></a>Örnek  
  
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
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Yeni proje şablonları için kaynak KIMLIĞI.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Kayıtlı proje türünün projeleri için varsayılan yol.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Yeni projeler Sihirbazı iletişim kutusunda görünen projelerin sıralama sırasını ayarlar.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu türdeki projelerin yalnızca yeni proje iletişim kutusunda görüntülendiğini belirtir.|  
  
 Aşağıdaki örneklerin tümü, kayıt defterinde [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] anahtarı altında bulunur.  
  
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
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Hiçbiri|Diğer dosyalar proje girdileri için aşağıdaki girdilerin olduğunu gösteren varsayılan değer.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Yeni öğe Ekle şablon dosyaları için kaynak KIMLIĞI değeri.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**Yeni öğe Ekle** iletişim kutusunda görüntülenecek olan öğelerin varsayılan yolu.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**Yeni öğe Ekle** iletişim kutusunun ağaç düğümünde görüntülenmek üzere sıralama düzeni oluşturur.|  
  
 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] anahtarı altında bulunur.  
  
## <a name="example"></a>Örnek  
  
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
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|% CLSID_Package%|REG_SZ|`,1000,1`|Menü bilgilerini almak için kaynak.|  
  
 Aşağıdaki örneklerin tümü, kayıt defterinde [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] anahtarı altında bulunur.  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Şekil projesi yeni proje şablonlarının kaynak KIMLIĞI değeri.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Yeni projeler dizininin varsayılan yolu. Bu dizindeki öğeler, **Yeni proje Sihirbazı** iletişim kutusunda görüntülenir.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|**Projenin yeni proje** iletişim kutusunun ağaç düğümünde gösterileceği sırayı belirler.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0, bu türdeki projelerin yalnızca **Yeni proje** iletişim kutusunda görüntülendiğini belirtir.|  
  
 Aşağıdaki örnek kayıt defterinde [HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio\9.0exp\ınstalınstalsınk\products] anahtarı altında bulunur.  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Ad|Tür|Veriler|Description|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Kayıtlı VSPackage sınıf KIMLIĞI.|  
|`UseInterface`|REG_DWORD|`1`|1 Kullanıcı arabiriminin bu proje ile etkileşim kurmak için kullanılacağını gösterir. 0, UI arabirimi olmadığını gösterir.|  
  
 Yeni proje türlerini denetleyen. vsz dosyaları sıklıkla bir RELATIVE_PATH girişi içerir. Bu yol, aşağıdaki kurulum anahtarında proje türünün \ProductDir girişinde belirtilen yola göredir:  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Örneğin, kurumsal çerçeveler proje şablonları aşağıdaki kayıt defteri girdilerini ekler:  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Yani,. vsz dosyasına bir PROJECT_TYPE = EF girişi eklerseniz, ortam daha önce belirtilen ProductDir dizininde. vsz dosyalarınızı bulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Proje modelinin öğeleri](../../extensibility/internals/elements-of-a-project-model.md)   
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
