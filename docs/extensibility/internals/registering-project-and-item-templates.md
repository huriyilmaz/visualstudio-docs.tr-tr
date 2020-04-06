---
title: Proje ve Madde Şablonlarını Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705820"
---
# <a name="registering-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Kaydetme
Proje türlerinin, proje ve proje öğesi şablonlarının bulunduğu dizinleri kaydetmesi gerekir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**Yeni Proje Ekle** ve Yeni Öğe **Ekle** iletişim kutularında ne gösterilenleri belirlemek için proje türlerinızla ilişkili kayıt bilgilerini kullanır.

 Şablonlar hakkında daha fazla bilgi için [bkz.](../../extensibility/internals/adding-project-and-project-item-templates.md)

## <a name="registry-entries-for-projects"></a>Projeler için Kayıt Girişleri
 Aşağıdaki örnekler, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Sürüm*> altında kayıt defteri girişlerini gösterir. Eşlik eden tablolar örneklerde kullanılan öğeleri açıklar.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Adı|Tür|Açıklama|
|----------|----------|-----------------|
|@|REG_SZ|Bu tür projelerin varsayılan adı.|
|DisplayName|REG_SZ|Paketler altında kayıtlı dll uydudan alınacak adın kaynak kimliği.|
|Paket|REG_SZ|Paketler altında kayıtlı paketin sınıf kimliği.|
|ProjeTemplatesDir|REG_SZ|Proje Şablonu dosyalarının varsayılan yolu. Proje Şablonu dosyaları **Yeni Proje** şablonu tarafından görüntülenir.|

### <a name="registering-item-templates"></a>Madde Şablonlarını Kaydetme
 Madde şablonlarını depoladığınız dizini kaydetmeniz gerekir.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Adı | Tür | Açıklama |
|--------------------------|-----------| - |
| @ | REG_SZ | Madde Ekle şablonları için kaynak kimliği. |
| ŞablonlarDir | REG_SZ | **Yeni Öğe Ekle** sihirbazı için iletişim kutusunda görüntülenen proje öğelerinin yolu. |
| ŞablonlarYerelleştirilmişSubDir | REG_SZ | Yerelleştirilmiş şablonlar tutan TemplatesDir alt dizinini adlandıran bir dizenin kaynak kimliği. Dize kaynağını uydu DL'lerinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yükler, çünkü bunlara sahipseniz, her uydu DLL farklı bir yerelleştirilmiş alt dizin adı içerebilir. |
| SıralamaÖnceliği | REG_DWORD | **Yeni Öğe Ekle** iletişim kutusunda şablonların görüntülenme sırasını yönetmek için SıralamaÖnceliği'ni ayarlayın. Daha büyük SıralamaÖnceliği değerleri şablon listesinde daha önce görünür. |

### <a name="registering-file-filters"></a>Dosya filtrelerini kaydetme
 İsteğe bağlı olarak, dosya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adları için istendiğinde kullanan filtreleri kaydedebilirsiniz. Örneğin, Dosya [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] **aç** iletişim kutusunun filtresi:

 **Görsel C#\*Dosyaları (\*.cs,\*.resx, .settings,\*.xsd,\*.wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Birden çok filtrenin kaydını desteklemek için, her filtre HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Sürüm* \\>\ProjectGUID\<*ProjectGUID*>}\Filters\\<Subkey> altında kendi alt*anahtarında* kaydedilir. Alt anahtar adı rasgele; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alt anahtarın adını yok sayar ve yalnızca değerlerini kullanır.

 Aşağıdaki tabloda gösterilen bayrakları ayarlayarak filtrenin kullanıldığı bağlamları denetleyebilirsiniz. Bir filtrede bayrak kümesi yoksa, **Varolan Öğe Ekle** iletişim kutusundaki ve **Dosyayı Aç** iletişim kutusundaki yaygın filtrelerden sonra listelenir, ancak **Dosyalarda Bul** iletişim kutusunda kullanılmaz.

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

|Adı|Tür|Açıklama|
|----------|----------|-----------------|
|CommonFindFilesFiltresi|REG_DWORD|Filtreyi **Dosyalarda Bul** iletişim kutusundaki yaygın filtrelerden biri yapar. Yaygın filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|CommonOpenFilesFiltresi|REG_DWORD|Filtreyi **Dosya Aç** iletişim kutusundaki yaygın filtrelerden biri yapar. Yaygın filtreler ortak olarak işaretlenmeden önce filtre listesinde listelenir.|
|FindinFilesFilter|REG_DWORD|**Dosyaları Bul** iletişim kutusundaki yaygın filtrelerden sonra filtreyi listeler.|
|NotOpenFileFilter|REG_DWORD|**Dosya aç** iletişim kutusunda filtrenin kullanılmadığını gösterir.|
|NotAddExistingItemFilter|REG_DWORD|**Filtrenin Varolan Öğe Ekle** iletişim kutusunda kullanılmadığını gösterir.|
|SıralamaÖnceliği|REG_DWORD|Filtrelerin görüntülenme sırasını yönetmek için SıralamaÖnceliği'ni ayarlayın. Daha büyük Sıralama Önceliği değerleri filtre listesinde daha önce görünür.|

## <a name="directory-structure"></a>Dizin Yapısı
 VSPackages, konum tümleşik geliştirme ortamı (IDE) üzerinden kayıtlı olduğu sürece şablon dosyalarını ve klasörlerini yerel veya uzak bir diske koyabilir. Ancak, organizasyon kolaylığı için, ürününüzün yükleme yolu altında aşağıdaki dizin yapısını öneririz.

 \Şablonlar

 \Projeler (proje şablonlarını içerir)

 \Uygulamalar

 \Bileşenler

 \ ...

 \ProjectItems (proje öğelerini içerir)

 \Sınıf

 \Form

 \Web Sayfası

 \HelperFiles (çok dosyalı proje öğelerinde kullanılan dosyaları içerir)

 \Sihirbaz Dosyaları

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve Proje Öğesi Şablonları Ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Uygulamaları Yerelleştirme](../../ide/globalizing-and-localizing-applications.md)
- [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
