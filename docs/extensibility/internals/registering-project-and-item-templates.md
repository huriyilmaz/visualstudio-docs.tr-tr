---
title: Proje ve Öğe Şablonlarını | Microsoft Docs
description: Proje Visual Studio kayıt bilgilerini kullanarak Yeni Proje Ekle ve Yeni Öğe Ekle iletişim kutularında neler göster göstereceğiz?
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
ms.workload:
- vssdk
ms.openlocfilehash: 8b60022c6adf65d0b0d60d32b4ad7ae72067726d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905638"
---
# <a name="registering-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Kaydetme
Proje türleri, proje ve proje öğesi şablonlarının bulunduğu dizinleri kaydetmeli. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , Proje türleriniz ile ilişkili kayıt bilgilerini kullanarak Yeni Proje Ekle ve Yeni **Öğe Ekle** iletişim **kutularında nelerin göster göstereceğizlerini** belirler.

 Şablonlar hakkında daha fazla bilgi için [bkz. Proje ve Proje Öğesi Şablonları Ekleme.](../../extensibility/internals/adding-project-and-project-item-templates.md)

## <a name="registry-entries-for-projects"></a>Projeler için Kayıt Defteri Girdileri
 Aşağıdaki örneklerde, Sürüm HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudioaltında kayıt \\ < *defteri girdileri*>. Eşlik eden tablolar, örneklerde kullanılan öğeleri açıklar.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Ad|Tür|Açıklama|
|----------|----------|-----------------|
|@|REG_SZ|Bu tür projelerin varsayılan adı.|
|DisplayName|REG_SZ|Paketler altında kayıtlı uydu DLL'den alınarak alınan adın kaynak kimliği.|
|Paket|REG_SZ|Paketler altında kayıtlı paketin sınıf kimliği.|
|ProjectTemplatesDir|REG_SZ|Proje Şablonu dosyalarının varsayılan yolu. Proje Şablonu dosyaları Yeni Proje şablonu **tarafından** görüntülenir.|

### <a name="registering-item-templates"></a>Öğe Şablonlarını Kaydetme
 Öğe şablonlarını depolayacaksınız dizinini kaydetmeniz gerekir.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Ad | Tür | Açıklama |
|--------------------------|-----------| - |
| @ | REG_SZ | Öğe Ekle şablonları için Kaynak Kimliği. |
| TemplatesDir | REG_SZ | Yeni Öğe Ekle sihirbazının iletişim kutusunda görüntülenen **proje öğelerinin** yolu. |
| ŞablonlarLocalizedSubDir | REG_SZ | Yerelleştirilmiş şablonların yer alan TemplatesDir alt dizinine ad sağlayan bir dizenin kaynak kimliği. Varsa, uydu DLL'lerinden dize kaynağını yükleyemediklerinden, her uydu DLL farklı bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yerelleştirilmiş alt dizin adı içerebilir. |
| SortPriority | REG_DWORD | Şablonların Yeni Öğe Ekle iletişim kutusunda görüntülenme sıralarını  idare etmek için SortPriority'yi ayarlayın. Şablon listesinde daha önce daha büyük SortPriority değerleri görünür. |

### <a name="registering-file-filters"></a>Dosya filtrelerini kaydetme
 İsteğe bağlı olarak, dosya adları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] istendiğinde kullanan filtreleri kaydedebilirsiniz. Örneğin, Dosya [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Aç iletişim kutusu **filtresi** şöyledir:

 **Visual C# Files ( \* .cs, \* .resx, \* .settings, \* .xsd, \* .wsdl); \* . cs, \* .resx, \* .settings, \* .xsd, \* .wsdl)**

 Birden çok filtrenin kaydını desteklemek için her filtre, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Version*>\Projects { \\ \<*ProjectGUID*> }\Filters \\ < *Subkey*>. Alt anahtar adı rastgeledir; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alt anahtarın adını yoksayır ve yalnızca değerlerini kullanır.

 Aşağıdaki tabloda gösterilen bayrakları ayarerek filtrenin hangi bağlamlarda kullanıldığına bakabilirsiniz. Bir filtrede ayarlanmış bayrak yoksa, Mevcut Öğe Ekle iletişim  kutusunda ve Dosya Aç  iletişim kutusunda ortak filtrelerden sonra listelenir, ancak Dosyalarda Bul iletişim kutusunda kullanılmaz. 

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
|CommonFindFilesFilter|REG_DWORD|Filtreyi Dosyalarda Bul iletişim kutusundaki yaygın **filtrelerden biri** yapar. Genel filtreler, filtreler ortak olarak işaretlenmiyor olmadan önce filtre listesinde listelenir.|
|CommonOpenFilesFilter|REG_DWORD|Filtreyi Dosya Aç iletişim kutusundaki yaygın **filtrelerden biri** yapar. Genel filtreler, filtreler ortak olarak işaretlenmiyor olmadan önce filtre listesinde listelenir.|
|FindInFilesFilter|REG_DWORD|Dosyalarda Bul iletişim kutusunda sık kullanılan **filtreden sonra gelen filtreyi** listeler.|
|NotOpenFileFilter|REG_DWORD|Filtrenin Dosya Aç iletişim kutusunda **kullanılma olmadığını** gösterir.|
|NotAddExistingItemFilter|REG_DWORD|Filtrenin Var Olan Öğe Ekle iletişim **kutusunda kullanılma olmadığını** gösterir.|
|SortPriority|REG_DWORD|Filtrelerin görüntülenme sıralarını idare etmek için SortPriority'yi ayarlayın. Daha büyük SortPriority değerleri filtre listesinde daha önce görünür.|

## <a name="directory-structure"></a>Dizin Yapısı
 Konum tümleşik geliştirme ortamı (IDE) aracılığıyla kayıtlı olduğu sürece VSPackage'lar şablon dosyalarını ve klasörleri yerel veya uzak diskin herhangi bir yerine yerleştirebilirsiniz. Ancak, kuruluş kolaylığı için, ürününüz yükleme yolu altında aşağıdaki dizin yapısını öneririz.

 \Templates

 \Projeler (proje şablonlarını içerir)

 \Applications

 \Components

 \ ...

 \ProjectItems (proje öğelerini içerir)

 \Class

 \Form

 \Web Sayfası

 \HelperFiles (çok dosyalı proje öğelerinde kullanılan dosyaları içerir)

 \WizardFiles

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Uygulamaları Yerelleştirme](../../ide/globalizing-and-localizing-applications.md)
- [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
