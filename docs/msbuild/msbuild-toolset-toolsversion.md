---
title: MSBuild Araç Takımı (araçları sürümü) | Microsoft Docs
description: Bir uygulama oluşturmak için bir görev, hedef ve araç araç kümesi belirtmek üzere MSBuild proje dosyasındaki Araçlar sürümü özniteliğini nasıl kullanacağınızı öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0b27a1914d85f5fde8ef6c5c467d73197c084ce
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049022"
---
# <a name="msbuild-toolset-toolsversion"></a>MSBuild Araç Takımı (ToolsVersion)

MSBuild bir uygulama oluşturmak için bir görev, hedef ve araç araç kümesi kullanır. Genellikle bir MSBuild Araç Takımı, *Microsoft. Common. Tasks* dosyasını, *Microsoft. Common. targets* dosyasını ve *csc.exe* ve *vbc.exe* gibi derleyicileri içerir. Çoğu araç kümesi, .NET Framework birden fazla sürümüne ve birden fazla sistem platformuna uygulama derlemek için kullanılabilir. Ancak, MSBuild 2,0 araç takımı yalnızca .NET Framework 2,0 ' i hedeflemek için kullanılabilir.

## <a name="toolsversion-attribute"></a>Araçları sürüm özniteliği

::: moniker range=">=vs-2019"
 `ToolsVersion`Proje dosyasındaki [Proje](../msbuild/project-element-msbuild.md) öğesindeki özniteliğinde araç takımını belirtin. Aşağıdaki örnek, projenin MSBuild "Current" araç takımı kullanılarak oluşturulması gerektiğini belirtir.

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 `ToolsVersion`Proje dosyasındaki [Proje](../msbuild/project-element-msbuild.md) öğesindeki özniteliğinde araç takımını belirtin. Aşağıdaki örnek, projenin MSBuild 15,0 araç kümesi kullanılarak oluşturulması gerektiğini belirtir.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> Bazı proje türleri `sdk` yerine özniteliğini kullanır `ToolsVersion` . Daha fazla bilgi için bkz. [.NET Core için csproj biçimine ekleme](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Araçları sürüm özniteliği nasıl kullanılır?

 Visual Studio 'da bir proje oluşturduğunuzda veya mevcut bir projeyi yükselttiğinizde, adlı bir öznitelik `ToolsVersion` proje dosyasına otomatik olarak eklenir ve değeri Visual Studio sürümüne dahil olan MSBuild sürümüne karşılık gelir. Daha fazla bilgi için bkz. [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

 Bir `ToolsVersion` Proje dosyasında bir değer tanımlandığında, MSBuild bu değeri, projenin kullanabildiği araç kümesi özelliklerinin değerlerini belirlemekte kullanır. Bir araç takımı özelliği `$(MSBuildToolsPath)` , .NET Framework araçlarının yolunu belirtir. Yalnızca bu araç takımı özelliği (veya `$(MSBuildBinPath)` ) gereklidir.

 Visual Studio 2013 başlayarak, MSBuild Araç Takımı sürümü Visual Studio sürüm numarasıyla aynıdır. MSBuild, proje dosyasında belirtilen araç kümesi sürümünden bağımsız olarak Visual Studio içinde ve komut satırında bu araç takımını varsayılan olarak belirler.  Bu davranış,-, sürüm bayrağı kullanılarak geçersiz kılınabilir. Daha fazla bilgi için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).

 Aşağıdaki örnekte, MSBuild, ayrılmış özelliğini kullanarak *Microsoft. CSharp. targets* dosyasını bulur `MSBuildToolsPath` .

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Değerini `MSBuildToolsPath` özel bir araç kümesi tanımlayarak değiştirebilirsiniz. Daha fazla bilgi için bkz. [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md).

 Komut satırında bir çözüm oluşturduğunuzda ve bir `ToolsVersion` *msbuild.exe* belirtirseniz, `ToolsVersion` çözümdeki her bir proje kendi kendine belirtse bile tüm projeler ve proje-proje bağımlılıkları buna göre oluşturulur `ToolsVersion` . `ToolsVersion`Değeri proje başına olarak tanımlamak için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).

 `ToolsVersion`Özniteliği, proje geçişi için de kullanılır. Örneğin, Visual Studio 2010 ' de bir Visual Studio 2008 projesi açarsanız proje dosyası, araçları sürümü = "4.0" olarak güncelleştirilir. Daha sonra bu projeyi Visual Studio 2008 ' de açmaya çalışırsanız bu, yükseltilen öğesini tanımaz `ToolsVersion` ve bu nedenle projeyi özniteliği hala 3,5 olarak ayarlanmış gibi oluşturur.

 Visual Studio 2010 ve Visual Studio 2012, 4,0 için bir araçları sürümü kullanır. Visual Studio 2013, 12,0 'in bir araçları sürümünü kullanır. Visual Studio 2015, araçları sürüm 14,0 ' nı kullanır ve Visual Studio 2017, araçları sürüm 15,0 kullanır. Birçok durumda, Visual Studio 'nun birden çok sürümünde değişiklik yapmadan projeyi açabilirsiniz. Visual Studio daima doğru araç takımını kullanır, ancak kullanılan sürüm proje dosyasındaki sürümle eşleşmezse size bildirilir. Neredeyse her durumda, araç kümeleri çoğu durumda uyumlu olduğu için bu uyarı zararsız olur.

 Bu konunun ilerleyen kısımlarında açıklanan alt araç kümeleri, MSBuild 'in çalıştırıldığı bağlama göre kullanılacak araç kümesini otomatik olarak değiştirmesine izin verir. Örneğin, MSBuild, proje dosyasını açıkça değiştirmek zorunda kalmadan Visual Studio 2012 ' de çalıştırıl2010 masından daha yeni bir araç kümesi kullanır.

