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
ms.openlocfilehash: e93e7d30a194df70260ef010b81c3026299f8565
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76923316"
---
# <a name="msbuild"></a>MSBuild

[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)], uygulama oluşturmaya yönelik bir platformdur. MSBuild olarak da bilinen bu altyapı, derleme platformunun yazılım işleme ve derleme şeklini denetleyen bir proje dosyası için bir XML şeması sağlar. Visual Studio MSBuild kullanır, ancak MSBuild, Visual Studio 'ya bağlı değildir. Proje veya çözüm dosyanızda *MSBuild. exe* ' yi çağırarak, ürünleri Visual Studio 'nun yüklü olmadığı ortamlarda düzenleyebilir ve oluşturabilirsiniz.

 Visual Studio, yönetilen projeleri yüklemek ve derlemek için MSBuild 'i kullanır. Visual Studio 'daki proje dosyaları ( *. csproj*, *. vbproj*, *. vcxproj*ve diğerleri), IDE kullanarak bir proje oluşturduğunuzda yürütülen MSBuild xml kodunu içerir. Visual Studio projeleri tipik geliştirme işlerini yapmak için gerekli tüm ayarları ve derleme süreçlerini içeri aktarır, ancak bunları Visual Studio içinden genişletebilir veya bir XML Düzenleyicisi kullanarak değiştirebilirsiniz.

 MSBuild C++hakkında daha fazla bilgi için bkz. [MSBuildC++()](/cpp/build/msbuild-visual-cpp).

 Aşağıdaki örneklerde, Visual Studio IDE yerine komut satırından MSBuild 'i çağırarak derlemeleri nasıl çalıştırabileceğiniz gösterilmektedir.

