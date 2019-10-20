---
title: 'Nasıl yapılır: birim testlerini .NET Framework önceki bir sürümünü hedeflemek için yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fd212eb304e6cba022b067b8b432cf00fc3f87ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660547"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Nasıl yapılır: Birim Testlerini .NET Framework'ün Önceki Sürümünü Hedefleyecek Şekilde Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Visual Studio ' de bir test projesi oluşturduğunuzda, varsayılan olarak .NET Framework en son sürümü hedef olarak ayarlanır. Ayrıca, Visual Studio 'nun önceki sürümlerinden test projelerini yükseltirseniz, .NET Framework en son sürümünü hedeflemek üzere yükseltilir. Proje özelliklerini düzenleyerek, projeyi .NET Framework önceki sürümlerine açık bir şekilde yeniden hedefleyebilirsiniz.

 .NET Framework belirli sürümlerini hedefleyen birim testi projeleri oluşturabilirsiniz. Hedeflenen sürüm 3,5 veya üzeri olmalıdır ve istemci sürümü olamaz. Visual Studio, belirli sürümleri hedefleyen birim testleri için aşağıdaki temel desteği sunar:

- Birim testi projeleri oluşturabilir ve bunları .NET Framework belirli bir sürümüne hedefleyebilirsiniz.

- Yerel makinenizde Visual Studio 'dan belirli bir .NET Framework sürümünü hedefleyen birim testlerini çalıştırabilirsiniz.

- Komut isteminden MSTest. exe ' yi kullanarak .NET Framework belirli bir sürümünü hedefleyen birim testlerini çalıştırabilirsiniz.