## <a name="toolset-implementation"></a>Araç takımı uygulama

 Araç takımını oluşturan çeşitli araçların, hedeflerin ve görevlerin yollarını seçerek bir araç takımı uygulayın. MSBuild 'in tanımladığı araç takımı içindeki Araçlar aşağıdaki kaynaklardan gelir:

- .NET Framework klasörü.

- Ek yönetilen araçlar.

  Yönetilen Araçlar *ResGen.exe* ve *TlbImp.exe* içerir.

MSBuild, araç seti 'ne erişmenin iki yolunu sağlar:

- Araç kümesi özelliklerini kullanarak

- Yöntemleri kullanarak <xref:Microsoft.Build.Utilities.ToolLocationHelper>

Araç kümesi özellikleri araçların yollarını belirtir. Visual Studio 2017 ' den başlayarak MSBuild artık sabit bir konuma sahip değildir. Varsayılan olarak, Visual Studio yükleme konumuna göre *Msbuild\15.0\Bin* klasöründe bulunur. Daha önceki sürümlerde MSBuild, `ToolsVersion` karşılık gelen kayıt defteri anahtarını bulmak için proje dosyasındaki özniteliğin değerini kullanır ve ardından araç kümesi özelliklerini ayarlamak için kayıt defteri anahtarındaki bilgileri kullanır. Örneğin, değeri varsa `ToolsVersion` `12.0` MSBuild, araç kümesi özelliklerini bu kayıt defteri anahtarına göre ayarlar: **Hklm\software\microsoft\msbuild\tools\versions\12.0** .

 Araç kümesi özellikleri şunlardır:

- `MSBuildToolsPath` MSBuild ikili dosyalarının yolunu belirtir.

- `SDK40ToolsPath` MSBuild 4. x için ek yönetilen araçların yolunu belirtir (4,0 veya 4,5 olabilir).

- `SDK35ToolsPath` MSBuild 3,5 için ek yönetilen araçların yolunu belirtir.

Alternatif olarak, sınıfının yöntemlerini çağırarak araç takımını programlı bir şekilde belirleyebilirsiniz <xref:Microsoft.Build.Utilities.ToolLocationHelper> . Sınıfı şu yöntemleri içerir:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> .NET Framework klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> .NET Framework klasöründeki bir dosyanın yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> yönetilen araçlar klasörünün yolunu döndürür.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> genellikle yönetilen Araçlar klasöründe bulunan bir dosyanın yolunu döndürür.

- [Getpathtobuildtools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) , derleme araçlarının yolunu döndürür.

### <a name="sub-toolsets"></a>Alt araç kümeleri

 MSBuild 15,0 ' den önceki sürümler için, temel araçların yolunu belirtmek üzere bir kayıt defteri anahtarı kullanır. Anahtarın bir alt anahtarı varsa, MSBuild bunu ek araçlar içeren bir alt araç takımının yolunu belirtmek için kullanır. Bu durumda, araç takımı her iki anahtar içinde tanımlanmış özellik tanımlarını birleştirerek tanımlanır.

> [!NOTE]
> Araç kümesi özellik adları çakışıyorsa, alt anahtar yolu için tanımlanan değer kök anahtar yolu için tanımlanan değeri geçersiz kılar.

 Alt araç kümeleri Build özelliğinin varlığı içinde etkin hale gelir `VisualStudioVersion` . Bu özellik şu değerlerden birini alabilir:

- "10,0" .NET Framework 4 alt araç takımını belirtir

- "11,0" .NET Framework 4,5 alt araç takımını belirtir

- "12,0" .NET Framework 4.5.1 alt araç takımını belirtir

10,0 ve 11,0 alt araç kümeleri, Araçlar sürüm 4,0 ile kullanılmalıdır. Sonraki sürümlerde alt araç takımı sürümü ve araçları sürümü eşleşmelidir.

Bir derleme sırasında, MSBuild, zaten tanımlanmamışsa özellik için varsayılan değeri otomatik olarak belirler ve ayarlar `VisualStudioVersion` .

MSBuild, `ToolLocationHelper` `VisualStudioVersion` bir parametre olarak numaralandırılmış değer ekleyen yöntemler için aşırı yüklemeler sağlar

.NET Framework 4,5 ' de alt araç kümeleri tanıtılmıştı.

## <a name="see-also"></a>Ayrıca bkz.

- [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)
- [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)
