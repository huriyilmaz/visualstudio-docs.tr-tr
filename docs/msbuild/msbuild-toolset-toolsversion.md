---
title: MSBuild Araç Seti (ToolsVersion) | Microsoft Dokümanlar
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6aaa6309e04f5143b70ff233c0b621ab2350b9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633128"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Araç Takımı (ToolsVersion)

MSBuild, bir uygulama oluşturmak için görevlerin, hedeflerin ve araçların araç kümesini kullanır. Genellikle, BIR MSBuild Araç Seti bir *microsoft.common.tasks* dosyası, bir *microsoft.common.targets* dosyası ve *csc.exe* ve *vbc.exe*gibi derleyiciler içerir. Çoğu Araç Kümesi, .NET Framework'ün birden fazla sürümüne ve birden fazla sistem platformuna uygulama derlemek için kullanılabilir. Ancak, MSBuild 2.0 Araç Seti yalnızca .NET Framework 2.0'ı hedeflemek için kullanılabilir.

## <a name="toolsversion-attribute"></a>ToolsVersion özniteliği

::: moniker range=">=vs-2019"
 Proje dosyasındaki `ToolsVersion` [Proje](../msbuild/project-element-msbuild.md) öğesindeki öznitelikte Araç Kümesini belirtin. Aşağıdaki örnekte, projenin MSBuild "Current" Araç Seti kullanılarak oluşturulması gerektiği belirtilmiştir.

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Proje dosyasındaki `ToolsVersion` [Proje](../msbuild/project-element-msbuild.md) öğesindeki öznitelikte Araç Kümesini belirtin. Aşağıdaki örnekte, projenin MSBuild 15.0 Araç Seti kullanılarak oluşturulması gerektiği belirtilmiştir.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Bazı proje türleri `sdk` `ToolsVersion`özniteliği yerine kullanır. Daha fazla bilgi için [,NET Core için csproj formatına](/dotnet/core/tools/csproj) [paketler, meta veriler ve çerçeveler](/dotnet/core/packages) ve Eklemeler bölümüne bakın.

## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion özniteliği nasıl çalışır?

 Visual Studio'da bir proje oluşturduğunuzda veya varolan `ToolsVersion` bir projeyi yükselttiğinde, adı geçen bir öznitelik otomatik olarak proje dosyasına dahil edilir ve değeri Visual Studio sürümünde bulunan MSBuild sürümüne karşılık gelir. Daha fazla bilgi için çerçeve [hedefleme genel bakış'a](../ide/visual-studio-multi-targeting-overview.md)bakın.

 Bir `ToolsVersion` proje dosyasında bir değer tanımlandığında, MSBuild bu değeri projede kullanılabilen Araç Kümesi özelliklerinin değerlerini belirlemek için kullanır. Bir Araç Kümesi `$(MSBuildToolsPath)`özelliği , .NET Framework araçlarının yolunu belirtir. Yalnızca Araç Kümesi özelliği `$(MSBuildBinPath)`(veya), gereklidir.

 Visual Studio 2013'ten itibaren MSBuild Toolset sürümü Visual Studio sürüm numarasıyla aynıdır. MSBuild, proje dosyasında belirtilen Araç Seti sürümünden bağımsız olarak Visual Studio'daki ve komut satırındaki bu Araç Kümesi'ne varsayılan olarak yer alır.  Bu davranış -ToolsVersion bayrağı kullanılarak geçersiz kılınabilir. Daha fazla bilgi için, [Override ToolsVersion ayarlarına](../msbuild/overriding-toolsversion-settings.md)bakın.

 Aşağıdaki örnekte, MSBuild ayrılmış özelliği kullanarak *Microsoft.CSharp.targets* dosyasını `MSBuildToolsPath` bulur.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Özel bir Araç `MSBuildToolsPath` Kümesi tanımlayarak değerini değiştirebilirsiniz. Daha fazla bilgi için [Standart ve özel Araç Seti yapılandırmalarına](../msbuild/standard-and-custom-toolset-configurations.md)bakın.

 Komut satırında bir çözüm oluşturduğunuzda `ToolsVersion` ve *msbuild.exe*için bir çözüm belirttiğiniz zaman, tüm `ToolsVersion`projeler ve projeden projeye bağımlılıkları buna `ToolsVersion`göre inşa edilir , çözümdeki her proje kendi . `ToolsVersion` Proje bazında değeri tanımlamak [için, Geçersiz Kılma AraçlarıSürümü ayarlarına](../msbuild/overriding-toolsversion-settings.md)bakın.

 Öznitelik, `ToolsVersion` proje geçişi için de kullanılır. Örneğin, Visual Studio 2010'da visual studio 2008 projesini açarsanız, proje dosyası ToolsVersion="4.0" içerecek şekilde güncelleştirilir. Daha sonra Visual Studio 2008'de bu projeyi açmaya çalışırsanız, yükseltilmiş `ToolsVersion` olanları tanımaz ve bu nedenle projeyi öznitelik hala 3,5 olarak ayarlanmış gibi oluşturur.

 Visual Studio 2010 ve Visual Studio 2012 4.0 bir ToolsVersion kullanın. Visual Studio 2013 12.0 bir ToolsVersion kullanır. Visual Studio 2015 ToolsVersion 14.0 kullanır ve Visual Studio 2017 ToolsVersion 15.0 kullanır. Çoğu durumda, projeyi Visual Studio'nun birden çok sürümünde değişiklik yapmadan açabilirsiniz. Visual Studio her zaman doğru Araç Kümesini kullanır, ancak kullanılan sürüm proje dosyasındaki sürümle eşleşmiyorsa size bildirilir. Hemen hemen her durumda, Araç Kümeleri çoğu durumda uyumlu olduğundan bu uyarı iyi huyludur.

 Bu konuda daha sonra açıklanan alt araç kümeleri, MSBuild'in yapının çalıştırıldığı bağlamı temel alınabilmek için hangi araç kümesini otomatik olarak kullanacağını değiştirmesine olanak sağlar. Örneğin, MSBuild Visual Studio 2012'de çalıştırıldığında, proje dosyasını açıkça değiştirmenize gerek kalmadan Visual Studio 2010'da çalıştırıldığından daha yeni bir araç kümesi kullanır.

