---
title: BuildProjectOnload öğesi (Visual Studio şablonları) | Microsoft Docs
description: BuildProjectOnload öğesi hakkında bilgi edinin ve bunları, oluşturup bir çözüme eklerken yalnızca yeni projeleri nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e2a1f542e89851cb430f8d80934933351e9349e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882277"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>BuildProjectOnload öğesi (Visual Studio şablonları)
Oluştururken yalnızca yeni projeler oluşturur ve bunları bir çözüme ekler. Tüm çözüm derlenmez.

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
|`TemplateData`|Şablonu kategorilere ayırır ve hem **Yeni proje** hem de **Yeni öğe Ekle** iletişim kutularında nasıl göründüğünü tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin ya da `true` `false` şablondan oluşturulduğunda yalnızca yeni proje oluşturulup oluşturulmayacağını göstermek için olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `BuildProjectOnLoad` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir Visual C# şablonu için meta verileri gösterir.

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
