---
title: ProjectItem Öğesi (Visual Studio Öğe Şablonları) | Microsoft Docs
description: Öğe şablonları için ProjectItem öğesini ve şablonun bir proje mi yoksa bir öğe için mi olduğuna bağlı olarak farklı öznitelikleri nasıl kabul eder? hakkında bilgi öğrenin.
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 460f5ea31913e57dd095f7cbdf6677e24acb3a12a2fa70f80abb0acb67a34f8a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447811"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem öğesi (Visual Studio öğe şablonları)
Öğe şablonuna dahil edilen bir dosyayı belirtir.

> [!NOTE]
> öğesi, `ProjectItem` şablonun bir proje mi yoksa bir öğe mi olduğuna bağlı olarak farklı öznitelikleri kabul eder. Bu konuda `ProjectItem` öğenin öğesi açıklanmıştır. Proje şablonları için `ProjectItem` öğesinin açıklaması için bkz. [ProjectItem öğesi (Visual Studio proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md).

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
| `SubType` | İsteğe bağlı öznitelik.<br /><br /> Çok dosyalı bir öğe şablonunda bir öğenin alt türü belirtir. Bu değer, öğeyi açmak için kullanılacak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] düzenleyiciyi belirlemek için kullanılır. |
| `CustomTool` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasındaki öğe için CustomTool'ları ayarlar. |
| `ItemType` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasındaki öğe için ItemType'i ayarlar. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Şablondan proje oluşturulduğunda öğenin değiştirilmesi gereken parametre değerlerine sahip olup olmadığını belirten boole değeri. Varsayılan değer `false` olarak belirlenmiştir. |
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Şablondan oluşturulan öğenin adını belirtir. Bu öznitelik, öğe adı oluşturmak için parametre değiştirme kullanmak için kullanışlıdır. |

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Şablonda `string` bir dosyanın adını temsil  eden bir.zip.

## <a name="remarks"></a>Açıklamalar
 `ProjectItem` isteğe bağlı bir alt alt `TemplateContent` veridir.

 özniteliği, `TargetFileName` dosyaları parametrelerle yeniden adlandırmak için kullanılabilir. Örneğin, *MyFile.vb* dosyası şablon *.zip* dosyasının kök dizininde mevcutsa, ancak dosyanın Yeni Öğe Ekle iletişim kutusunda kullanıcı  tarafından sağlanan dosya adına göre adlandırılmış olması gerekirse, aşağıdaki XML'yi kullanırsınız:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Bu şablondan bir öğe oluşturulduğunda, dosya adı kullanıcının Yeni Öğe Ekle iletişim kutusuna girdiği **adı temel** alır. Bu, çok dosyalı öğe şablonları oluştururken kullanışlıdır. Daha fazla bilgi [için, bkz. How to: Create multi-file item templates and](../ide/how-to-create-multi-file-item-templates.md) [Template parameters](../ide/template-parameters.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir sınıf için standart öğe şablonunun meta verilerini [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] gösterir.

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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl kullanılır: Çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
