---
title: 'Nasıl yapilir: Projeleri hedef platformlara yapılandırma'
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
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
ms.openlocfilehash: 9cbe4bc3f982ae18b9f85fe8bf5c21495c98beee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112545"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Nasıl yapilir: Projeleri hedef platformlara yapılandırma

Visual Studio, uygulamalarınızı 64 bit platformlar da dahil olmak üzere farklı platformları hedeflayacak şekilde ayarlamanızı sağlar. Visual Studio'da 64 bit platform desteği hakkında daha fazla bilgi için [64 bit uygulamalara](/dotnet/framework/64-bit-apps)bakın.

## <a name="target-platforms-with-the-configuration-manager"></a>Configuration Manager ile hedef platformlar

**Configuration Manager,** projenizle hedefe hızlı bir şekilde yeni bir platform eklemeniz için bir yol sağlar. Visual Studio ile birlikte verilen platformlardan birini seçerseniz, projenizin özellikleri, projenizi seçili platform için oluşturmak üzere değiştirilir.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Bir projeyi 64 bit platform hedeflenebilmek için yapılandırmak için

1. Menü çubuğunda**Yapı Yapılandırma Yöneticisi'ni** **seçin.** > 

2. Etkin **çözüm platformu** listesinde, çözüm için hedef için 64 bit lik bir platform seçin ve ardından **Kapat** düğmesini seçin.

    1. İstediğiniz platform **Etkin çözüm platformu** listesinde görünmüyorsa, **Yeni'yi**seçin.

         **Yeni Çözüm Platformu** iletişim kutusu görüntülenir.

    2. Türü veya yeni platform listesini **seçin,** **x64**seçin.

        > [!NOTE]
        > Yapılandırmanıza yeni bir ad verirseniz, doğru platformu hedeflemek için **Proje Tasarımcısı'ndaki** ayarları değiştirmeniz gerekebilir.

    3. Ayarları geçerli bir platform yapılandırmasından kopyalamak istiyorsanız, bunu seçin ve ardından **Tamam** düğmesini seçin.

64 bit platformu hedefleyen tüm projelerin özellikleri güncelleştirilir ve projenin bir sonraki yapısı 64 bit platformlar için optimize edilir.

## <a name="target-platforms-in-the-project-designer"></a>Proje Tasarımcısı'nda hedef platformlar

**Proje Tasarımcısı,** projenizle farklı platformları hedeflemenin de bir yolunu sağlar. **Yeni Çözüm Platformu** iletişim kutusunda ki listede yer alan platformlardan birini seçmek çözümünüz için işe yaramazsa, özel bir yapılandırma adı oluşturabilir ve doğru platformu hedeflemek için Project **Designer'daki** ayarları değiştirebilirsiniz.

Bu görevi gerçekleştirmek, kullanmakta olduğunuz programlama diline göre değişir. Daha fazla bilgi için aşağıdaki bağlantılara bakın:

- Projeler [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] için bkz: [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

- Projeler [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] için Yapı [sayfasına, Proje Tasarımcısına (C#)](../ide/reference/build-page-project-designer-csharp.md)bakın.

- Projeler [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] için bkz: [/clr (Ortak Dil Çalışma Zamanı derlemesi).](/cpp/build/reference/clr-common-language-runtime-compilation)

## <a name="manually-editing-the-project-file"></a>Proje dosyasını el ile düzenleme

Bazen, bazı özel yapılandırma için proje dosyasını el ile düzenlemeniz gerekir. Aşağıdaki örnekte olduğu gibi, iki farklı platform için farklı bir başvuru gibi IDE'de belirtilemeyen koşullar varsa, buna bir örnektir.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>Örnek: X86 ve x64 montajları ve DL'lere başvurma

Hem x86 hem de x64 sürümleri olan bir .NET derlemeniz veya DLL'niz olabilir. Projenizi bu başvuruları kullanacak şekilde ayarlamak için önce başvuruyu ekleyin ve ardından proje `ItemGroup` dosyasını açın ve hem yapılandırmaya hem de hedef platforma başvuran bir koşul eklemek için onu düzenlemeyi sağlayın.  Örneğin, başvurduğunuz ikilinin ClassLibrary1 olduğunu ve Hata Ayıklama ve Sürüm yapılandırmalarının yanı sıra x86 ve x64 sürümleri için farklı yollar olduğunu varsayalım.  Ardından, aşağıdaki `ItemGroup` gibi tüm ayar kombinasyonlarını içeren dört öğe kullanın:

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
> Visual Studio 2017'de, proje dosyasını düzenlemesi için önce projeyi boşaltmanız gerekir. Projeyi boşaltmak için proje düğümüne sağ tıklayın ve **Projeyi Boşalt'ı**seçin. Düzenleme yapıldığında, değişikliklerinizi kaydedin ve proje düğümüne sağ tıklayarak ve **Projeyi Yeniden Yükle'yi**seçerek projeyi yeniden yükleyin.
::: moniker-end

Proje dosyası hakkında daha fazla bilgi için [MSBuild proje dosyası şeması başvurusuna](../msbuild/msbuild-project-file-schema-reference.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme platformlarını anlama](../ide/understanding-build-platforms.md)
- [/platform (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64 bit uygulamalar](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64-Bit desteği](../ide/visual-studio-ide-64-bit-support.md)
- [Proje dosyasını anlama](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