- Visual Studio yüklü değil. ([Visual Studio olmadan MSBuild 'ı indirin](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- MSBuild 'in 64 bitlik sürümünü kullanmak istiyorsunuz. MSBuild 'in bu sürümü genellikle gereksizdir, ancak MSBuild 'in daha fazla belleğe erişmesine izin verir.

- Bir derlemeyi birden çok işlemde çalıştırmak istiyorsunuz. Ancak, ve C++ C#içindeki projelerde aynı sonuca ulaşmak için IDE 'yi kullanabilirsiniz.

- Yapı sistemini değiştirmek istiyorsunuz. Örneğin, aşağıdaki eylemleri etkinleştirmek isteyebilirsiniz:

  - Dosyaları derleyiciye ulaşmadan önce ön işleme.

  - Yapı çıktılarını farklı bir yere kopyalayın.

  - Derleme çıktılarından sıkıştırılmış dosyalar oluşturun.

  - İşlem sonrası bir adım yapın. Örneğin, bir derlemeyi farklı bir sürümle damgalamak isteyebilirsiniz.

Visual Studio IDE 'de kod yazabilir, ancak MSBuild kullanarak yapıları çalıştırabilirsiniz. Başka bir alternatif olarak, geliştirme bilgisayarında IDE 'de kod oluşturabilir, ancak birden çok geliştiriciden tümleştirilmiş kod oluşturmak için komut satırından MSBuild 'i çalıştırabilirsiniz. .NET Core projeleri oluşturmak için MSBuild 'i kullanan [.NET Core komut satırı arabirimi 'ni (CLI)](/dotnet/core/tools/)de kullanabilirsiniz.

> [!NOTE]
> Uygulamanızı otomatik olarak derlemek, test etmek ve dağıtmak için Azure Pipelines kullanabilirsiniz. Derleme sisteminiz, geliştiriciler kod iade edildiğinde (örneğin, sürekli tümleştirme stratejisinin bir parçası olarak) veya bir zamanlamaya göre (örneğin, gecelik bir derleme doğrulama test derlemesi), yapıları otomatik olarak çalıştırabilir. Azure Pipelines, MSBuild kullanarak kodunuzu derler. Daha fazla bilgi için [Azure işlem hatları](/azure/devops/pipelines/index?view=vsts).

Bu makalede MSBuild 'e genel bakış sunulmaktadır. Tanıtım öğreticisi için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Bir komut isteminde MSBuild kullanma
 Bir komut isteminde [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] çalıştırmak için, uygun komut satırı seçenekleriyle birlikte *MSBuild. exe*' ye bir proje dosyası geçirin. Komut satırı seçenekleri özellikleri ayarlamanıza, belirli hedefleri yürütmenizi ve yapı sürecini denetleyen diğer seçenekleri ayarlamanıza olanak sağlar. Örneğin, `Configuration` özelliği `Debug`olarak ayarlanan *myproj. proj* dosyasını oluşturmak için aşağıdaki komut satırı sözdizimini kullanın.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] komut satırı seçenekleri hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Bir projeyi indirmadan önce kodun güvenilirliğini saptayın.

## <a name="project-file"></a>Proje dosyası
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], basit ve genişletilebilir bir XML tabanlı proje dosyası biçimi kullanır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası biçimi, geliştiricilerin oluşturulacak öğeleri ve ayrıca farklı işletim sistemleri ve yapılandırmalara yönelik olarak nasıl derlenmelerini betimler. Buna ek olarak, proje dosyası biçimi, geliştiricilerin ayrı dosyalara ayrılabildiği yeniden kullanılabilir derleme kuralları yazarlarına olanak tanıyarak, derlemelerin üründeki farklı projelerde tutarlı bir şekilde gerçekleştirilmesini sağlar.

 Aşağıdaki bölümlerde [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası biçiminin bazı temel öğeleri açıklanır. Temel proje dosyası oluşturma hakkında bir öğretici için, bkz. [Izlenecek yol: bir MSBuild proje dosyası sıfırdan oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="BKMK_Properties"></a>Özelliklerinin
 Özellikler, yapıları yapılandırmak için kullanılabilen anahtar/değer çiftlerini temsil eder. Özellikler, bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesinin alt öğesi olarak özelliğin adına sahip bir öğe oluşturularak belirtilir. Örneğin, aşağıdaki kod, `Build`değerine sahip `BuildDir` adlı bir özellik oluşturur.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Öğesine bir `Condition` özniteliği yerleştirerek koşullu bir özellik tanımlayabilirsiniz. Koşul `true`olarak değerlendirilmediği takdirde koşullu öğelerin içeriği yoksayılır. Aşağıdaki örnekte, `Configuration` öğesi henüz tanımlanmadıysa tanımlanmıştır.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Özellikler, $ (\<PropertyName >) sözdizimi kullanılarak proje dosyası genelinde başvurulabilirler. Örneğin, `$(BuildDir)` ve `$(Configuration)`kullanarak önceki örneklerde bulunan özelliklere başvurabilirsiniz.

 Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

### <a name="BKMK_Items"></a>Öğeler
 Öğeler, derleme sistemine giriş ve genellikle dosyaları temsil eder. Öğeler, Kullanıcı tanımlı öğe adlarına göre öğe türlerine göre gruplandırılır. Bu öğe türleri, oluşturma işleminin adımlarını gerçekleştirmek için bireysel öğeleri kullanan görevler için parametre olarak kullanılabilir.

 Öğeler, öğe türünün adı bir [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğesi olan bir öğe oluşturularak proje dosyasında belirtilir. Örneğin, aşağıdaki kod iki dosya içeren `Compile`adlı bir öğe türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Öğe türlerine @ (\<ItemType >) sözdizimi kullanılarak proje dosyası içinde başvurulabilir. Örneğin, örnekteki öğe türüne `@(Compile)`kullanılarak başvurulur.

 MSBuild 'de, öğe ve öznitelik adları büyük/küçük harfe duyarlıdır. Ancak özellik, öğe ve meta veri adları değildir. Aşağıdaki örnek, `Compile`, `comPile`ya da başka bir örnek olarak öğe türünü oluşturur ve "bir. cs; Two. cs" değerini verir.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Öğeler joker karakterler kullanılarak bildirilebilecek ve daha gelişmiş derleme senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için bkz. [Items](../msbuild/msbuild-items.md).

### <a name="BKMK_Tasks"></a>Görevlerinize
 Görevler, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projelerin derleme işlemleri gerçekleştirmek için kullandığı çalıştırılabilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya bir dış araç çalıştırabilir. Görevler yeniden kullanılabilir ve farklı projelerde farklı geliştiriciler tarafından paylaşılabilir.

 Bir görevin yürütme mantığı yönetilen kodda yazılır ve [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi kullanılarak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] eşleştirilir. <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan yönetilen bir tür yazarak kendi görevinizi yazabilirsiniz. Görevlerin nasıl yazılacağı hakkında daha fazla bilgi için bkz. [görev yazma](../msbuild/task-writing.md).

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], gereksinimlerinize uyacak şekilde değiştirebileceğiniz ortak görevleri içerir. Örnekler, dosyaları kopyalayan, dizin oluşturan [MakeDir](../msbuild/makedir-task.md), ve Visual C# Source Code dosyalarını derleyen [CSC](../msbuild/csc-task.md)olan [kopyalardır](../msbuild/copy-task.md). Kullanım bilgileri ile birlikte kullanılabilir görevlerin bir listesi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

 Bir görev, bir [hedef](../msbuild/target-element-msbuild.md) öğenin alt öğesi olarak görevin adına sahip olan bir öğe oluşturarak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasında yürütülür. Görevler genellikle öğesinin öznitelikleri olarak geçirilen parametreleri kabul eder. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Özellikler ve öğeler, parametre olarak kullanılabilir. Örneğin, aşağıdaki kod [MakeDir](../msbuild/makedir-task.md) görevini çağırır ve önceki örnekte bildirildiği `BuildDir` özelliğinin değerini geçirir.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Görevler hakkında daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

### <a name="BKMK_Targets"></a>Lerden
 Hedefleri belirli bir sırada gruplar ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak kullanıma sunar. Hedefler, okunabilirliği artırmak ve genişletmeye izin vermek için genellikle mantıksal bölümler halinde gruplandırılır. Derleme adımlarının hedeflere bölünmesi, bu kod bölümünü her hedefe kopyalamadan, diğer hedeflerden derleme işleminin bir parçasını çağırmanıza olanak sağlar. Örneğin, yapı işlemine bazı giriş noktaları oluşturulması gerekiyorsa, başvuruları oluşturan bir hedef oluşturabilir ve bu hedefi, gereken her giriş noktasından çalıştırabilirsiniz.

 Hedefler, [hedef](../msbuild/target-element-msbuild.md) öğe kullanılarak proje dosyasında belirtilir. Örneğin, aşağıdaki kod `Compile`adlı bir hedef oluşturur ve daha sonra önceki örnekte belirtilen öğe listesine sahip olan [CSC](../msbuild/csc-task.md) görevini çağırır.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Daha Gelişmiş senaryolarda, hedefler bir diğeri arasındaki ilişkileri ve bağımlılık analizini gerçekleştirirken, bu hedefin güncel olması durumunda yapı işleminin bütün bölümlerinin atlanabilmesi için kullanılabilir. Hedefler hakkında daha fazla bilgi için bkz. [targets](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Derleme günlükleri
 Yapılandırma hatalarını, uyarıları ve iletileri konsola veya başka bir çıkış cihazına kaydedebilirsiniz. Daha fazla bilgi için bkz. [MSBuild 'de](../msbuild/logging-in-msbuild.md) [derleme günlükleri](../msbuild/obtaining-build-logs-with-msbuild.md) ve günlüğü alma.

## <a name="use-msbuild-in-visual-studio"></a>Visual Studio 'da MSBuild 'i kullanma
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], yönetilen projeler hakkında yapı bilgilerini depolamak için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosya biçimini kullanır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arabirimi kullanılarak eklenen veya değiştirilen proje ayarları, her proje için oluşturulan *.\*proj* dosyasında yansıtılır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yönetilen projeler oluşturmak için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] barındırılan bir örneğini kullanır. Bu, yönetilen bir projenin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya bir komut isteminde ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü olmasa bile) oluşturabileceğiniz anlamına gelir ve sonuçlar aynı olur.

 Visual Studio 'da MSBuild 'i kullanma hakkında bir öğretici için bkz. [Izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).

## <a name="BKMK_Multitargeting"></a>Çoklu sürüm desteği
 Visual Studio 'yu kullanarak, .NET Framework çeşitli sürümlerinden herhangi birini çalıştırmak için bir uygulamayı derleyebilirsiniz. Örneğin, bir uygulamayı 32 bit platformda .NET Framework 2,0 ' de çalışacak şekilde derleyebilir ve aynı uygulamayı bir 64-bit platformunda .NET Framework 4,5 üzerinde çalışacak şekilde derleyebilirsiniz. Birden fazla çerçeveye derleme yeteneği Çoklu hedefleme olarak adlandırılır.

 Çoklu hedefleme avantajlarından bazıları şunlardır:

- .NET Framework önceki sürümlerini hedefleyen uygulamalar geliştirebilirsiniz, örneğin 2,0, 3,0 ve 3,5 sürümleri.

- Örneğin, Silverlight gibi .NET Framework dışındaki çerçeveleri hedefleyebilirsiniz.

- Hedef çerçevenin önceden tanımlanmış bir alt kümesi olan bir *çerçeve profilini*hedefleyebilirsiniz.

- Geçerli .NET Framework sürümü için bir hizmet paketi yayınlanmışsa, hedefleyebilirsiniz.

- Çoklu hedefleme, bir uygulamanın yalnızca hedef çerçeve ve platformda kullanılabilir olan işlevleri kullanmasını güvence altına alır.

Daha fazla bilgi için [çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

| Başlık | Açıklama |
| - | - |
| [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Yalnızca bir metin düzenleyicisi kullanarak basit bir proje dosyasının artımlı olarak nasıl oluşturulacağını gösterir. |
| [İzlenecek Yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md) | MSBuild 'in yapı taşlarını tanıtır ve Visual Studio IDE 'yi kapatmadan MSBuild projelerinin nasıl yazılacağını, değiştirileceğini ve hata ayıklacağınızı gösterir. |
| [MSBuild kavramları](../msbuild/msbuild-concepts.md) | MSBuild: özellikler, öğeler, hedefler ve görevler için dört bina bloğunu gösterir. |
| [Öğeler](../msbuild/msbuild-items.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dosya biçiminin arkasındaki genel kavramları ve parçaların nasıl bir araya uyduğunu açıklar. |
| [MSBuild özellikleri](../msbuild/msbuild-properties.md) | Özellikleri ve özellik koleksiyonlarını tanıtır. Özellikler, yapıları yapılandırmak için kullanılabilen anahtar/değer çiftleridir. |
| [Hedefler](../msbuild/msbuild-targets.md) | Görevlerin belirli bir sırada nasıl gruplandırılacağını ve derleme işleminin bölümlerinin komut satırında çağrılacağını etkinleştirir. |
| [Görevler](../msbuild/msbuild-tasks.md) | Atomik derleme işlemleri gerçekleştirmek için [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarafından kullanılabilecek bir yürütülebilir kod birimi oluşturmayı gösterir. |
| [Koşullar](../msbuild/msbuild-conditions.md) | MSBuild öğesinde `Condition` özniteliğinin nasıl kullanılacağını açıklar. |
| [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md) | Toplu işleme, dönüşümler gerçekleştirme, Çoklu hedefleme ve diğer gelişmiş teknikleri gösterir. |
| [MSBuild'de Günlük Kaydı](../msbuild/logging-in-msbuild.md) | Oluşturma olaylarının, iletilerinin ve hatalarının nasıl günlüğe alınacağını açıklar. |
| [Ek kaynaklar](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | MSBuild hakkında daha fazla bilgi için topluluk ve destek kaynaklarını listeler. |

## <a name="reference"></a>Başvuru
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)\
 Başvuru bilgilerini içeren konuların bağlantıları.

- [Sözlük](msbuild-glossary.md)\
 Ortak MSBuild koşullarını tanımlar.
