---
title: TemplateId öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a52b360994c53eef69ceafa45828ec1020be16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186417"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) öğesi tarafından bir öğe şablonları grubuna kategorize edilmiş bir öğe şablonu için tanımlayıcıyı belirtir.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateID>  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateID> ... </TemplateID>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Öğe `string` tarafından bir öğe şablonları grubuna kategorize edilmiş bir öğe şablonu için tanımlayıcıyı temsil eden bir `TemplateGroupID` .  
  
## <a name="remarks"></a>Açıklamalar  
 `TemplateID` isteğe bağlı bir öğedir.  
  
 Bir. vstemplate dosyası öğesi atladığında `TemplateID` , [Name](../extensibility/name-element-visual-studio-templates.md) öğesi şablon için tanımlayıcı olarak kullanılır.  
  
 Öğe değeri, `TemplateID` Proje sistem kaydı (HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\11.0\Projects) ile birlikte, \\ **Yeni öğe Ekle** iletişim kutusunda görünen şablonları filtrelemek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
