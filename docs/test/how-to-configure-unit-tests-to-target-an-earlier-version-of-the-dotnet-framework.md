---
title: Birim testleri .NET Framework önceki sürümünü hedefleyin
description: .NET Framework belirli sürümlerini hedeflemek için birim testi projeleri oluşturmayı öğrenin. Hedeflenen sürüm 3,5 veya üzeri olmalıdır ve istemci sürümü olamaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 19c0300cf8549b01b36f911bfb287bbdc3a22f1e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123040"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Nasıl yapılır: birim testlerini .NET Framework önceki bir sürümünü hedeflemek için yapılandırma

Microsoft Visual Studio ' de bir test projesi oluşturduğunuzda, varsayılan olarak .NET Framework en son sürümü hedef olarak ayarlanır. ayrıca, önceki Visual Studio sürümlerinden test projelerini yükseltirseniz, .NET Framework en son sürümü hedefleyecek şekilde yükseltilir. Proje özelliklerini düzenleyerek, projeyi .NET Framework önceki sürümlerine açık bir şekilde yeniden hedefleyebilirsiniz.

.NET Framework belirli sürümlerini hedefleyen birim testi projeleri oluşturabilirsiniz. Hedeflenen sürüm 3,5 veya üzeri olmalıdır ve istemci sürümü olamaz. Visual Studio, belirli sürümleri hedefleyen birim testleri için aşağıdaki temel desteği sunar:

- Birim testi projeleri oluşturabilir ve bunları .NET Framework belirli bir sürümüne hedefleyebilirsiniz.

- yerel makinenizde Visual Studio .NET Framework belirli bir sürümünü hedefleyen birim testlerini çalıştırabilirsiniz.

- komut isteminden *MSTest.exe* kullanarak .NET Framework belirli bir sürümünü hedefleyen birim testlerini çalıştırabilirsiniz.

- Yapı aracısında bir derleme parçası olarak birim testlerini çalıştırabilirsiniz.

**SharePoint uygulamaları test etme**

yukarıda listelenen yetenekler, Visual Studio kullanarak SharePoint uygulamalar için birim testleri ve tümleştirme testleri yazmanızı de sağlar. Visual Studio kullanarak SharePoint uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [SharePoint çözümleri oluşturma](../sharepoint/create-sharepoint-solutions.md), [SharePoint çözümleri derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md) ve [SharePoint kodunu doğrulama ve hata ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Sınırlamalar**

.NET Framework önceki sürümlerini kullanmak için test projelerinizi yeniden hedeflediğinizde aşağıdaki sınırlamalar geçerlidir:

- .NET Framework 3,5 ' de, çoklu hedefleme yalnızca birim testleri içeren test projeleri için desteklenir. .NET Framework 3,5, kodlanmış uı veya yük testi gibi başka herhangi bir test türünü desteklemez. Yeniden hedefleme, birim testi dışındaki test türleri için engellenir.

- .NET Framework önceki bir sürümünü hedefleyen testlerin yürütülmesi yalnızca varsayılan ana bilgisayar bağdaştırıcısında desteklenir. ASP.NET ana bilgisayar bağdaştırıcısında desteklenmez. ASP.NET geliştirme sunucusu bağlamında çalıştırılması gereken ASP.NET uygulamalar, .NET Framework güncel sürümüyle uyumlu olmalıdır.

- .NET Framework 3,5 çoklu hedefleme desteği olan testler çalıştırdığınızda veri toplama desteği devre dışıdır. Visual Studio komut satırı araçlarını kullanarak kod kapsamını çalıştırabilirsiniz.

- .NET Framework 3,5 kullanan birim testleri uzak makinede çalıştırılamaz.

- Birim testlerini Framework 'ün önceki istemci sürümlerine hedeflenemez.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Visual Basic birim testi projeleri için yeniden hedefleme

1. yeni bir Visual Basic **birim testi Project** projesi oluşturun.

2. **Çözüm Gezgini**' de, yeni Visual Basic test projesinin sağ tıklama menüsünden **özellikler** ' i seçin.

     Visual Basic test projenizin özellikleri görüntülenir.

3. **Derle** sekmesinde, aşağıdaki çizimde gösterildiği gibi **Gelişmiş derleme seçenekleri** ' ni seçin.

     ![Gelişmiş derleme seçenekleri](../test/media/howtoconfigureunittest35frameworka.png)

4. hedef framework 'ü **.NET Framework 3,5** veya sonraki bir sürümü, aşağıdaki çizimde yer alarak B çağrısında gösterildiği gibi değiştirmek için **hedef framework (tüm yapılandırma)** açılan listesini kullanın. İstemci sürümü belirtmemelisiniz.

     ![gelişmiş derleyici Ayarlar iletişim kutusunun ekran görüntüsü. Hedef çerçeve açılır listesi vurgulanır ve değer ' .NET Frameowrk 3,5 ' olarak ayarlanır.](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>C# birim testi projeleri için yeniden hedefleme

1. Yeni bir C# **birim testi Project** projesi oluşturun.

2. **Çözüm Gezgini**' de, yeni C# test projenizin sağ tıklama menüsünden **Özellikler** ' i seçin.

   C# test projenizin özellikleri görüntülenir.

3. **Uygulama** sekmesinde **hedef çerçeve**' yi seçin. aşağı açılan listeden, aşağıdaki çizimde gösterildiği gibi **.NET Framework 3,5** veya sonraki bir sürümü seçin. İstemci sürümü belirtmemelisiniz.

   ![Hedef çerçeve açılan listesinin konumunu vurgulayan Çözüm Gezgini Özellikler bölmesindeki uygulama sekmesinin çizimi.](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>C++/CLı birim testi projeleri için yeniden hedefleme

1. Yeni bir C++ **birim testi Project** projesi oluşturun.

   > [!WARNING]
   > Visual C++ için .NET Framework 'ün önceki bir sürümü için C++/CLı birim testlerini derlemek için, Visual Studio karşılık gelen sürümü kullanmanız gerekir.

2. **Çözüm Gezgini**' de, yeni C++ test projenizden **Project kaldır** ' ı seçin.

3. **Çözüm Gezgini**' de, yüklenmeyen C++ test projesini ve ardından **Edit \<project name> . vcxproj** öğesini seçin.

   *. Vcxproj* dosyası düzenleyicide açılır.

4. `TargetFrameworkVersion`Etiketli bir sürüm 3,5 veya sonraki bir sürümü olarak ayarlayın `PropertyGroup` `"Globals"` . İstemci sürümü belirtmemelisiniz:

    ```xml
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>
    ```

5. *. Vcxproj* dosyasını kaydedin ve kapatın.

6. **Çözüm Gezgini**' de, yeni C++ test projenizin sağ tıklama menüsünden **yeniden yükle Project** seç ' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri oluşturma](../sharepoint/create-sharepoint-solutions.md)
- [SharePoint çözümleri oluşturun ve hata ayıklayın](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Gelişmiş derleyici ayarları iletişim kutusu (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
