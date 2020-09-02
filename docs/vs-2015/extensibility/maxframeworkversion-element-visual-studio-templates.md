---
title: MaxFrameworkVersion öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194323"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablonun gerektirdiği .NET Framework en yüksek sürümünü belirtir. Şablon, yeni **Proje Ekle iletişim** kutusunun **hedef Framework sürümü** kutusunda seçilen değere bağlı olarak **Yeni Proje Ekle** iletişim kutusunun **Şablonlar** bölümünde görüntülenip görüntülenmeyeceğini belirler.  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>Syntax  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** ya da **Yeni öğe Ekle** iletişim kutusunda nasıl görüntüleneceğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Metin, şablon tarafından izin verilen .NET Framework en yüksek sürüm numarası olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `MaxFrameworkVersion` isteğe bağlı bir öğedir. `TemplateData`. Vstemplate dosyasının bölümündeki öğesi, **Yeni Proje Ekle** iletişim kutusunun **Şablonlar** bölümü için bir filtre işlevi görür. `MaxFrameworkVersion` **Yeni Proje Ekle** Iletişim kutusunun **hedef Framework sürümü** kutusunda seçilen değere bağlı olarak yalnızca .NET Framework gereksinimleri öğe değerlerinden daha az olan şablonlar görüntülenecektir. `MaxFrameworkVersion`Öğe gerekli olmadığı sürece atlanmalıdır, bu nedenle, .NET Framework daha yeni sürümleriyle kullanıldığında şablonların görüntülenmesini istemeden neden olmaz.  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Bu örnekte, şablon için gereken .NET Framework en yüksek sürümü, tarafından temsil edilir `MaxFrameworkVersion` 3,5. Yukarıdaki şablon yalnızca **Yeni Proje Ekle** Iletişim kutusundaki **hedef Framework sürümü** kutusunda 3,0 veya 3,5 ' i seçtiğinizde görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
