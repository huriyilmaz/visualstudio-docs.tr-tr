---
title: BuildProjectOnload Element (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72d1981aab67762b3ee4aa8d62e0643f4c2a8963
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739957"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>BuildProjectOnload öğesi (Visual Studio şablonları)
Yalnızca oluşturduğunuz yeni projeler oluşturur ve bunları bir çözüme ekler. Tüm çözüm oluşturulmadı.

Öğe hiyerarşisi:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Sözdizimi

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
|`TemplateData`|Şablonu kategorilere ayırAr ve hem **Yeni Proje'de** hem de **Yeni Öğe Ekle** iletişim kutularında nasıl görününcürün denli tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, şablondan `true` `false` oluşturulduğunda yalnızca yeni proje oluşturulup oluşturulmayacağını belirtmek için olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `BuildProjectOnLoad`isteğe bağlı bir unsurdur. Varsayılan değer: `false`.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, Visual C# şablonu için meta verileri göstermektedir.

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
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
