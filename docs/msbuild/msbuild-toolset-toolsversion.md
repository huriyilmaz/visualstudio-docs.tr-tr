---
title: MSBuild Araç Takımı (araçları sürümü) | Microsoft Docs
description: bir uygulama oluşturmak için bir görev, hedef ve araç araç kümesi belirtmek üzere MSBuild proje dosyasında araçlar sürüm özniteliğini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 3cbe0b0e60ef7d8fa1e80f56ba4757bbca678cd2bf9b4b7813a2bf95ae599d09
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397390"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Araç Takımı (ToolsVersion)

MSBuild, bir uygulama oluşturmak için bir görev, hedef ve araç araç kümesi kullanır. genellikle, bir MSBuild araç takımı *microsoft. common. tasks* dosyasını, *microsoft. common. targets* dosyasını ve *csc.exe* ve *vbc.exe* gibi derleyicileri içerir. çoğu araç kümesi, .NET Framework birden fazla sürümüne ve birden fazla sistem platformuna uygulama derlemek için kullanılabilir. ancak, MSBuild 2,0 araç takımı yalnızca .NET Framework 2,0 ' i hedeflemek için kullanılabilir.

## <a name="toolsversion-attribute"></a>Araçları sürüm özniteliği

::: moniker range=">=vs-2019"
 `ToolsVersion`proje dosyasındaki [Project](../msbuild/project-element-msbuild.md) öğesindeki özniteliğinde araç takımını belirtin. aşağıdaki örnek, projenin MSBuild "geçerli" araç takımı kullanılarak oluşturulması gerektiğini belirtir.

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 `ToolsVersion`proje dosyasındaki [Project](../msbuild/project-element-msbuild.md) öğesindeki özniteliğinde araç takımını belirtin. aşağıdaki örnek, projenin MSBuild 15,0 araç kümesi kullanılarak oluşturulması gerektiğini belirtir.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Bazı proje türleri `sdk` yerine özniteliğini kullanır `ToolsVersion` . Daha fazla bilgi için bkz. [.NET Core için csproj biçimine ekleme](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Araçları sürüm özniteliği nasıl kullanılır?

 Visual Studio bir proje oluşturduğunuzda veya mevcut bir projeyi yükselttiğinizde, adlı bir öznitelik `ToolsVersion` proje dosyasına otomatik olarak eklenir ve değeri Visual Studio sürümünde bulunan MSBuild sürümüne karşılık gelir. Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

 bir `ToolsVersion` proje dosyasında bir değer tanımlandığında MSBuild, projenin kullanabildiği araç kümesi özelliklerinin değerlerini belirleyebilmek için bu değeri kullanır. bir araç takımı özelliği `$(MSBuildToolsPath)` , .NET Framework araçlarının yolunu belirtir. Yalnızca bu araç takımı özelliği (veya `$(MSBuildBinPath)` ) gereklidir.

 Visual Studio 2013 başlayarak, MSBuild araç takımı sürümü Visual Studio sürüm numarasıyla aynıdır. proje dosyasında belirtilen araç kümesi sürümünden bağımsız olarak, Visual Studio ve komut satırındaki bu araç takımını varsayılan olarak MSBuild.  Bu davranış,-, sürüm bayrağı kullanılarak geçersiz kılınabilir. Daha fazla bilgi için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).

 aşağıdaki örnekte, MSBuild ayrılmış özelliğini kullanarak *Microsoft. CSharp. targets* dosyasını bulur `MSBuildToolsPath` .

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Değerini `MSBuildToolsPath` özel bir araç kümesi tanımlayarak değiştirebilirsiniz. Daha fazla bilgi için bkz. [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md).

 Komut satırında bir çözüm oluşturduğunuzda ve bir `ToolsVersion` *msbuild.exe* belirtirseniz, `ToolsVersion` çözümdeki her bir proje kendi kendine belirtse bile tüm projeler ve proje-proje bağımlılıkları buna göre oluşturulur `ToolsVersion` . `ToolsVersion`Değeri proje başına olarak tanımlamak için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).

 `ToolsVersion`Özniteliği, proje geçişi için de kullanılır. örneğin, Visual Studio 2010 ' de bir Visual Studio 2008 projesi açarsanız proje dosyası, araçları sürüm = "4.0" olarak güncelleştirilir. daha sonra bu projeyi Visual Studio 2008 ' de açmaya çalışırsanız, bu, yükseltilen öğesini tanımaz `ToolsVersion` ve bu nedenle projeyi özniteliği hala 3,5 olarak ayarlanmış gibi oluşturur.

 Visual Studio 2010 ve Visual Studio 2012, 4,0 'in bir araçları sürümünü kullanır. Visual Studio 2013, 12,0 'in bir araçları sürümünü kullanır. Visual Studio 2015, araçları sürüm 14,0 ' i kullanır ve Visual Studio 2017, araçları sürüm 15,0 kullanır. birçok durumda, projeyi değişiklik yapmadan Visual Studio birden çok sürümünde açabilirsiniz. Visual Studio her zaman doğru araç takımını kullanır, ancak kullanılan sürüm proje dosyasındaki sürümle eşleşmezse size bildirilir. Neredeyse her durumda, araç kümeleri çoğu durumda uyumlu olduğu için bu uyarı zararsız olur.

 bu konunun ilerleyen kısımlarında açıklanan alt araç kümeleri, MSBuild, yapılandırmanın çalıştırıldığı bağlama göre kullanılacak araç kümesini otomatik olarak değiştirmesine izin verir. örneğin, MSBuild Visual Studio 2012 ' de çalıştırıldığında, proje dosyasını açıkça değiştirmek zorunda kalmadan Visual Studio 2010 ' de çalıştırıldığında daha yeni bir araç kümesi kullanır.

