---
title: Proje şablonlarına etiket ekleme veya düzenleme
description: Visual Studio 'da proje şablonlarına etiket ekleme veya düzenleme hakkında bilgi edinin.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: ef26a566229c228711ba6e57de50402df255c3dd
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82153025"
---
# <a name="add-tags-to-project-templates"></a>Proje şablonlarına etiketler ekleme

[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) sürüm 16,1 Preview 2 ' den başlayarak, proje şablonlarınıza dil, platform ve proje türü etiketleri ekleyebilirsiniz. 

Etiketler, **Yeni proje** iletişim kutusunda iki yerde kullanılır:

- Etiketler Şablon açıklaması altında görüntülenir.

   ![Yeni proje iletişim kutusunda etiketlerle birlikte proje şablonu](media/npd-item-with-template-tags.png)

- Etiketler, şablonun aranmasına ve filtrelenmesini sağlar.

   ![Yeni proje iletişim kutusunda arama ve filtreleme](media/npd-search-and-filter.png)

*. Vstemplate* XML dosyasını güncelleştirerek Etiketler ekleyebilirsiniz. Visual Studio 'da yerleşik olarak bulunan şablon etiketlerini kullanabilir veya özel şablon etiketleri oluşturabilirsiniz. Şablon Etiketleri yalnızca Visual Studio 2019 **Yeni proje** iletişim kutusunda görünür. Şablon Etiketleri, şablonun Visual Studio 'nun önceki sürümlerinde nasıl işlediğini etkilemez.

## <a name="add-or-edit-tags"></a>Etiket ekleme veya düzenleme

Aşağıdaki eylemlerden birini gerçekleştirdiğinizde proje şablonunuzda *. vstemplate* XML 'e etiket eklemek veya bunları düzenlemek isteyebilirsiniz:

* Şablonu dışarı aktarma Sihirbazı 'nı kullanarak [Yeni bir proje şablonu oluşturun](how-to-create-project-templates.md) .
* [Mevcut proje şablonunuzu güncelleştirin](how-to-update-existing-templates.md).
* [Yeni BIR VSIX proje şablonu oluşturun](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Sözdizimi

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Öznitelikler

Gelişmiş Kullanıcı senaryolarında aşağıdaki isteğe bağlı öznitelikleri kullanabilirsiniz:

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Package`|Visual Studio paket KIMLIĞINI belirten bir GUID.|
|`ID`|Visual Studio kaynak KIMLIĞINI belirtir.|

Söz dizimi:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Öğeler

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Istenir Şablonu kategorilere ayırır ve **Yeni proje** iletişim kutusunda ya da **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri

Ve `Package` `ID` özniteliklerini kullanmadığınız durumlar için metin değeri gereklidir.

Metin, şablonun adını sağlar.

## <a name="built-in-tags"></a>Yerleşik Etiketler

Visual Studio, yerleşik etiketlerin bir listesini sunar. Yerleşik bir etiket eklediğinizde, etiket yerelleştirilmiş bir kaynak oluşturur. 

Aşağıdaki listede, Visual Studio 'da kullanılabilen yerleşik Etiketler gösterilmektedir. Karşılık gelen değerler parantez içinde gösterilir.

| Dil etiketi | Platform etiketi | Proje türü etiketi |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Bulut (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Console (`console`) |
| F # (`fsharp`) | iOS (`ios`) | Masaüstü (`desktop`) |
| Java (`java`) | Linux (`linux`) | Uzantılar (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Oyunlar (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Sorgu Languate (`querylanguage`) | Windows (`windows`) | Library (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Mobile (`mobile`) |
| | | Office (`office`) |
| | | Diğer (`other`) |
| | | Hizmet (`service`) |
| | | Test (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir Visual C# uygulaması için bir proje şablonu meta verilerini gösterir:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
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

- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](creating-project-and-item-templates.md)
- [Proje ve öğe şablonlarını özelleştirme](customizing-project-and-item-templates.md)
- [VSıX proje şablonu ile çalışmaya başlama](../extensibility/getting-started-with-the-vsix-project-template.md)
