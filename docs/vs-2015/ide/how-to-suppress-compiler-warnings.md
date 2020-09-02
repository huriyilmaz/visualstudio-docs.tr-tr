---
title: 'Nasıl yapılır: derleyici uyarılarını gizleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeb404c479edec5dec89f28e80584d435f5c370a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670652"
---
# <a name="how-to-suppress-compiler-warnings"></a>Nasıl yapılır: Derleyici Uyarılarını Gizleme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir yapı günlüğünü, içermesini istemediğiniz bir veya daha fazla derleyici uyarısı türü belirterek declutter yapabilirsiniz. Örneğin, derleme günlüğü ayrıntı düzeyini normal, ayrıntılı veya tanılama olarak ayarladığınızda otomatik olarak oluşturulan bilgilerin tümünü gözden geçirmek için bu tekniği kullanabilirsiniz. Ayrıntı düzeyi hakkında daha fazla bilgi için bkz. [nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md).

### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Visual C# veya F için belirli uyarıları gizlemek için\#

1. **Çözüm Gezgini**içinde, uyarılarını bastırmak istediğiniz projeyi seçin.

2. Menü çubuğunda **Görünüm**, **Özellik sayfaları**' nı seçin.

3. **Yapı** sayfasını seçin.

4. **Uyarıları bastır** kutusunda, gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin ve sonra çözümü yeniden derleyin.

### <a name="to-suppress-specific-warnings-for-visual-c"></a>Visual C++ için belirli uyarıları gizlemek için

1. **Çözüm Gezgini**, içinde uyarıları bastırmak istediğiniz proje veya kaynak dosyasını seçin.

2. Menü çubuğunda **Görünüm**, **Özellik sayfaları**' nı seçin.

3. **Yapılandırma özellikleri** kategorisini seçin, **C/C++** kategorisini seçin ve ardından **Gelişmiş** sayfasını seçin.

4. Aşağıdaki adımlardan birini uygulayın:

    - **Belirli uyarıları devre dışı bırak** kutusunda, gizlemek istediğiniz uyarıların hata kodlarını noktalı virgülle ayırarak belirtin.

    - **Belirli uyarıları devre dışı bırak** kutusunda, daha fazla seçenek göstermek için **Düzenle** ' yi seçin.

5. **Tamam** düğmesini seçin ve çözümü yeniden derleyin.

## <a name="suppressing-warnings-for-visual-basic"></a>Visual Basic uyarılarını gizleme

Projenin. vbproj dosyasını düzenleyerek Visual Basic için belirli derleyici uyarılarını gizleyebilirsiniz. Ayrıca, uyarıları kategoriye göre gizlemek için [derleme sayfası, proje Tasarımcısı ' nı](../ide/reference/compile-page-project-designer-visual-basic.md) da kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).

#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic için belirli uyarıları gizlemek için

1. **Çözüm Gezgini**içinde, uyarılarını bastırmak istediğiniz projeyi seçin.

2. Menü çubuğunda **Proje**, **Projeyi Kaldır**' ı seçin.

3. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından_ProjectName_**. vbproj**öğesini **Düzenle**' yi seçin.

    Proje dosyası kod düzenleyicisinde açılır.

4. `<NoWarn></NoWarn>`Oluşturmakta olduğunuz yapı yapılandırmasındaki öğeyi bulun.

    Aşağıdaki örnek, `<NoWarn></NoWarn>` bir x86 platformunda hata ayıklama derleme yapılandırması için öğeyi kalın metinle gösterir:

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
       <NoWarn></NoWarn>
       <WarningLevel>1</WarningLevel>
     </PropertyGroup>
   ```

5. Öğenin değeri olarak bir veya daha fazla uyarı numarası ekleyin `<NoWarn>` . Birden çok uyarı numarası belirtirseniz, aşağıdaki örnekte gösterildiği gibi bunları virgülle ayırın.

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

6. Değişiklikleri. vbproj dosyasına kaydedin.

7. Menü çubuğunda **Proje**, **projeyi yeniden yükle**' yi seçin.

8. Menü çubuğunda **Oluştur**, **çözümü yeniden derle**öğesini seçin.

    **Çıktı** penceresi artık belirttiğiniz uyarıları göstermez.

   Daha fazla bilgi için bkz. [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).

## <a name="see-also"></a>Ayrıca Bkz.

- [İzlenecek yol: Uygulama Oluşturma](../ide/walkthrough-building-an-application.md)
- [Nasıl yapılır: Derleme Günlüğü Dosyalarını Görüntüleme, Kaydetme ve Yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme ve Oluşturma](../ide/compiling-and-building-in-visual-studio.md)
