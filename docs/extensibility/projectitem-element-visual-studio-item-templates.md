---
title: ProjectItem öğesi (Visual Studio öğe şablonları) | Microsoft Docs
description: Öğe şablonları için ProjectItem öğesi ve şablonun bir proje ya da öğe için olup olmadığına bağlı olarak farklı öznitelikleri kabul etme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 201f6e7845f1294892836de4cca24195fb0f1596
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928243"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem öğesi (Visual Studio öğe şablonları)
Öğe şablonunda bulunan bir dosyayı belirtir.

> [!NOTE]
> `ProjectItem`Öğesi, şablonun bir proje veya öğe için olup olmadığına bağlı olarak farklı öznitelikleri kabul eder. Bu konuda `ProjectItem` öğesi için öğesi açıklanmaktadır. `ProjectItem`Proje şablonları için bir açıklama için bkz. [ProjectItem öğesi (Visual Studio proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
|---------------------| - |
| `SubType` | İsteğe bağlı öznitelik.<br /><br /> Birden çok dosya öğesi şablonundaki bir öğenin alt türünü belirtir. Bu değer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] öğeyi açmak için kullanılacak düzenleyiciyi belirlemekte kullanılır. |
| `CustomTool` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasındaki öğe için CustomTool 'ı ayarlar. |
| `ItemType` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasındaki öğe için ItemType 'ı ayarlar. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda, öğenin değiştirilmesini gerektiren parametre değerleri olup olmadığını belirten bir Boole değeri. Varsayılan değer `false` olarak belirlenmiştir. |
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Şablondan oluşturulan öğenin adını belirtir. Bu öznitelik, bir öğe adı oluşturmak için parametre değişimini kullanmak için yararlıdır. |

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 `string`Şablon *. zip* dosyasındaki bir dosyanın adını temsil eden bir.

## <a name="remarks"></a>Açıklamalar
 `ProjectItem` , öğesinin isteğe bağlı bir alt öğesidir `TemplateContent` .

 `TargetFileName`Özniteliği parametreleri olan dosyaları yeniden adlandırmak için kullanılabilir. Örneğin, File *. vb* dosyası template *. zip* dosyasının kök dizininde mevcutsa, ancak dosyanın **Yeni öğe Ekle** iletişim kutusunda belirtilen dosya ADıNA göre adlandırılmış olmasını istiyorsanız aşağıdaki XML 'i kullanacaksınız:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Bu şablondan bir öğe oluşturulduğunda, dosya adı kullanıcının **Yeni öğe Ekle** iletişim kutusuna girdiği adı temel alır. Bu, çok dosya öğesi şablonları oluştururken faydalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: birden çok dosya öğesi şablonları](../ide/how-to-create-multi-file-item-templates.md) ve [şablon parametreleri](../ide/template-parameters.md)oluşturma.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir sınıf için standart öğe şablonu meta verilerini gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: birden çok dosya öğesi şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
