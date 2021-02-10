---
title: Yeni proje Iletişim kutusuna dizin ekleme | Microsoft Docs
description: Yeni proje türleri oluşturabilmeniz ve bunları şablon olarak kullanmak üzere görüntüleyebilmeniz için Visual Studio 'daki yeni proje iletişim kutusuna dizin eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d65b7e4adc6d235bcb925efae1cef20d0aa2c9c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969041"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Yeni proje iletişim kutusuna dizin ekleme
Yeni proje türleri oluşturduğunuzda, yeni **Proje** iletişim kutusunda şablon olarak kullanmak üzere yeni bir dizin de kaydedebilirsiniz. Aşağıdaki kod örneğinde, düğüm olarak da bilinen yeni bir dizinin nasıl kaydedileceği açıklanmaktadır. Örnekte, VSPackage, *CLSID_Package* tarafından kullanıma sunulan şablonlar kaydedilir. Sonuç olarak, **Yeni proje** iletişim kutusunun sol tarafı, eklenen düğümü *Folder_Label_ResID* kaynak tarafından belirlenen bir adla birlikte sunar. Bu kaynak VSPackage uydu DLL 'sinden yüklenir.

 **Klasör** değeri, *Folder_Label_ResID* düğümünün görüntülendiği bir klasörün GUID 'sini temsil eder. Örnekte GUID, **Yeni proje** Iletişim kutusunun **Proje türleri** bölmesinde **diğer projeler** klasörünü temsil eder. **Diğer projeler** değeri yoksa, etiket en üst düzeyde konumlandırılır.

 `TemplatesDir`Değer, proje şablonlarını içeren dizinin tam yolunu belirtir. Bu dosyalar, klonlanacak *. vsz* dosyası ya da tipik şablon dosyaları olabilir.

 Belirtirseniz `TemplatesLocalizedSubDir` , `TemplatesDir` yerelleştirilmiş şablonları tutan öğesinin alt dizinini isimeden bir DIZENIN kaynak kimliği olmalıdır. , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Varsa, bir uydu dll 'sinden dize kaynağını yükler, her uydu dll farklı bir alt dizin adı içerebilir. `SortPriority`Değer bir sıralama önceliği belirtir.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)
- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Yeni öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
