---
title: TemplateContent Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699227"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent Öğesi (Visual Studio Şablonları)

Şablonun içeriğini belirtir.

Öğe hiyerarşisi:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Sözdizimi

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Şablondan bir proje oluşturulduğunda çözümün oluşturulup oluşturulmayacağını belirtir.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Birden fazla projeli şablonların içeriğini ve düzenini belirtir.|
|[Project](../extensibility/project-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklenecek dosyaları veya dizinleri belirtir.|
|[Başvurular](../extensibility/references-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Madde şablonu için gereken derleme başvurularını belirtir.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablonda bulunan bir dosyayı belirtir.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel parametreleri belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Proje şablonu, öğe şablonu veya başlangıç kiti için tüm meta verileri içerir.|

## <a name="remarks"></a>Açıklamalar
 `TemplateContent`gerekli bir unsurdur.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] uygulama için proje şablonu için meta verileri gösterir.

```xml
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
            <ProjectItem>Form1.cs</ProjectItem>
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

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
