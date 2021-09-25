---
title: 'Nasıl yapılandırılır: Projeleri platformları hedef olarak yapılandırma'
description: Uygulamalarınızı Visual Studio 64 bit platformlar da dahil olmak üzere farklı platformları hedeflemek üzere ayarlamanızı nasıl sağlar?
ms.custom: SEO-VS-2020
ms.date: 09/13/2021
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b74eb7d0220867b80337b89ef70506bac31b7f6a
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429023"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Nasıl yapılandırılır: Projeleri platformları hedef olarak yapılandırma

Visual Studio, uygulama derlemelerinizi 64 bit platformlar da dahil olmak üzere farklı platformları hedeflemek üzere ayarlamanızı sağlar. 64 bit platform desteği hakkında daha fazla bilgi için Visual Studio bkz. [64 bit uygulamalar.](/dotnet/framework/64-bit-apps)

::: moniker range="vs-2022"
> [!NOTE]
> Visual Studio 2022 Preview 64 bit uygulama olarak çalışır. Bu, Visual Studio'daki projeleriniz için hedefleyebiliyorsunuz platformlardan tamamen Visual Studio. Hem 32 bit hem de 64 bit platformları hedeflemek için herhangi bir Visual Studio sürümünü kullanabilirsiniz.
::: moniker-end
::: moniker range="<=vs-2019"
> [!NOTE]
> Visual Studio 32 bit uygulama olarak çalışır. Bu, Visual Studio'daki projeleriniz için hedefleyebiliyorsunuz platformlardan tamamen Visual Studio. Hem 32 bit hem de 64 bit platformları hedeflemek için herhangi bir Visual Studio sürümünü kullanabilirsiniz.
::: moniker-end

## <a name="target-platforms-with-the-configuration-manager"></a>Platformları hedef Yapılandırma Yöneticisi

Bu **Yapılandırma Yöneticisi,** projenizi hedeflemek için hızla yeni bir platform eklemeniz için bir yol sağlar. Visual Studio'a dahil edilen platformlardan birini Visual Studio projenizin özellikleri, seçilen platform için projenizi derlemek üzere değiştirilir.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Projeyi 64 bit platformu hedefle olacak şekilde yapılandırmak için

1. Menü çubuğunda Derleme ve **oluşturma'Yapılandırma Yöneticisi.**  >  

2. Etkin **çözüm platformu listesinde,** çözümün hedeflemesi için bir 64 bit platform seçin ve ardından Kapat **düğmesini** seçin.

    1. Istediğiniz platform Etkin çözüm platformu listesinde görünmüyorsa **Yeni'yi** **seçin.**

         Yeni **Çözüm Platformu iletişim** kutusu görüntülenir.

    2. Yeni **platform yazın veya seçin listesinde** **x64'ü seçin.**

        > [!NOTE]
        > Yapılandırmanıza yeni bir ad sağlarsanız, doğru platformu hedeflemek için **Project Tasarımcısı'nda** ayarları değiştirmeniz gerekebilir.

    3. Geçerli bir platform yapılandırmasından ayarları kopyalamak için bunu seçin ve ardından Tamam **düğmesini** seçin.

Çözümünüzde 64 bit platformu hedef alan tüm projelerin özellikleri güncelleştirilir ve projenin sonraki derlemesi 64 bit platformlar için iyileştirilmiş olur.

> [!NOTE]
> **Win32** platform adı C++ projeleri için kullanılır ve **x86 anlamına gelir.** Visual Studio hem proje düzeyi platformları hem de çözüm düzeyi platformları göz önünde bulundurarak proje platformları dile özgü proje sistemlerinden gelir. C++ projeleri **Win32** ve **x64 kullanır,** ancak çözüm platformları **x86** ve **x64 kullanır.** Çözüm yapılandırması **olarak x86'Visual Studio** C++ projeleri için **Win32** platformunu seçer. Hem proje düzeyi platform hem de çözüm düzeyi platform ayarlarını görmek için, Yapılandırma Yöneticisi'i **açın** ve iki platform ayarlarını not edin. Çözüm düzeyinde platform Etkin çözüm  platformu açılan listesinde, tabloda ise her projenin proje düzeyi platformu gösterilir.
> ![Çözüm platformu ve proje platformunu gösteren ekran görüntüsü](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Project Designer'da hedef platformlar

Project **Tasarımcısı ayrıca** projeniz ile farklı platformları hedeflemek için bir yol sağlar. Yeni Çözüm Platformu iletişim kutusundaki listede yer  alan platformlardan birini seçmek çözümünüz için uygunsa özel bir yapılandırma adı oluşturabilir ve **Project Designer'daki** ayarları doğru platformu hedeflemek için değiştirebilirsiniz.

Bu görevi gerçekleştirmek, kullanmakta olduğu programlama diline göre değişiklik gösterir. Daha fazla bilgi için aşağıdaki bağlantılara bakın:

- Daha Visual Basic için bkz. [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- C# projeleri için [bkz. Derleme sayfası, Project Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

- C++/CLI projeleri için bkz. [/clr (Ortak Dil Çalışma Zamanı derlemesi)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Proje dosyasını el ile düzenleme

Bazen, bazı özel yapılandırmalar için proje dosyasını el ile düzenlemeniz gerekir. Aşağıdaki örnekte olduğu gibi iki farklı platform için farklı bir başvuru gibi IDE'de belirtileemeyen koşullarınız olması buna örnek olarak gösterilebilir.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Örnek: x86 ve x64 derlemelerine ve URL'lerine başvuru

Hem x86 hem de x64 sürümlerine sahip bir .NET derlemeye veya DLL'ye sahip olabilirsiniz. Projenizi bu başvuruları kullanmak üzere ayarlamak için, önce başvuru ekleyin, sonra proje dosyasını açın ve hem yapılandırmaya hem de hedef platforma başvuran bir koşula sahip olacak şekilde `ItemGroup` düzenleyin.  Örneğin, başvururken ikili dosyanın ClassLibrary1 olduğunu ve Hata Ayıklama ve Yayın yapılandırmalarının yanı sıra x86 ve x64 sürümleri için farklı yollar olduğunu varsayalım.  Ardından, aşağıdaki `ItemGroup` gibi tüm ayar birleşimleriyle birlikte dört öğe kullanın:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> 2017 Visual Studio de proje dosyasını düzenlemeden önce projeyi kaldırmanız gerekir. Projeyi kaldırma için proje düğümüne sağ tıklayın ve Projeyi **kaldır'ı seçin.** Düzenleme tamam olduğunda, proje düğümüne sağ tıklar ve Projeyi yeniden yükle'ye tıklayarak değişikliklerinizi kaydedin **ve projeyi yeniden yükleyin.**
::: moniker-end

Proje dosyası hakkında daha fazla bilgi için [bkz. MSBuild proje dosyası şema başvurusu.](../msbuild/msbuild-project-file-schema-reference.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme platformlarını anlama](../ide/understanding-build-platforms.md)
- [/platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64 bit uygulamalar](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64 Bit desteği](../ide/visual-studio-ide-64-bit-support.md)
- [Proje dosyasını anlama](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
