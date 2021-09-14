---
title: WizardExtension Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: WizardExtension öğesi ve şablon sihirbazını özelleştirmek için kayıt öğelerini nasıl içerdiği hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c32f9f2050e04741a2612de30e2718f45c0603de
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724947"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension Öğesi (Visual Studio Şablonları)
Şablon sihirbazını özelleştirmek için kayıt öğelerini içerir.

 \<VSTemplate> ... \<WizardExtension>

## <a name="syntax"></a>Syntax

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Bütünleştirilmiş Kod](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Gerekli öğe.<br /><br /> Genel derleme önbelleğinde görünen derlemenin adını veya güçlü adını belirtir. Bir öğede en az `Assembly` bir öğe `WizardExtension` olması gerekir.|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Gerekli öğe.<br /><br /> Arabirimi uygulayan sınıfın tam `IWizard` adı. Bir öğede en az `FullClassName` bir öğe `WizardExtension` olması gerekir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Proje şablonu, öğe şablonu veya başlangıç seti için tüm meta verileri içerir.|

## <a name="remarks"></a>Açıklamalar
 `WizardExtension` isteğe bağlı bir alt `VSTemplate` öğesidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için standart proje şablonunun meta [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verilerini Windows göstermektedir.

```
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
