---
title: Proje şablonlarına etiket ekleme veya düzenlemesi
description: Visual Studio'da proje şablonlarına etiket eklemeyi veya nasıl edinleyeceğinizi öğrenin.
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
ms.openlocfilehash: 37fa5449847eb4c093475df11a07decb31168f1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189513"
---
# <a name="add-tags-to-project-templates"></a>Proje şablonlarına etiket ekleme

Visual [Studio 2019](https://visualstudio.microsoft.com/downloads/) sürüm 16.1 Preview 2'den başlayarak proje şablonlarınıza dil, platform ve proje türü etiketleri ekleyebilirsiniz. 

Etiketler **Yeni Proje** iletişim kutusunda iki yerde kullanılır:

- Etiketler şablon açıklamasının altında görünür.

   ![Yeni Proje iletişim kutusunda etiketlerle proje şablonu](media/npd-item-with-template-tags.png)

- Etiketler şablonun aranmasını ve filtrelanmasını sağlar.

   ![Yeni Proje iletişim kutusunda arama ve filtreleme](media/npd-search-and-filter.png)

*.vstemplate* XML dosyasını güncelleştirerek etiket ekleyebilirsiniz. Visual Studio'da yerleşik şablon etiketleri kullanabilir veya özel şablon etiketleri oluşturabilirsiniz. Şablon etiketleri yalnızca Visual Studio 2019 **Yeni Proje** iletişim kutusunda görünür. Şablon etiketleri, şablonun Visual Studio'nun önceki sürümlerinde nasıl işleyiş olduğunu etkilemez.

## <a name="add-or-edit-tags"></a>Etiket ekleme veya bu etiketi daha iyi bir şekilde dolandır

Aşağıdaki eylemlerden birini yaptığınızda proje şablonunuzun *.vstemplate* XML'ine etiket eklemek veya onları dizinebilirsiniz:

* Dışa Aktarma Şablonu sihirbazını kullanarak [yeni bir proje şablonu oluşturun.](how-to-create-project-templates.md)
* [Varolan proje şablonunuzu güncelleştirin.](how-to-update-existing-templates.md)
* [Yeni bir VSIX proje şablonu oluşturun.](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="syntax"></a>Sözdizimi

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Öznitelikler

Gelişmiş kullanıcı senaryolarında aşağıdaki isteğe bağlı öznitelikleri kullanabilirsiniz:

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Package`|Visual Studio paket kimliğini belirten bir GUID.|
|`ID`|Visual Studio kaynak kimliğini belirtir.|

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Gerekli) Şablonu kategorilere ayırın ve Yeni **Proje** iletişim kutusunda veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri

Öznitelikleri `Package` ve `ID` öznitelikleri kullanmadığınız sürece metin değeri gereklidir.

Metin şablonun adını sağlar.

## <a name="built-in-tags"></a>Yerleşik etiketler

Visual Studio yerleşik etiketlerin bir listesini sunar. Yerleşik bir etiket eklediğinizde, etiket yerelleştirilmiş bir kaynak işler. 

Aşağıdaki liste Visual Studio'da bulunan yerleşik etiketleri gösterir. Karşılık gelen değerler parantez içinde gösterilir.

| Dil | Platform | Proje türü |
| -- | -- | -- |
| C++`cpp`( ) | Android`android`( ) | Bulut`cloud`( ) |
| C#`csharp`( ) | Azure`azure`( ) | Konsol`console`( ) |
| F#`fsharp`( ) | iOS`ios`( ) | Masaüstü`desktop`( ) |
| Java`java`( ) | Linux`linux`( ) | Uzantılar`extension`( ) |
| JavaScript`javascript`( ) | macOS`macos`( ) | Oyunlar`games`( ) |
| Python`python`( ) | tvOS`tvos`( ) | IoT`iot`( ) |
| Sorgu Languate`querylanguage`( ) | Windows`windows`( ) | Kütüphane`library`( ) |
| TypeScript`typescript`( ) | Xbox`xbox`( ) | Makine Öğrenimi (`machinelearning`) |
| Visual Basic`visualbasic`( ) | | Mobil`mobile`( ) |
| | | Ofis`office`( ) |
| | | Diğer`other`( ) |
| | | Hizmet`service`( ) |
| | | Test`test`( ) |
| | | UWP`uwp`( ) |
| | | Web`web`( ) |

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual C# uygulaması için proje şablonu meta verilerini gösterir:

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

- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](creating-project-and-item-templates.md)
- [Proje ve öğe şablonlarını özelleştirme](customizing-project-and-item-templates.md)
- [VSIX proje şablonu yla başlayın](../extensibility/getting-started-with-the-vsix-project-template.md)
