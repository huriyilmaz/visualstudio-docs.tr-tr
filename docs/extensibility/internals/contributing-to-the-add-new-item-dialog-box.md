---
title: Yeni öğe Ekle Iletişim kutusuna katkıda bulunma | Microsoft Docs
description: proje kayıt defteri alt anahtarı altında öğe ekle şablonları ' na kaydolarak Visual Studio yeni öğe ekle iletişim kutusuna nasıl katkıda bulunabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc3f986f47d81c0425568fbd9fab1217b257687fe7b70037a50e405d3861c0b1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305821"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Yeni öğe Ekle iletişim kutusuna katkıda bulunun
Proje alt türü **, proje kayıt defteri alt** anahtarının altına **öğe Ekle** şablonları kaydederek **Yeni öğe Ekle** iletişim kutusu için yeni bir öğe dizini sağlayabilir.

## <a name="register-add-new-item-templates"></a>Yeni öğe ekleme şablonları Kaydet
 Bu bölüm, kayıt defterindeki **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** altında bulunur. Aşağıdaki kayıt defteri girişlerinde, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kuramsal bir proje alt türü tarafından toplanan bir proje varsayılmaktadır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projenin girişleri aşağıda listelenmiştir.

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

 **AddItemTemplates\TemplateDirs** alt anahtarı, **Yeni öğe Ekle** iletişim kutusunda kullanılabilir öğelerin yerleştirildiği dizinin yolunu içeren kayıt defteri girdilerini içerir.

 Ortam, tüm **Additemtemplate** verilerini **Projeler** kayıt defteri alt anahtarı altında otomatik olarak yükler. Bu veriler, temel proje uygulamalarının verilerini ve ayrıca belirli proje alt türü türleri için verileri içerebilir. Her proje alt türü bir proje türü **GUID** ile tanımlanır. Proje alt türü,  `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Proje alt türünün GUID değerini döndürmek için uygulamadaki sabit listesini destekleyerek, belirli bir flavored proje örneği için farklı bir Add Item şablonu kullanılması gerektiğini belirtebilir. `VSHPROPID_AddItemTemplatesGuid`Özelliği belirtilmemişse, temel proje GUID 'si kullanılır.

 Proje alt türü toplayıcısı nesnesi üzerinde arabirimini uygulayarak **Yeni öğe Ekle** iletişim kutusundaki öğeleri filtreleyebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> . Örneğin, bir projeyi toplayarak bir veritabanı projesi uygulayan bir proje alt türü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] filtre uygulayarak **Yeni öğe Ekle** iletişim kutusundan belirli öğeleri filtreleyebilir ve sırasıyla ' de destekleyerek veritabanına projeye özgü öğeler ekleyebilirler `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . **Yeni öğe Ekle** iletişim kutusuna öğe filtreleme ve ekleme hakkında daha fazla bilgi Için, [Yeni öğe Ekle Iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Projeleri genişletmek için genellikle kullanılan nesneler için CATIDs](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
