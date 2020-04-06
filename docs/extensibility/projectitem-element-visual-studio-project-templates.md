---
title: ProjectItem Öğesi (Visual Studio Proje Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701848"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem öğesi (Visual Studio proje şablonları)
Proje şablonuna dahil olan bir dosyayı belirtir.

> [!NOTE]
> Öğe, `ProjectItem` şablonun bir proje veya öğe için olup olmadığına bağlı olarak farklı öznitelikleri kabul eder. Bu konu, `ProjectItem` proje şablonları için öğeyi açıklar. Öğe şablonları `ProjectItem` için öğenin açıklaması için [ProjectItem Öğesi (Visual Studio Item Templates)](../extensibility/projectitem-element-visual-studio-item-templates.md)bölümüne bakın.

 \<VSTemplate \<> TemplateContent \< \<> Proje> ProjeÖğesi>

## <a name="syntax"></a>Sözdizimi

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
| `TargetFileName` | İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda proje öğesinin adını ve yolunu belirtir. Bu öznitelik, şablon *.zip* dosyasındaki dizin yapısından farklı bir dizin yapısı oluşturmak veya bir öğe adı oluşturmak için parametre değiştirme kullanmak için yararlıdır. |
| `ReplaceParameters` | İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan oluşturulduğunda değiştirilmesi gereken öğenin parametre değerlerine sahip olup olmadığını belirten boolean değeri. Varsayılan değer. `false` |
| `OpenInEditor` | İsteğe bağlı öznitelik.<br /><br /> Bir proje şablondan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturulduğunda öğenin ilgili düzenleyicisinde açılıp açılmayacağını belirten bir Boolean değeri.<br /><br /> Ve `OpenInWebBrowser` `OpenInHelpBrowser` öznitelikleri değeri olan bir `OpenInEditor` öğeüzerinde `true`yoksayılır.<br /><br /> Varsayılan değer: `false`. |
| `OpenInWebBrowser` | İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin Web tarayıcısının açılıp açılmayacağını belirten boolean değeri.<br /><br /> Web tarayıcısında yalnızca projeye yerel olan HTML dosyaları ve metin dosyaları açılabilir. Dış URL'ler bu öznitelik ile açılamaz.<br /><br /> Varsayılan değer: `false`. |
| `OpenInHelpBrowser` | İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin Yardım görüntüleyicisinde açılıp açılmayacağını belirten bir Boolean değeri.<br /><br /> Yardım tarayıcısında yalnızca projeye yerel olan HTML dosyaları ve metin dosyaları açılabilir. Dış URL'ler bu öznitelik ile açılamaz.<br /><br /> Varsayılan değer: `false`. |
| `OpenOrder` | İsteğe bağlı öznitelik.<br /><br /> Öğelerin ilgili editörlerinde açılacağına sırasını temsil eden sayısal bir değer belirtir. Tüm değerler 10'un katları olmalıdır. Önce daha `OpenOrder` yüksek değerlere sahip öğeler açılır. |

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Projeye eklenecek dosyaları veya dizinleri belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Şablon `string` *.zip* dosyasındaki bir dosyanın adını veya yolunu temsil eden bir dosya.

## <a name="remarks"></a>Açıklamalar
 `ProjectItem`isteğe bağlı `Project`bir çocuktur.

 Öznitelik `TargetFileName` şablon *.zip* dosyasında dizin yapısından farklı bir dizin yapısı oluşturmak için kullanılabilir. Örneğin, *MyFile.vb* dosyası şablon *.zip* dosyasının kökünde varsa, ancak dosyanın şablondan oluşturulan tüm projelerde *CustomFiles* adlı bir dizine yerleştirilmesini istiyorsanız, aşağıdaki XML'yi kullanırsınız:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Öznitelik, `TargetFileName` dosya adlarında uluslararası karakterler içeren dosyaları yeniden adlandırmak için de kullanılabilir. Örneğin, bir şablon *.zip* dosyası Unicode karakterleri içeren dosya adları içeremez, bu nedenle dosyanın *bir .zip* dosyasına sıkıştırılabilmek için yeniden adlandırılması gerekir. Öznitelik, `TargetFileName` dosya adını özgün Unicode dosya adına geri ayarlamak için kullanılabilir.

 Öznitelik, `TargetFileName` parametrelerle dosyaları yeniden adlandırmak için de kullanılabilir. Aşağıdaki yordam, şablon *.zip* dosyasının kök dizininde bulunan *MyFile.vb*dosyasının proje adına dayalı bir dosya adına nasıl yeniden adlandırılabildiğini açıklar.

### <a name="to-rename-files-with-parameters"></a>Parametrelerle dosyaları yeniden adlandırmak için

1. *.vstemplate* dosyasında aşağıdaki XML'yi kullanın:

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Proje dosyasını (proje [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] için *.vbproj)* bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]metin düzenleyicisinde veya .

3. Proje dosyasında aşağıdaki XML'e benzeyen satırı bulun:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Kod satırını aşağıdaki XML ile değiştirin:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Bu şablondan bir proje oluşturulduğunda, dosya adı, tüm güvenli olmayan karakterler ve boşluklar kaldırılarak, kullanıcının **Yeni Proje** iletişim kutusuna girdiği adı temel alacaktır. Daha fazla bilgi için [Şablon parametrelerine](../ide/template-parameters.md)bakın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] uygulama için proje şablonu için meta verileri gösterir.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
