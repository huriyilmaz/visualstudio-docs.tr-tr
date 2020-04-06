---
title: Montaj Öğesi (Visual Studio Template Wizard Uzantı) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43f5adb8abc17f0509fb58263f307e5051af85dc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740067"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Montaj öğesi (Visual Studio şablon sihirbazı uzantısı)
`IWizard` Arabirimi uygulayan derlemenin adını veya güçlü adını belirtir.

 \<VSTemplate \<> WizardExtension> \<Montaj>

## <a name="syntax"></a>Sözdizimi

```
<Assembly>AssemblyName</Assembly>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Şablon sihirbazını özelleştirmek için kayıt öğelerini içerir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu metin, arabirimi uygulayan derlemeyi `IWizard` belirtir. Bu derleme adı tam derleme adı olarak belirtilmelidir. Örneğin, `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.

## <a name="remarks"></a>Açıklamalar
 `Assembly`gerekli bir alt `WizardExtension`öğedir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows uygulaması için standart proje şablonu için meta veriler gösterilmektedir.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl kullanılır: Proje şablonları ile sihirbazları kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
