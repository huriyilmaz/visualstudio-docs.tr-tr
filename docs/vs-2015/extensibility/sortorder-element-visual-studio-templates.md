---
title: SortOrder öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 825ec785a83cae0aaa8a31ae1375e956228b634e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205521"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda göründüğü gibi, şablonu düzenlemek için kullanılan bir değeri belirtir.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SortOrder>  
  
## <a name="syntax"></a>Syntax  
  
```  
<SortOrder> ... </SortOrder>  
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
 Bir metin değeri gereklidir.  
  
 `integer`Sıralama düzeni değerini temsil eden bir.  
  
## <a name="remarks"></a>Açıklamalar  
 `SortOrder` isteğe bağlı bir öğedir. Varsayılan değer 100 ' dir ve tüm değerler 10 ' un katları olmalıdır.  
  
 `SortOrder`Öğe, Kullanıcı tarafından oluşturulan şablonlar için yok sayılır. Kullanıcı tarafından oluşturulan tüm şablonlar alfabetik olarak sıralanır.  
  
 Düşük sıralama düzeni değerleri olan şablonlar, yüksek sıralama düzeni değerlerine sahip şablonlardan önce **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda görünür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, standart sınıf şablonu için meta verileri gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Bu örnekte, `SortOrder` öğesi nispeten yüksektir. Diğer öğe şablonları, daha [!INCLUDE[csprcs](../includes/csprcs-md.md)] düşük bir değere sahip olacak `SortOrder` `290` ve **Yeni öğe** iletişim kutusunda Bu şablondan önce görünecektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
