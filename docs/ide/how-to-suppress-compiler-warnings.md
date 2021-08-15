---
title: Projeler ve proje paketleri için uyarıları NuGet gizleme
description: Bir veya daha fazla Visual Studio uyarılarını filtreleerek derleme günlüğünü azalan şekilde filtrelemek için Visual Studio'i nasıl kullanabileceğiniz hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55c3a0b0d5d7bd41b564467936252f3c0a3cafc3c40e2549b673c4f8046136fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121272258"
---
# <a name="how-to-suppress-compiler-warnings"></a>Nasıllı: Derleyici uyarılarını gizleme

Bir veya daha fazla tür derleyici uyarılarını filtreleerek derleme günlüğünün düşüşe neden olabilir. Örneğin, derleme günlüğü ayrıntılılığı **Normal,** Ayrıntılı veya Tanılama olarak ayarlanırken oluşturulan çıktılardan yalnızca bir kaçını **gözden** geçirmek istiyor **olabilir.** Ayrıntılılık hakkında daha fazla bilgi için bkz. Nasıl kullanılır: Derleme günlüğü [dosyalarını görüntüleme, kaydetme ve yapılandırma.](../ide/how-to-view-save-and-configure-build-log-files.md)

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Visual C# veya F için belirli uyarıları gizleme\#

C# **ve** F# projelerine yönelik belirli uyarıları gizlemeye yönelik Derleme özelliği sayfasını kullanın.

1. Bu **Çözüm Gezgini'** içinde uyarıların gizlenmesini istediğiniz projeyi seçin.

1. Menü çubuğunda Özellik Sayfalarını **Görüntüle'yi**  >  **seçin.**

1. Derleme **sayfasını** seçin.

1. Uyarıları **bastır kutusunda,** gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin.

1. Çözümü yeniden derleyin.

## <a name="suppress-specific-warnings-for-c"></a>C++ için belirli uyarıları gizleme

C++ **projeleri için** belirli uyarıların gizlenmelerini için Yapılandırma Özellikleri özellik sayfasını kullanın.

1. Bu **Çözüm Gezgini,** uyarıların gizlenmesini istediğiniz projeyi veya kaynak dosyayı seçin.

1. Menü çubuğunda Özellik Sayfalarını **Görüntüle'yi**  >  **seçin.**

1. Yapılandırma **Özellikleri kategorisini** seçin, **C/C++ kategorisini** ve ardından Gelişmiş **sayfasını** seçin.

1. Aşağıdaki adımlardan birini uygulayın:

    - Belirli **Uyarıları Devre Dışı** Bırak kutusunda, gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin.

    - Daha fazla **seçenek görüntülemek için Belirli** Uyarıları Devre Dışı Bırak **kutusunda** Düzenle'yi seçin.

1. Tamam düğmesini **seçin** ve çözümü yeniden üretin.

## <a name="suppress-warnings-for-visual-basic"></a>Uyarı uyarılarını Visual Basic

Projenin *.vbproj* dosyasını düzenleyerek Visual Basic için belirli derleyici uyarılarını gizleyebilirsiniz. Uyarıları kategorisine göre *gizlemek* için Derleme özellik [sayfasını kullanabilirsiniz.](../ide/reference/compile-page-project-designer-visual-basic.md) Daha fazla bilgi için [bkz. Visual Basic.](../ide/configuring-warnings-in-visual-basic.md)

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Belirli uyarı uyarılarını Visual Basic

Bu örnekte, belirli derleyici uyarılarını bastırmak *için .vbproj* dosyasının nasıl düzenleneceğini gösterir.

1. Bu **Çözüm Gezgini'** içinde uyarıların gizlenmesini istediğiniz projeyi seçin.

1. Menü çubuğunda, Yüklemeden **kaldır'Project**  >  **seçin Project.**

1. Bu **Çözüm Gezgini** proje için sağ tıklayın veya kısayol menüsünü açın ve **ardından Düzenle \<ProjectName> .vbproj öğesini seçin.**

    XML proje dosyası kod düzenleyicisinde açılır.

1. Oluşturmakta olduğunu derleme yapılandırması için öğesini bulun ve öğenin değeri olarak `<NoWarn>` bir veya daha fazla uyarı numarası `<NoWarn>` ekleyin. Birden çok uyarı numarası belirtirsiniz, bunları virgülle ayırabilirsiniz.

     Aşağıdaki örnek, bir `<NoWarn>` x86 platformunda *hata* ayıklama derleme yapılandırması için iki derleyici uyarısı gizlenen öğesini gösterir:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > .NET Core projeleri varsayılan olarak derleme yapılandırma özellik gruplarına sahip değildir. Bir .NET Core projesinde uyarıları bastırmak için derleme yapılandırması bölümünü dosyaya el ile ekleyin. Örnek:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. *Değişiklikleri .vbproj dosyasına* kaydedin.

1. Menü çubuğunda Yeniden Yükle'yi  >  **Project'yi Project.**

1. Menü çubuğunda Çözümü Yeniden **Derleme'yi**  >  **seçin.**

    Çıkış  penceresinde artık belirttiğiniz uyarılar gösterilir.

Daha fazla bilgi için, komut satırı derleyicisi için [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) Visual Basic seçeneğine bakın.

## <a name="suppress-warnings-for-nuget-packages"></a>Paketlerde uyarıları NuGet gizleme

Bazı durumlarda, bir projenin tamamı NuGet tek bir NuGet için derleyici uyarılarını gizlemeniz iyi olabilir. Uyarı bir amaca hizmet ettiği için bunu proje düzeyinde gizlemeniz gerekmemektedir. Örneğin, uygulama uyarılarından NuGet paketin projeniz ile tam olarak uyumlu olmadığını söyler. Bunu proje düzeyinde gizlemeniz ve daha sonra ek bir NuGet paketi eklemeniz, uyumluluk uyarısının üret olup oluğunu asla bilemeyebilirsiniz.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Tek bir paket için belirli bir uyarıyı NuGet için

1. Bu **Çözüm Gezgini,** derleyici uyarılarını NuGet istediğiniz paket paketini seçin.

   ![NuGet paketi Çözüm Gezgini](media/nuget-package-with-warning.png)

1. Sağ tıklama veya bağlam menüsünde Özellikler'i **seçin.**

1. Paketin **özelliklerinin NoWarn** kutusuna, bu paket için gizlemek istediğiniz uyarı numarasını girin. Birden fazla uyarıyı gizlemeyi istemiyorsanız uyarı numaralarını ayırmak için virgül kullanın.

   ![NuGet paket özellikleri](media/nuget-properties-nowarn.png)

   Uyarı, Çözüm Gezgini  **listesinden kaybolur.**

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Nasıl kullanılır: Derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
