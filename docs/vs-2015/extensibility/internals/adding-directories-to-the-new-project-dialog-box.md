---
title: Yeni proje Iletişim kutusuna dizin ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203869"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Yeni Proje İletişim Kutusuna Dizin Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni proje türleri oluşturduğunuzda, yeni **Proje** iletişim kutusunda şablon olarak kullanmak üzere yeni bir dizin de kaydedebilirsiniz. Aşağıdaki kod örneğinde, düğüm olarak da bilinen yeni bir dizinin nasıl kaydedileceği açıklanmaktadır. Örnekte, VSPackage CLSID_Package tarafından sunulan şablonlar kaydedilir. Sonuç olarak, **Yeni proje** iletişim kutusunun sol tarafı, eklenen düğümü Folder_Label_ResID kaynak tarafından belirlenen bir adla birlikte sunar. Bu kaynak VSPackage uydu DLL 'sinden yüklenir.  
  
 **Klasör** değeri, Folder_Label_ResID düğümünün görüntülendiği bir klasörün GUID 'sini temsil eder. Örnekte GUID, **Yeni proje** Iletişim kutusunun **Proje türleri** bölmesinde **diğer projeler** klasörünü temsil eder. **Diğer projeler** değeri yoksa, etiket en üst düzeyde konumlandırılır.  
  
 Templates dır değeri, proje şablonlarını içeren dizinin tam yolunu belirtir. Bu dosyalar, klonlanacak. vsz dosyası ya da tipik şablon dosyaları olabilir.  
  
 Templates Localizedsubdir belirtirseniz, yerelleştirilmiş şablonları tutan Templates dizini 'nin alt dizinini isimeden bir dizenin kaynak KIMLIĞI olmalıdır. , [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Varsa, bir uydu dll 'sinden dize kaynağını yükler, her uydu dll farklı bir alt dizin adı içerebilir. SortPriority değeri bir sıralama önceliği belirtir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Yeni öğe Ekle Iletişim kutularına öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Yeni Öğe Ekleme İletişim Kutusuna Dizin Ekleme](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
