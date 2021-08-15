---
title: supportsmasterpage öğesi (Visual Studio şablonları) | Microsoft Docs
description: SupportsMasterPage öğesi hakkında bilgi edinin ve yeni öğe Ekle iletişim kutusunda ana sayfa seç onay kutusunun etkin olup olmadığını belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4138f7ffdb227c0a7bacd09fb514d2d22c63d5962ab3c9787b616dedde3d8d38
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121320990"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage Öğesi (Visual Studio Şablonları)
**Yeni öğe Ekle** Iletişim kutusunda **Ana sayfa seç** onay kutusunun etkin olup olmadığını belirtir.

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

## <a name="syntax"></a>Syntax

```
<SupportsMasterPage> true/false </SupportsMasterPage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|şablonu kategorilere ayırır ve **yeni Project** veya **yeni öğe** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin ya da ya da `true` `false` **Yeni öğe Ekle** Iletişim kutusunda **Ana sayfa seç** onay kutusunun etkin olup olmadığını gösteren bir değer olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `SupportsMasterPage` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

 `SupportsMasterPage`Öğesi yalnızca Web öğesi şablonları için kullanılabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir ana sayfa için destek içeren bir Web projesinin meta verilerini gösterir.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
