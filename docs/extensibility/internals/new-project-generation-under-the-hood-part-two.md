---
title: 'yeni Project oluşturma: devlet, ikinci bölüm | Microsoft Docs'
description: Visual Studio tümleşik geliştirme ortamında (ıde), kendi proje türünü (2. bölüm) oluştururken ayrıntılı bir bakış alın.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 77ee63fbc49554ad3d9037f7d5bf3d19e4cf29f16ec43d384a0489da9ec06184
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432363"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Yeni Proje Oluşturma: Arka Plan, 2. Bölüm

[yeni Project oluşturma bölümünde: birinci bölüm bölümünde](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) **yeni Project** iletişim kutusunun nasıl doldurulduğu gördünüz. bir **Visual C# Windows uygulaması** seçtiğinizi, **ad** ve **konum** metin kutularını doldurduktan ve tamam ' a tıkladığınızı varsayalım.

## <a name="generating-the-solution-files"></a>Çözüm dosyalarını oluşturma
 Uygulama şablonu seçme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , unzip ve ilgili. vstemplate dosyasını açmak ve bu DOSYADAKI xml komutlarını yorumlamak için bir şablon başlatmak üzere yönlendirir. Bu komutlar yeni veya mevcut çözümde projeler ve proje öğeleri oluşturur.

 Şablon, öğe şablonları olarak adlandırılan kaynak dosyalarını,. vstemplate dosyasını tutan .zip klasörden kaldırır. Şablon bu dosyaları yeni projeye kopyalar ve bunları uygun şekilde özelleştiriliyor.

### <a name="template-parameter-replacement"></a>Şablon parametresi değiştirme
 Şablon bir öğe şablonunu yeni bir projeye kopyaladığında, dosyayı özelleştirmek için tüm şablon parametrelerini dizeler ile değiştirir. Şablon parametresi, önce ve ardından dolar işareti (örneğin, $date $) gelen özel bir belirteçtir.

 Tipik bir proje öğesi şablonuna göz atalım. program Files \ Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki program. cs dosyasını ayıklayın ve inceleyin.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

basit adlı yeni bir Windows uygulama projesi oluşturursanız, şablon `$safeprojectname$` parametreyi projenin adıyla değiştirir.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Şablon parametrelerinin tüm listesi için bkz. [şablon parametreleri](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Içindeki bir görünüm. VSTemplate dosyası
 Temel bir. vstemplate dosyası bu biçime sahiptir

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 \<TemplateData>yeni Project oluşturma bölümündeki bölümüne baktık [: birinci bölüm, birinci](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)bölüm. bu bölümdeki etiketler, **yeni Project** iletişim kutusunun görünümünü denetlemek için kullanılır.

 \<TemplateContent>Bölümdeki Etiketler yeni projelerin ve proje öğelerinin oluşturulmasını denetler. \<TemplateContent>\program Files \ Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki cswindowsapplication. vstemplate dosyasının bölümü aşağıda verilmiştir.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 \<Project>Etiketi bir projenin neslini denetler ve \<ProjectItem> etiketi bir proje öğesinin oluşturulmasını denetler. ReplaceParameters parametresi true ise, şablon proje dosyasındaki veya öğedeki tüm şablon parametrelerini özelleştirecek. bu durumda, tüm proje öğeleri Ayarlar. ayarlar dışında özelleştirilir.

 TargetFileName parametresi, sonuçta elde edilen proje dosyasının veya öğesinin adını ve göreli yolunu belirtir. Bu, projeniz için bir klasör yapısı oluşturmanızı sağlar. Bu bağımsız değişkeni belirtmezseniz, proje öğesi proje öğesi şablonuyla aynı ada sahip olacaktır.

 elde edilen Windows uygulama klasörü yapısı şöyle görünür:

 ![Visual Studio Çözüm Gezgini ' basit ' çözümü için Windows uygulama klasörü yapısının ekran görüntüsü.](../../extensibility/internals/media/simplesolution.png)

 Şablondaki ilk ve tek \<Project> etiket şunu okur:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 bu, yeni Project şablonuna, windowsapplication. csproj şablon öğesini kopyalayarak ve özelleştirerek basit. csproj proje dosyası oluşturmasını söyler.

### <a name="designers-and-references"></a>Tasarımcılar ve başvurular
 Çözüm Gezgini Özellikler klasörünün mevcut olduğunu ve beklenen dosyaları içerdiğini görebilirsiniz. Ancak, proje başvuruları ve kaynak. cs-resources. resx ve Form1. Designer. cs ile Form1. cs 'ye kadar dosya bağımlılıkları hakkında ne olacak?  Bunlar, oluşturulduğu sırada basit. csproj dosyasında ayarlanır.

 İşte \<ItemGroup> proje başvurularını oluşturan Simple. csproj.

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Bunların Çözüm Gezgini görüntülenen altı proje başvurusu olduğunu görebilirsiniz. Diğer bir bölümü aşağıda verilmiştir \<ItemGroup> . Birçok kod satırı açıklık için silindi. bu bölüm Ayarlar yapar. tasarımcı. cs Ayarlar. ayarlar 'a bağımlıdır:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni Proje Oluşturma: Arka Plan, 1. Bölüm](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
