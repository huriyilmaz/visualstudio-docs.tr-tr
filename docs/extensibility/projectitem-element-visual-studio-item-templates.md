---
title: ProjectItem Öğesi (Visual Studio Item Templates) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701871"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem öğesi (Visual Studio öğe şablonları)
Öğe şablonuna dahil olan bir dosyayı belirtir.

> [!NOTE]
> Öğe, `ProjectItem` şablonun bir proje veya öğe için olup olmadığına bağlı olarak farklı öznitelikleri kabul eder. Bu konu `ProjectItem` öğe için öğe öğeöğeyi açıklar. Proje şablonları `ProjectItem` için öğenin açıklaması için [ProjectItem öğesine (Visual Studio proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md)bakın.

 \<VSTemplate \<> Şablonİçerik> \<ProjectItem>

## <a name="syntax"></a>Sözdizimi

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
| `SubType` | İsteğe bağlı öznitelik.<br /><br /> Çok dosyalı öğe şablonundaki bir öğenin alt türünü belirtir. Bu değer, öğeyi açmak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için kullanılacak düzenleyiciyi belirlemek için kullanılır. |
| `CustomTool` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasındaki öğe için CustomTool'u ayarlar. |
| `ItemType` | İsteğe bağlı öznitelik.<br /><br /> Proje dosyasındaki öğe için ItemType'ı ayarlar. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda değiştirilmesi gereken öğenin parametre değerlerine sahip olup olmadığını belirten boolean değeri. Varsayılan değer. `false` |
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Şablondan oluşturulan öğenin adını belirtir. Bu öznitelik, bir madde adı oluşturmak için parametre değiştirme kullanmak için yararlıdır. |

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Şablon `string` *.zip* dosyasındaki bir dosyanın adını temsil eden a.

## <a name="remarks"></a>Açıklamalar
 `ProjectItem`isteğe bağlı `TemplateContent`bir çocuktur.

 Öznitelik `TargetFileName` parametreleri ile dosyaları yeniden adlandırmak için kullanılabilir. Örneğin, *MyFile.vb* dosyası şablon *.zip* dosyasının kök dizininde varsa, ancak yeni **öğe ekle** iletişim kutusunda kullanıcı tarafından sağlanan dosya adına göre dosyanın adlandırılmasını istiyorsanız, aşağıdaki XML'yi kullanırsınız:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Bu şablondan bir öğe oluşturulduğunda, dosya adı kullanıcının **Yeni Öğe Ekle** iletişim kutusuna girdiği adı temel alacaktır. Bu, çok dosyalı öğe şablonları oluştururken yararlıdır. Daha fazla bilgi için [bkz: Çok dosyalı öğe şablonları](../ide/how-to-create-multi-file-item-templates.md) ve [Şablon parametreleri](../ide/template-parameters.md)oluşturun.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıfın standart madde şablonu için meta veriler gösterilmektedir.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılı: Çok dosyalı öğe şablonları oluşturma](../ide/how-to-create-multi-file-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
