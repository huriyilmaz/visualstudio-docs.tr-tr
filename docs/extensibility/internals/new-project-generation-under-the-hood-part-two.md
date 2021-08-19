---
title: 'Yeni Project Oluşturma: Başlık Altında, Bölüm İki | Microsoft Docs'
description: Kendi proje türünüz (Bölüm 2/2) Visual Studio tümleşik geliştirme ortamında (IDE) neler olduğunu ayrıntılı bir şekilde göz atabilirsiniz.
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
ms.openlocfilehash: 56e1fa13846525221ec96dca3a8b744590e1dc8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042263"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Yeni Proje Oluşturma: Arka Plan, 2. Bölüm

New [Project Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) bölümünde New **Project** iletişim kutusunun nasıl dolduruldu olduğunu gördük. Bir **Visual C#** Windows Uygulaması seçtiğinizi, Ad ve Konum  metin  kutularını doldurarak Tamam'a tıklamış olduğunu varsayalım.

## <a name="generating-the-solution-files"></a>Çözüm Dosyalarını Oluşturma
 Bir uygulama şablonu seçmek, sıkıştırmasını açıp ilgili .vstemplate dosyasını açmaya ve bu dosyada XML komutlarını yorumlamak için bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] şablon başlatmaya yönlendiriyor. Bu komutlar yeni veya mevcut çözümde projeler ve proje öğeleri oluşturun.

 Şablon, .vstemplate dosyasını tutan aynı .zip klasördeki öğe şablonları olarak adlandırılan kaynak dosyaları paketinden çıkartır. Şablon, bu dosyaları uygun şekilde özelleştirerek yeni projeye kopyalar.

### <a name="template-parameter-replacement"></a>Şablon Parametresi Değiştirme
 Şablon bir öğe şablonunu yeni bir projeye kopyalarsa, dosyayı özelleştirmek için şablon parametrelerini dizelerle değiştirir. Şablon parametresi, önünde ve ardından dolar işareti gelen özel bir belirteçtir ( örneğin, $date$ ).

 Şimdi tipik bir proje öğesi şablonuna bakalım. Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki Program.cs'yi ayık Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

Simple adlı yeni bir Windows uygulama projesi oluşturursanız, şablon `$safeprojectname$` parametresini projenin adıyla değiştirir.

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

 Şablon parametrelerinin tam listesi için bkz. [Şablon Parametreleri.](../../ide/template-parameters.md)

## <a name="a-look-inside-a-vstemplate-file"></a>A Look Inside a . VSTemplate Dosyası
 Temel bir .vstemplate dosyası bu biçime sahip

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 New Project \<TemplateData> [Generation: Under the Hood, Part One bölümündeki bölümü inceledik.](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) Bu bölümdeki etiketler, Yeni Görünüm iletişim kutusunun **görünümünü Project** kullanılır.

 bölümündeki etiketler \<TemplateContent> yeni projelerin ve proje öğelerinin neslini kontrol ediyor. \<TemplateContent>\Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki cswindowsapplication.vstemplate dosyasındaki bölümü Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip edinebilirsiniz.

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

 Etiket \<Project> bir projenin neslini, etiket ise \<ProjectItem> proje öğesinin neslini kontrol eder. ReplaceParameters parametresi true ise şablon, proje dosyasındaki veya öğede tüm şablon parametrelerini özeller. Bu durumda, Ayarlar.settings dışındaki tüm proje öğeleri özelleştirilebilir.

 TargetFileName parametresi, sonuçta elde edilen proje dosyasının veya öğenin adını ve göreli yolunu belirtir. Bu, projeniz için bir klasör yapısı oluşturmanıza olanak sağlar. Bu bağımsız değişkeni belirtmezseniz, proje öğesi proje öğesi şablonuyla aynı adı verir.

 Elde edilen Windows klasör yapısı şöyle görünür:

 ![Visual Studio Çözüm Gezgini'Windows 'Basit' Çözüm için uygulama klasör yapısının ekran Visual Studio Çözüm Gezgini.](../../extensibility/internals/media/simplesolution.png)

 Şablonda ilk \<Project> ve tek etiket şu şekildedir:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Bu, Windowsapplication.csproj şablon öğesini kopyalayıp özelleştirerek New Project şablonuna Simple.csproj proje dosyasını oluşturması talimatı sağlar.

### <a name="designers-and-references"></a>Tasarımcılar ve Başvurular
 Özellikler klasörünün mevcut Çözüm Gezgini beklenen dosyaları içerdiğini, bu klasördeki dosyaları görebilir. Peki Resources.Designer.cs'den Resources.resx'e ve Form1.Designer.cs'den Form1.cs'ye proje başvuruları ve tasarımcı dosyası bağımlılıkları ne olacak?  Bunlar, üretilen Simple.csproj dosyasında ayarlanır.

 Proje başvurularını \<ItemGroup> oluşturan Simple.csproj'dan aşağıdakiler yer almaktadır:

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

 Bunların, veri kaynaklarında görünen altı proje başvurusu olduğunu Çözüm Gezgini. İşte başka bir bölümünden bir \<ItemGroup> bölüm. Netlik sağlamak için birçok kod satırı silindi. Bu bölüm, Ayarlar. designer.cs, Ayarlar.settings'a bağımlıdır:

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