## <a name="toolset-implementation"></a>Araç seti uygulaması

 Araç Kümesini oluşturan çeşitli araçların, hedeflerin ve görevlerin yollarını seçerek bir Araç Kümesi uygulayın. MSBuild'in tanımladığı Araç Kümesi'ndeki araçlar aşağıdaki kaynaklardan gelir:

- .NET Framework klasörü.

- Ek yönetilen araçlar.

  Yönetilen araçlar *ResGen.exe* ve *TlbImp.exe*içerir.

MSBuild, Araç Kümesi'ne erişmek için iki yol sağlar:

- Araç Kümesi özelliklerini kullanarak

- Yöntemleri <xref:Microsoft.Build.Utilities.ToolLocationHelper> kullanarak

Araç kümesi özellikleri araçların yollarını belirtir. Visual Studio 2017'den itibaren MSBuild artık sabit bir konuma sahip değil. Varsayılan olarak, Visual Studio yükleme konumuna göre *MSBuild\15.0\Bin* klasöründe bulunur. Önceki sürümlerde, MSBuild ilgili `ToolsVersion` kayıt defteri anahtarını bulmak için proje dosyasındaki özniteliğin değerini kullanır ve sonra Araç Kümesi özelliklerini ayarlamak için kayıt defteri anahtarındaki bilgileri kullanır. Örneğin, değeri `ToolsVersion` `12.0`varsa, MSBuild bu kayıt defteri anahtarına göre Araç Seti özelliklerini ayarlar: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Araç Kümesi özellikleri şunlardır:

- `MSBuildToolsPath`MSBuild ikililerinin yolunu belirtir.

- `SDK40ToolsPath`MSBuild 4.x için ek yönetilen araçların yolunu belirtir (4.0 veya 4.5 olabilir).

- `SDK35ToolsPath`MSBuild 3.5 için ek yönetilen araçların yolunu belirtir.

Alternatif olarak, sınıfın yöntemlerini çağırarak Araç Kümesini <xref:Microsoft.Build.Utilities.ToolLocationHelper> programlı olarak belirleyebilirsiniz. Sınıf şu yöntemleri içerir:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>.NET Framework klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>.NET Framework klasöründeki bir dosyanın yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A>yönetilen araçlar klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A>genellikle yönetilen araçlar klasöründe bulunan bir dosyanın yolunu döndürür.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) yapı araçlarının yolunu döndürür.

### <a name="sub-toolsets"></a>Alt araç kümeleri

 MSBuild 15.0'dan önceki sürümler için, MSBuild temel araçların yolunu belirtmek için bir kayıt defteri anahtarı kullanır. Anahtarın bir alt anahtarı varsa, MSBuild bunu ek araçlar içeren bir alt araç kümesinin yolunu belirtmek için kullanır. Bu durumda, Araç Kümesi her iki anahtarda da tanımlanan özellik tanımları birleştirilerek tanımlanır.

> [!NOTE]
> Araç kümesi özellik adları çarpışırsa, alt anahtar yolu için tanımlanan değer kök anahtar yolu için tanımlanan değeri geçersiz kılar.

 Alt araç kümeleri `VisualStudioVersion` yapı özelliğinin varlığında etkin hale gelir. Bu özellik şu değerlerden birini alabilir:

- "10.0" .NET Framework 4 alt araç kümesini belirtir

- "11.0" .NET Framework 4.5 alt araç kümesini belirtir

- "12.0" .NET Framework 4.5.1 alt araç kümesini belirtir

ToolsVersion 4.0 ile 10.0 ve 11.0 alt takım kümeleri kullanılmalıdır. Sonraki sürümlerde, alt araç kümesi sürümü ve ToolsVersion eşleşmelidir.

Bir yapı sırasında MSBuild, önceden tanımlanmamışsa, `VisualStudioVersion` özellik için varsayılan değeri otomatik olarak belirler ve ayarlar.

MSBuild, parametre `ToolLocationHelper` olarak numaralandırılmış `VisualStudioVersion` bir değer ekleyen yöntemler için aşırı yükler sağlar

Alt araç setleri .NET Framework 4.5'te tanıtıldı.

## <a name="see-also"></a>Ayrıca bkz.

- [Standart ve özel Araç Seti yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
