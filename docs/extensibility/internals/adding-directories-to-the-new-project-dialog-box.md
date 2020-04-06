---
title: Yeni Proje İletişim Kutusuna Dizin Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710240"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Yeni Proje iletişim kutusuna dizin ekleme
Yeni proje türleri oluşturduğunuzda, **yeni** proje iletişim kutusuna yeni bir dizin kaydedebilirsiniz. Aşağıdaki kod örneği, düğüm olarak da bilinen yeni bir dizinin nasıl kaydedilenin açıklanmaktadır. Örnekte, *CLSID_Package*VSPackage tarafından ortaya çıkarılan şablonlar kaydedilir. Sonuç olarak, **Yeni Proje** iletişim kutusunun sol *tarafında, Folder_Label_ResID* kaynağı tarafından belirlenen bir adla eklenen düğüm sunar. Bu kaynak VSPackage uydu DLL yüklenir.

 **Klasör** değeri, *Folder_Label_ResID* düğümünün görüntülendiği bir klasörün GUID'ini temsil eder. Örnekte GUID, **Yeni** **Proje** iletişim kutusunun Proje **Türleri** bölmesinde Diğer Projeler klasörünü temsil eder. Diğer **Projeler** değeri yoksa, etiket en üst düzeyde konumlandırılır.

 Değer, `TemplatesDir` proje şablonlarını içeren dizinin tam yolunu belirtir. Bu dosyalar *klonlanacak .vsz* dosyaları veya tipik şablon dosyaları olabilir.

 Belirtirseniz, `TemplatesLocalizedSubDir`yerelleştirilmiş şablonları tutan alt dizinini adlandıran `TemplatesDir` bir dizenin kaynak kimliği olmalıdır. Dize kaynağını bir uydu DLL'den yükler, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çünkü varsa, her uydu DLL farklı bir alt dizin adı içerebilir. Değer `SortPriority` bir sıralama önceliği belirtir.

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
- [Proje ve madde şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Yeni Öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
