---
title: Yeni öğe Ekle Iletişim kutusuna katkıda bulunma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197015"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekleme İletişim Kutusuna Katkıda Bulunma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje alt türü, kayıt defteri alt anahtarı altına **öğe Ekle** şablonları kaydederek **Yeni öğe Ekle** iletişim kutusu için yeni bir öğe dizini sağlayabilir `Projects` .  
  
## <a name="registering-add-new-item-templates"></a>Yeni öğe ekleme şablonları kaydediliyor  
 Bu bölüm, kayıt defterindeki **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0\Projects** altında bulunur. Aşağıdaki kayıt defteri girişlerinde, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kuramsal bir proje alt türü tarafından toplanan bir proje varsayılmaktadır. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Projenin girişleri aşağıda listelenmiştir.  
  
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
  
 `AddItemTemplates\TemplateDirs`Alt anahtar, **Yeni öğe Ekle** iletişim kutusunda kullanılabilir öğelerin yerleştirildiği dizinin yolunu içeren kayıt defteri girdilerini içerir.  
  
 Ortam, `AddItemTemplates` `Projects` kayıt defteri alt anahtarı altındaki tüm verileri otomatik olarak yükler. Bu, temel proje uygulamalarının verilerini ve ayrıca belirli proje alt türü türleri için verileri içerebilir. Her proje alt türü bir proje türü tarafından tanımlanır `GUID` . Proje alt türü, `Add Item` `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Proje alt türünün GUID değerini döndürmek için uygulamadaki sabit listesini destekleyerek, belirli bir flavored proje örneği için başka bir şablon kümesinin kullanılması gerektiğini belirtebilir. `VSHPROPID_AddItemTemplatesGuid`Özellik belirtilmezse, temel proje GUID 'si kullanılır.  
  
 Proje alt türü toplayıcısı nesnesi üzerinde arabirimini uygulayarak **Yeni öğe Ekle** iletişim kutusundaki öğeleri filtreleyebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> . Örneğin, bir projeyi toplayarak bir veritabanı projesi uygulayan bir proje alt türü [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] filtre uygulayarak **Yeni öğe Ekle** iletişim kutusundan belirli öğeleri filtreleyebilir ve sırasıyla ' de destekleyerek veritabanı projesine özgü öğeler ekleyebilir `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . **Yeni öğe Ekle** iletişim kutusuna öğe filtreleme ve ekleme hakkında daha fazla bilgi için, bkz. [Yeni öğe Ekle Iletişim kutularına öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
