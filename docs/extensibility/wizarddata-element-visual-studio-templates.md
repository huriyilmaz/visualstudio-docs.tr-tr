---
title: wizarddata öğesi (Visual Studio şablonları) | Microsoft Docs
description: WizardData öğesi ve nasıl özel bir XML belirtir hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d51d9827c5edcbcf522eb206add4769a8583f34ac7aa72732b472523e197bb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400445"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData Öğesi (Visual Studio Şablonları)

Özel XML belirtir

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Syntax

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Proje şablonu, öğe şablonu veya başlangıç seti için tüm meta verileri içerir.|

## <a name="text-value"></a>Metin Değeri

Metin değeri isteğe bağlıdır.

Bu metin, [Wizardexgeri](../extensibility/wizardextension-element-visual-studio-templates.md) öğesinde belirtilen özel sihirbaz uzantısına GEÇIRILECEK özel XML 'i belirtir.

## <a name="remarks"></a>Açıklamalar

Bu öğede herhangi bir XML belirtilebilir. XML özel sihirbaz uzantısına bir parametre olarak geçirilir ve bu da uzantının bu öğenin içeriğini kullanmasına izin verir. Bu verilerde doğrulama yapılmadı.

**WizardData** öğesinin içeriği, yöntemindeki parametrelerin dize Sözlüğü içindeki bir parametre olarak geçirilir, değiştirilmez `IWizard.RunStarted` . Sözlük anahtarı olarak adlandırılır `$wizarddata$` .

## <a name="example"></a>Örnek

aşağıdaki örnek, bir C# Windows uygulaması için standart proje şablonu meta verilerini gösterir.

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
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
- [WizardExtension Öğesi (Visual Studio Şablonları)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
