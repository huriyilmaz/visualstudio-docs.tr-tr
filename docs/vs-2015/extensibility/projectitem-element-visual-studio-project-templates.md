---
title: ProjectItem öğesi (Visual Studio proje şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84fb371460bc697660e176ca9df4c984d2b234bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799304"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem Öğesi (Visual Studio Proje Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje şablonuna dahil olan bir dosyayı belirtir.  
  
> [!NOTE]
> `ProjectItem`Öğesi, şablonun bir proje veya öğe için olup olmadığına bağlı olarak farklı öznitelikleri kabul eder. Bu konuda `ProjectItem` Proje şablonları için öğesi açıklanmaktadır. `ProjectItem`Öğe şablonları için bir açıklama için bkz. [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda proje öğesinin adını ve yolunu belirtir. Bu öznitelik, şablon. zip dosyasındaki dizin yapısından farklı bir dizin yapısı oluşturmak veya bir öğe adı oluşturmak için parametre değişimini kullanmak için yararlıdır.|  
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda, öğenin değiştirilmesini gerektiren parametre değerleri olup olmadığını belirten bir Boole değeri. Varsayılan değer `false` .|  
|`OpenInEditor`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin ilgili düzenleyicide açılıp açılmayacağını belirten bir Boole değeri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .<br /><br /> `OpenInWebBrowser`Ve `OpenInHelpBrowser` öznitelikleri, değeri olan bir öğe üzerinde yok sayılır `OpenInEditor` `true` .<br /><br /> Varsayılan değer: `false`.|  
|`OpenInWebBrowser`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin Web tarayıcısını açıp açılmayacağını belirten bir Boole değeri.<br /><br /> Web tarayıcısında yalnızca proje için yerel olan HTML dosyaları ve metin dosyaları açılabilir. Dış URL 'Ler Bu öznitelikle açılamaz.<br /><br /> Varsayılan değer: `false`.|  
|`OpenInHelpBrowser`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda öğenin yardım görüntüleyicisinde açılıp açılmayacağını belirten bir Boole değeri.<br /><br /> Yardım tarayıcısında yalnızca proje için yerel olan HTML dosyaları ve metin dosyaları açılabilir. Dış URL 'Ler Bu öznitelikle açılamaz.<br /><br /> Varsayılan değer: `false`.|  
|`OpenOrder`|İsteğe bağlı öznitelik.<br /><br /> Öğelerin ilgili düzenleyicilerde açılacak sırayı temsil eden sayısal bir değer belirtir. Tüm değerler 10 ' un katları olmalıdır. Daha yüksek değerlere sahip öğeler `OpenOrder` önce açılır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Projeye eklenecek dosyaları veya dizinleri belirtir.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 `string`Şablon. zip dosyasındaki bir dosyanın adını veya yolunu temsil eden bir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProjectItem` , öğesinin isteğe bağlı bir alt öğesidir `Project` .  
  
 `TargetFileName`Özniteliği, şablon. zip dosyasındaki dizin yapısından farklı bir dizin yapısı oluşturmak için kullanılabilir. Örneğin, dosya `MyFile.vb` Template. zip dosyasının kökünde varsa, ancak dosyanın şablondan oluşturulan tüm projelerde adlı bir dizine yerleştirilmesini istiyorsanız `CustomFiles` aşağıdaki XML 'i kullanırsınız:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 Özniteliği, dosya `TargetFileName` adlarında uluslararası karakterler içeren dosyaları yeniden adlandırmak için de kullanılabilir. Örneğin, bir şablon. zip dosyası Unicode karakterler içeren dosya adlarını içeremez, bu yüzden dosyanın bir. zip dosyasına sıkıştırılabilmesi için önce yeniden adlandırılması gerekir. `TargetFileName`Özniteliği, dosya adını özgün Unicode dosya adına geri ayarlamak için kullanılabilir.  
  
 `TargetFileName`Özniteliği parametreleri olan dosyaları yeniden adlandırmak için de kullanılabilir. Aşağıdaki yordamda, `MyFile.vb` şablon. zip dosyasının kök dizininde bulunan dosyayı proje adına göre bir dosya adına olan dosyanın nasıl yeniden adlandırılacağı açıklanmaktadır.  
  
### <a name="to-rename-files-with-parameters"></a>Dosyaları parametrelerle yeniden adlandırmak için  
  
1. . Vstemplate dosyasında aşağıdaki XML 'i kullanın:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2. Proje dosyasını (bir proje için. vbproj [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) bir metin düzenleyicisinde veya içinde açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. Proje dosyasında aşağıdaki XML 'e benzeyen satırı bulun:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4. Kod satırını aşağıdaki XML ile değiştirin:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Bu şablondan bir proje oluşturulduğunda, dosya adı, kullanıcının **Yeni proje** iletişim kutusunda girdiği, tüm güvenli olmayan karakterler ve boşluklar kaldırılmış şekilde adı temel alır. Daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Şablon parametreleri](../ide/template-parameters.md)   
 [ProjectItem Öğesi (Visual Studio Öğe Şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
