---
title: ProjectType öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b01dd370fe5e3d7a5207363c5ab7ec4f2a0254c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783058"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje şablonunu **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda belirtilen grup altında görünecek şekilde kategorilere ayırır.  
  
> [!WARNING]
> Proje şablonları, Visual Studio 2012 ' den itibaren C++ için desteklenir. Visual Studio 2010 ve önceki sürümlerde C++ için desteklenmez.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectType>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Bu değer, şablonun oluşturulacağı projenin türünü belirtir ve aşağıdaki değerlerden birini içermelidir:  
  
- `CSharp`: Şablonun bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] Proje veya öğe oluşturduğunu belirtir.  
  
- `VisualBasic`: Şablonun bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Proje veya öğe oluşturduğunu belirtir.  
  
- `Web`: Şablonun bir Web projesi veya öğe oluşturduğunu belirtir. `ProjectType`Öğesi bu değeri içeriyorsa, projenin veya öğenin dili [ProjectSubType öğesinde tanımlanır (Visual Studio şablonları)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectType` , öğesinin gerekli bir alt öğesidir `TemplateData` .  
  
 Öğesinin değeri, `ProjectType` şablonun **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nerede olduğunu belirtir. Örneğin, değeri bulunan bir şablon, `ProjectType` `CSharp` **Yeni proje** iletişim kutusunda **Visual C#** düğümünün altında görünür.  
  
 Bir şablon alt türü, [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi kullanılarak belirtilebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [ProjectSubType Öğesi (Visual Studio Şablonları)](../extensibility/projectsubtype-element-visual-studio-templates.md)
