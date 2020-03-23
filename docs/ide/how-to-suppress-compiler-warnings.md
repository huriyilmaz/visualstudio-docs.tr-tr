---
title: Projeler ve NuGet paketleri için derleyici uyarılarını bastırma
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b604f6a1392353d304897a233b74c0d81fc258df
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114500"
---
# <a name="how-to-suppress-compiler-warnings"></a>Nasıl yapılsın: Derleyici uyarılarını bastırma

Bir veya daha fazla türderuyarıyı filtreleyerek yapı günlüğünü bozabilirsiniz. Örneğin, yapı günlüğü ayrıntılılığını **Normal,** **Ayrıntılı**veya **Tanılama**olarak ayarladığınızda oluşturulan çıktının yalnızca bir kısmını gözden geçirmek isteyebilirsiniz. Ayrıntılı bilgi için [bkz: Yapı günlüğü dosyalarını görüntülemek, kaydetmek ve yapılandırmak.](../ide/how-to-view-save-and-configure-build-log-files.md)

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Visual C# veya F için belirli uyarıları bastırma\#

C# ve F# projeleri için belirli uyarıları bastırmak için **Yapı** özelliği sayfasını kullanın.

1. **Çözüm Gezgini'nde,** uyarıları bastırmak istediğiniz projeyi seçin.

1. Menü çubuğunda**Özellik Sayfalarını** **Görüntüle'yi** > seçin.

1. **Yapı** sayfasını seçin.

1. Uyarıları **Bastır** kutusunda, bastırmak istediğiniz uyarıların hata kodlarını belirtin, yarım nokta nokta ile ayrılmıştır.

1. Çözümü yeniden derleyin.

## <a name="suppress-specific-warnings-for-c"></a>C++ için belirli uyarıları bastırma

C++ projeleri için belirli uyarıları bastırmak için **Configuration Properties** özellik sayfasını kullanın.

1. **Çözüm Gezgini'nde,** uyarıları bastırmak istediğiniz projeyi veya kaynak dosyayı seçin.

1. Menü çubuğunda**Özellik Sayfalarını** **Görüntüle'yi** > seçin.

1. Yapılandırma **Özellikleri** kategorisini seçin, **C/C++** kategorisini seçin ve ardından **Gelişmiş** sayfayı seçin.

1. Aşağıdaki adımlardan birini uygulayın:

    - Belirli **Uyarıları Devre Dışı Al** kutusunda, bastırmak istediğiniz uyarıların hata kodlarını belirtin, bir yarı nokta nokta ile ayrılmıştır.

    - Belirli **Uyarıları Devre Dışı Aç** kutusunda, daha fazla seçenek görüntülemek için **Edit'i** seçin.

1. **Tamam** düğmesini seçin ve ardından çözümü yeniden oluşturun.

## <a name="suppress-warnings-for-visual-basic"></a>Visual Basic için uyarıları bastırma

Proje için *.vbproj* dosyasını düzenleyerek Visual Basic için belirli derleyici uyarılarını gizleyebilirsiniz. Uyarıları *kategoriye*göre bastırmak [için, Derle özelliği sayfasını](../ide/reference/compile-page-project-designer-visual-basic.md)kullanabilirsiniz. Daha fazla bilgi için [Visual Basic'teki uyarıları yapılandır' a](../ide/configuring-warnings-in-visual-basic.md)bakın.

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic için belirli uyarıları bastırmak için

Bu örnek, belirli derleyici uyarılarını bastırmak için *.vbproj* dosyasını nasıl yapılandırabileceğinizi gösterir.

1. **Çözüm Gezgini'nde,** uyarıları bastırmak istediğiniz projeyi seçin.

1. Menü çubuğunda **Project** > **Unload Project'i**seçin.

1. **Çözüm Gezgini'nde,** proje için sağ tıklatma veya kısayol menüsünü açın ve ardından **ProjectName>.vbproj'u edit'i \<** seçin.

    Kod düzenleyicisinde XML proje dosyası açılır.

1. Birlikte `<NoWarn>` oluşturduğunuz yapı yapılandırması için öğeyi bulun ve `<NoWarn>` öğenin değeri olarak bir veya daha fazla uyarı numarası ekleyin. Birden çok uyarı numarası belirtirseniz, bunları virgülle ayırın.

     Aşağıdaki örnek, `<NoWarn>` bir x86 platformunda *Hata Ayıklama* yapı yapılandırması öğesini gösterir ve iki derleyici uyarısı bastırılır:

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
   > .NET Core projeleri varsayılan olarak yapı yapılandırma özellik grupları içermez. .NET Core projesindeki uyarıları bastırmak için yapı yapılandırma bölümünü dosyaya el ile ekleyin. Örnek:
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

1. Değişiklikleri *.vbproj* dosyasına kaydedin.

1. Menü çubuğunda **Project** > **Reload Project'i**seçin.

1. Menü çubuğunda, **Çözüm** > **Oluştur'u**seçin.

    **Çıktı** penceresi artık belirttiğiniz uyarıları göstermez.

Daha fazla bilgi için Visual Basic komut satırı derleyicisi için [/nowarn derleyici seçeneğine](/dotnet/visual-basic/reference/command-line-compiler/nowarn) bakın.

## <a name="suppress-warnings-for-nuget-packages"></a>NuGet paketleri için uyarıları bastırma

Bazı durumlarda, tüm proje yerine tek bir NuGet paketi için NuGet derleyici uyarılarını bastırmak isteyebilirsiniz. Uyarı bir amaca hizmet eder, bu nedenle proje düzeyinde bastırmak istemezsin. Örneğin, NuGet uyarılarından biri paketin projenizle tam olarak uyumlu olmayabileceğini söyler. Proje düzeyinde bastırır ve daha sonra ek bir NuGet paketi eklerseniz, uyumluluk uyarısını yapıp yaptığını asla bilemezsiniz.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Tek bir NuGet paketi için belirli bir uyarıyı bastırmak için

1. **Solution**Explorer'da, derleyici uyarılarını bastırmak istediğiniz NuGet paketini seçin.

   ![Solution Explorer'da NuGet paketi](media/nuget-package-with-warning.png)

1. Sağ tıklatma veya bağlam menüsünden **Özellikler'i**seçin.

1. Paketin özelliklerinin **NoWarn** kutusuna, bu paket için bastırmak istediğiniz uyarı numarasını girin. Birden fazla uyarıyı bastırmak istiyorsanız, uyarı numaralarını ayırmak için virgül kullanın.

   ![NuGet paket özellikleri](media/nuget-properties-nowarn.png)

   Uyarı, Çözüm **Gezgini'nden** ve **Hata Listesinden**kaybolur.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Nasıl yapılsın: Yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
