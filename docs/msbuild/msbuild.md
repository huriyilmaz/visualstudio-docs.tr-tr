---
title: MSBuild | Microsoft Docs
description: Microsoft Build Engine (MSBuild) platformunun derlemeleri denetlemeye olanak sağlayan xml şemasına sahip bir proje dosyası sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 372fc5c81b963cbb8e46cab689713e476fcfff7d
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848285"
---
# <a name="msbuild"></a>MSBuild

Bu Microsoft Build Engine, uygulamalar için bir platformdur. MSBuild olarak da bilinen bu altyapı, derleme platformunun yazılım işleme ve derleme işlemlerini kontrol eden bir proje dosyası için bir XML şeması sağlar. Visual Studio MSBuild kullanır, ancak MSBuild bu yapılandırmaya Visual Studio. Projeniz *veyamsbuild.exe* dosyanıza bir uygulama kullanarak, uygulamanın yüklenmemiş olduğu ortamlarda ürünleri Visual Studio ve derlemeniz gerekir.

 Visual Studio projeleri yüklemek ve derlemek için MSBuild kullanır. Visual Studio 'daki proje dosyaları (*.csproj*, *.vbproj*, *.vcxproj* ve diğerleri) IDE kullanarak bir proje derlemeniz zaman yürütülen MSBuild XML kodunu içerir. Visual Studio tüm gerekli ayarları ve derleme işlemlerini tipik geliştirme çalışmalarını yapmak için içeri aktarabilirsiniz, ancak bunları bir XML düzenleyicisini kullanarak Visual Studio veya değiştirebilirsiniz.

 C++ için MSBuild hakkında daha fazla bilgi için bkz. [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Aşağıdaki örneklerde, IDE'nin komut satırı yerine MSBuild'i ne zaman Visual Studio gösterebilirsiniz.

- Visual Studio yüklü değil. ([MSBuild'i Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools)indirin.)

- MSBuild'in 64 bit sürümünü kullanmak istiyor siniz. MSBuild'in bu sürümü genellikle gereksizdir, ancak MSBuild'in daha fazla belleğe erişmesi için izin verir.

- Bir derlemeyi birden çok işlemde çalıştırmak istediğiniz. Ancak, C++ ve C# projelerinde aynı sonucu elde etmek için IDE'yi kullanabilirsiniz.

- Derleme sistemini değiştirmek istediğiniz. Örneğin, aşağıdaki eylemleri etkinleştirmek istiyor olabilir:

  - Dosyaları derleyiciye ulaşmadan önce ön işleme.

  - Yapı çıktılarını farklı bir yere kopyalayın.

  - Derleme çıktılarından sıkıştırılmış dosyalar oluşturun.

  - İşlem sonrası bir adım yapın. Örneğin, bir derlemeyi farklı bir sürümle damgalamak isteyebilirsiniz.

Visual Studio IDE 'de kod yazabilir, ancak MSBuild kullanarak yapıları çalıştırabilirsiniz. Başka bir alternatif olarak, geliştirme bilgisayarında IDE 'de kod oluşturabilir, ancak birden çok geliştiriciden tümleştirilmiş kod oluşturmak için komut satırından MSBuild 'i çalıştırabilirsiniz. .NET Core projeleri oluşturmak için MSBuild 'i kullanan [.NET Core komut satırı arabirimi 'ni (CLI)](/dotnet/core/tools/)de kullanabilirsiniz.

> [!NOTE]
> Uygulamanızı otomatik olarak derlemek, test etmek ve dağıtmak için Azure Pipelines kullanabilirsiniz. Derleme sisteminiz, geliştiriciler kod iade edildiğinde (örneğin, sürekli tümleştirme stratejisinin bir parçası olarak) veya bir zamanlamaya göre (örneğin, gecelik bir derleme doğrulama test derlemesi), yapıları otomatik olarak çalıştırabilir. Azure Pipelines, MSBuild kullanarak kodunuzu derler. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Bu makalede MSBuild 'e genel bakış sunulmaktadır. Tanıtım öğreticisi için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Bir komut isteminde MSBuild kullanma

 MSBuild 'i komut isteminde çalıştırmak için, uygun komut satırı seçenekleriyle birlikte *MSBuild.exe* bir proje dosyası geçirin. Komut satırı seçenekleri özellikleri ayarlamanıza, belirli hedefleri yürütmenizi ve yapı sürecini denetleyen diğer seçenekleri ayarlamanıza olanak sağlar. Örneğin, özelliği olarak ayarlanmış *myproj. proj* dosyasını oluşturmak için aşağıdaki komut satırı sözdizimini kullanın `Configuration` `Debug` .

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 MSBuild komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Bir projeyi indirmadan önce kodun güvenilirliğini saptayın.

## <a name="project-file"></a>Proje dosyası

 MSBuild, basit ve Genişletilebilir olan XML tabanlı bir proje dosyası biçimi kullanır. MSBuild proje dosyası biçimi, geliştiricilerin oluşturulacak öğeleri ve ayrıca farklı işletim sistemleri ve yapılandırmalara yönelik olarak nasıl derlenmelerini betimler. Buna ek olarak, proje dosyası biçimi, geliştiricilerin ayrı dosyalara ayrılabildiği yeniden kullanılabilir derleme kuralları yazarlarına olanak tanıyarak, derlemelerin üründeki farklı projelerde tutarlı bir şekilde gerçekleştirilmesini sağlar.

 Aşağıdaki bölümlerde MSBuild proje dosyası biçiminin bazı temel öğeleri açıklanır. Temel proje dosyası oluşturma hakkında bir öğretici için, bkz. [Izlenecek yol: bir MSBuild proje dosyası sıfırdan oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

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

 Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Öğeler

 Öğeler, derleme sistemine giriş ve genellikle dosyaları temsil eder. Öğeler, Kullanıcı tanımlı öğe adlarına göre öğe türlerine göre gruplandırılır. Bu öğe türleri, oluşturma işleminin adımlarını gerçekleştirmek için bireysel öğeleri kullanan görevler için parametre olarak kullanılabilir.

 Öğeler, öğe türünün adı bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğesi olan bir öğe oluşturularak proje dosyasında belirtilir. Örneğin, aşağıdaki kod iki dosya içeren `Compile` adlı bir öğe türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Öğe türlerine proje dosyası boyunca @( söz dizimi kullanılarak \<ItemType> başvurulabilirsiniz. Örneğin, örnekteki öğe türüne kullanılarak `@(Compile)` başvurulabilirsiniz.

 MSBuild'de öğe ve öznitelik adları büyük/büyük/büyük harfe duyarlıdır. Ancak özellik, öğe ve meta veri adları değildir. Aşağıdaki örnek , veya başka bir büyük/küçük harf varyasyonu öğe türünü oluşturur ve öğe türüne `Compile` `comPile` "one.cs;two.cs" değerini verir.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Öğeler joker karakterler kullanılarak bildirebilirsiniz ve daha gelişmiş derleme senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Görev

 Görevler, MSBuild projelerinin derleme işlemlerini gerçekleştirmek için kullanabileceği yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derler veya bir dış araç çalıştırabilirsiniz. Görevler yeniden kullanılabilir ve farklı projelerde farklı geliştiriciler tarafından paylaşılır.

 Bir görevin yürütme mantığı yönetilen kodda yazılır ve [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi kullanılarak MSBuild'e eşilir. Arabirimi uygulayan bir yönetilen tür yazarak kendi görevinizi <xref:Microsoft.Build.Framework.ITask> yazabilirsiniz. Görevleri yazma hakkında daha fazla bilgi için bkz. [Görev yazma.](../msbuild/task-writing.md)

 MSBuild, gereksinimlerinize uyacak şekilde değiştirebilirsiniz ortak görevleri içerir. Örnek [olarak,](../msbuild/copy-task.md)dosyaları kopyalayıp dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve Visual C# kaynak kodu dosyalarını derleye [Csc](../msbuild/csc-task.md)örnek olarak verilmiştir. Kullanılabilir görevlerin kullanım bilgileriyle birlikte listesi için bkz. [Görev başvurusu.](../msbuild/msbuild-task-reference.md)

 Görev, bir Hedef öğenin alt öğesi olarak görev adına sahip bir öğe oluşturarak MSBuild proje dosyasında [yürütülür.](../msbuild/target-element-msbuild.md) Görevler genellikle öğesinin öznitelikleri olarak geçirilen parametreleri kabul eder. MSBuild özellikleri ve öğeleri parametre olarak kullanılabilir. Örneğin, aşağıdaki kod [MakeDir](../msbuild/makedir-task.md) görevini çağırır ve `BuildDir` Önceki örnekte belirtilen özelliğin değerini geçirir.

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

 Yapılandırma hatalarını, uyarıları ve iletileri konsola veya başka bir çıkış cihazına kaydedebilirsiniz. Daha fazla bilgi için bkz. [MSBuild 'de](../msbuild/logging-in-msbuild.md) [derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md) ve günlüğü alma.

## <a name="use-msbuild-in-visual-studio"></a>Visual Studio 'da MSBuild 'i kullanma

 Visual Studio, yönetilen projeler hakkında yapı bilgilerini depolamak için MSBuild proje dosyası biçimini kullanır. Visual Studio arabirimi kullanılarak eklenen veya değiştirilen proje ayarları, içinde yansıtılır *. \** her proje için oluşturulan proj dosyası. Visual Studio yönetilen projeler oluşturmak için MSBuild 'in barındırılan bir örneğini kullanır. Bu, yönetilen bir projenin Visual Studio komut isteminde (Visual Studio yüklü olsa bile) ve sonuçların aynı olacağını ifade ediyor.

 Visual Studio'da MSBuild'i kullanma hakkında bir öğretici için, bkz. [Walkthrough: USING MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Çoklu hedef

 Bu Visual Studio kullanarak, bir uygulamayı derlemek için uygulamanın farklı sürümlerinden herhangi biri üzerinde .NET Framework. Örneğin, bir uygulamayı 32 bitlik bir platformda .NET Framework 2.0 üzerinde çalıştıracak şekilde derleyebilirsiniz ve aynı uygulamayı 64 bitlik bir platformda .NET Framework 4.5 üzerinde çalıştıracak şekilde derleyebilirsiniz. Birden fazla çerçeveye derleme özelliği multitargeting olarak adlandırılmıştır.

 Çoklu hedeflere sahip olmak için aşağıdaki avantajlardan faydalanır:

- 2.0, 3.0 ve 3.5 gibi önceki .NET Framework sürümlerini hedef alan uygulamalar geliştirebilirsiniz.

- Silverlight gibi diğer .NET Framework çerçeveleri hedefleysiniz.

- Hedef çerçevenin *önceden tanımlanmış* bir alt kümesi olan bir çerçeve profilini hedefleyebilirsiniz.

- Geçerli sürümüne yönelik bir hizmet paketi .NET Framework, bunu hedefleyabilirsiniz.

- Çoklu hedefleme, bir uygulamanın yalnızca hedef çerçevede ve platformda kullanılabilen işlevleri kullanmalarını garantiler.

Daha fazla bilgi için [bkz. Çoklu Hedef.](../msbuild/msbuild-multitargeting-overview.md)

## <a name="see-also"></a>Ayrıca bkz.

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Yalnızca bir metin düzenleyicisi kullanarak, temel bir proje dosyasının artımlı olarak nasıl oluşturul olduğunu gösterir. |
| [İzlenecek yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md) | MSBuild'in yapı taşlarını tanıtarak, IDE'yi kapatmadan MSBuild projelerini yazma, işleme ve Visual Studio gösterir. |
| [MSBuild kavramları](../msbuild/msbuild-concepts.md) | MSBuild'in dört yapı taşlarını sunar: özellikler, öğeler, hedefler ve görevler. |
| [Öğeler](../msbuild/msbuild-items.md) | MSBuild dosya biçiminin ardındaki genel kavramları ve parçaların nasıl bir araya sığacaklarını açıklar. |
| [MSBuild özellikleri](../msbuild/msbuild-properties.md) | Özellikler ve özellik koleksiyonları sunar. Özellikler, derlemeleri yapılandırmak için kullanılan anahtar/değer çiftleridir. |
| [Targets](../msbuild/msbuild-targets.md) | Görevleri belirli bir sırada grupla ve derleme işleminin bölümlerinin komut satırı üzerinde çağrılmalarını etkinleştirmeyi açıklar. |
| [Görevler](../msbuild/msbuild-tasks.md) | Atomik derleme işlemleri gerçekleştirmek için MSBuild tarafından kullanılabilecek bir yürütülebilir kod birimi oluşturmayı gösterir. |
| [Koşullar](../msbuild/msbuild-conditions.md) | `Condition`Bir MSBuild öğesinde özniteliğin nasıl kullanılacağını açıklar. |
| [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md) | Toplu işleme, dönüşümler gerçekleştirme, Çoklu hedefleme ve diğer gelişmiş teknikleri gösterir. |
| [MSBuild'de Günlük Kaydı](../msbuild/logging-in-msbuild.md) | Oluşturma olaylarının, iletilerinin ve hatalarının nasıl günlüğe alınacağını açıklar. |
| [MSBuild nasıl proje oluşturur](build-process-overview.md) | MSBuild içinde kullanılan iç derleme işlemini açıklar |
| [Ek Kaynaklar](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | MSBuild hakkında daha fazla bilgi için topluluk ve destek kaynaklarını listeler. |

## <a name="reference"></a>Başvuru

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)\
 Başvuru bilgilerini içeren konuların bağlantıları.

- [Sözlüğü](msbuild-glossary.md)\
 Ortak MSBuild koşullarını tanımlar.
