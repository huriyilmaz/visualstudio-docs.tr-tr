---
title: MSBuild | Microsoft Docs
description: Microsoft Build Engine (MSBuild) platformunun derlemeleri denetlemeye olanak sağlayan bir XML şemasına sahip bir proje dosyası sağladığını öğrenin.
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
ms.openlocfilehash: 1703f915203a7e91176117571442b2d1b171d76e
ms.sourcegitcommit: 3cfe24a74b611440b831d9591e067874c51a3bfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "130087390"
---
# <a name="msbuild"></a>MSBuild

Bu Microsoft Build Engine, uygulamalar için bir platformdur. MSBuild olarak da bilinen bu altyapı, derleme platformunun yazılım işleme ve derleme işlemlerini kontrol eden bir proje dosyası için bir XML şeması sağlar. Visual Studio, MSBuild kullanır, MSBuild veri türüne Visual Studio. Projeniz *msbuild.exe* çözüm dosyanıza bir uygulama kullanarak, uygulamanın yüklenmemiş olduğu ortamlarda Visual Studio ve derlemeniz gerekir.

Visual Studio yönetilen MSBuild yüklemek ve derlemek için MSBuild kullanır. Visual Studio (*.csproj*, *.vbproj*, *.vcxproj* ve diğerleri) proje dosyaları, IDE kullanarak bir proje derlemeniz zaman yürütülen MSBuild XML kodunu içerir. Visual Studio tüm gerekli ayarları ve derleme işlemlerini tipik geliştirme çalışmaları yapmak için içeri aktarabilirsiniz, ancak bunları bir XML düzenleyicisi kullanarak veya Visual Studio içinde genişletebilirsiniz veya değiştirebilirsiniz.

::: moniker range=">=vs-2022"
Visual Studio 2022'den başlayarak, Visual Studio'de derleme 64 bit MSBuild kullanılır.
::: moniker-end

