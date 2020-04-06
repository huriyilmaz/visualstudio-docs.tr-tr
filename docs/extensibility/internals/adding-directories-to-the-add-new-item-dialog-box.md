---
title: Yeni Öğe Ekle İletişim Kutusu'na Dizin Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710260"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusuna dizin ekleme
Aşağıdaki kod örneği, **Yeni Öğe Ekle** iletişim kutusu için yeni bir dizin kümesinin nasıl kaydedilebildiğini gösterir. Yeni Öğe **Ekle** iletişim kutusunun dizinleri her proje için farklıdır. Bu nedenle, dizinler **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**bulunan **Projeler** alt anahtarı altında kaydedilir.

## <a name="registry-script"></a>Kayıt defteri komut dosyası

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

 Değer, `%Template_Path%` proje şablonlarını içeren dizinin tam yolunu belirtir. Bu şablonlar klonlanacak *.vsz* dosyaları veya prototipşablon dosyaları olabilir.

 Değer `SortPriority` bir sıralama önceliği belirtir.

## <a name="add-items-to-an-existing-project"></a>Varolan bir projeye öğe ekleme
 Varolan bir projeye öğe de ekleyebilirsiniz. Örneğin, bir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje için kök * \<>\Program Dosyaları\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems* klasörüne öğeler ekleyebilirsiniz. Bu durumda, `%GUID_Project%` Bir C# projesinin GUID'i ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Ayrıca, varolan bir proje alt türünü programlayarak varolan bir projeyi genişletebilirsiniz. Proje alt türüyle, yeni bir proje türü yazmadan projeyi genişletebilirsiniz. Proje alt türleri hakkında daha fazla bilgi için [Bkz. Proje alt türleri.](../../extensibility/internals/project-subtypes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve madde şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Yeni Proje iletişim kutusuna dizin ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
