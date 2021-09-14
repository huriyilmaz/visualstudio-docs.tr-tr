---
title: MSBuild | Microsoft Docs
description: Microsoft Build Engine (MSBuild) platformunun derlemeleri denetlemek için bir XML şemasına sahip bir proje dosyası nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/11/2021
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b9e2e3acd40bb5a5b7f45b636b3539b5c24f7f29
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725707"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine, uygulama oluşturmaya yönelik bir platformdur. MSBuild olarak da bilinen bu altyapı, derleme platformunun yazılım işleme ve derleme şeklini denetleyen bir proje dosyası için bir XML şeması sağlar. Visual Studio MSBuild kullanır, ancak MSBuild Visual Studio bağımlı değildir. proje veya çözüm dosyanızda *msbuild.exe* çağırarak, ürünleri Visual Studio yüklü olmayan ortamlarda düzenleyebilir ve oluşturabilirsiniz.

 Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild kullanır. Visual Studio (*. csproj*, *. vbproj*, *. vcxproj* ve diğerleri) içindeki proje dosyaları, ıde kullanarak bir proje oluşturduğunuzda yürütülen MSBuild XML kodu içerir. Visual Studio projeler, tipik geliştirme işlerini yapmak için gerekli tüm ayarları ve derleme süreçlerini içeri aktarır, ancak bunları Visual Studio veya bir XML düzenleyicisi kullanarak genişletebilir veya değiştirebilirsiniz.

 C++ için MSBuild hakkında daha fazla bilgi için bkz. [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 aşağıdaki örnekler, Visual Studio ıde yerine komut satırından MSBuild çağırarak derlemeleri nasıl çalıştırabileceğinizi göstermektedir.

- Visual Studio yüklü değil. ([Visual Studio olmadan MSBuild indir](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- MSBuild 64 bit sürümünü kullanmak istiyorsunuz. MSBuild bu sürümü genellikle gereksizdir, ancak MSBuild daha fazla belleğe erişmesine izin verir.

- Bir derlemeyi birden çok işlemde çalıştırmak istiyorsunuz. Bununla birlikte, C++ ve C# ' deki projelerde aynı sonuca ulaşmak için IDE 'yi de kullanabilirsiniz.

- Yapı sistemini değiştirmek istiyorsunuz. Örneğin, aşağıdaki eylemleri etkinleştirmek isteyebilirsiniz:

  - Dosyaları derleyiciye ulaşmadan önce ön işleme.

  - Yapı çıktılarını farklı bir yere kopyalayın.

  - Derleme çıktılarından sıkıştırılmış dosyalar oluşturun.

  - İşlem sonrası bir adım yapın. Örneğin, bir derlemeyi farklı bir sürümle damgalamak isteyebilirsiniz.

Visual Studio ıde 'de kod yazabilir, ancak MSBuild kullanarak yapıları çalıştırabilirsiniz. başka bir alternatif olarak, bir geliştirme bilgisayarında ıde 'de kod oluşturabilir, ancak birden çok geliştiriciden tümleştirilen kodu oluşturmak için komut satırından MSBuild çalıştırabilirsiniz. .net core projelerini derlemek için MSBuild kullanan [.net core komut satırı arabirimini (clı)](/dotnet/core/tools/)de kullanabilirsiniz.

> [!NOTE]
> uygulamanızı otomatik olarak derlemek, test etmek ve dağıtmak için Azure Pipelines kullanabilirsiniz. Derleme sisteminiz, geliştiriciler kod iade edildiğinde (örneğin, sürekli tümleştirme stratejisinin bir parçası olarak) veya bir zamanlamaya göre (örneğin, gecelik bir derleme doğrulama test derlemesi), yapıları otomatik olarak çalıştırabilir. Azure Pipelines, MSBuild kullanarak kodunuzu derler. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Bu makalede MSBuild bir genel bakış sunulmaktadır. Tanıtım öğreticisi için bkz. [Izlenecek yol: Using MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>komut isteminde MSBuild kullanma

 bir komut isteminde MSBuild çalıştırmak için, uygun komut satırı seçenekleriyle birlikte *MSBuild.exe* bir proje dosyası geçirin. Komut satırı seçenekleri özellikleri ayarlamanıza, belirli hedefleri yürütmenizi ve yapı sürecini denetleyen diğer seçenekleri ayarlamanıza olanak sağlar. Örneğin, özelliği olarak ayarlanmış *myproj. proj* dosyasını oluşturmak için aşağıdaki komut satırı sözdizimini kullanın `Configuration` `Debug` .

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 MSBuild komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Bir projeyi indirmadan önce kodun güvenilirliğini saptayın.

## <a name="project-file"></a>Project dosyası

 MSBuild, basit ve genişletilebilir bir XML tabanlı proje dosyası biçimi kullanır. MSBuild proje dosyası biçimi, geliştiricilerin oluşturulacak öğeleri ve ayrıca farklı işletim sistemleri ve yapılandırmalara yönelik olarak nasıl derlenmelerini betimler. Buna ek olarak, proje dosyası biçimi, geliştiricilerin ayrı dosyalara ayrılabildiği yeniden kullanılabilir derleme kuralları yazarlarına olanak tanıyarak, derlemelerin üründeki farklı projelerde tutarlı bir şekilde gerçekleştirilmesini sağlar.

 Visual Studio yapı sistemi, projeye özgü mantığı proje dosyanızın kendisinde depolar ve standart derleme mantığını tanımlamak için *. props* ve *. targets* gibi uzantılara sahip MSBuild XML dosyalarını kullanır. *. props* dosyaları MSBuild özellikleri tanımlar ve *. targets* dosyaları MSBuild hedeflerini tanımlar. bu içeri aktarmalar bazen Visual Studio proje dosyasında görünür, ancak .net Core, .net 5 ve .net 6 projeleri gibi daha yeni projelerde içeri aktarmaları proje dosyasında görmezsiniz. Bunun yerine, bir SDK başvurusu görürsünüz. Bunlar SDK stili projeler olarak adlandırılır. .NET SDK gibi bir SDK 'ya başvurduğunuzda,. props ve. Target dosyalarının içeri aktarmaları, SDK tarafından örtülü olarak belirtilir.

 aşağıdaki bölümlerde MSBuild proje dosyası biçiminin bazı temel öğeleri açıklanır. temel proje dosyası oluşturma hakkında bir öğretici için, bkz. [izlenecek yol: sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a> Özellikler

 Özellikler, yapıları yapılandırmak için kullanılabilen anahtar/değer çiftlerini temsil eder. Özellikler, bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesinin alt öğesi olarak özelliğin adına sahip bir öğe oluşturularak belirtilir. Örneğin, aşağıdaki kod, değeri olan adlı bir özellik oluşturur `BuildDir` `Build` .

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Bir özelliği öğesine bir özniteliği yerleştirerek koşullu olarak tanımlayabilirsiniz `Condition` . Koşul olarak değerlendirilmediği takdirde koşullu öğelerin içeriği yoksayılır `true` . Aşağıdaki örnekte, `Configuration` öğesi henüz tanımlanmadıysa tanımlanmıştır.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Özellikler, proje dosyasında $ () sözdizimi kullanılarak başvurulabilirler \<PropertyName> . Örneğin, ve kullanarak önceki örneklerde bulunan özelliklere başvurabilirsiniz `$(BuildDir)` `$(Configuration)` .

 özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Öğeler

 Öğeler, derleme sistemine giriş ve genellikle dosyaları temsil eder. Öğeler, Kullanıcı tanımlı öğe adlarına göre öğe türlerine göre gruplandırılır. Bu öğe türleri, oluşturma işleminin adımlarını gerçekleştirmek için bireysel öğeleri kullanan görevler için parametre olarak kullanılabilir.

 Öğeler, öğe türünün adı bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğesi olan bir öğe oluşturularak proje dosyasında belirtilir. Örneğin, aşağıdaki kod iki dosya içeren adlı bir öğe türü oluşturur `Compile` .

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Öğe türlerine @ () sözdizimi kullanılarak proje dosyası boyunca başvurulabilir \<ItemType> . Örneğin, örnekteki öğe türüne kullanılarak başvurulur `@(Compile)` .

 MSBuild, öğe ve öznitelik adları büyük/küçük harfe duyarlıdır. Ancak özellik, öğe ve meta veri adları değildir. Aşağıdaki örnek, öğe türünü `Compile` , ya da `comPile` herhangi bir diğer durum varyasyonunu oluşturur ve "bir. cs; Two. cs" değerini verir.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Öğeler joker karakterler kullanılarak bildirilebilecek ve daha gelişmiş derleme senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için bkz. [Items](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Görevlerinize

 görevler, MSBuild projelerin derleme işlemleri gerçekleştirmek için kullandığı çalıştırılabilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya bir dış araç çalıştırabilir. Görevler yeniden kullanılabilir ve farklı projelerde farklı geliştiriciler tarafından paylaşılabilir.

 bir görevin yürütme mantığı yönetilen kodda yazılır ve [usingtask](../msbuild/usingtask-element-msbuild.md) öğesi kullanılarak MSBuild eşleştirilir. Arabirimini uygulayan bir yönetilen tür yazarak kendi görevinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ITask> . Görevlerin nasıl yazılacağı hakkında daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).

 MSBuild, gereksinimlerinize uyacak şekilde değiştirebileceğiniz ortak görevleri içerir. Örnekler, dosyaları kopyalayan, dizin oluşturan [MakeDir](../msbuild/makedir-task.md), ve Visual C# kaynak kodu dosyalarını derleyen [CSC](../msbuild/csc-task.md)olan [kopyalardır](../msbuild/copy-task.md). Kullanım bilgileri ile birlikte kullanılabilir görevlerin bir listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

 bir görev, bir [hedef](../msbuild/target-element-msbuild.md) öğenin alt öğesi olarak görevin adına sahip olan bir öğe oluşturarak MSBuild proje dosyasında yürütülür. Görevler genellikle öğesinin öznitelikleri olarak geçirilen parametreleri kabul eder. MSBuild özellikler ve öğeler, parametre olarak kullanılabilir. Örneğin, aşağıdaki kod [MakeDir](../msbuild/makedir-task.md) görevini çağırır ve `BuildDir` Önceki örnekte belirtilen özelliğin değerini geçirir.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Görevler hakkında daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Lerden

 Hedefleri belirli bir sırada gruplar ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak kullanıma sunar. Hedefler, okunabilirliği artırmak ve genişletmeye izin vermek için genellikle mantıksal bölümler halinde gruplandırılır. Derleme adımlarının hedeflere bölünmesi, bu kod bölümünü her hedefe kopyalamadan, diğer hedeflerden derleme işleminin bir parçasını çağırmanıza olanak sağlar. Örneğin, yapı işlemine bazı giriş noktaları oluşturulması gerekiyorsa, başvuruları oluşturan bir hedef oluşturabilir ve bu hedefi, gereken her giriş noktasından çalıştırabilirsiniz.

 Hedefler, [hedef](../msbuild/target-element-msbuild.md) öğe kullanılarak proje dosyasında belirtilir. Örneğin, aşağıdaki kod adlı bir hedef oluşturur, daha `Compile` sonra önceki örnekte belirtilen öğe listesine sahip olan [CSC](../msbuild/csc-task.md) görevini çağırır.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Daha Gelişmiş senaryolarda, hedefler bir diğeri arasındaki ilişkileri ve bağımlılık analizini gerçekleştirirken, bu hedefin güncel olması durumunda yapı işleminin bütün bölümlerinin atlanabilmesi için kullanılabilir. Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Derleme günlükleri

 Yapılandırma hatalarını, uyarıları ve iletileri konsola veya başka bir çıkış cihazına kaydedebilirsiniz. Daha fazla bilgi için [bkz. Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md) [ve](../msbuild/logging-in-msbuild.md)MSBuild.

## <a name="use-msbuild-in-visual-studio"></a>MSBuild'da Visual Studio

 Visual Studio, yönetilen MSBuild derleme bilgilerini depolamak için MSBuild proje dosyası biçimini kullanır. Project arabirimi kullanılarak eklenen veya değiştirilen Visual Studio ayarları içinde *yansıtıldı. \* her* proje için oluşturulan proj dosyası. Visual Studio yönetilen projeler derlemek için MSBuild barındırılan bir örnek kullanır. Bu, yönetilen bir projenin Visual Studio komut isteminde (Visual Studio yüklü olsa bile) ve sonuçlar aynı olacağını ifade ediyor.

 Visual Studio'de MSBuild hakkında bir öğretici için bkz. [MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Çoklu hedef

 Bu Visual Studio kullanarak, bir uygulamayı derlemek için uygulamanın çeşitli sürümlerinden herhangi biri üzerinde .NET Framework. Örneğin, bir uygulamayı 32 bitlik bir platformda .NET Framework 2.0'da çalıştıracak şekilde derler ve aynı uygulamayı 64 bitlik bir platformda .NET Framework 4.5 üzerinde çalıştırmak için derlersiniz. Birden fazla çerçeveye derleme özelliği multitargeting olarak adlandırılmıştır.

 Çoklu hedeflere sahip olmak için aşağıdaki avantajlardan faydalanır:

- 3.5 ve 4.7.2 gibi .NET Framework önceki sürümlerini hedef alan uygulamalar geliştirebilirsiniz.

- Hedef çerçevenin *önceden tanımlanmış* bir alt kümesi olan bir çerçeve profilini hedefleyebilirsiniz.

- Geçerli sürüme yönelik bir hizmet paketi .NET Framework, hedefleyabilirsiniz.

- Çoklu hedefleme, bir uygulamanın yalnızca hedef çerçevede ve platformda kullanılabilen işlevleri kullanmalarını garantiler.

Daha fazla bilgi için [bkz. Çoklu Hedef.](../msbuild/msbuild-multitargeting-overview.md)

## <a name="see-also"></a>Ayrıca bkz.

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Yalnızca bir metin düzenleyicisi kullanarak, temel bir proje dosyasının artımlı olarak nasıl oluşturul olduğunu gösterir. |
| [İzlenecek yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md) | IDE'nin yapı taşlarını MSBuild, IDE'yi kapatmadan projelerde yazma, işleme ve MSBuild ayıklama Visual Studio gösterir. |
| [MSBuild kavramları](../msbuild/msbuild-concepts.md) | Özelliklerin, öğelerin, MSBuild görevlerin dört yapı taşlarını sunar. |
| [Öğeler](../msbuild/msbuild-items.md) | Dosya biçiminin temel MSBuild ve parçaların nasıl bir araya sığmalarını açıklar. |
| [MSBuild özellikleri](../msbuild/msbuild-properties.md) | Özellikler ve özellik koleksiyonları sunar. Özellikler, derlemeleri yapılandırmak için kullanılan anahtar/değer çiftleridir. |
| [Targets](../msbuild/msbuild-targets.md) | Görevleri belirli bir sırada grupla ve derleme işleminin bölümlerinin komut satırı üzerinde çağrılmalarını etkinleştirmeyi açıklar. |
| [Görevler](../msbuild/msbuild-tasks.md) | Atomik derleme işlemleri gerçekleştirmek için MSBuild bir yürütülebilir kod biriminin nasıl oluşturulacaklarını gösterir. |
| [Koşullar](../msbuild/msbuild-conditions.md) | Bir MSBuild `Condition` öğesinde özniteliğinin nasıl MSBuild tartışan. |
| [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md) | Toplu işleme, dönüşüm gerçekleştirme, çoklu hedef ve diğer gelişmiş teknikleri sunar. |
| [MSBuild'de Günlük Kaydı](../msbuild/logging-in-msbuild.md) | Derleme olaylarının, iletilerin ve hataların nasıl günlüğe kaydedilir? |
| [MSBuild nasıl proje oluşturur](build-process-overview.md) | Şirket içinde kullanılan iç derleme işlemini MSBuild |
| [Ek Kaynaklar](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Daha fazla bilgi için topluluk ve destek kaynaklarını MSBuild. |

## <a name="reference"></a>Başvuru

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)\
 Başvuru bilgilerini içeren konulara bağlantılar.

- [Sözlük](msbuild-glossary.md)\
 Yaygın kullanılan MSBuild tanımlar.
