---
title: 'Nasıl yapılır: projeleri hedef platformlar için yapılandırma'
ms.date: 08/16/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a58b60e23bf08fb86a8dd7bc09d760085b6ea25f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284613"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Nasıl yapılır: projeleri hedef platformlar için yapılandırma

Visual Studio, uygulamalarınızı 64 bitlik platformlar dahil farklı platformları hedefleyecek şekilde ayarlamanıza olanak sağlar. Visual Studio 'da 64 bit platform desteği hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](/dotnet/framework/64-bit-apps).

## <a name="target-platforms-with-the-configuration-manager"></a>Configuration Manager ile hedef platformları

**Configuration Manager** , projenizde hedeflemek üzere yeni bir platform eklemek için bir yol sağlar. Visual Studio 'ya dahil olan platformlardan birini seçerseniz, projenizin özellikleri seçili platform için projenizi oluşturmak üzere değiştirilir.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Bir projeyi 64 bitlik bir platformu hedefleyecek şekilde yapılandırmak için

1. Menü çubuğunda Configuration Manager **Oluştur**' u seçin  >  **Configuration Manager**.

2. **Etkin çözüm platformu** listesinde, çözümün hedeflenecek 64 bitlik bir platform seçin ve sonra **Kapat** düğmesini seçin.

    1. İstediğiniz Platform **etkin çözüm platformu** listesinde görünmüyorsa, **Yeni**' yi seçin.

         **Yeni çözüm platformu** iletişim kutusu görüntülenir.

    2. **Yazın veya yeni platform listesini seçin** , **x64**öğesini seçin.

        > [!NOTE]
        > Yapılandırmanıza yeni bir ad verirseniz, **Proje tasarımcısında** ayarları doğru platformu hedefleyecek şekilde değiştirmeniz gerekebilir.

    3. Ayarları geçerli platform yapılandırmasından kopyalamak istiyorsanız, seçin ve sonra **Tamam** düğmesini seçin.

64 bitlik platformu hedefleyen tüm projeler için özellikler güncellenir ve projenin sonraki derlemesi 64 bit platformlar için iyileştirilir.

> [!NOTE]
> **Win32** platform adı C++ projeleri için kullanılır ve **x86**anlamına gelir. Visual Studio hem proje düzeyi platformları hem de çözüm düzeyi platformları ve proje platformları dile özgü proje sistemlerinden gelir. C++ projeleri **Win32** ve **x64**kullanır, ancak çözüm platformları **x86** ve **x64**kullanır. Çözüm yapılandırması olarak **x86** seçeneğini belirlediğinizde, Visual Studio, C++ projeleri için **Win32** platformunu seçer. Hem proje düzeyi platformu hem de çözüm düzeyi platform ayarlarını görmek için **Configuration Manager** açın ve iki platform ayarını aklınızda yapın. Çözüm düzeyi Platform **etkin çözüm platformu** açılan listesinde gösterilir ve tablo her proje için proje düzeyi platformu gösterir.
> ![Çözüm platformunu ve proje platformunu gösteren ekran görüntüsü](media/project-platform-win32.png)

## <a name="target-platforms-in-the-project-designer"></a>Proje tasarımcısında hedef platformlar

**Proje Tasarımcısı** Ayrıca, projenizle farklı platformları hedeflemek için bir yol sağlar. **Yeni çözüm platformu** iletişim kutusundaki listede yer alan platformlardan birini seçmek çözümünüz için çalışmazsa, özel bir yapılandırma adı oluşturabilir ve **Proje tasarımcısında** ayarları değiştirerek doğru platformu hedefleyebilirsiniz.

Bu görevin gerçekleştirilmesi, kullanmakta olduğunuz programlama diline göre farklılık gösterir. Daha fazla bilgi için aşağıdaki bağlantılara bakın:

- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Projeler için bkz. [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Projeler için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

- [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]Projeler için bkz. [/clr (ortak dil çalışma zamanı derlemesi)](/cpp/build/reference/clr-common-language-runtime-compilation).

## <a name="manually-editing-the-project-file"></a>Proje dosyasını el ile Düzenle

Bazen, bazı özel yapılandırma için proje dosyasını el ile düzenlemeniz gerekir. Örneğin, aşağıdaki örnekte olduğu gibi, iki farklı platformda farklı bir başvuru gibi IDE 'de belirtime koşullarınız vardır.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Örnek: x86 ve x64 derlemelerine ve DLL 'Lere başvurma

Hem x86 hem de x64 sürümlerine sahip bir .NET bütünleştirilmiş kodu veya DLL 'SI olabilir. Projenizi bu başvuruları kullanacak şekilde ayarlamak için, önce başvuruyu ekleyin ve ardından proje dosyasını açın ve sonra `ItemGroup` hem yapılandırmaya hem de hedef platforma başvuran bir koşula sahip bir koşul ekleyerek düzenleyin.  Örneğin, başvurduğunuz ikilinin ClassLibrary1 olduğunu ve hata ayıklama ve sürüm yapılandırmalarının yanı sıra x86 ve x64 sürümleri için farklı yollar bulunduğunu varsayalım.  Ardından, `ItemGroup` aşağıdaki gibi, tüm ayar birleşimleriyle dört öğe kullanın:

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
> Visual Studio 2017 ' de proje dosyasını düzenlemeden önce projeyi kaldırmanız gerekir. Projeyi kaldırmak için proje düğümüne sağ tıklayın ve **Projeyi Kaldır**' ı seçin. Düzenlemeler tamamlandığında, değişiklikleri kaydedin ve proje düğümüne sağ tıklayıp **projeyi yeniden yükle**' yi seçerek projeyi yeniden yükleyin.
::: moniker-end

Proje dosyası hakkında daha fazla bilgi için bkz. [MSBuild proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme platformlarını anlama](../ide/understanding-build-platforms.md)
- [/Platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64 bitlik uygulamalar](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64 bit desteği](../ide/visual-studio-ide-64-bit-support.md)
- [Proje dosyasını anlama](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
