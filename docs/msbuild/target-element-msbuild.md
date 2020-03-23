---
title: Hedef Öğe (MSBuild) | Microsoft Dokümanlar
ms.date: 06/13/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79686132adce043b4864d545f0912564709cfe2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631984"
---
# <a name="target-element-msbuild"></a>Hedef eleman (MSBuild)

MSBuild'in sırayla yürütmesi için bir dizi görev içerir.

 \<Proje \<> Hedef>

## <a name="syntax"></a>Sözdizimi

```xml
<Target Name="Target Name"
        Inputs="Inputs"
        Outputs="Outputs"
        Returns="Returns"
        KeepDuplicateOutputs="true/false"
        BeforeTargets="Targets"
        AfterTargets="Targets"
        DependsOnTargets="DependentTarget"
        Condition="'String A' == 'String B'"
        Label="Label">
    <Task>... </Task>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <OnError... />
</Target>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli öznitelik.<br /><br /> Hedefin adı.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek durum. Koşul `false`değerlendirirse, hedef hedefin gövdesini veya öznitelikte `DependsOnTargets` ayarlanan herhangi bir hedefi yürütmez. Koşullar hakkında daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|
|`Inputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefe giriş oluşturan dosyalar. Birden çok dosya yarım iki nokta ile ayrılır. Dosyaların zaman damgaları, dosyaların güncel olup olmadığını `Outputs` `Target` belirlemek için dosyaların zaman damgalarıyla karşılaştırılır. Daha fazla bilgi için [bkz: Artımlı yapılar](../msbuild/incremental-builds.md), [Nasıl yapılı: Artımlı olarak oluşturun](../msbuild/how-to-build-incrementally.md)ve [Dönüşümler](../msbuild/msbuild-transforms.md).|
|`Outputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefe çıktı oluşturan dosyalar. Birden çok dosya yarım iki nokta ile ayrılır. Dosyaların zaman damgaları, dosyaların güncel olup olmadığını `Inputs` `Target` belirlemek için dosyaların zaman damgalarıyla karşılaştırılır. Daha fazla bilgi için [bkz: Artımlı yapılar](../msbuild/incremental-builds.md), [Nasıl yapılı: Artımlı olarak oluşturun](../msbuild/how-to-build-incrementally.md)ve [Dönüşümler](../msbuild/msbuild-transforms.md).|
|`Returns`|İsteğe bağlı öznitelik.<br /><br /> MsBuild görevleri gibi, bu hedefi çağıran görevler için kullanılabilir hale getirilecek öğeler kümesi. Birden fazla hedef yarı kolonile ayrılır. Dosyadaki hedeflerin öznitelikleri `Returns` yoksa, bu amaç için Çıktılar öznitelikleri kullanılır.|
|`KeepDuplicateOutputs`|İsteğe bağlı Boolean özniteliği.<br /><br /> Hedefin `true`İadeleri'nde aynı öğeye birden çok başvuru kaydedilirse.  Varsayılan olarak, bu `false`öznitelik .|
|`BeforeTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların yarı sütunlu ayrılmış listesi.  Belirtildiğinde, bu hedefin belirtilen hedef veya hedeflerden önce çalışması gerektiğini gösterir. Bu, proje yazarının varolan bir hedef kümesini doğrudan değiştirmeden genişletmesini sağlar. Daha fazla bilgi için Bkz. [Hedef oluşturma sırası.](../msbuild/target-build-order.md)|
|`AfterTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların yarı sütunlu ayrılmış listesi. Belirtildiğinde, bu hedefin belirtilen hedef veya hedeflerden sonra çalışması gerektiğini gösterir. Bu, proje yazarının varolan bir hedef kümesini doğrudan değiştirmeden genişletmesini sağlar. Daha fazla bilgi için Bkz. [Hedef oluşturma sırası.](../msbuild/target-build-order.md)|
|`DependsOnTargets`|İsteğe bağlı öznitelik.<br /><br /> Bu hedef yürütülebilir veya üst düzey bağımlılık çözümlemesi oluşabilir önce yürütülmesi gereken hedefler. Birden fazla hedef yarı kolonile ayrılır.|
|`Label`|İsteğe bağlı öznitelik.<br /><br /> Sistem ve kullanıcı öğelerini tanımlayabilen veya sipariş edebilen bir tanımlayıcı.|

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | MSBuild görevinin bir örneğini oluşturur ve yürütür. Bir hedefte sıfır veya daha fazla görev olabilir. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | Kullanıcı tanımlı `Property` öğeler kümesi içerir. .NET Framework 3.5'ten `Target` başlayarak, `PropertyGroup` bir öğe öğeleri içerebilir. |
| [ıtemgroup](../msbuild/itemgroup-element-msbuild.md) | Kullanıcı tanımlı `Item` öğeler kümesi içerir. .NET Framework 3.5'ten `Target` başlayarak, `ItemGroup` bir öğe öğeleri içerebilir. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın. |
| [Onerror](../msbuild/onerror-element-msbuild.md) | Öznitelik başarısız bir görev `ContinueOnError` için ErrorAndStop (veya) `false`ise bir veya daha fazla hedefin yürütülmesine neden olur. Bir hedefte sıfır `OnError` veya daha fazla öğe olabilir. `OnError` Öğeler varsa, `Target` öğedeki son öğeler olmalıdır.<br /><br /> Öznitelik hakkında `ContinueOnError` bilgi için [Görev öğesine (MSBuild)](../msbuild/task-element-msbuild.md)bakın. |

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar

 Yürütülecek ilk hedef çalışma zamanında belirtilir. Hedeflerin diğer hedeflere bağımlılığı olabilir. Örneğin, dağıtım hedefi derleme için bir hedefe bağlıdır. MSBuild altyapısı, bağımlılıkları öznitelikte `DependsOnTargets` soldan sağa doğru göründükleri sırada yürütür. Daha fazla bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md)

 MSBuild alma siparişine bağlıdır ve belirli `Name` bir özniteliğe sahip bir hedefin son tanımı kullanılan tanımdır.

 Bir hedef, birden fazla hedefin üzerinde bir bağımlılığı olsa bile, bir yapı sırasında yalnızca bir kez yürütülür.

 `Condition` Bir hedef atlanırsa, çünkü özniteliği `false`değerlendirirse, yapıda daha sonra çağrılması ve `Condition` özniteliği o `true` zamana göre değerlendirildiği durumlarda yine de yürütülebilir.

 MSBuild 4'ten önce, `Target` öznitelikte `Outputs` belirtilen tüm öğeleri döndürdü.  Bunu yapmak için, MSBuild bu öğeleri daha sonra yapıda istenen görevlere sahip olması durumunda kaydetmek zorunda kaldı. Hangi hedeflerin arayanların gerektireceği çıktılar olduğunu belirtmenin bir yolu olmadığından, `Outputs` MSBuild `Target`tüm çağrılan s'lerde tüm öğeleri birikti. Bu, çok sayıda çıktı öğesi olan yapılar için ölçekleme sorunlarına yol açar.

 Kullanıcı bir projedeki `Returns` herhangi `Target` bir öğeüzerinde bir öğe `Target`belirtirse, yalnızca bu `Returns` öğeleri bir öznitelik kaydı var s.

 A, `Target` hem `Outputs` bir öznitelik `Returns` hem de öznitelik içerebilir.  `Outputs`hedefin `Inputs` güncel olup olmadığını belirlemek için kullanılır. `Returns`, varsa, arayanlara döndürülen öğelerin `Outputs` değerini geçersiz kılar.  `Returns` Yoksa, daha önce `Outputs` açıklanan durumlar dışında arayanlar ın kullanımına sunulacaktır.

 MSBuild 4'ten önce, `Target` aynı öğeye birden çok `Outputs`başvuru nun dahil olduğu her zaman, bu yinelenen öğeler kaydedilir. Çok sayıda çıktısı ve çok sayıda proje karşılıklı bağımlılığı olan çok büyük yapılarda, yinelenen öğelerin herhangi bir kullanımı olmadığı için bu büyük miktarda belleğin boşa harcanmasını sağlar. `KeepDuplicateOutputs` Öznitelik `true`ayarlandığında, bu yinelenenler kaydedilir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, `Target` görevi yürüten `Csc` bir öğeyi gösterir.

```xml
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef](../msbuild/msbuild-targets.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
