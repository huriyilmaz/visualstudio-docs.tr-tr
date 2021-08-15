---
title: BuildProjectOnload Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: BuildProjectOnload öğesini ve siz bunları bir çözüme eklerken yalnızca yeni projeleri nasıl derlemesi olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9ca65dee11938f4152a30dedd25a3b4f3e566dd3b88e9e54da46579e30fa3243
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308369"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>BuildProjectOnload öğesi (Visual Studio şablonları)
Yalnızca siz yeni projeler oluşturun ve bunları bir çözüme ekleyin. Çözümün tamamı yerleşik değildir.

Öğe hiyerarşisi:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Syntax

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`TemplateData`|Şablonu kategorilere ayırarak hem Yeni Şablon'da hem de **Project** Ekle iletişim **kutularında nasıl görüntülendiğinden** emin olur.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, `true` şablondan `false` oluşturulduğunda yalnızca yeni projenin oluşturulıp oluşturulmayacaklarını belirtmek için veya olması gerekir.

## <a name="remarks"></a>Açıklamalar
 `BuildProjectOnLoad` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, Visual C# şablonunun meta verilerini göstermektedir.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

## <a name="see-also"></a>Ayrıca bkz.

- [BuildOnLoad özniteliği ve öğesi](buildonload-visual-studio-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
