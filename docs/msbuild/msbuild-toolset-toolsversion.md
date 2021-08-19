---
title: MSBuild Araç Kümesi (ToolsVersion) | Microsoft Docs
description: Uygulama derlemek üzere bir görev, hedef ve MSBuild araç kümesi belirtmek için MSBuild proje dosyasında ToolsVersion özniteliğini kullanmayı öğrenin.
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
ms.openlocfilehash: 93c6dc19375e5cbcde13fc8e26d58a337139cfe1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084980"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Araç Takımı (ToolsVersion)

MSBuild bir uygulama oluşturmak için görev, hedef ve araç araç kümesi kullanır. Genellikle, MSBuild Araç Seti bir *microsoft.common.tasks* dosyası, *microsoft.common.targets* dosyası vecsc.exeve *vbc.exe.* ** Çoğu Araç Kümeleri, birden fazla sürümde ve birden fazla sistem platformunda .NET Framework derlemek için kullanılabilir. Ancak, MSBuild 2.0 Araç Seti yalnızca 2.0 .NET Framework için kullanılabilir.

## <a name="toolsversion-attribute"></a>ToolsVersion özniteliği

::: moniker range=">=vs-2019"
 Proje dosyasındaki Project `ToolsVersion` araç [](../msbuild/project-element-msbuild.md) kümesi belirtin. Aşağıdaki örnek, projenin "Geçerli" Araç Kümesi kullanılarak MSBuild gerektiğini belirtir.

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 Proje dosyasındaki Project `ToolsVersion` araç [](../msbuild/project-element-msbuild.md) kümesi belirtin. Aşağıdaki örnek, projenin 15.0 Araç Kümesi MSBuild gerektiğini belirtir.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Bazı proje türleri yerine `sdk` özniteliğini `ToolsVersion` kullanır. Daha fazla bilgi için [bkz. .NET Core için csproj biçimine eklemeler.](/dotnet/core/tools/csproj)

## <a name="how-the-toolsversion-attribute-works"></a>ToolsVersion özniteliği nasıl çalışır?

 Visual Studio'de bir proje oluşturma veya mevcut projeyi yükseltme sırasında, adlı bir öznitelik proje dosyasına otomatik olarak eklenir ve değeri Visual Studio sürümüne dahil edilen MSBuild sürümüne karşılık `ToolsVersion` gelen değerdir. Daha fazla bilgi için [bkz. Çerçeve hedeflemeye genel bakış.](../ide/visual-studio-multi-targeting-overview.md)

 Bir proje dosyasında bir değer tanımlandığı MSBuild, proje için kullanılabilen Araç Kümesi özelliklerinin değerlerini belirlemek `ToolsVersion` için bu değeri kullanır. Araç Kümesi özelliklerinden `$(MSBuildToolsPath)` biri, uygulama araçlarının yolunu .NET Framework özelliğidir. Yalnızca araç kümesi özelliği (veya `$(MSBuildBinPath)` ) gereklidir.

 Bu Visual Studio 2013 başlayarak MSBuild Araç Seti sürümü, Visual Studio sürümü numarasıyla aynıdır. MSBuild dosyada belirtilen Araç Kümesi sürümüne bakılmaksızın Visual Studio ve komut satırı içinde bu Araç Seti'ne varsayılan olarak kullanılır.  Bu davranış - ToolsVersion bayrağı kullanılarak geçersiz kılınabilir. Daha fazla bilgi için [bkz. ToolsVersion ayarlarını geçersiz kılma.](../msbuild/overriding-toolsversion-settings.md)

 Aşağıdaki örnekte, MSBuild *Microsoft.CSharp.targets* dosyasını ayrılmış özelliğini `MSBuildToolsPath` kullanarak bulur.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 değerini, özel bir Araç `MSBuildToolsPath` Kümesi tanımlayarak değiştirebilirsiniz. Daha fazla bilgi için [bkz. Standart ve özel Araç Kümesi yapılandırmaları.](../msbuild/standard-and-custom-toolset-configurations.md)

 Komut satırına bir çözüm derlemek vemsbuild.exeiçin bir belirttiğinizde, çözümde her proje kendi başına belirtse bile tüm projeler ve bunların projeden projeye bağımlılıkları bu çözüme `ToolsVersion` göre inşa ** `ToolsVersion` `ToolsVersion` edilmiştir. Değeri proje `ToolsVersion` başına temelinde tanımlamak için bkz. [ToolsVersion ayarlarını geçersiz kılma.](../msbuild/overriding-toolsversion-settings.md)

 özniteliği `ToolsVersion` proje geçişi için de kullanılır. Örneğin, Visual Studio 2010'da bir Visual Studio 2008 projesi açarsanız, proje dosyası ToolsVersion="4.0" içerecek şekilde güncelleştirilir. Ardından bu projeyi Visual Studio 2008'de açmayı denersiniz, yükseltileni tanımaz ve bu nedenle projeyi yine öznitelik 3.5 olarak ayarlanmış gibi `ToolsVersion` derlemesini sağlar.

 Visual Studio 2010 ve Visual Studio 2012 için ToolsVersion 4.0 kullanın. Visual Studio 2013 12.0 ToolsVersion kullanır. Visual Studio 2015'te ToolsVersion 14.0 ve Visual Studio 2017'de ToolsVersion 15.0 15.0 2015 14.0 ve 2017'de ise ToolsVersion 15.0 2015 14.0 2017 14.0 ve 2017 sürümler 14.0'dır. Çoğu durumda projeyi değişiklik yapmadan birden çok sürümde Visual Studio açabiliyoruz. Visual Studio her zaman doğru Araç Seti'nin kullanılır, ancak kullanılan sürüm proje dosyasındaki sürümle eşleşmezse size bildirilecek. Araç kümeleri çoğu durumda uyumlu olduğundan, neredeyse tüm durumlarda bu uyarı zararsızdır.

 Bu konu başlığında daha sonra açıklanan alt araç kümeleri, derlemenin çalıştır MSBuild bağlama göre hangi araç kümesinde otomatik olarak değiştireceğiz? Örneğin MSBuild, proje dosyasını açıkça değiştirmek zorunda kalmadan Visual Studio 2012'de Visual Studio 2010'da çalıştırılana göre daha yeni bir araç kümesi kullanır.

