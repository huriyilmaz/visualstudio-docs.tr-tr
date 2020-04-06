---
title: LocationField Element (Visual Studio Proje Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702880"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField öğesi (Visual Studio proje şablonları)
**Yeni Proje** iletişim kutusundaki **Konum** metin kutusunun proje şablonu için etkin, devre dışı veya gizli olup olmadığını belirtir.

 \<VSTemplate \<> ŞablonVeri> \<LocationAlan>

## <a name="syntax"></a>Sözdizimi

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırıyor ve Yeni **Proje'de**nasıl görüntülenebildiğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Geçerli metin değerleri şunlardır:

- `Enabled`, **Yeni Proje** iletişim kutusunun **Konum** kutusunun etkin olduğunu belirtir.

- `Disabled`, **Yeni Proje** iletişim kutusunun **Konum** kutusunun devre dışı bırakıldığını belirtir.

- `Hidden`, **Yeni Proje** iletişim kutusunun **Konum** kutusunun gizli olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar
 Varsayılan değer: `Enabled`.

 **Yeni Proje** iletişim kutusundaki **Konum** metin kutusu, kullanıcıların yeni projelerin kaydedildiği varsayılan dizini değiştirmesini sağlar.

 `Location` Öğede belirtilen değer yalnızca temel proje sistemi destekliyorsa iletişim kutusu tarafından onurlanır.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, şablonun [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] meta verileri gösteriş verilmiştir.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
