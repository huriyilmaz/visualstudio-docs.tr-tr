---
title: Project ve öğe şablonlarını kaydetme | Microsoft Docs
description: Visual Studio yeni Project ekle ve yeni öğe ekle iletişim kutularında nelerin gösterileceğini belirlemek için proje türleriniz için kayıt bilgilerini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 791e8d9713b1f12cf7e388d87449b4a171c029a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062985"
---
# <a name="registering-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Kaydetme
Project türler, proje ve proje öğesi şablonlarının bulunduğu dizinleri kaydetmelidir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**yeni Project ekle** ve **yeni öğe ekle** iletişim kutularında nelerin gösterileceğini belirlemek için proje türleriniz ile ilişkili kayıt bilgilerini kullanır.

 şablonlar hakkında daha fazla bilgi için bkz. [Project ve Project öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Projeler için kayıt defteri girişleri
 Aşağıdaki örneklerde HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Sürüm*> altında kayıt defteri girişleri gösterilmektedir. Eşlik eden tablolar örneklerde kullanılan öğeleri açıklar.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Ad|Tür|Açıklama|
|----------|----------|-----------------|
|@|REG_SZ|Bu türden projelerin varsayılan adı.|
|DisplayName|REG_SZ|Paketler altında kayıtlı olan uydu DLL 'sinden alınacak adın kaynak KIMLIĞI.|
|Paket|REG_SZ|Paketler altına kayıtlı paketin sınıf KIMLIĞI.|
|ProjectTemplates dir|REG_SZ|Project şablon dosyalarının varsayılan yolu. Project şablon dosyaları **yeni Project** şablonu tarafından görüntülenir.|

### <a name="registering-item-templates"></a>Öğe şablonlarını kaydetme
 Öğe şablonlarını depoladığınız dizini kaydetmeniz gerekir.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Ad | Tür | Açıklama |
|--------------------------|-----------| - |
| @ | REG_SZ | Öğe şablonları eklemek için kaynak KIMLIĞI. |
| Templates dizini | REG_SZ | **Yeni öğe Ekle** sihirbazının iletişim kutusunda görünen proje öğelerinin yolu. |
| Templates Localizedsubdir | REG_SZ | Yerelleştirilmiş şablonları tutan Templates dizini 'nin alt dizinini isimeden bir dizenin kaynak KIMLIĞI. , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Varsa, uydu dll 'lerinden dize kaynağını yükler, her uydu dll farklı bir yerelleştirilmiş alt dizin adı içerebilir. |
| SortPriority | REG_DWORD | **Yeni öğe Ekle** iletişim kutusunda Şablonların gösterileceği sırayı yönetmek Için SortPriority ayarlayın. Daha önce şablon listesinde daha büyük SortPriority değerleri görünür. |

### <a name="registering-file-filters"></a>Dosya filtrelerini kaydetme
 İsteğe bağlı olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dosya adlarını sorulduğunda kullanan filtreleri kaydedebilirsiniz. Örneğin, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] **Dosya Aç** iletişim kutusu için filtre:

 **Visual C# dosyaları ( \* . cs, \* . resx, \* . Settings, \* . xsd, \* . wsdl); \* . CS, \* . resx, \* . Settings, \* . xsd, \* . wsdl)**

 Birden çok filtrenin kaydedilmesini desteklemek için, her bir filtre HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Sürüm*> \projects \\ { \<*ProjectGUID*> } \filters \\ < *AltAnahtar*> altında kendi alt anahtarına kaydedilir. Alt anahtar adı rastgele; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alt anahtarın adını yoksayar ve yalnızca kendi değerlerini kullanır.

 Aşağıdaki tabloda gösterilen bayraklar ayarlanarak bir filtrenin kullanıldığı bağlamların denetimini yapabilirsiniz. Bir filtrenin bayrak ayarlanmamışsa, **Varolan öğe Ekle** iletişim kutusunda ve **Dosya Aç** iletişim kutusunda ortak filtrelerden sonra listelenir, ancak **dosyalarda bul** iletişim kutusunda kullanılmaz.

```
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]
@="#3"
"CommonOpenFilesFilter"=dword:00000000
"CommonFindFilesFilter"=dword:00000000
"FindInFilesFilter"=dword:00000000
"NotOpenFileFilter"=dword:00000000
"NotAddExistingItemFilter"=dword:00000000
"SortPriority"=dword:00000064
```

|Ad|Tür|Açıklama|
|----------|----------|-----------------|
|Commonfindfilesfiltresi|REG_DWORD|**Dosyalarda bul** iletişim kutusunda ortak filtrelerden birine filtre uygular. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|Commonopenfilesfiltresi|REG_DWORD|**Dosya Aç** iletişim kutusunda ortak filtrelerden birine filtre uygular. Ortak filtreler, filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|Finınfilesfiltresi|REG_DWORD|**Dosyalarda bul** iletişim kutusunda ortak filtrelerden sonra filtreyi listeler.|
|NotOpenFileFilter|REG_DWORD|Filtrenin **Dosya Aç** iletişim kutusunda kullanılmadığını gösterir.|
|Notaddexistingıtemfilter|REG_DWORD|Filtrenin **Varolan öğe Ekle** iletişim kutusunda kullanılmadığını gösterir.|
|SortPriority|REG_DWORD|Filtrelerin gösterileceği sırayı yönetmek için SortPriority ayarlayın. Daha büyük SortPriority değerleri, daha önce filtre listesinde görünür.|

## <a name="directory-structure"></a>Dizin yapısı
 VSPackages, konum tümleşik geliştirme ortamı (IDE) ile kaydedildiği sürece, şablon dosyalarını ve klasörlerini yerel veya uzak bir diskte herhangi bir yere yerleştirebilir. Ancak kuruluş kolaylığı için, ürününüzün yükleme yolu altında aşağıdaki dizin yapısını öneririz.

 \ Şablonlar

 \Projects (proje şablonlarını içerir)

 \ Uygulamalar

 \ Bileşenler

 \ ...

 \Projectıtems (proje öğelerini içerir)

 \Class

 \ Form

 \Web sayfası

 \ Helperfiles (birden çok dosya proje öğelerinde kullanılan dosyaları içerir)

 \WizardFiles

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Uygulamaları Yerelleştirme](../../ide/globalizing-and-localizing-applications.md)
- [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
