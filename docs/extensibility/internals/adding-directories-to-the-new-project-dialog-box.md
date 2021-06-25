---
title: Yeni Proje İletişim Kutusuna Dizin Ekleme | Microsoft Docs
description: Yeni proje türleri oluşturmak ve bunları şablon olarak kullanmak üzere görüntülemek için Visual Studio'da Yeni Proje iletişim kutusuna dizinler ekleme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44554c8bd7b758f1bf191d1a4bef9ba07941191d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901844"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Yeni Proje iletişim kutusuna dizin ekleme
Yeni proje türleri oluştururken, bunları şablon olarak kullanmak üzere görüntülemek için **Yeni** Proje iletişim kutusuna yeni bir dizin de kaydedebilirsiniz. Aşağıdaki kod örneğinde, düğüm olarak da bilinen yeni bir dizinin nasıl kayded silindiği açıklanır. Örnekte VSPackage tarafından CLSID_Package *şablonları* kaydedilir. Sonuç olarak, Yeni Proje iletişim **kutusunun sol** tarafında eklenen düğüm, kaynak tarafından belirlenen bir *adla Folder_Label_ResID* sunar. Bu kaynak VSPackage uydu DLL'lerinden yüklenir.

 Klasör **değeri,** Folder_Label_ResID düğümünün görüntü *Folder_Label_ResID* GUID değerini temsil eder. Örnekte GUID, Yeni Proje iletişim **kutusunun Proje** Türleri **bölmesindeki** Diğer Projeler **klasörünü temsil** eder. Diğer **Projeler değeri** yoksa etiket en üst düzeyde konumlandı.

 `TemplatesDir`değeri, proje şablonlarını içeren dizinin tam yolunu belirtir. Bu dosyalar kopyalanan *.vsz* dosyaları veya tipik şablon dosyaları olabilir.

 belirtirsanız, yerelleştirilmiş şablonları tutan alt dizinini ad alan `TemplatesLocalizedSubDir` bir `TemplatesDir` dizenin kaynak kimliği olmalıdır. Varsa, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir uydu DLL'den dize kaynağını yükleyemediklerinden, her uydu DLL farklı bir alt dizin adı içerebilir. değeri `SortPriority` bir sıralama önceliğini belirtir.

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
- [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Yeni Öğe Ekle iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
