---
title: Folder öğesi (Visual Studio proje şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35448f4324213739cb2dc14a95598ac9a3d4432f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204364"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder Öğesi (Visual Studio Proje Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projeye eklenecek klasörü belirtir.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
 \<Folder>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli öznitelik.<br /><br /> Proje klasörünün adı.|  
|`TargetFolderName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda klasöre verilecek adı belirtir. Bu öznitelik, bir klasör adı oluşturmak veya bir klasörü doğrudan. zip dosyasında kullanılamayan uluslararası bir dizeyle adlandırmak üzere parametre değişimini kullanmak için yararlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Folder`|Projeye eklenecek klasörü belirtir. `Folder` öğeler, alt `Folder` öğeleri içerebilir.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Projeye eklenecek bir dosya belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)öğesinin isteğe bağlı alt öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Folder` , öğesinin isteğe bağlı bir alt öğesidir `Project` .  
  
 Bir şablondaki klasörler halinde proje öğelerini düzenlemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz:  
  
- Klasörleri Template. zip dosyasına dahil edin ve öğe içinde dosya yolunu belirterek. vstemplate dosyasındaki projeye ekleyin ( `ProjectItem` hiçbir öğesi olmadan) `Folder` . Önerilen yöntem budur. Örneğin:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
- Klasörleri Template. zip dosyasına dahil edin ve. vstemplate dosyasındaki öğeleri öğeleriyle birlikte bu klasöre ekleyin `Folder` . Örneğin:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
- Şablon. zip dosyasına klasörler eklemeyin, ancak öğesinin özniteliğini kullanarak klasörler ekleyin `TargetFileName` `ProjectItem` . Örneğin:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir Windows uygulaması için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [ProjectItem Öğesi (Visual Studio Öğe Şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
