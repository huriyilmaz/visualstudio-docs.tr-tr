---
title: ProjectType Element (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701803"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType öğesi (Visual Studio şablonları)
Proje şablonu, **Yeni Proje'de** belirtilen grubun altında görünecek şekilde kategorilere ayırıyor veya **Yeni Öğe Ekle** iletişim kutusu.

> [!WARNING]
> Visual Studio 2012'den itibaren C++ için proje şablonları desteklenir. Visual Studio 2010 ve önceki sürümlerde C++ için desteklenmez.

 \<VSTemplate \<> ŞablonVeri> \<ProjectType>

## <a name="syntax"></a>Sözdizimi

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu değer, şablonun oluşturacağı proje türünü belirtir ve aşağıdaki değerlerden birini içermelidir:

- `CSharp`: Şablonun bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proje veya öğe oluşturduğunu belirtir.

- `VisualBasic`: Şablonun bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] proje veya öğe oluşturduğunu belirtir.

- `Web`: Şablonun bir Web projesi veya öğesi oluşturduğunu belirtir. `ProjectType` Öğe bu değeri içeriyorsa, [ProjectSubType Öğesi'nde (Visual Studio Templates)](../extensibility/projectsubtype-element-visual-studio-templates.md)proje veya öğenin dili tanımlanır.

## <a name="remarks"></a>Açıklamalar
 `ProjectType`gerekli bir alt `TemplateData`öğedir.

 Öğenin `ProjectType` değeri, şablonun **Yeni Proje** veya Yeni Öğe **Ekle** iletişim kutusunda nerede bulunduğunu belirtir. Örneğin, **Yeni Proje** `ProjectType` iletişim `CSharp` kutusunda Görsel **C#** düğümünün altında görünen değeri olan bir şablon.

 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi kullanılarak bir şablon alt türü belirtilebilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] uygulama için proje şablonu için meta verileri gösterir.

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

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectSubType öğesi (Visual Studio şablonları)](../extensibility/projectsubtype-element-visual-studio-templates.md)