C++ için MSBuild bilgi için bkz. [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

Aşağıdaki örnekler, IDE yerine komut MSBuild derlemeleri ne zaman çalıştırabilirsiniz Visual Studio göstermektedir.

- Visual Studio yüklü değil. ([MSBuild olmadan Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools)indirin.)

- MSBuild'nin 64 bit sürümünü kullanmak ve Visual Studio 2019 veya önceki bir sürümü kullanıyorsanız. Bu MSBuild genellikle gereksizdir, ancak daha fazla belleğe MSBuild izin verir.

- Bir derlemeyi birden çok işlemde çalıştırmak istediğiniz. Ancak, C++ ve C# projelerinde aynı sonucu elde etmek için IDE'yi kullanabilirsiniz.

- Derleme sistemini değiştirmek istediğiniz. Örneğin, aşağıdaki eylemleri etkinleştirmek istiyor olabilir:

  - Dosyaları derleyiciye ulaşmadan önce ön işleme.

  - Derleme çıkışlarını farklı bir yere kopyalayın.

  - Derleme çıkışlarından sıkıştırılmış dosyalar oluşturun.

  - İşleme sonrası adımını yapma. Örneğin, bir derlemeyi farklı bir sürümle damgalamak istiyor olabilir.

IDE'de kod Visual Studio ancak derlemeleri çalıştırmak için MSBuild. Başka bir alternatif olarak, IDE'de bir geliştirme bilgisayarına kod oluşturabilirsiniz ancak birden çok MSBuild tümleştirilmiş kod derlemek için komut MSBuild çalıştırabilirsiniz. .NET Core projeleri derlemek için MSBuild kullanan .NET Core komut satırı [arabirimini (CLI)](/dotnet/core/tools/)de kullanabilirsiniz.

> [!NOTE]
> Uygulamanızı otomatik Azure Pipelines, test etmek ve dağıtmak için Azure Pipelines'yi kullanabilirsiniz. Derleme sisteminiz, geliştiriciler kodu iade edince (örneğin, Sürekli Tümleştirme stratejisinin bir parçası olarak) veya bir zaman çizelgesine (örneğin, gecelik Derleme Doğrulama Testi derlemesi) göre derlemeleri otomatik olarak çalıştırabilir. Azure Pipelines kullanarak kodunuzu derler MSBuild. Daha fazla bilgi için [bkz. Azure Pipelines.](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

Bu makalede, genel bakış ve MSBuild. Giriş niteliğindeki bir öğretici için [bkz. Adım adım kılavuz: MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="use-msbuild-at-a-command-prompt"></a>Komut MSBuild komut isteminde komut satırı kullanma

 Komut isteminde MSBuild çalıştırmak için, uygun komut satırı *seçenekleriyleMSBuild.exe*'ye bir proje dosyası iletirsiniz. Komut satırı seçenekleri özellikleri ayarlamaya, belirli hedefleri yürütmeye ve derleme işlemini kontrol altına alan diğer seçenekleri ayarlamaya olanak sağlar. Örneğin, *myProj.proj* dosyasını özelliği olarak ayarlanmış şekilde oluşturmak için aşağıdaki komut satırı söz `Configuration` dizimlerini `Debug` kullanabilirsiniz.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Komut satırı seçeneklerini MSBuild daha fazla bilgi için [bkz. Komut satırı başvurusu.](../msbuild/msbuild-command-line-reference.md)

> [!IMPORTANT]
> Projeyi indirmeden önce kodun güvenilirliğini belirleme.

## <a name="project-file"></a>Project dosyası

 MSBuild, basit ve genişletilebilir XML tabanlı bir proje dosyası biçimi kullanır. Bu MSBuild dosyası biçimi, geliştiricilerin, farklı işletim sistemleri ve yapılandırmalar için nasıl geliştir edileceklerini ve nasıl oluşturacaklarını açıklamalarını sağlar. Buna ek olarak, proje dosyası biçimi geliştiricilerin derlemelerin üründe farklı projeler arasında tutarlı bir şekilde gerçekleştirilemeleri için ayrı dosyalarda dikkate alınarak yeniden kullanılabilir derleme kuralları yazmalarına olanak sağlar.

 Derleme Visual Studio, projeye özgü mantığı proje dosyanıza depolar ve standart derleme mantığını tanımlamak için *.props* ve *.targets* gibi uzantılara sahip içe aktarılan MSBuild XML dosyalarını kullanır. *.props dosyaları,* MSBuild özelliklerini, *.targets* dosyaları ise MSBuild tanımlar. Bu içeri aktarmalar bazen Visual Studio proje dosyasında görünür, ancak .NET Core, .NET 5 ve .NET 6 projeleri gibi daha yeni projelerde proje dosyasında içeri aktarmaları görmüyorsanız; bunun yerine, bir SDK başvurusu görüyorsunuz. Bunlar SDK stili projeler olarak adlandırılır. .NET SDK gibi bir SDK'ya başvurarak .props ve .target dosyalarının içeri aktarmaları SDK tarafından örtülü olarak belirtilir.

 Aşağıdaki bölümlerde, proje dosyası biçimindeki temel MSBuild açıklanmaktadır. Temel proje dosyası oluşturma hakkında bir öğretici için bkz. Kılavuz: Sıfırdan [MSBuild proje dosyası oluşturma.](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

### <a name="properties"></a><a name="BKMK_Properties"></a> Özellikler

 Özellikler, derlemeleri yapılandırmak için kullanılan anahtar/değer çiftlerini temsil ediyor. Özellikler, bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesinin alt öğesi olarak özelliğin adına sahip bir öğe oluşturarak bildirildi. Örneğin, aşağıdaki kod değerine sahip `BuildDir` adlı bir özellik `Build` oluşturur.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 öğesine öznitelik yerleştirerek koşullu olarak bir `Condition` özellik tanımlayabilirsiniz. Koşul olarak değerlendirilmediği sürece koşullu öğelerin içeriği `true` yoksayılır. Aşağıdaki örnekte, `Configuration` henüz tanımlanmamışsa öğesi tanımlanmıştır.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Özelliklere proje dosyası boyunca $( söz dizimi kullanılarak \<PropertyName> başvurulabilirsiniz. Örneğin, ve kullanarak önceki örneklerde yer alan özelliklere `$(BuildDir)` `$(Configuration)` başvurabilirsiniz.

 Özellikler hakkında daha fazla bilgi için [bkz. MSBuild.](../msbuild/msbuild-properties.md)

### <a name="items"></a><a name="BKMK_Items"></a> Bileşen

 Öğeler derleme sistemine giriştir ve genellikle dosyaları temsil eder. Öğeler, kullanıcı tanımlı öğe adlarına göre öğe türleri olarak gruplandı. Bu öğe türleri, derleme işleminin adımlarını gerçekleştirmek için tek tek öğeleri kullanan görevler için parametre olarak kullanılabilir.

 Öğeler, öğe türünün adı bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğesi olarak olan bir öğe oluşturarak proje dosyasında bildirildi. Örneğin, aşağıdaki kod iki dosya içeren `Compile` adlı bir öğe türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Öğe türlerine proje dosyası boyunca @( söz dizimi kullanılarak \<ItemType> başvurulabilirsiniz. Örneğin, örnekteki öğe türüne kullanılarak `@(Compile)` başvurulabilirsiniz.

 Bu MSBuild, öğe ve öznitelik adları büyük/büyük/büyük harfe duyarlıdır. Ancak özellik, öğe ve meta veri adları değildir. Aşağıdaki örnek , veya başka bir büyük/küçük harf varyasyonu öğe türünü oluşturur ve öğe türüne `Compile` `comPile` "one.cs;two.cs" değerini verir.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Öğeler joker karakterler kullanılarak bildirebilirsiniz ve daha gelişmiş derleme senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Görev

 Görevler, projelerin derleme işlemlerini gerçekleştirmek için MSBuild yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derler veya bir dış araç çalıştırabilirsiniz. Görevler yeniden kullanılabilir ve farklı projelerde farklı geliştiriciler tarafından paylaşılır.

 Bir görevin yürütme mantığı yönetilen kodda yazılır ve [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi MSBuild ile eşlenmiş. Arabirimi uygulayan bir yönetilen tür yazarak kendi görevinizi <xref:Microsoft.Build.Framework.ITask> yazabilirsiniz. Görevleri yazma hakkında daha fazla bilgi için bkz. [Görev yazma.](../msbuild/task-writing.md)

 MSBuild gereksinimlerinize uyacak şekilde değiştirebilirsiniz ortak görevleri içerir. Örnek [olarak,](../msbuild/copy-task.md)dosyaları kopyalayıp dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve Visual C# kaynak kodu dosyalarını derleye [Csc](../msbuild/csc-task.md)örnek olarak verilmiştir. Kullanılabilir görevlerin kullanım bilgileriyle birlikte listesi için bkz. [Görev başvurusu.](../msbuild/msbuild-task-reference.md)

 Bir görev, bir MSBuild hedef öğenin alt öğesi olarak görev adına sahip bir öğe oluşturarak bir proje dosyasında [yürütülür.](../msbuild/target-element-msbuild.md) Görevler genellikle öğesinin öznitelikleri olarak geçirilen parametreleri kabul eder. Hem MSBuild özellikleri hem de öğeleri parametre olarak kullanılabilir. Örneğin, aşağıdaki kod [MakeDir](../msbuild/makedir-task.md) görevini çağırarak önceki örnekte bildirilen `BuildDir` özelliğin değerini iletir.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Görevler hakkında daha fazla bilgi için bkz. [Görevler.](../msbuild/msbuild-tasks.md)

### <a name="targets"></a><a name="BKMK_Targets"></a> Hedef

 Grup görevlerini belirli bir sırada birlikte hedefler ve proje dosyasının bölümlerini derleme sürecine giriş noktaları olarak sunar. Hedefler genellikle okunabilirliği artırmak ve genişlemeye olanak sağlamak için mantıksal bölümler halinde gruplanmıştır. Derleme adımlarını hedeflere bozmak, kodun bu bölümünü her hedefe kopyalamadan derleme işleminin bir parçasını diğer hedeflerden çağırmaya olanak sağlar. Örneğin, derleme işleminin birkaç giriş noktasının oluşturulacak başvurular gerektirmesi, başvuruların oluşturulacak bir hedef oluşturması ve ardından bu hedefi gerekli olduğu her giriş noktasından çalıştırması gerekir.

 Hedefler, Target öğesi kullanılarak proje dosyasında [bildirildi.](../msbuild/target-element-msbuild.md) Örneğin, aşağıdaki kod adlı bir hedef oluşturur ve daha sonra önceki örnekte bildirilen öğe listesine sahip `Compile` [Csc](../msbuild/csc-task.md) görevini çağıran.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Daha gelişmiş senaryolarda hedefler, aralarındaki ilişkileri tanımlamak ve bağımlılık analizi gerçekleştirmek için kullanılabilir. Böylece, hedef güncelse derleme işleminin tüm bölümleri atlanabilir. Hedefler hakkında daha fazla bilgi için bkz. [Hedefler.](../msbuild/msbuild-targets.md)

## <a name="build-logs"></a>Derleme günlükleri

 Derleme hatalarını, uyarıları ve iletileri konsola veya başka bir çıkış cihazına günlüğe alabilirsiniz. Daha fazla bilgi için [bkz. Derleme günlüklerini alma](../msbuild/obtaining-build-logs-with-msbuild.md) [ve](../msbuild/logging-in-msbuild.md)MSBuild.

## <a name="use-msbuild-in-visual-studio"></a>MSBuild'de Visual Studio

 Visual Studio, yönetilen MSBuild derleme bilgilerini depolamak için MSBuild proje dosyası biçimini kullanır. Project arabirimi kullanılarak eklenen veya değiştirilen Visual Studio ayarları içinde *yansıtıldı. \* her* proje için oluşturulan proj dosyası. Visual Studio yönetilen projeler derlemek için MSBuild barındırılan bir örnek kullanır. Bu, yönetilen bir projenin Visual Studio komut isteminde (Visual Studio yüklü olsa bile) ve sonuçların aynı olacağını ifade ediyor.

 Visual Studio'de MSBuild kullanma hakkında bir öğretici için bkz. [MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Çoklu hedef

 Bir Visual Studio kullanarak, bir uygulamayı derlemek için uygulamanın çeşitli sürümlerinden herhangi biri üzerinde .NET Framework. Örneğin, bir uygulamayı 32 bitlik bir platformda .NET Framework 2.0'da çalıştıracak şekilde derleyebilirsiniz ve aynı uygulamayı 64 bitlik bir platformda .NET Framework 4.5 üzerinde çalıştıracak şekilde derleyebilirsiniz. Birden fazla çerçeveye derleme özelliği multitargeting olarak adlandırılmıştır.

 Çoklu hedeflere sahip olmak için aşağıdaki avantajlardan faydalanır:

- 3.5 ve 4.7.2 gibi .NET Framework önceki sürümlerini hedef alan uygulamalar geliştirebilirsiniz.

- Hedef çerçevenin *önceden tanımlanmış* bir alt kümesi olan bir çerçeve profilini hedefleyebilirsiniz.

- Geçerli sürümü için bir hizmet paketi .NET Framework, hedefleyabilirsiniz.

- Çoklu hedefleme, bir uygulamanın yalnızca hedef çerçevede ve platformda kullanılabilen işlevleri kullanmalarını garantiler.

Daha fazla bilgi için [bkz. Çoklu Hedef.](../msbuild/msbuild-multitargeting-overview.md)

## <a name="see-also"></a>Ayrıca bkz.

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Yalnızca bir metin düzenleyicisi kullanarak, temel bir proje dosyasının artımlı olarak nasıl oluşturul olduğunu gösterir. |
| [İzlenecek yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md) | IDE'nin yapı taşlarını MSBuild, IDE'yi kapatmadan projelerde yazma, işleme ve MSBuild ayıklamayı Visual Studio gösterir. |
| [MSBuild kavramları](../msbuild/msbuild-concepts.md) | Özelliklerin, öğelerin, MSBuild görevlerin dört yapı taşlarını sunar. |
| [Öğeler](../msbuild/msbuild-items.md) | Dosya biçimini ve parçaların nasıl MSBuild temel kavramları açıklar. |
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
