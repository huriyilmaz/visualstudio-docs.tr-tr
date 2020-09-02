---
title: Promptforsaveonoluşturma öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a523190a9e5c143667355c222e0fbe9441cc231a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675367"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>PromptForSaveOnCreation Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje oluştururken, kullanıcıdan **Yeni proje** iletişim kutusu aracılığıyla bir proje kaydetme konumu istenip istenmediğini belirtir. Bu öğe olarak ayarlandıysa `true` , kullanıcıdan bir kayıt konumu istenir; varsa `false` , bunlar istenmez. (Yani geçici bir proje oluşturulur.)  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<PromptForSaveOnCreation>  
  
## <a name="syntax"></a>Syntax  
  
```  
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>  
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
  
 Metin ya da ya da `true` `false` `true` Yeni bir proje oluştururken kullanıcıdan kaydetme konumu istenmeyeceğini belirten bir olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `PromptForSaveOnCreation` isteğe bağlı bir öğedir. Varsayılan değer: `false`.  
  
 Geçici projeler, bu projenin içeriğini diskte kaydetmeden oluşturabileceğiniz ve değiştirebileceğiniz projelerdir. Daha fazla bilgi için bkz. [nib geçici projeleri](https://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `PromptForSaveOnCreation` `false` , projenin geçici bir proje olarak oluşturulmasını izin vermeyi belirten değerine eşit değer olarak ayarlar.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
