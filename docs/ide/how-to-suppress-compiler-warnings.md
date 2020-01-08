---
title: Projeler ve NuGet paketleri için Derleyici uyarılarını gizleme
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbcef86187ad03545066f3c595d00b56f83be5c5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591430"
---
# <a name="how-to-suppress-compiler-warnings"></a>Nasıl yapılır: Derleyici uyarılarını gizleme

Derleyici uyarılarını bir veya daha fazla tür filtreleyerek yapı günlüğüne declutter. Örneğin, derleme günlük ayrıntı düzeyini ayarlamak, oluşturulan çıktıyı yalnızca bir bölümünü incelemek isteyebilirsiniz **Normal**, **ayrıntılı**, veya **tanılama**. Ayrıntı düzeyi hakkında daha fazla bilgi için bkz. [nasıl yapılır: görüntüleme, kaydetme ve yapılandırma derleme günlüğü dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Görsel C# veya F\# için belirli uyarıları gösterme

Kullanım **derleme** için belirli uyarıları bastırmak için özellik sayfası C# ve F# projeleri.

1. İçinde **Çözüm Gezgini**, uyarıları bastırmak istediğiniz projeyi seçin.

1. Menü çubuğunda, **görünümü** > **özellik sayfaları**.

1. Seçin **derleme** sayfası.

1. İçinde **uyarıları bastırma** kutusunda, gizlemek istediğiniz uyarıları hata kodlarının noktalı virgülle ayırarak belirtin.

1. Çözümü yeniden derleyin.

## <a name="suppress-specific-warnings-for-c"></a>İçin belirli uyarıları göstermeC++

Kullanım **yapılandırma özellikleri** C++ projeleri için belirli uyarıları bastırmak için özellik sayfası.

1. İçinde **Çözüm Gezgini**, projeyi seçin veya uyarıları bastırmak istediğiniz dosya kaynağı.

1. Menü çubuğunda, **görünümü** > **özellik sayfaları**.

1. Seçin **yapılandırma özellikleri** kategorisi seçin **C/C++** kategori seçip **Gelişmiş** sayfası.

1. Aşağıdaki adımlardan birini gerçekleştirin:

    - İçinde **belirli uyarıları devre dışı** kutusunda, gizlemek istediğiniz uyarıları hata kodlarının noktalı virgülle ayrılmış belirtin.

    - İçinde **belirli uyarıları devre dışı** kutusunda **Düzenle** daha fazla seçenek görüntülenecek.

1. Seçin **Tamam** düğmesini ve ardından çözümü yeniden oluşturun.

## <a name="suppress-warnings-for-visual-basic"></a>Visual Basic için uyarıları bastırma

Visual Basic için belirli bir derleyici uyarılarını düzenleyerek gizleyebilirsiniz *.vbproj* proje dosyası. Tarafından uyarıları bastırmak için *kategori*, kullanabileceğiniz [derleme özellik sayfasında](../ide/reference/compile-page-project-designer-visual-basic.md). Daha fazla bilgi için [Visual Basic ile uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic için belirli uyarıları bastırmak için

Bu örnek nasıl düzenleneceğini gösterir *.vbproj* belirli derleyici uyarıları bastırmak için dosya.

1. İçinde **Çözüm Gezgini**, uyarıları bastırmak istediğiniz projeyi seçin.

1. Menü çubuğunda, **proje** > **projeyi**.

1. **Çözüm Gezgini**, proje için sağ tıklama veya kısayol menüsünü açın ve sonra **\<ProjectName >. vbproj öğesini Düzenle**' yi seçin.

    XML proje dosyasını Kod düzenleyicisinde açılır.

1. Bulun `<NoWarn>` öğesi için yapı yapılandırmasını, oluşturmakta olduğumuz ve değeri olarak bir veya daha fazla uyarı numaralarını ekleme `<NoWarn>` öğesi. Birden çok uyarı numaralarını belirtirseniz, bunların virgülle ayırın.

     Aşağıdaki örnekte gösterildiği `<NoWarn>` öğesi için *hata ayıklama* derleme yapılandırması bir x86 platformuyla gizlenen iki derleyici uyarıları:

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
   > .NET core projeleri derleme Yapılandırma özelliği grupları varsayılan olarak içermez. .NET Core projesinde uyarıları bastırmak için dosyaya derleme yapılandırma bölümü el ile ekleyin. Örneğin:
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

1. Değişiklikleri kaydetmek *.vbproj* dosya.

1. Menü çubuğunda, **proje** > **projeyi**.

1. Menü çubuğunda, **derleme** > **çözümü yeniden derle**.

    **Çıkış** penceresi artık belirtilen uyarıları gösterir.

Daha fazla bilgi için [/nowarn derleyici seçeneği](/dotnet/visual-basic/reference/command-line-compiler/nowarn) Visual Basic komut satırı derleyicisi için.

## <a name="suppress-warnings-for-nuget-packages"></a>NuGet paketleri için uyarıları bastırma

Bazı durumlarda, bir projenin tamamı için yerine tek bir NuGet paketi için NuGet Derleyici uyarılarını bastırma isteyebilirsiniz. Proje düzeyinde bastırmak istemediğiniz için uyarı bir amaca hizmet verir. Örneğin, bir NuGet uyarıları, paketi projenize ile tam olarak uyumlu olmayabilir bildirir. Proje düzeyinde gösterme ve daha sonra ek bir NuGet paketi ekleme, uyumluluk uyarısı üreten, hiçbir zaman anlarsınız.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Tek bir NuGet paketi için belirli bir uyarıyı bastırmak için

1. İçinde **Çözüm Gezgini**, istediğiniz Derleyici uyarılarını bastırmak için NuGet paketini seçin.

   ![Çözüm Gezgini'nde NuGet paketi](media/nuget-package-with-warning.png)

1. Sağ tıklayın veya bağlam menüsünü seçin **özellikleri**.

1. İçinde **NoWarn** kutusu paket özelliklerini bu paket için gizlemek istediğiniz uyarı numarasını girin. Birden fazla uyarıyı engellemek istiyorsanız, uyarı numaralarını ayırmak için virgül kullanın.

   ![NuGet paket özellikleri](media/nuget-properties-nowarn.png)

   Uyarı kaybolur **Çözüm Gezgini** ve **hata listesi**.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Uygulama oluşturma](../ide/walkthrough-building-an-application.md)
- [Nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
