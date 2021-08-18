---
title: yeni Project iletişim kutusuna dizin ekleme | Microsoft Docs
description: yeni proje türleri oluşturabilmek ve bunları şablon olarak kullanmak üzere görüntüleyebilmeniz için Visual Studio yeni Project iletişim kutusuna dizin eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 62d3cfaeca91595e13456b454400e79b50dc6017
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086928"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>yeni Project iletişim kutusuna dizin ekleme
yeni proje türleri oluşturduğunuzda, yeni **Project** iletişim kutusunda yeni bir dizin kaydedebilir ve bunları şablon olarak kullanmak üzere görüntüleyebilirsiniz. Aşağıdaki kod örneğinde, düğüm olarak da bilinen yeni bir dizinin nasıl kaydedileceği açıklanmaktadır. Örnekte, VSPackage, *CLSID_Package* tarafından kullanıma sunulan şablonlar kaydedilir. sonuç olarak, **yeni Project** iletişim kutusunun sol tarafında, eklenen düğüm, *Folder_Label_ResID* kaynağına göre belirlenen bir adla sunulur. Bu kaynak VSPackage uydu DLL 'sinden yüklenir.

 **Klasör** değeri, *Folder_Label_ResID* düğümünün görüntülendiği bir klasörün GUID 'sini temsil eder. örnekte guıd, **yeni Project** iletişim kutusunun **Project türler** bölmesindeki **diğer projeler** klasörünü temsil eder. **Diğer projeler** değeri yoksa, etiket en üst düzeyde konumlandırılır.

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
