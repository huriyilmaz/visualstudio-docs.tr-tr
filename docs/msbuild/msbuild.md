---
title: MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1bd4c4ab15364e9e2ac8e189fcde01f65244b7a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289202"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine, uygulama oluşturmaya yönelik bir platformdur. MSBuild olarak da bilinen bu altyapı, derleme platformunun yazılım işleme ve derleme şeklini denetleyen bir proje dosyası için bir XML şeması sağlar. Visual Studio MSBuild kullanır, ancak MSBuild, Visual Studio 'ya bağlı değildir. Proje veya çözüm dosyanızda *msbuild.exe* çağırarak, ürünleri Visual Studio 'nun yüklü olmadığı ortamlarda düzenleyebilir ve oluşturabilirsiniz.

 Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild 'i kullanır. Visual Studio 'daki proje dosyaları (*. csproj*, *. vbproj*, *. vcxproj*ve diğerleri), IDE kullanarak bir proje oluşturduğunuzda yürütülen MSBuild xml kodunu içerir. Visual Studio projeleri tipik geliştirme işlerini yapmak için gerekli tüm ayarları ve derleme süreçlerini içeri aktarır, ancak bunları Visual Studio içinden genişletebilir veya bir XML Düzenleyicisi kullanarak değiştirebilirsiniz.

 C++ için MSBuild hakkında daha fazla bilgi için bkz. [MSBuild (c++)](/cpp/build/msbuild-visual-cpp).

 Aşağıdaki örneklerde, Visual Studio IDE yerine komut satırından MSBuild 'i çağırarak derlemeleri nasıl çalıştırabileceğiniz gösterilmektedir.

