---
title: ProjectItem Öğesi (Visual Studio Project Şablonları) | Microsoft Docs
description: Proje şablonları için ProjectItem öğesini ve şablonun bir proje mi yoksa bir öğe için mi olduğuna bağlı olarak farklı öznitelikleri nasıl kabul eder? hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d72272da255d51e5ef3423806744ef7c95e00193e6895daa9d96e702b48ef206
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305301"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem öğesi (Visual Studio şablonları için)
Proje şablonuna dahil edilen bir dosyayı belirtir.

> [!NOTE]
> öğesi, `ProjectItem` şablonun bir proje mi yoksa bir öğe mi olduğuna bağlı olarak farklı öznitelikleri kabul eder. Bu konu başlığında `ProjectItem` proje şablonlarının öğesi açıklanmıştır. Öğe şablonları için öğe `ProjectItem` açıklaması için bkz. [ProjectItem Öğesi (Visual Studio Öğe Şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
|---------------------| - |
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Şablondan proje oluşturulduğunda proje öğesinin adını ve yolunu belirtir. Bu öznitelik, şablon.zipdosyasındaki dizin yapısından  farklı bir dizin yapısı oluşturmak veya öğe adı oluşturmak için parametre değiştirme kullanmak için kullanışlıdır. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Şablondan proje oluşturulduğunda öğenin değiştirilmesi gereken parametre değerlerine sahip olup olmadığını belirten boole değeri. Varsayılan değer `false` olarak belirlenmiştir. |
| `OpenInEditor` | İsteğe bağlı öznitelik.<br /><br /> Şablondan proje oluşturulduğunda öğenin ilgili düzenleyicide açılması gerekip gerek olmadığını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] belirten Boole değeri.<br /><br /> ve `OpenInWebBrowser` `OpenInHelpBrowser` öznitelikleri değerine sahip bir öğede `OpenInEditor` yoksayılır. `true`<br /><br /> `false` varsayılan değerdir. |
| `OpenInWebBrowser` | İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin Web tarayıcısına açılması gerekip gerek olmadığını belirten Boole değeri.<br /><br /> Web tarayıcısında yalnızca proje için yerel olan HTML dosyaları ve metin dosyaları açılabilir. Dış URL'ler bu öznitelikle açılamıyor.<br /><br /> `false` varsayılan değerdir. |
| `OpenInHelpBrowser` | İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin Yardım görüntüleyicisinde açılması gerekip gerek olmadığını belirten boole değeri.<br /><br /> Yardım tarayıcısında yalnızca proje için yerel olan HTML dosyaları ve metin dosyaları açılabilir. Dış URL'ler bu öznitelikle açılamıyor.<br /><br /> `false` varsayılan değerdir. |
| `OpenOrder` | İsteğe bağlı öznitelik.<br /><br /> Öğelerin ilgili düzenleyicilerinde açılması için sırayı temsil eden sayısal bir değer belirtir. Tüm değerlerin 10'dan katları olması gerekir. Daha yüksek `OpenOrder` değerlere sahip öğeler önce açılır. |

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Projeye eklenecek dosyaları veya dizinleri belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Şablonda `string` dosyanın adını veya yolunu temsil  eden bir.zip.

## <a name="remarks"></a>Açıklamalar
 `ProjectItem` isteğe bağlı bir alt alt `Project` veridir.

 özniteliği, `TargetFileName` şablon dosyasındaki dizin yapısından farklı bir dizin yapısı oluşturmak *.zip* kullanılabilir. Örneğin, *MyFile.vb* dosyası şablon *.zip* dosyasının kökünde mevcutsa ama dosyanın şablondan oluşturulan tüm projelerde *CustomFiles* adlı bir dizine yerleştirilmelerini istiyorsanız, aşağıdaki XML'yi kullanırsınız:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 özniteliği, `TargetFileName` dosya adlarında uluslararası karakterler içeren dosyaları yeniden adlandırmak için de kullanılabilir. Örneğin, bir *.zip* dosyası Unicode karakterli dosya adları içeremez, bu nedenle dosya bir dosyada sıkıştırılamadan önce *yeniden.zip* gerekir. özniteliği, `TargetFileName` dosya adını özgün Unicode dosya adına geri ayarlamak için kullanılabilir.

 özniteliği, `TargetFileName` dosyaları parametrelerle yeniden adlandırmak için de kullanılabilir. Aşağıdaki yordamda, şablon dosyanın kök dizininde bulunan *MyFile.vb* dosyasının, proje adına *göre.zip* dosya adına nasıl yeniden adlandırılacağını açıklar.

### <a name="to-rename-files-with-parameters"></a>Dosyaları parametrelerle yeniden adlandırmak için

1. *.vstemplate dosyasında aşağıdaki XML'yi* kullanın:

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Proje dosyasını ( proje *için .vbproj)* bir metin [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] düzenleyicisinde veya içinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açın.

3. Proje dosyasında aşağıdaki XML'e benzer şekilde görünen satırı bulun:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Kod satırı aşağıdaki XML ile değiştirin:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Bu şablondan bir proje oluşturulduğunda, dosya adı kullanıcının Yeni Project  iletişim kutusuna girdiği adı temel alır ve tüm güvenli olmayan karakterler ve boşluklar kaldırılır. Daha fazla bilgi için [bkz. Şablon parametreleri.](../ide/template-parameters.md)

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için proje şablonu meta verilerini [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] gösterir.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
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
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