## <a name="toolset-implementation"></a>Araç takımı uygulama

 Araç takımını oluşturan çeşitli araçların, hedeflerin ve görevlerin yollarını seçerek bir araç takımı uygulayın. MSBuild tanımladığı araç takımının araçları aşağıdaki kaynaklardan gelir:

- .NET Framework klasörü.

- Ek yönetilen araçlar.

  Yönetilen Araçlar *ResGen.exe* ve *TlbImp.exe* içerir.

MSBuild araç seti 'ne erişmenin iki yolu vardır:

- Araç kümesi özelliklerini kullanarak

- Yöntemleri kullanarak <xref:Microsoft.Build.Utilities.ToolLocationHelper>

Araç kümesi özellikleri araçların yollarını belirtir. Visual Studio 2017 ' den başlayarak MSBuild artık sabit bir konuma sahip değildir. varsayılan olarak, Visual Studio yükleme konumuna göre *MSBuild \15.0\bin* klasöründe bulunur. önceki sürümlerde, MSBuild `ToolsVersion` karşılık gelen kayıt defteri anahtarını bulmak için proje dosyasındaki özniteliğin değerini kullanır ve ardından araç kümesi özelliklerini ayarlamak için kayıt defteri anahtarındaki bilgileri kullanır. örneğin, değeri varsa `ToolsVersion` `12.0` , MSBuild araç kümesi özelliklerini bu kayıt defteri anahtarına göre ayarlar: **hklm\software\microsoft\ MSBuild \tools\versions\12.0**.

 Araç kümesi özellikleri şunlardır:

- `MSBuildToolsPath`MSBuild ikili dosyalarının yolunu belirtir.

- `SDK40ToolsPath`MSBuild 4. x için ek yönetilen araçların yolunu belirtir (4,0 veya 4,5 olabilir).

- `SDK35ToolsPath`MSBuild 3,5 için ek yönetilen araçların yolunu belirtir.

Alternatif olarak, sınıfının yöntemlerini çağırarak araç takımını programlı bir şekilde belirleyebilirsiniz <xref:Microsoft.Build.Utilities.ToolLocationHelper> . Sınıfı şu yöntemleri içerir:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>.NET Framework klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>.NET Framework klasöründeki bir dosyanın yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> yönetilen araçlar klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> genellikle yönetilen Araçlar klasöründe bulunan bir dosyanın yolunu döndürür.

- [Getpathtobuildtools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) , derleme araçlarının yolunu döndürür.

### <a name="sub-toolsets"></a>Alt araç kümeleri

 15,0 ' dan önceki sürümlerde MSBuild için MSBuild temel araçların yolunu belirtmek üzere bir kayıt defteri anahtarı kullanır. anahtarın bir alt anahtarı varsa MSBuild, ek araçlar içeren bir alt araç takımının yolunu belirtmek için onu kullanır. Bu durumda, araç takımı her iki anahtar içinde tanımlanmış özellik tanımlarını birleştirerek tanımlanır.

> [!NOTE]
> Araç kümesi özellik adları çakışıyorsa, alt anahtar yolu için tanımlanan değer kök anahtar yolu için tanımlanan değeri geçersiz kılar.

 Alt araç kümeleri Build özelliğinin varlığı içinde etkin hale gelir `VisualStudioVersion` . Bu özellik şu değerlerden birini alabilir:

- "10,0" .NET Framework 4 alt araç takımını belirtir

- "11,0" .NET Framework 4,5 alt araç takımını belirtir

- "12,0" .NET Framework 4.5.1 alt araç takımını belirtir

10,0 ve 11,0 alt araç kümeleri, Araçlar sürüm 4,0 ile kullanılmalıdır. Sonraki sürümlerde alt araç takımı sürümü ve araçları sürümü eşleşmelidir.

yapı sırasında, MSBuild, zaten tanımlanmamışsa özellik için varsayılan değeri otomatik olarak belirler ve ayarlar `VisualStudioVersion` .

MSBuild, `ToolLocationHelper` `VisualStudioVersion` bir parametre olarak numaralandırılmış bir değer ekleyen yöntemler için aşırı yüklemeler sağlar

.NET Framework 4,5 ' de alt araç kümeleri tanıtılmıştı.

## <a name="see-also"></a>Ayrıca bkz.

- [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