- Visual Studio yüklü değil. ([Visual Studio olmadan MSBuild 'ı indirin](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- MSBuild 'in 64 bitlik sürümünü kullanmak istiyorsunuz. MSBuild 'in bu sürümü genellikle gereksizdir, ancak MSBuild 'in daha fazla belleğe erişmesine izin verir.

- Bir derlemeyi birden çok işlemde çalıştırmak istiyorsunuz. Bununla birlikte, C++ ve C# ' deki projelerde aynı sonuca ulaşmak için IDE 'yi de kullanabilirsiniz.

- Yapı sistemini değiştirmek istiyorsunuz. Örneğin, aşağıdaki eylemleri etkinleştirmek isteyebilirsiniz:

  - Dosyaları derleyiciye ulaşmadan önce ön işleme.

  - Yapı çıktılarını farklı bir yere kopyalayın.

  - Derleme çıktılarından sıkıştırılmış dosyalar oluşturun.

  - İşlem sonrası bir adım yapın. Örneğin, bir derlemeyi farklı bir sürümle damgalamak isteyebilirsiniz.

Visual Studio IDE 'de kod yazabilir, ancak MSBuild kullanarak yapıları çalıştırabilirsiniz. Başka bir alternatif olarak, geliştirme bilgisayarında IDE 'de kod oluşturabilir, ancak birden çok geliştiriciden tümleştirilmiş kod oluşturmak için komut satırından MSBuild 'i çalıştırabilirsiniz. .NET Core projeleri oluşturmak için MSBuild 'i kullanan [.NET Core komut satırı arabirimi 'ni (CLI)](/dotnet/core/tools/)de kullanabilirsiniz.

> [!NOTE]
> Uygulamanızı otomatik olarak derlemek, test etmek ve dağıtmak için Azure Pipelines kullanabilirsiniz. Derleme sisteminiz, geliştiriciler kod iade edildiğinde (örneğin, sürekli tümleştirme stratejisinin bir parçası olarak) veya bir zamanlamaya göre (örneğin, gecelik bir derleme doğrulama test derlemesi), yapıları otomatik olarak çalıştırabilir. Azure Pipelines, MSBuild kullanarak kodunuzu derler. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

Bu makalede MSBuild 'e genel bakış sunulmaktadır. Tanıtım öğreticisi için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Bir komut isteminde MSBuild kullanma

 MSBuild 'i komut isteminde çalıştırmak için, uygun komut satırı seçenekleriyle birlikte *MSBuild.exe*bir proje dosyası geçirin. Komut satırı seçenekleri özellikleri ayarlamanıza, belirli hedefleri yürütmenizi ve yapı sürecini denetleyen diğer seçenekleri ayarlamanıza olanak sağlar. Örneğin, özelliği olarak ayarlanmış *myproj. proj* dosyasını oluşturmak için aşağıdaki komut satırı sözdizimini kullanın `Configuration` `Debug` .

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 MSBuild komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Bir projeyi indirmadan önce kodun güvenilirliğini saptayın.

## <a name="project-file"></a>Proje dosyası

 MSBuild, basit ve Genişletilebilir olan XML tabanlı bir proje dosyası biçimi kullanır. MSBuild proje dosyası biçimi, geliştiricilerin oluşturulacak öğeleri ve ayrıca farklı işletim sistemleri ve yapılandırmalara yönelik olarak nasıl derlenmelerini betimler. Buna ek olarak, proje dosyası biçimi, geliştiricilerin ayrı dosyalara ayrılabildiği yeniden kullanılabilir derleme kuralları yazarlarına olanak tanıyarak, derlemelerin üründeki farklı projelerde tutarlı bir şekilde gerçekleştirilmesini sağlar.

 Aşağıdaki bölümlerde MSBuild proje dosyası biçiminin bazı temel öğeleri açıklanır. Temel proje dosyası oluşturma hakkında bir öğretici için, bkz. [Izlenecek yol: bir MSBuild proje dosyası sıfırdan oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a>Özelliklerinin

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

 Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a>Öğeler

 Öğeler, derleme sistemine giriş ve genellikle dosyaları temsil eder. Öğeler, Kullanıcı tanımlı öğe adlarına göre öğe türlerine göre gruplandırılır. Bu öğe türleri, oluşturma işleminin adımlarını gerçekleştirmek için bireysel öğeleri kullanan görevler için parametre olarak kullanılabilir.

 Öğeler, öğe türünün adı bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğesi olan bir öğe oluşturularak proje dosyasında belirtilir. Örneğin, aşağıdaki kod iki dosya içeren adlı bir öğe türü oluşturur `Compile` .

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Öğe türlerine @ () sözdizimi kullanılarak proje dosyası boyunca başvurulabilir \<ItemType> . Örneğin, örnekteki öğe türüne kullanılarak başvurulur `@(Compile)` .

 MSBuild 'de, öğe ve öznitelik adları büyük/küçük harfe duyarlıdır. Ancak özellik, öğe ve meta veri adları değildir. Aşağıdaki örnek, öğe türünü `Compile` , ya da `comPile` herhangi bir diğer durum varyasyonunu oluşturur ve "bir. cs; Two. cs" değerini verir.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Öğeler joker karakterler kullanılarak bildirilebilecek ve daha gelişmiş derleme senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için bkz. [Items](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a>Görevlerinize

 Görevler, MSBuild projelerinin derleme işlemlerini gerçekleştirmek için kullandığı yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya bir dış araç çalıştırabilir. Görevler yeniden kullanılabilir ve farklı projelerde farklı geliştiriciler tarafından paylaşılabilir.

 Bir görevin yürütme mantığı yönetilen kodda yazılır ve [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi kullanılarak MSBuild ile eşleştirilir. Arabirimini uygulayan bir yönetilen tür yazarak kendi görevinizi yazabilirsiniz <xref:Microsoft.Build.Framework.ITask> . Görevlerin nasıl yazılacağı hakkında daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).

 MSBuild, gereksinimlerinize uyacak şekilde değiştirebileceğiniz ortak görevleri içerir. Örnekler, dosyaları kopyalayan, dizin oluşturan [MakeDir](../msbuild/makedir-task.md), ve Visual C# kaynak kodu dosyalarını derleyen [CSC](../msbuild/csc-task.md)olan [kopyalardır](../msbuild/copy-task.md). Kullanım bilgileri ile birlikte kullanılabilir görevlerin bir listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

 Bir görev, bir [hedef](../msbuild/target-element-msbuild.md) öğenin alt öğesi olarak görevin adına sahip olan bir öğe oluşturularak MSBuild proje dosyasında yürütülür. Görevler genellikle öğesinin öznitelikleri olarak geçirilen parametreleri kabul eder. MSBuild özellikleri ve öğeleri parametre olarak kullanılabilir. Örneğin, aşağıdaki kod [MakeDir](../msbuild/makedir-task.md) görevini çağırır ve `BuildDir` Önceki örnekte belirtilen özelliğin değerini geçirir.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Görevler hakkında daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a>Lerden

 Hedefleri belirli bir sırada gruplar ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak kullanıma sunar. Hedefler, okunabilirliği artırmak ve genişletmeye izin vermek için genellikle mantıksal bölümler halinde gruplandırılır. Derleme adımlarının hedeflere bölünmesi, bu kod bölümünü her hedefe kopyalamadan, diğer hedeflerden derleme işleminin bir parçasını çağırmanıza olanak sağlar. Örneğin, yapı işlemine bazı giriş noktaları oluşturulması gerekiyorsa, başvuruları oluşturan bir hedef oluşturabilir ve bu hedefi, gereken her giriş noktasından çalıştırabilirsiniz.

 Hedefler, [hedef](../msbuild/target-element-msbuild.md) öğe kullanılarak proje dosyasında belirtilir. Örneğin, aşağıdaki kod adlı bir hedef oluşturur, daha `Compile` sonra önceki örnekte belirtilen öğe listesine sahip olan [CSC](../msbuild/csc-task.md) görevini çağırır.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Daha Gelişmiş senaryolarda, hedefler bir diğeri arasındaki ilişkileri ve bağımlılık analizini gerçekleştirirken, bu hedefin güncel olması durumunda yapı işleminin bütün bölümlerinin atlanabilmesi için kullanılabilir. Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Derleme günlükleri

 Yapılandırma hatalarını, uyarıları ve iletileri konsola veya başka bir çıkış cihazına kaydedebilirsiniz. Daha fazla bilgi için bkz. [MSBuild 'de](../msbuild/logging-in-msbuild.md) [derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md) ve günlüğü alma.

## <a name="use-msbuild-in-visual-studio"></a>Visual Studio 'da MSBuild 'i kullanma

 Visual Studio, yönetilen projeler hakkında yapı bilgilerini depolamak için MSBuild proje dosyası biçimini kullanır. Visual Studio arabirimi kullanılarak eklenen veya değiştirilen proje ayarları, içinde yansıtılır *. \* *her proje için oluşturulan proj dosyası. Visual Studio yönetilen projeler oluşturmak için MSBuild 'in barındırılan bir örneğini kullanır. Bu, yönetilen bir projenin Visual Studio 'da veya bir komut isteminde (Visual Studio yüklü olmasa bile) derolabileceği ve sonuçların aynı olacağı anlamına gelir.

 Visual Studio 'da MSBuild 'i kullanma hakkında bir öğretici için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>Çoklu sürüm desteği

 Visual Studio 'yu kullanarak, .NET Framework çeşitli sürümlerinden herhangi birini çalıştırmak için bir uygulamayı derleyebilirsiniz. Örneğin, bir uygulamayı 32 bit platformda .NET Framework 2,0 ' de çalışacak şekilde derleyebilir ve aynı uygulamayı bir 64-bit platformunda .NET Framework 4,5 üzerinde çalışacak şekilde derleyebilirsiniz. Birden fazla çerçeveye derleme yeteneği Çoklu hedefleme olarak adlandırılır.

 Çoklu hedefleme avantajlarından bazıları şunlardır:

- .NET Framework önceki sürümlerini hedefleyen uygulamalar geliştirebilirsiniz, örneğin 2,0, 3,0 ve 3,5 sürümleri.

- Örneğin, Silverlight gibi .NET Framework dışındaki çerçeveleri hedefleyebilirsiniz.

- Hedef çerçevenin önceden tanımlanmış bir alt kümesi olan bir *çerçeve profilini*hedefleyebilirsiniz.

- Geçerli .NET Framework sürümü için bir hizmet paketi yayınlanmışsa, hedefleyebilirsiniz.

- Çoklu hedefleme, bir uygulamanın yalnızca hedef çerçeve ve platformda kullanılabilir olan işlevleri kullanmasını güvence altına alır.

Daha fazla bilgi için bkz. [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Yalnızca bir metin düzenleyicisi kullanarak basit bir proje dosyasının artımlı olarak nasıl oluşturulacağını gösterir. |
| [İzlenecek Yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md) | MSBuild 'in yapı taşlarını tanıtır ve Visual Studio IDE 'yi kapatmadan MSBuild projelerinin nasıl yazılacağını, değiştirileceğini ve hata ayıklacağınızı gösterir. |
| [MSBuild kavramları](../msbuild/msbuild-concepts.md) | MSBuild: özellikler, öğeler, hedefler ve görevler için dört bina bloğunu gösterir. |
| [Öğeleri](../msbuild/msbuild-items.md) | MSBuild dosya biçiminin arkasındaki genel kavramları ve parçaların birbirine nasıl uyduğunu açıklar. |
| [MSBuild özellikleri](../msbuild/msbuild-properties.md) | Özellikleri ve özellik koleksiyonlarını tanıtır. Özellikler, yapıları yapılandırmak için kullanılabilen anahtar/değer çiftleridir. |
| [Lerden](../msbuild/msbuild-targets.md) | Görevlerin belirli bir sırada nasıl gruplandırılacağını ve derleme işleminin bölümlerinin komut satırında çağrılacağını etkinleştirir. |
| [Görevler](../msbuild/msbuild-tasks.md) | Atomik derleme işlemleri gerçekleştirmek için MSBuild tarafından kullanılabilecek bir yürütülebilir kod birimi oluşturmayı gösterir. |
| [Koşullar](../msbuild/msbuild-conditions.md) | `Condition`Bir MSBuild öğesinde özniteliğin nasıl kullanılacağını açıklar. |
| [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md) | Toplu işleme, dönüşümler gerçekleştirme, Çoklu hedefleme ve diğer gelişmiş teknikleri gösterir. |
| [MSBuild'de Günlük Kaydı](../msbuild/logging-in-msbuild.md) | Oluşturma olaylarının, iletilerinin ve hatalarının nasıl günlüğe alınacağını açıklar. |
| [MSBuild 'in projeleri nasıl oluşturur](build-process-overview.md) | MSBuild içinde kullanılan iç derleme işlemini açıklar |
| [Ek Kaynaklar](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | MSBuild hakkında daha fazla bilgi için topluluk ve destek kaynaklarını listeler. |

## <a name="reference"></a>Başvuru

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)\
 Başvuru bilgilerini içeren konuların bağlantıları.

- [Sözlüğü](msbuild-glossary.md)\
 Ortak MSBuild koşullarını tanımlar.
