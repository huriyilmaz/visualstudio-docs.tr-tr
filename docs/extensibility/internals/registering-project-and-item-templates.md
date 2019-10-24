---
title: Proje ve öğe şablonlarını kaydetme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724622"
---
# <a name="registering-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Kaydetme
Proje türleri, proje ve proje öğesi şablonlarının bulunduğu dizinleri kaydetmelidir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Yeni Proje Ekle** ve **Yeni öğe Ekle** iletişim kutularında nelerin gösterileceğini belirlemek için proje türleriniz ile ilişkili kayıt bilgilerini kullanır.

 Şablonlar hakkında daha fazla bilgi için bkz. [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Projeler için kayıt defteri girişleri
 Aşağıdaki örneklerde, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*sürümü*> altında kayıt defteri girişleri gösterilmektedir. Eşlik eden tablolar örneklerde kullanılan öğeleri açıklar.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Name|Tür|Açıklama|
|----------|----------|-----------------|
|@|REG_SZ|Bu türden projelerin varsayılan adı.|
|DisplayName|REG_SZ|Paketler altında kayıtlı olan uydu DLL 'sinden alınacak adın kaynak KIMLIĞI.|
|Paket|REG_SZ|Paketler altına kayıtlı paketin sınıf KIMLIĞI.|
|ProjectTemplates dir|REG_SZ|Proje şablonu dosyalarının varsayılan yolu. Proje şablonu dosyaları **Yeni proje** şablonu tarafından görüntülenir.|

### <a name="registering-item-templates"></a>Öğe şablonlarını kaydetme
 Öğe şablonlarını depoladığınız dizini kaydetmeniz gerekir.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Name | Tür | Açıklama |
|--------------------------|-----------| - |
| @ | REG_SZ | Öğe şablonları eklemek için kaynak KIMLIĞI. |
| Templates dizini | REG_SZ | **Yeni öğe Ekle** sihirbazının iletişim kutusunda görünen proje öğelerinin yolu. |
| Templates Localizedsubdir | REG_SZ | Yerelleştirilmiş şablonları tutan Templates dizini 'nin alt dizinini isimeden bir dizenin kaynak KIMLIĞI. @No__t_0, varsa, uydu DLL 'Lerinden dize kaynağını yüklediği için, her uydu DLL farklı bir yerelleştirilmiş alt dizin adı içerebilir. |
| SortPriority | REG_DWORD | **Yeni öğe Ekle** iletişim kutusunda Şablonların gösterileceği sırayı yönetmek Için SortPriority ayarlayın. Daha önce şablon listesinde daha büyük SortPriority değerleri görünür. |

### <a name="registering-file-filters"></a>Dosya filtrelerini kaydetme
 İsteğe bağlı olarak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dosya adlarını sorulduğunda kullandığı filtreleri kaydedebilirsiniz. Örneğin, **Dosya Aç** iletişim kutusu için [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtresi:

 **Görsel C# dosyalar (\*. cs, \*. resx, \*. settings, \*. xsd, \*. wsdl); \*. cs, \*. resx, \*. Settings, 0. xsd, 1. wsdl)**

 Birden çok filtrenin kaydedilmesini desteklemek için her bir filtre, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*sürümü*> \projects \\ {\<*projectguıd*>} \filters altında kendi alt anahtarına kaydedilir \\ <*alt anahtarı*>. Alt anahtar adı rastgele;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alt anahtarın adını yoksayar ve yalnızca değerlerini kullanır.

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

|Name|Tür|Açıklama|
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