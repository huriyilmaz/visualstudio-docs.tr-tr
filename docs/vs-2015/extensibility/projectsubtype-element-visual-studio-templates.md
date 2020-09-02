---
title: ProjectSubType öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d07a62027b494242d3c25aba00fbd5f4d75df78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193915"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablonu, öğesinde belirtilen değerin bir alt kategorisine sınıflandırır `ProjectType` .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectSubType>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
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
  
 Bu değer, şablonun alt kategorisini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectSubType` , öğesinin isteğe bağlı bir alt öğesidir `TemplateData` .  
  
 `ProjectSubType`Öğesi [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) öğesine bir alt kategori sağlar. Bu değer şunlar olabilir:  
  
- `SmartDevice-NETCFv1`: Şablonun 1,0 sürümünü hedeflediğini belirtir [!INCLUDE[Compact](../includes/compact-md.md)] .  
  
- `SmartDevice-NETCFv2`: Tempalate 'nın 2,0 sürümünü hedeflediğini belirtir [!INCLUDE[Compact](../includes/compact-md.md)] .  
  
  Bir şablon `ProjectType` değeri olan bir öğesi içeriyorsa `Web` , `ProjectSubType` öğesi şablonun programlama dilini belirtir. Bu öğe aşağıdaki değerlere sahip olabilir:  
  
- `CSharp`: Şablonun bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] Web projesi veya öğe oluşturduğunu belirtir.  
  
- `VisualBasic`: Şablonun bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Web projesi veya öğe oluşturduğunu belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [!INCLUDE[csprcs](../includes/csprcs-md.md)] 2,0 sürümünü hedefleyen bir cihaz uygulaması için bir proje şablonu meta verilerini gösterir [!INCLUDE[Compact](../includes/compact-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [ProjectType Öğesi (Visual Studio Şablonları)](../extensibility/projecttype-element-visual-studio-templates.md)
