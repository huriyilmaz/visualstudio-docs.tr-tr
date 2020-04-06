---
title: Yeni Öğe Ekle İletişim Kutusu'na Katkıda Bulunmak | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709283"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna katkıda bulunun
Proje alt türü, **Projeler** kayıt defteri alt anahtarının altına **Öğe Ekle** şablonlarını kaydederek Yeni **Öğe Ekle** iletişim kutusu için öğelerin tam yeni bir dizinini sağlayabilir.

## <a name="register-add-new-item-templates"></a>Kaydol Yeni Öğe Şablonları Ekle
 Bu bölüm kayıt defterinde **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** altında yer almaktadır. Aşağıdaki kayıt defteri girişleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] varsayımsal bir proje alt türü tarafından toplanan bir proje varsayar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje girişleri aşağıda listelenmiştir.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]
@="#2143"
"DefaultProjectExtension"="vbproj"
"PossibleProjectExtensions"="vbproj;vbp"
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]
@="#100"
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"
```

 **AddItemTemplates\TemplateDirs** alt tuşu, **Yeni Öğe Ekle** iletişim kutusunda kullanıma sunulan öğelerin yerleştirildiği dizin yolu olan kayıt defteri girişleri içerir.

 Ortam, **Projeler** kayıt defteri alt anahtarının altındaki **Tüm AddItemTemplates** verilerini otomatik olarak yükler. Bu veriler, temel proje uygulamaları için verilerin yanı sıra belirli proje alt türü türleri için verileri de içerebilir. Her proje alt türü bir proje türü **GUID**ile tanımlanır. Proje alt türü, proje alt türünün GUID değerini döndürmek için <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> uygulamada numaralandırmayı destekleyerek `VSHPROPID_ AddItemTemplatesGuid` belirli bir aromalı proje örneği için alternatif bir Öğe **Ekle** şablonları kümesinin kullanılması gerektiğini belirtebilir. Özellik `VSHPROPID_AddItemTemplatesGuid` belirtilmemişse, temel proje GUID kullanılır.

 **Proje** alt türü toplayıcı nesnesine <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> arabirimi uygulayarak Yeni Öğe Ekle iletişim kutusundaki öğeleri filtreleyebilirsiniz. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Örneğin, bir projeyi toplayarak bir veritabanı projesi uygulayan bir proje alt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] türü, filtreleme uygulayarak Yeni **Öğe Ekle** iletişim kutusundan belirli öğeleri filtreleyebilir ve `VSHPROPID_ AddItemTemplatesGuid` buna <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>karşılık, 'de destekleyerek veritabanı projesine özgü öğeler ekleyebilirsiniz. **Yeni Öğe Ekle** iletişim kutusuna filtreleme ve öğe ekleme hakkında daha fazla bilgi için bkz. [Add items to the Add New Item dialog box](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Genellikle projeleri genişletmek için kullanılan nesnelerin CATID'leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