- Yapı aracısında bir derleme parçası olarak birim testlerini çalıştırabilirsiniz.

  **SharePoint uygulamalarını test etme**

  Yukarıda listelenen yetenekler, Visual Studio kullanarak SharePoint uygulamaları için birim testleri ve tümleştirme testleri yazmanızı de sağlar. Visual Studio kullanarak SharePoint uygulamaları geliştirmeyi [!INCLUDE[crabout](../includes/crabout-md.md)], bkz. SharePoint [çözümleri oluşturma](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [SharePoint çözümlerini derleme ve hata ayıklama](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) ve [SharePoint kodunu doğrulama ve hata ayıklama](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).

  **Sınırlamalar**

  .NET Framework önceki sürümlerini kullanmak için test projelerinizi yeniden hedeflediğinizde aşağıdaki sınırlamalar geçerlidir:

- .NET Framework 3,5 ' de, Çoklu hedefleme yalnızca birim testleri içeren test projeleri için desteklenir. .NET Framework 3,5, kodlanmış UI veya yük testi gibi başka herhangi bir test türünü desteklemez. Yeniden hedefleme, birim testi dışındaki test türleri için engellenir.

- .NET Framework önceki bir sürümünü hedefleyen testlerin yürütülmesi yalnızca varsayılan ana bilgisayar bağdaştırıcısında desteklenir. ASP.NET ana bilgisayar bağdaştırıcısında desteklenmez. ASP.NET Development Server bağlamında çalıştırılması gereken ASP.NET uygulamaları .NET Framework geçerli sürümüyle uyumlu olmalıdır.

- .NET Framework 3,5 Çoklu hedefleme desteği olan testler çalıştırdığınızda veri toplama desteği devre dışıdır. Visual Studio komut satırı araçlarını kullanarak kod kapsamını çalıştırabilirsiniz.

- .NET Framework 3,5 kullanan birim testleri uzak makinede çalıştırılamaz.

- Birim testlerini Framework 'ün önceki istemci sürümlerine hedeflenemez.

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Visual Basic birim testi projeleri için .NET Framework belirli bir sürümüne yeniden hedefleme

1. Yeni bir Visual Basic birim testi projesi oluşturun. **Dosya** menüsünde **Yeni** ' yi ve ardından **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu görüntülenir.

2. **Yüklü şablonlar**altında **Visual Basic**' ı genişletin. **Test** ' i seçin ve ardından **test projesi** şablonunu seçin.

3. **Ad** metin kutusuna Visual Basic test projeniz için bir ad yazın ve ardından **Tamam**' ı seçin.

4. Çözüm Gezgini ' de, yeni Visual Basic test projesinin kısayol menüsünden **Özellikler** ' i seçin.

     Visual Basic test projenizin özellikleri görüntülenir.

5. **Derle** sekmesinde, aşağıdaki çizimde gösterildiği gibi **Gelişmiş derleme seçenekleri** ' ni seçin.

     ![Gelişmiş derleme seçenekleri](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")

6. Hedef Framework 'ü **.NET Framework 3,5** veya sonraki bir sürümü, aşağıdaki çizimde yer alarak B çağrısında gösterildiği gibi değiştirmek için **hedef Framework (tüm yapılandırma)** açılan listesini kullanın. İstemci sürümü belirtmemelisiniz.

     ![Hedef çerçeve açılan&#45;listesi](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Visual C# Unit Test projeleri için .NET Framework belirli bir sürümüne yeniden hedefleme

1. Yeni bir görsel C# birim test projesi oluşturun. **Dosya** menüsünde **Yeni** ' yi ve ardından **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu görüntülenir.

2. **Yüklü şablonlar**altında, **görsel C#** ' i genişletin. **Test** ' i seçin ve ardından **test projesi** şablonunu seçin.

3. **Ad** metin kutusuna görsel C# test projeniz için bir ad yazın ve ardından **Tamam**' ı seçin.

4. Çözüm Gezgini ' de, yeni görsel C# test projenizin kısayol menüsünden Özellikler ' i seçin.

     Görsel C# test projenizin özellikleri görüntülenir.

5. **Uygulama** sekmesinde **hedef çerçeve** ' yi seçin ve ardından aşağı açılan listeden **.NET Framework 3,5** veya sonraki bir sürümü seçerek aşağıdaki çizimde gösterilen hedef Framework.as değiştirin. İstemci sürümü belirtmemelisiniz.

     ![Hedef çerçeve açılan&#45;listesi](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>/CLI birim testi projeleri için C++.NET Framework belirli bir sürümüne yeniden hedefleme

1. Yeni C++ bir birim testi projesi oluşturun. **Dosya** menüsünde, **Yeni** ' yi seçin ve ardından **Proje**' ye tıklayın.

     **Yeni proje** iletişim kutusu görüntülenir.

    > [!WARNING]
    > Visual C++Studio C++için .NET Framework 'ün önceki bir sürümü için/CLI birim testlerini derlemek için, Visual Studio 'nun karşılık gelen sürümünü kullanmanız gerekir. Örneğin, .NET Framework 3,5 ' i hedeflemek için [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] ve [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Service Pack 1 ' i yüklemelisiniz.

2. **Yüklü şablonlar**altında, **Visual C + +** ' yi genişletin. **Test** ' i seçin ve ardından **test projesi** şablonunu seçin.

3. **Ad** metin kutusuna görsel C++ test projeniz için bir ad yazın ve ardından **Tamam**' a tıklayın.

4. Çözüm Gezgini, yeni görsel C++ test projenizden **Projeyi Kaldır** ' ı seçin.

5. Çözüm Gezgini, yüklenmeyen görsel C++ test projesini seçin ve ardından **\<project adı Düzenle >. vcxproj**öğesini seçin.

     . Vcxproj dosyası düzenleyicide açılır.

6. @No__t_0 sürüm 3,5 ' e veya `"Globals"` etiketli `PropertyGroup` sonraki bir sürüme ayarlayın. İstemci sürümü belirtmemelisiniz:

    ```
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>

    ```

7. . Vcxproj dosyasını kaydedin ve kapatın.

8. Çözüm Gezgini ' de, yeni görsel C++ test projenizin kısayol menüsünden **projeyi yeniden yükle** ' yi seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Mevcut kod Için birim testleri oluşturma ve çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) SharePoint çözümleri [oluşturma](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [ve hata ayıklama SharePoint çözümleri](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [Gelişmiş derleyici ayarları iletişim kutusu (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
