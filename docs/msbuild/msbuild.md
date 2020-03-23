---
title: MSBuild | Microsoft Dokümanlar
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
ms.openlocfilehash: c2387526860b7d6da136a72cf83727f6714e2e52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633076"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine, uygulama oluşturmak için bir platformdur. MSBuild olarak da bilinen bu altyapı, yapı platformunun nasıl işlediğini ve yazılım oluşturduğunu kontrol eden bir proje dosyası için bir XML şeması sağlar. Visual Studio MSBuild kullanır, ancak MSBuild Visual Studio bağlı değildir. Proje veya çözüm dosyanıza *msbuild.exe'yi* çağırarak Visual Studio'nun yüklü olmadığı ortamlarda ürün düzenleyebilir ve oluşturabilirsiniz.

 Visual Studio, yönetilen projeleri yüklemek ve oluşturmak için MSBuild'i kullanır. Visual Studio'daki proje dosyaları (*.csproj*, *.vbproj*, *.vcxproj*, ve diğerleri) IDE'yi kullanarak bir proje oluşturduğunuzda çalıştıran MSBuild XML kodu içerir. Visual Studio projeleri, tipik geliştirme çalışmaları yapmak için gerekli tüm ayarları ve oluşturma işlemlerini içe aktarır, ancak Visual Studio içinden veya bir XML düzenleyicisi kullanarak bunları genişletebilir veya değiştirebilirsiniz.

 C++için MSBuild hakkında daha fazla bilgi için [bkz.](/cpp/build/msbuild-visual-cpp)

 Aşağıdaki örnekler, Visual Studio IDE yerine komut satırından MSBuild çağırarak ne zaman yapı çalıştırabileceğinizi göstermektedir.

