---
title: CreateInPlace öğesi (Visual Studio Şablonları)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab2b5d68be069f30c8f71536b6d47cb1ce8823b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739665"
---
# <a name="createinplace-element-visual-studio-templates"></a>CreateInPlace öğesi (Visual Studio şablonları)
Projeyi oluşturup belirtilen konumda parametre değiştirme mi gerçekleştireceklerini veya geçici bir konumda parametre değiştirme yapıp sonra da projeyi belirtilen konuma kaydedip kaydetmeyeceklerini belirtir.

 \<VSTemplate \<> ŞablonVeri> \<CreateInPlace>

## <a name="syntax"></a>Sözdizimi

```
<CreateInPlace> true/false </CreateInPlace>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin ya da `true` `false`olmalıdır . Proje oluşturulurve parametre değiştirme Yeni Proje iletişim kutusunda belirtilen konumda gerçekleştirilir. **New Project** `true` `false`Eğer , parametre değiştirme geçici bir konumda gerçekleştirilir ve proje daha sonra belirtilen konuma kopyalanır.

## <a name="remarks"></a>Açıklamalar
 `CreateInPlace`isteğe bağlı bir unsurdur. Varsayılan değer: `true`.

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
        <CreateInPlace>false</CreateInPlace>
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
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