## <a name="toolset-implementation"></a>Araç kümesi uygulaması

 Araç Kümesi'ne yönelik çeşitli araçların, hedeflerin ve görevlerin yollarını seçerek bir Araç Kümesi uygulama. Araçlar kümesinde tanımladığı MSBuild aşağıdaki kaynaklardan gelir:

- .NET Framework klasörü.

- Ek yönetilen araçlar.

  Yönetilen araçlar, *ResGen.exe* ve *TlbImp.exe.*

MSBuild araç kümesine erişmek için iki yol sağlar:

- Araç kümesi özelliklerini kullanarak

- Yöntemleri <xref:Microsoft.Build.Utilities.ToolLocationHelper> kullanarak

Araç kümesi özellikleri araçların yollarını belirtir. 2017'Visual Studio başlayarak, MSBuild artık sabit bir konuma sahip değil. Varsayılan olarak, yükleme konumuyla *MSBuild\15.0\Bin* klasöründe Visual Studio bulunur. Önceki sürümlerde MSBuild, karşılık gelen kayıt defteri anahtarını bulmak için proje dosyasında özniteliğinin değerini kullanır ve ardından araç takımı özelliklerini ayarlamak için kayıt defteri `ToolsVersion` anahtarındaki bilgileri kullanır. Örneğin, değerine sahipse, MSBuild araç takımı özelliklerini şu kayıt defteri anahtarına göre `ToolsVersion` `12.0` ayarlar: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Bunlar Araç Kümesi özellikleridir:

- `MSBuildToolsPath`dosya ikililerinin yolunu MSBuild belirtir.

- `SDK40ToolsPath`MSBuild 4.x (4.0 veya 4.5 olabilir) için ek yönetilen araçların yolunu belirtir.

- `SDK35ToolsPath`3.5 için ek yönetilen MSBuild yolunu belirtir.

Alternatif olarak, sınıfının yöntemlerini çağırarak Araç Kümesi'nin program aracılığıyla <xref:Microsoft.Build.Utilities.ToolLocationHelper> belirlenebilirsiniz. sınıfı şu yöntemleri içerir:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A>, .NET Framework döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A>, .NET Framework klasöründeki bir dosyanın yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> yönetilen araçlar klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> genellikle yönetilen araçlar klasöründe bulunan bir dosyanın yolunu döndürür.

- [GetPathToBuildTools,](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) derleme araçlarının yolunu döndürür.

### <a name="sub-toolsets"></a>Alt araç kümeleri

 15.0'MSBuild önceki sürümler için MSBuild temel araçların yolunu belirtmek için bir kayıt defteri anahtarı kullanır. Anahtarın bir alt anahtarı varsa MSBuild araç takımı yolunu belirtmek için anahtarı kullanır. Bu durumda Araç Seti, her iki anahtarda da tanımlanan özellik tanımları birleştirerek tanımlanır.

> [!NOTE]
> Araç takımı özellik adları birlikte olursa, alt anahtar yolu için tanımlanan değer kök anahtar yolu için tanımlanan değeri geçersiz kılar.

 Alt araç kümeleri derleme özelliğinin varlığında etkin `VisualStudioVersion` hale geldi. Bu özellik şu değerlerden birini alır:

- "10.0", .NET Framework 4 alt araç kümesi belirtir

- "11.0", .NET Framework 4.5 alt araç kümesi belirtir

- "12.0", .NET Framework 4.5.1 alt araç kümesi belirtir

ToolsVersion 4.0 ile 10.0 ve 11.0 alt araç kümeleri kullanılmalıdır. Sonraki sürümlerde, alt araç kümesi sürümü ve ToolsVersion eşleşmeli.

Derleme sırasında, MSBuild önceden tanımlanmamışsa özelliği için varsayılan bir değeri otomatik olarak belirler `VisualStudioVersion` ve ayarlar.

MSBuild, parametre olarak `ToolLocationHelper` numaralandı değeri ekli `VisualStudioVersion` yöntemler için aşırı yüklemeler sağlar

Alt araç kümeleri 4.5 .NET Framework tanıtıldı.

## <a name="see-also"></a>Ayrıca bkz.

- [Standart ve özel Araç Kümesi yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