- Visual Studio yüklü değil. (Visual[Studio olmadan MSBuild indirin](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- MSBuild'in 64 bit sürümünü kullanmak istiyorsunuz. MSBuild'in bu sürümü genellikle gereksizdir, ancak MSBuild'in daha fazla belleğe erişmesine izin verir.

- Bir yapıyı birden çok işlemde çalıştırmak istiyorsunuz. Ancak, C++ ve C#'daki projelerde aynı sonucu elde etmek için IDE'yi kullanabilirsiniz.

- Yapı sistemini değiştirmek istiyorsunuz. Örneğin, aşağıdaki eylemleri etkinleştirmek isteyebilirsiniz:

  - Derleyiciye ulaşmadan önce ön işlem dosyaları.

  - Yapı çıktılarını farklı bir yere kopyalayın.

  - Yapı çıktılarından sıkıştırılmış dosyalar oluşturun.

  - İşlem sonrası bir adım atın. Örneğin, bir derlemeyi farklı bir sürümle damgalamak isteyebilirsiniz.

Visual Studio IDE'ye kod yazabilirsiniz, ancak MSBuild kullanarak yapıyı çalıştırabilirsiniz. Başka bir alternatif olarak, geliştirme bilgisayarında IDE'de kod oluşturabilir, ancak birden çok geliştiriciden entegre edilmiş kod oluşturmak için komut satırından MSBuild çalıştırabilirsiniz. MSBuild kullanan [.NET Core komut satırı arabirimini (CLI)](/dotnet/core/tools/)de kullanarak .NET Core projeleri oluşturabilirsiniz.

> [!NOTE]
> Uygulamanızı otomatik olarak derlemek, sınamak ve dağıtmak için Azure Ardışık Hatlar'ı kullanabilirsiniz. Yapı sisteminiz, geliştiriciler kodu iade ettiğinde (örneğin, Sürekli Tümleştirme stratejisinin bir parçası olarak) veya bir zamanlamaya (örneğin, bir gecelik Yapı Doğrulama Testi yapısı) göre yapılar otomatik olarak çalıştırılabilir. Azure Pipelines, MSBuild'i kullanarak kodunuzu derler. Daha fazla bilgi için [Azure Ardışık Hatları'na](/azure/devops/pipelines/index?view=vsts)bakın.

Bu makalede, MSBuild genel bir bakış sağlar. Bir giriş öğreticisi için [Walkthrough: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md)' ya bakın.

## <a name="use-msbuild-at-a-command-prompt"></a>MSBuild komut isteminde kullanma

 MSBuild'i komut istemiyle çalıştırmak için, uygun komut satırı seçenekleriyle birlikte bir proje dosyasını *MSBuild.exe'ye*geçirin. Komut satırı seçenekleri, özellikleri ayarlamanızı, belirli hedefleri yürütmenizi ve yapı işlemini denetleyen diğer seçenekleri ayarlamanızı sağlar. Örneğin, aşağıdaki komut satırı sözdizimini *myProj.proj* dosyasını oluşturmak `Configuration` için `Debug`kullanırsınız.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 MSBuild komut satırı seçenekleri hakkında daha fazla bilgi için [Komut satırı başvurusuna](../msbuild/msbuild-command-line-reference.md)bakın.

> [!IMPORTANT]
> Bir projeyi karşıdan yüklemeden önce, kodun güvenilirliğini belirleyin.

## <a name="project-file"></a>Proje dosyası

 MSBuild, basit ve genişletilebilir XML tabanlı bir proje dosyası biçimi kullanır. MSBuild proje dosya biçimi, geliştiricilerin oluşturulacak öğeleri ve farklı işletim sistemleri ve yapılandırmaları için nasıl oluşturulacaklarını açıklamalarına olanak tanır. Buna ek olarak, proje dosya biçimi, geliştiricilerin, yapının üründeki farklı projeler arasında tutarlı bir şekilde gerçekleştirilebilmesi için ayrı dosyalara çarpanabilebilen yeniden kullanılabilir yapı kuralları yazmalarına olanak tanır.

 Aşağıdaki bölümlerde MSBuild proje dosya biçiminin bazı temel öğeleri açıklayınız. Temel bir proje dosyasının nasıl oluşturulabildiğini anlatan bir öğretici için [bkz.](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

### <a name="properties"></a><a name="BKMK_Properties"></a>Özellikler

 Özellikler, yapıyapılandırmak için kullanılabilecek anahtar/değer çiftlerini temsil eder. Özellikler, özellik grubunun bir [özelliğinin](../msbuild/propertygroup-element-msbuild.md) alt öğesi olarak adını içeren bir öğe oluşturarak bildirilir. Örneğin, aşağıdaki kod . değeri `BuildDir` olan bir `Build`özellik oluşturur

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Öğeye bir `Condition` öznitelik yerleştirerek bir özelliği koşullu olarak tanımlayabilirsiniz. Koşullu öğelerin içeriği, koşul değerlendirilmesi `true`sürece yoksayılır. Aşağıdaki örnekte, `Configuration` öğe henüz tanımlanmamışsa tanımlanır.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Özellikler,\<"PropertyName>) sözdizimi kullanılarak proje dosyası boyunca başvurulabilir. Örneğin, önceki örneklerdeki özellikleri kullanarak `$(BuildDir)` ve `$(Configuration)`.

 Özellikler hakkında daha fazla bilgi için [MSBuild özelliklerine](../msbuild/msbuild-properties.md)bakın.

### <a name="items"></a><a name="BKMK_Items"></a>Bileşen

 Öğeler yapı sistemine girer ve genellikle dosyaları temsil eder. Öğeler, kullanıcı tanımlı madde adlarına göre madde türlerine ayrılır. Bu madde türleri, yapı işleminin adımlarını gerçekleştirmek için tek tek öğeleri kullanan görevler için parametre olarak kullanılabilir.

 Öğeler, [itemgroup](../msbuild/itemgroup-element-msbuild.md) öğesinin alt öğesi olarak madde türünün adını içeren bir öğe oluşturarak proje dosyasında bildirilir. Örneğin, aşağıdaki kod iki dosya içeren `Compile`adlandırılmış bir madde türü oluşturur.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Madde türleri sözdizimi @(ItemType\<>) kullanılarak proje dosyası boyunca başvurulabilir. Örneğin, örnekteki madde türü kullanılarak `@(Compile)`başvurulmalıdır.

 MSBuild'te öğe ve öznitelik adları büyük/küçük harf duyarlıdır. Ancak, özellik, öğe ve meta veri adları değildir. Aşağıdaki örnek, madde türünü `Compile` `comPile`veya başka bir büyük/küçük harf varyasyonu oluşturur ve öğe türüne "one.cs;two.cs" değerini verir.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Öğeler joker karakter kullanılarak bildirilebilir ve daha gelişmiş yapı senaryoları için ek meta veriler içerebilir. Öğeler hakkında daha fazla bilgi için [Bkz. Öğeler.](../msbuild/msbuild-items.md)

### <a name="tasks"></a><a name="BKMK_Tasks"></a>Görev

 Görevler, MSBuild projelerinin yapı işlemleri gerçekleştirmek için kullandığı yürütülebilir kod birimleridir. Örneğin, bir görev giriş dosyalarını derleyebilir veya harici bir araç çalıştırabilir. Görevler yeniden kullanılabilir ve farklı projelerde farklı geliştiriciler tarafından paylaşılabilir.

 Bir görevin yürütme mantığı yönetilen kodla yazılır ve [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi kullanılarak MSBuild'e eşlenir. <xref:Microsoft.Build.Framework.ITask> Arabirimi uygulayan yönetilen bir tür yazarak kendi görevinizi yazabilirsiniz. Görevlerin nasıl yazılması hakkında daha fazla bilgi için [Görev yazısına](../msbuild/task-writing.md)bakın.

 MSBuild, gereksinimlerinize uyacak şekilde değiştirebileceğiniz yaygın görevleri içerir. Örnekler [kopya](../msbuild/copy-task.md)dosyaları, [MakeDir](../msbuild/makedir-task.md), dizinler oluşturur ve [Csc](../msbuild/csc-task.md), Visual C# kaynak kod dosyaları derleyen kopyavardır. Kullanılabilir görevlerin ve kullanım bilgilerinin listesi için [Görev başvurusuna](../msbuild/msbuild-task-reference.md)bakın.

 Görev, [Hedef](../msbuild/target-element-msbuild.md) öğenin alt öğesi olarak görevin adını taşıyan bir öğe oluşturarak MSBuild proje dosyasında yürütülür. Görevler genellikle öğenin öznitelikleri olarak geçirilen parametreleri kabul eder. Hem MSBuild özellikleri hem de öğeleri parametre olarak kullanılabilir. Örneğin, aşağıdaki kod [MakeDir](../msbuild/makedir-task.md) görevini çağırır ve önceki `BuildDir` örnekte bildirilen özelliğin değerini ona iletir.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Görevler hakkında daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

### <a name="targets"></a><a name="BKMK_Targets"></a>Hedef

 Görevleri belirli bir sırada gruplandırmayı hedefler ve proje dosyasının bölümlerini yapı işlemine giriş noktası olarak ortaya çıkarır. Hedefler genellikle okunabilirliği artırmak ve genişlemeye izin vermek için mantıksal bölümler halinde gruplandırılır. Yapı adımlarını hedeflere bölme, kod bölümünü her hedefe kopyalamadan yapı işleminin bir parçasını diğer hedeflerden aramanıza olanak tanır. Örneğin, yapı işlemine birkaç giriş noktası oluşturulacak başvurular gerektiriyorsa, referanslar oluşturan bir hedef oluşturabilir ve bu hedefi gerekli olan her giriş noktasından çalıştırabilirsiniz.

 Hedefler [Hedef](../msbuild/target-element-msbuild.md) öğesi kullanılarak proje dosyasında bildirilir. Örneğin, aşağıdaki kod, daha sonra `Compile`önceki örnekte bildirilen madde listesi olan [Csc](../msbuild/csc-task.md) görevi çağıran adlı bir hedef oluşturur.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 Daha gelişmiş senaryolarda, hedefler birbirleri arasındaki ilişkileri açıklamak ve bağımlılık çözümlemesi gerçekleştirmek için kullanılabilir, böylece bu hedef güncelse yapı işleminin tüm bölümleri atlanabilir. Hedefler hakkında daha fazla bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md)

## <a name="build-logs"></a>Günlükler oluşturma

 Yapı hatalarını, uyarıları ve iletileri konsola veya başka bir çıktı aygıtına günlüğe kaydedebilirsiniz. Daha fazla bilgi için yapı [günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md) ve [MSBuild'te günlüğe kaydetme'ye](../msbuild/logging-in-msbuild.md)bakın.

## <a name="use-msbuild-in-visual-studio"></a>MSBuild'i Visual Studio'da kullanma

 Visual Studio, yönetilen projeler hakkında yapı bilgilerini depolamak için MSBuild proje dosya biçimini kullanır. Visual Studio arabirimi *\* kullanılarak eklenen veya değiştirilen proje ayarları. *her proje için oluşturulan proj dosyası. Visual Studio yönetilen projeler oluşturmak için MSBuild barındırılan bir örnek kullanır. Bu, yönetilen bir projenin Visual Studio'da veya komut isteminde (Visual Studio yüklü olmasa bile) oluşturulabileceği ve sonuçların aynı olacağı anlamına gelir.

 Visual Studio'da MSBuild'in nasıl kullanılacağı yla ilgili bir öğretici için [Walkthrough: MSBuild'i kullanma](../msbuild/walkthrough-using-msbuild.md)' ya bakın.

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>Çoklu hedefleme

 Visual Studio'yu kullanarak,.NET Framework'ün çeşitli sürümlerinden herhangi birinde çalışacak bir uygulama derleyebilirsiniz. Örneğin, 32 bit platformda .NET Framework 2.0 üzerinde çalışacak bir uygulama derleyebilir ve aynı uygulamayı 64 bit platformda .NET Framework 4.5'te çalışacak şekilde derleyebilirsiniz. Birden fazla çerçeveyi derleme yeteneği çok hedefleme olarak adlandırılır.

 Çoklu hedeflemenin avantajlarından bazıları şunlardır:

- .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar geliştirebilirsiniz, örneğin, sürüm 2.0, 3.0 ve 3.5.

- .NET Framework dışındaki çerçeveleri hedefleyebilirsiniz, örneğin Silverlight.

- Hedef *çerçevenin*önceden tanımlanmış bir alt kümesi olan bir çerçeve profilini hedefleyebilirsiniz.

- .NET Framework'ün geçerli sürümü için bir hizmet paketi serbest bırakılırsa, bunu hedefleyebilirsiniz.

- Çoklu hedefleme, bir uygulamanın yalnızca hedef çerçeve de ve platformda kullanılabilen işlevselliği kullandığını garanti eder.

Daha fazla bilgi için [Multitargeting'e](../msbuild/msbuild-multitargeting-overview.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

| Başlık | Açıklama |
| - | - |
| [Walkthrough: Sıfırdan bir MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Yalnızca bir metin düzenleyicisi kullanarak temel bir proje dosyasının nasıl artımlı olarak oluşturularak oluşturularak gösterin. |
| [İzlenecek Yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md) | MSBuild'in yapı taşlarını tanır ve Visual Studio IDE'yi kapatmadan MSBuild projelerinin nasıl yazılabildiğini, manipüle edilip hata ayıklanınan bir şekilde yazılmasıgerektiğini gösterir. |
| [MSBuild kavramları](../msbuild/msbuild-concepts.md) | MSBuild'in dört yapı taşını sunar: özellikler, öğeler, hedefler ve görevler. |
| [Öğeler](../msbuild/msbuild-items.md) | MSBuild dosya biçiminin arkasındaki genel kavramları ve parçaların birbirine nasıl uyduğunu açıklar. |
| [MSBuild özellikleri](../msbuild/msbuild-properties.md) | Özellikleri ve özellik koleksiyonlarını tanıtir. Özellikler, yapı yapılandırmak için kullanılabilecek anahtar/değer çiftleridir. |
| [Hedef](../msbuild/msbuild-targets.md) | Görevleri belirli bir sırada nasıl gruplandırılacak ve yapı işleminin bölümlerinin komut satırında çağrılmasını nasıl sağlayacağınızı açıklar. |
| [Görevler](../msbuild/msbuild-tasks.md) | Atomik yapı işlemleri gerçekleştirmek için MSBuild tarafından kullanılabilecek bir yürütülebilir kod biriminin nasıl oluşturulabileceğini gösterir. |
| [Koşullar](../msbuild/msbuild-conditions.md) | Bir MSBuild öğesinde özniteliğin nasıl kullanılacağını `Condition` tartışır. |
| [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md) | Toplu iş, dönüşümler, çoklu hedefleme ve diğer gelişmiş teknikler sunar. |
| [MSBuild'de Günlük Kaydı](../msbuild/logging-in-msbuild.md) | Yapı olaylarının, iletilerin ve hataların nasıl günlüğe kaydedilebildiğini açıklar. |
| [Ek kaynaklar](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | MSBuild hakkında daha fazla bilgi için topluluk ve destek kaynaklarını listeler. |

## <a name="reference"></a>Başvuru

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)\
 Başvuru bilgilerini içeren konulara bağlantılar.

- [Sözlük](msbuild-glossary.md)\
 Ortak MSBuild terimlerini tanımlar.
