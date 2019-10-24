---
title: Wizardexgeri öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfd46573f70b31559f9d6c4749c142d763537764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748945"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension Öğesi (Visual Studio Şablonları)
Şablon Sihirbazı ' nı özelleştirmek için kayıt öğelerini içerir.

 \<VSTemplate >... \<WizardExtension >

## <a name="syntax"></a>Sözdizimi

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
|[Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Gerekli öğe.<br /><br /> Genel derleme önbelleğinde görüntülenen bir derlemenin adını veya tanımlayıcı adını belirtir. Bir `WizardExtension` öğesinde en az bir `Assembly` öğesi olmalıdır.|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Gerekli öğe.<br /><br /> @No__t_0 arabirimini uygulayan sınıfın tam adı. Bir `WizardExtension` öğesinde en az bir `FullClassName` öğesi olmalıdır.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Proje şablonu, öğe şablonu veya başlangıç seti için tüm meta verileri içerir.|

## <a name="remarks"></a>Açıklamalar
 `WizardExtension`, `VSTemplate` isteğe bağlı bir alt öğesidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] bir Windows uygulaması için Standart proje şablonu meta verilerini gösterir.

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