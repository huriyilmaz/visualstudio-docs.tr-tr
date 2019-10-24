---
title: Projeler ve NuGet paketleri için derleyici uyarılarını gösterme
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aec3dfb45471a3349e14419671ef1fb3b5e05db5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747954"
---
# <a name="how-to-suppress-compiler-warnings"></a>Nasıl yapılır: derleyici uyarılarını gösterme

Bir veya daha fazla derleyici uyarısına filtre uygulayarak bir yapı günlüğü declutter yapabilirsiniz. Örneğin, derleme günlüğü ayrıntı düzeyini **normal**, **ayrıntılı**veya **Tanılama**olarak ayarladığınızda oluşturulan çıktının yalnızca bir kısmını gözden geçirmek isteyebilirsiniz. Ayrıntı düzeyi hakkında daha fazla bilgi için bkz. [nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Görsel C# veya F \# için belirli uyarıları gösterme

C# Ve F# projeleri için belirli uyarıları bastırmak üzere **derleme** özelliği sayfasını kullanın.

1. **Çözüm Gezgini**içinde, uyarılarını bastırmak istediğiniz projeyi seçin.

1. Menü çubuğunda **görünüm**  > **Özellik sayfaları**' nı seçin.

1. **Yapı** sayfasını seçin.

1. **Uyarıları bastır** kutusunda, gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin.

1. Çözümü yeniden derleyin.

## <a name="suppress-specific-warnings-for-c"></a>İçin belirli uyarıları göstermeC++

Projelere yönelik C++ belirli uyarıları bastırmak Için **yapılandırma özellikleri** özellik sayfasını kullanın.

1. **Çözüm Gezgini**, içinde uyarıları bastırmak istediğiniz proje veya kaynak dosyasını seçin.

1. Menü çubuğunda **görünüm**  > **Özellik sayfaları**' nı seçin.

1. **Yapılandırma özellikleri** kategorisini seçin, **C/C++**  kategorisini seçin ve ardından **Gelişmiş** sayfasını seçin.

1. Aşağıdaki adımlardan birini uygulayın:

    - **Belirli uyarıları devre dışı bırak** kutusunda, gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin.

    - **Belirli uyarıları devre dışı bırak** kutusunda, daha fazla seçenek göstermek için **Düzenle** ' yi seçin.

1. **Tamam** düğmesini seçin ve çözümü yeniden derleyin.

## <a name="suppress-warnings-for-visual-basic"></a>Visual Basic uyarılarını gösterme

Projenin *. vbproj* dosyasını düzenleyerek Visual Basic için belirli derleyici uyarılarını gizleyebilirsiniz. Uyarıları *kategoriye*göre gizlemek için [derleme özellik sayfasını](../ide/reference/compile-page-project-designer-visual-basic.md)kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic için belirli uyarıları gizlemek için

Bu örnekte, belirli derleyici uyarılarını gizlemek için *. vbproj* dosyasının nasıl düzenleneceği gösterilmektedir.

1. **Çözüm Gezgini**içinde, uyarılarını bastırmak istediğiniz projeyi seçin.

1. Menü çubuğunda **proje  >  projeyi** **Kaldır**' ı seçin.

1. **Çözüm Gezgini**, proje için sağ tıklama veya kısayol menüsünü açın ve ardından **Düzenle \<ProjectName >. vbproj**öğesini seçin.

    XML projesi dosyası kod düzenleyicisinde açılır.

1. Oluşturmakta olduğunuz yapı yapılandırması için `<NoWarn>` öğesini bulun ve `<NoWarn>` öğesinin değeri olarak bir veya daha fazla uyarı numarası ekleyin. Birden çok uyarı numarası belirtirseniz bunları virgülle ayırın.

     Aşağıdaki örnek, bir x86 platformunda *hata ayıklama* oluşturma yapılandırması için `<NoWarn>` öğesini gösterir ve iki derleyici uyarısı bastırılır:

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
   > .NET Core projeleri varsayılan olarak derleme yapılandırma Özellik grupları içermez. Bir .NET Core projesinde uyarıları gizlemek için, derleme yapılandırma bölümünü dosyaya el ile ekleyin. Örneğin:
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

1. Değişiklikleri *. vbproj* dosyasına kaydedin.

1. Menü çubuğunda **proje**  >  projeyi**yeniden yükle**' yi seçin.

1. Menü çubuğunda **derleme**  > **yeniden oluştur çözüm**' ü seçin.

    **Çıktı** penceresi artık belirttiğiniz uyarıları göstermez.

Daha fazla bilgi için, Visual Basic komut satırı derleyicisi için [/nowarn derleyici seçeneğine](/dotnet/visual-basic/reference/command-line-compiler/nowarn) bakın.

## <a name="suppress-warnings-for-nuget-packages"></a>NuGet paketleri için uyarıları bastır

Bazı durumlarda, tüm proje için değil tek bir NuGet paketi için NuGet derleyici uyarılarını bastırmak isteyebilirsiniz. Uyarı bir amaca hizmet eder, bu nedenle projeyi proje düzeyinde bastırmak istemezsiniz. Örneğin, NuGet uyarılarından biri paketin projenizle tamamen uyumlu olmadığını söyler. Proje düzeyinde bastırın ve daha sonra ek bir NuGet paketi eklerseniz, uyumluluk uyarısını üretmediğini hiçbir zaman bilemezsiniz.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Tek bir NuGet paketine yönelik belirli bir uyarıyı gizlemek için

1. **Çözüm Gezgini**' de, derleyici uyarılarını gizlemek istediğiniz NuGet paketini seçin.

   ![Çözüm Gezgini NuGet paketi](media/nuget-package-with-warning.png)

1. Sağ tıklama veya bağlam menüsünde **Özellikler**' i seçin.

1. Paketin özelliklerinin **nowarn** kutusunda, bu paket için bastırmak istediğiniz uyarı numarasını girin. Birden fazla uyarıyı gizlemek istiyorsanız, uyarı numaralarını ayırmak için virgül kullanın.

   ![NuGet paket özellikleri](media/nuget-properties-nowarn.png)

   Uyarı **Çözüm Gezgini** ve **hata listesi**kayboluyor.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)