---
title: Ünite Testleri .NET Framework'ün Önceki Önceki Hali
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 32380ddc802d1421f39d4920073fc277876cfef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596027"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Nasıl yapilir: Birim testlerini .NET Framework'ün önceki bir sürümünü hedef almak üzere yapılandır

Microsoft Visual Studio'da bir test projesi oluşturduğunuzda, .NET Framework'ün en son sürümü varsayılan olarak hedef olarak ayarlanır. Ayrıca, Visual Studio'nun önceki sürümlerindeki test projelerini yükseltirseniz, bu projeler .NET Framework'ün en son sürümünü hedefedecek şekilde yükseltilir. Proje özelliklerini düzenleyerek, projeyi açıkça .NET Framework'ün önceki sürümlerine yeniden hedefleyebilirsiniz.

.NET Framework'ün belirli sürümlerini hedefleyen birim test projeleri oluşturabilirsiniz. Hedeflenen sürüm 3,5 veya daha yeni olmalıdır ve istemci sürümü olamaz. Visual Studio, belirli sürümleri hedefleyen birim testleri için aşağıdaki temel desteği sağlar:

- Birim test projeleri oluşturabilir ve onları .NET Framework'ün belirli bir sürümüne hedefleyebilirsiniz.

- Yerel makinenizde Visual Studio'dan .NET Framework'ün belirli bir sürümünü hedefleyen birim testleri çalıştırabilirsiniz.

- Komut isteminden *MSTest.exe'yi* kullanarak .NET Framework'ün belirli bir sürümünü hedefleyen birim testleri çalıştırabilirsiniz.

- Yapının bir parçası olarak bir yapı aracısı üzerinde birim testleri çalıştırabilirsiniz.

**SharePoint Uygulamalarını Test Etme**

Yukarıda listelenen özellikler, Visual Studio'yu kullanarak SharePoint uygulamaları için birim testleri ve tümleştirme testleri yazmanızı da sağlar. Visual Studio'yu kullanarak SharePoint uygulamalarının nasıl geliştirilenhakkında daha fazla bilgi için bkz: [SharePoint çözümleri oluştur,](../sharepoint/create-sharepoint-solutions.md) [SharePoint çözümleri oluştur ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md) ve [SharePoint kodunu doğrula ve hataayıkla.](../sharepoint/verifying-and-debugging-sharepoint-code.md)

**Sınırlamalar**

Test projelerinizi .NET Framework'ün önceki sürümlerini kullanmak üzere yeniden hedeflediğinizde aşağıdaki sınırlamalar geçerlidir:

- .NET Framework 3.5'te, yalnızca birim testleri içeren test projeleri için çoklu hedefleme desteklenir. .NET Framework 3.5, kodlanmış UI veya yük testi gibi başka bir test türünü desteklemez. Yeniden hedefleme, birim testleri dışındaki test türleri için engellenir.

- .NET Framework'ün önceki bir sürümünü hedefleyen testlerin yürütülmesi yalnızca varsayılan ana bilgisayar bağdaştırıcısında desteklenir. ASP.NET ana bilgisayar adaptöründe desteklenmez. ASP.NET Geliştirme Sunucusu bağlamında çalışması gereken ASP.NET uygulamaların .NET Framework'ün geçerli sürümüyle uyumlu olması gerekir.

- .NET Framework 3.5 çok hedefli liği destekleyen testler çalıştırdığınızda veri toplama desteği devre dışı bırakılır. Visual Studio komut satırı araçlarını kullanarak kod kapsamını çalıştırabilirsiniz.

- .NET Framework 3.5 kullanan birim testleri uzak bir makinede çalıştırılamaz.

- Birim testlerini çerçevenin önceki istemci sürümlerine hedefleyemezsiniz.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Visual Basic birim test projeleri için yeniden hedefleme

1. Yeni bir Görsel Temel **Birim Test Projesi projesi** oluşturun.

2. **Çözüm Gezgini'nde,** yeni Visual Basic test projesinin sağ tıklama menüsünden **Özellikler'i** seçin.

     Visual Basic test projenizin özellikleri görüntülenir.

3. **Derle** sekmesinde, aşağıdaki resimde gösterildiği gibi **Gelişmiş Derleme Seçenekleri'ni** seçin.

     ![Gelişmiş Derleme Seçenekleri](../test/media/howtoconfigureunittest35frameworka.png)

4. Hedef çerçeveyi **.NET Framework 3.5** veya sonraki bir sürüm olarak değiştirmek için **Hedef çerçevesini (tüm yapılandırmalar)** açılır listeyi kullanın. İstemci sürümünü belirtmemelisiniz.

     ![Hedef çerçeve bırakma&#45;aşağı listesi](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>C# birim test projeleri için yeniden hedefleme

1. Yeni bir C# **Unit Test Project** projesi oluşturun.

2. **Çözüm Gezgini'nde,** yeni C# test projenizin sağ tıklama menüsünden **Özellikler'i** seçin.

   C# test projenizin özellikleri görüntülenir.

3. **Uygulama** sekmesinde **Hedef çerçevesini**seçin. Açılan listeden aşağıdaki resimde gösterildiği gibi **.NET Framework 3.5** veya daha sonraki bir sürümü seçin. İstemci sürümünü belirtmemelisiniz.

   ![Hedef çerçeve bırakma&#45;aşağı listesi](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>C++/CLI birim test projeleri için yeniden hedefleme

1. Yeni bir C++ **Birim Test Projesi** projesi oluşturun.

   > [!WARNING]
   > Visual C++için .NET çerçevesinin önceki bir sürümü için C++/CLI birim testleri oluşturmak için Visual Studio'nun ilgili sürümünü kullanmanız gerekir.

2. **Çözüm Gezgini'nde,** yeni C++ test projenizden Project'i **Boşalt'ı** seçin.

3. **Solution**Explorer'da, boşaltılan C++ test projesini seçin ve ardından **proje adını>.vcxproj'u edit'i \<** seçin.

   *.vcxproj* dosyası editörde açılır.

4. Sürüm 3.5'i veya etiketteki `"Globals"`daha sonraki bir sürümü ayarlayın. `TargetFrameworkVersion` `PropertyGroup` İstemci sürümünü belirtmemelisiniz:

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

5. *.vcxproj* dosyasını kaydedin ve kapatın.

6. **Çözüm Gezgini'nde,** yeni C++ test projenizin sağ tıklama menüsünden **Project'i Yeniden Yükle'yi** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri oluşturun](../sharepoint/create-sharepoint-solutions.md)
- [SharePoint çözümleri oluşturma ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Gelişmiş derleyici ayarları iletişim kutusu (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
