---
title: Proje şablonlarında etiket ekleme veya düzenleme
description: Proje şablonlarında etiket ekleme veya düzenleme hakkında bilgi Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 515d6ff5e489ce7d586eb29682b817d63008fd0bf90e2f3eda7a7138e7dd0240
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386984"
---
# <a name="add-tags-to-project-templates"></a>Proje şablonlarına etiket ekleme

[2019 Visual Studio](https://visualstudio.microsoft.com/downloads/) 16.1 Önizleme 2'den başlayarak, proje şablonlarınıza dil, platform ve proje türü etiketleri ekebilirsiniz. 

Etiketler Yeni Sayfa iletişim kutusundaki iki **Project** kullanılır:

- Etiketler şablon açıklaması altında görünür.

   ![Project iletişim kutusunda etiketlerin yer Project şablon oluşturma](media/npd-item-with-template-tags.png)

- Etiketler, şablonun aranma ve filtrelenene olanak sağlar.

   ![Yeni Uygulama iletişim kutusunda arama Project filtrele](media/npd-search-and-filter.png)

Etiket eklemek için *.vstemplate* XML dosyasını güncelleştirebilirsiniz. Yerleşik şablon etiketlerini kullanarak Visual Studio veya özel şablon etiketleri oluşturabilirsiniz. Şablon etiketleri yalnızca Visual Studio 2019 **Yeni** Project iletişim kutusunda görünür. Şablon etiketleri, şablonun Visual Studio'nin önceki sürümlerinde nasıl iş Visual Studio.

## <a name="add-or-edit-tags"></a>Etiket ekleme veya düzenleme

Aşağıdaki eylemlerden birini gerçekleştirebilirsiniz: 

* [Şablonu Dışarı Aktar sihirbazını](how-to-create-project-templates.md) kullanarak yeni bir proje şablonu oluşturun.
* [Mevcut proje şablonlarınızı güncelleştirin.](how-to-update-existing-templates.md)
* [Yeni bir VSIX proje şablonu oluşturun.](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="syntax"></a>Syntax

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Öznitelikler

Gelişmiş kullanıcı senaryolarında aşağıdaki isteğe bağlı öznitelikleri kullanabilirsiniz:

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Package`|Paket kimliğini belirten Visual Studio GUID.|
|`ID`|Kaynak kimliğini Visual Studio belirtir.|

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Gerekli) Şablonu kategorilere ayırarak Yeni Giriş  iletişim kutusunda Project Yeni Öğe Ekle **iletişim kutusunda nasıl görüntü olduğunu** tanımlar.|

## <a name="text-value"></a>Metin değeri

ve özniteliklerini kullanmadıkça metin `Package` değeri `ID` gereklidir.

Metin, şablonun adını sağlar.

## <a name="built-in-tags"></a>Yerleşik etiketler

Visual Studio yerleşik etiketlerin listesini sunar. Yerleşik bir etiket eklerken, etiket yerelleştirilmiş bir kaynağı işler. 

Aşağıdaki listede, Visual Studio'de bulunan yerleşik etiketler Visual Studio. Karşılık gelen değerler parantez içinde gösterilir.

| Dil etiketi | Platform etiketi | Project türü etiketi |
| -- | -- | -- |
| C++ ( `cpp` ) | Android ( `android` ) | Bulut ( `cloud` ) |
| C# ( `csharp` ) | Azure ( `azure` ) | Konsol ( `console` ) |
| F# ( `fsharp` ) | iOS ( `ios` ) | Masaüstü ( `desktop` ) |
| Java ( `java` ) | Linux ( `linux` ) | Uzantılar ( `extension` ) |
| JavaScript (`javascript`) | macOS ( `macos` ) | Oyunlar ( `games` ) |
| Python ( `python` ) | tvOS ( `tvos` ) | IoT ( `iot` ) |
| Sorgu Dili ( `querylanguage` ) | Windows ( `windows` ) | Kitaplık ( `library` ) |
| TypeScript ( `typescript` ) | Xbox ( `xbox` ) | Machine Learning ( `machinelearning` ) |
| Visual Basic ( `visualbasic` ) | | Mobil ( `mobile` ) |
| | | Office ( `office` ) |
| | | Diğer ( `other` ) |
| | | Hizmet ( `service` ) |
| | | Test ( `test` ) |
| | | UWP ( `uwp` ) |
| | | Web ( `web` ) |

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir Visual C# uygulaması için proje şablonunun meta verileri gösterir:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>csharp</LanguageTag>
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

- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](creating-project-and-item-templates.md)
- [Proje ve öğe şablonlarını özelleştirme](customizing-project-and-item-templates.md)
- [Kullanmaya başlayın VSIX proje şablonuyla birlikte kullanma](../extensibility/getting-started-with-the-vsix-project-template.md)
