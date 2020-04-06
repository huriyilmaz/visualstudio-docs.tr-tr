---
title: EnableLocationBrowseButton Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711983"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton öğesi (Visual Studio şablonları)
**Gözat** düğmesinin **Yeni Proje** iletişim kutusunda kullanılabilir olup olmadığını belirtir, böylece kullanıcılar yeni bir proje kaydedilirken varsayılan dizini kolayca değiştirebilir.

 \<VSTemplate \<> ŞablonVeri> \<EnableLocationBrowseButton>

## <a name="syntax"></a>Sözdizimi

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, `true` **Yeni Proje** iletişim kutusunda **Gözat** düğmesini gösterip göstermeyeceğini belirten bir `false`metin olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `EnableLocationBrowseButton`isteğe bağlı bir unsurdur. Varsayılan değer, `true` **Yeni Proje** iletişim kutusunda **Gözat** düğmesini görüntüleyen değerdir.

 Yeni **Proje** iletişim kutusunda, **Konum** metin kutusu yeni bir projenin kaydedildiği dizini belirtir. **Gözat** düğmesi, bilgisayarınızda bulunan farklı bir dizin için kolayca gezinmenizi ve ardından yeni projenin kaydedildiği dizin olarak seçmenize olanak tanıyan **Proje Konumu** iletişim kutusunu görüntüleyerek bu dizini değiştirmenize yardımcı olur.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows uygulamasının meta verileri gösteriş verilmiştir.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
