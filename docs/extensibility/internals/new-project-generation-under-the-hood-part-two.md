---
title: 'Yeni Proje Üretimi: Hood altında, Bölüm İki | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707015"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm İki

[Yeni Proje Oluşturma: Hood altında, Bölüm One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) biz Yeni **Proje** iletişim Kutusu doldurulur nasıl gördüm. **Bir Görsel C# Windows Uygulaması**seçtiğinizi, **Ad** ve **Konum** metin kutularını doldurduğunuzu ve Tamam'ı tıklatdığınızı varsayalım.

## <a name="generating-the-solution-files"></a>Çözüm Dosyalarını Oluşturma
 Bir uygulama şablonu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seçmek, ilgili .vstemplate dosyasını açmak ve açmak ve bu dosyadaki XML komutlarını yorumlamak için bir şablon başlatmak için yönlendirir. Bu komutlar, yeni veya varolan çözümde proje ve proje öğeleri oluşturur.

 Şablon, .vstemplate dosyasını tutan aynı .zip klasöründen öğe şablonları adı verilen kaynak dosyaları açar. Şablon bu dosyaları yeni projeye kopyalayarak buna göre özelleştirerek kopyalar.

### <a name="template-parameter-replacement"></a>Şablon Parametre Değiştirme
 Şablon, bir öğe şablonunu yeni bir projeye kopyaladığında, dosyayı özelleştirmek için herhangi bir şablon parametrelerini dizeleri ile değiştirir. Şablon parametresi, örneğin $date$ gibi bir dolar işaretiöncesinde ve ardından gelen özel bir belirteçtir.

 Tipik bir proje öğesi şablonuna bakalım. Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründe Program.cs ayıklayın ve inceleyin.

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

Basit adlı yeni bir Windows uygulama projesi oluşturursanız, şablon parametreyi `$safeprojectname$` projenin adı ile değiştirir.

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

 Şablon parametrelerinin tam listesi için [şablon parametrelerine](../../ide/template-parameters.md)bakın.

## <a name="a-look-inside-a-vstemplate-file"></a>Bir Bakış Inside a . VSTemplate Dosyası
 Temel bir .vstemplate dosyasıbu biçime sahiptir

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 [Yeni Proje Üretimi: Başlık Altında, Bölüm Bir](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) \<TemplateData> bölümüne baktık. Bu bölümdeki **etiketler, Yeni Proje** iletişim kutusunun görünümünü denetlemek için kullanılır.

 TemplateContent> \<bölümündeki etiketler yeni projelerin ve proje öğelerinin oluşumunu denetler. \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip klasöründeki cswindowsapplication.vstemplate dosyasından \<TemplateContent> bölümü aşağıda verilmiştir.

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
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
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

 \<Project> etiketi projenin oluşumunu denetler \<ve ProjectItem> etiketi proje öğesinin oluşumunu denetler. Parametre ReplaceParameters doğruysa, şablon proje dosyasındaki veya öğedeki tüm şablon parametrelerini özelleştirecektir. Bu durumda, Ayarlar ayarlar dışında tüm proje öğeleri özelleştirilmiştir.

 TargetFileName parametresi, ortaya çıkan proje dosyasının veya öğenin adını ve göreli yolunu belirtir. Bu, projeniz için bir klasör yapısı oluşturmanıza olanak tanır. Bu bağımsız değişkeni belirtmezseniz, proje öğesi proje öğesi şablonuyla aynı ada sahip olur.

 Ortaya çıkan Windows uygulama klasörü yapısı aşağıdaki gibi görünür:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Şablondaki ilk \<ve tek Project> etiketi şöyledir:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Bu, şablon öğesi windowsapplication.csproj'u kopyalayıp özelleştirerek Simple.csproj proje dosyasını oluşturmak için Yeni Proje şablonuna talimat verir.

### <a name="designers-and-references"></a>Tasarımcılar ve Referanslar
 Çözüm Gezgini'nde Özellikler klasöründe mevcut olduğunu ve beklenen dosyaları içerdiğini görebilirsiniz. Ancak Kaynak.resx'e Resources.Designer.cs ve Form1.cs Form1.Designer.cs gibi proje başvuruları ve tasarımcı dosya bağımlılıkları ne olacak?  Bunlar oluşturulduğunda Simple.csproj dosyasında ayarlanır.

 Burada, proje \<başvurularını oluşturan Simple.csproj'un ItemGroup>:

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

 Bunların Çözüm Gezgini'nde görünen altı proje referansı olduğunu görebilirsiniz. Burada başka \<bir ItemGroup> bir bölüm. Birçok kod satırı netlik için silindi. Bu bölüm, Settings.Designer.cs Ayarlar ayarlara bağımlı hale getirir:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni Proje Oluşturma: Altyapı Öğeleri, Bölüm Bir](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
