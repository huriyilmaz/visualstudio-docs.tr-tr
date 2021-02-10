---
title: Yeni öğe Ekle Iletişim kutusuna dizin ekleme | Microsoft Docs
description: Dizinleri kaydettirmek için bir kayıt defteri betiği kullanarak Visual Studio 'da yeni öğe Ekle iletişim kutusuna dizin eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 68a16d544147ca95512f8b6064d2b9712b26ed64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969028"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Yeni öğe Ekle iletişim kutusuna dizin ekleme
Aşağıdaki kod örneğinde **Yeni öğe Ekle** iletişim kutusu için yeni bir dizin kümesinin nasıl kaydedileceği gösterilmektedir. **Yeni öğe Ekle** iletişim kutusu için dizinler her proje için farklıdır. Bu nedenle, dizinler **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects** bulunan **Projeler** alt anahtarı altında kaydedilir.

## <a name="registry-script"></a>Kayıt defteri betiği

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 `%Template_Path%`Değer, proje şablonlarını içeren dizinin tam yolunu belirtir. Bu şablonlar, klonlanacak *. vsz* dosyaları ya da Prototipik şablon dosyaları olabilir.

 `SortPriority`Değer bir sıralama önceliği belirtir.

## <a name="add-items-to-an-existing-project"></a>Mevcut bir projeye öğe ekleme
 Ayrıca, varolan bir projeye öğe ekleyebilirsiniz. Örneğin, bir proje için [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *\<root> \Program Files\Microsoft Visual Studio\vc # \Csharpprojectıtems\localprojectıtems* klasörüne öğe ekleyebilirsiniz. Bu durumda, `%GUID_Project%` bir C# projesinin GUID 'sidir ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Ayrıca, varolan bir projeyi bir proje alt türünü programlamaya göre genişletebilirsiniz. Proje alt türü ile, yeni bir proje türü yazmadan bir projeyi genişletebilirsiniz. Proje alt türleri hakkında daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)
- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Yeni proje iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
