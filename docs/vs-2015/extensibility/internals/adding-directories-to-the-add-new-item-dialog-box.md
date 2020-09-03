---
title: Yeni öğe Ekle Iletişim kutusuna dizin ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203924"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekleme İletişim Kutusuna Dizin Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki kod örneğinde **Yeni öğe Ekle** iletişim kutusu için yeni bir dizin kümesinin nasıl kaydedileceği gösterilmektedir. **Yeni öğe Ekle** iletişim kutusu için dizinler her proje için farklıdır. Bu nedenle, dizinler altında bulunan projeler alt anahtarı altında kaydedilir \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Kayıt defteri betiği  
  
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
  
 Template_Path değeri, proje şablonlarını içeren dizinin tam yolunu belirtir. Bu şablonlar, klonlanacak. vsz dosyaları ya da Prototipik şablon dosyaları olabilir.  
  
 SortPriority değeri bir sıralama önceliği belirtir.  
  
## <a name="adding-items-to-an-existing-project"></a>Mevcut bir projeye öğe ekleme  
 Ayrıca, varolan bir projeye öğe ekleyebilirsiniz. Örneğin, bir proje için [!INCLUDE[csprcs](../../includes/csprcs-md.md)] \<root> \Program Files\Microsoft Visual Studio \VC # \Csharpprojectıtems\localprojectıtems klasörüne öğe ekleyebilirsiniz. Bu durumda, `%GUID_Project%` bir C# projesinin GUID 'sidir ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Ayrıca, varolan bir projeyi bir proje alt türünü programlamaya göre genişletebilirsiniz. Proje alt türü ile, yeni bir proje türü yazmadan bir projeyi genişletebilirsiniz. Proje alt türleri hakkında daha fazla bilgi için bkz. [Proje alt türleri](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Yeni öğe Ekle Iletişim kutularına öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Yeni Proje İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
