---
title: Target Öğesi (MSBuild) | Microsoft Docs
description: MSBuild için bir dizi görev içeren MSBuild Target öğesi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 35b4153eab1bbe2d320019c46d4b8e854f2ca6a3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628413"
---
# <a name="target-element-msbuild"></a>Hedef öğe (MSBuild)

Uygulamanın sıralı olarak yürütül MSBuild görevler kümesi içerir.

 \<Project> \<Target>

## <a name="syntax"></a>Syntax

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
|`Name`|Gerekli öznitelik.<br /><br /> Hedefin adı. Hedef ad dışında herhangi bir karakter `$@()%*?.` içerebilir.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Koşul olarak değerlendirilirse `false` hedef, hedefin gövdesini veya özniteliğinde ayarlanmış herhangi bir hedefi `DependsOnTargets` yürütmez. Koşullar hakkında daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|
|`Inputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefe girişler oluşturmak için dosyalar. Birden çok dosya noktalı virgülle ayrılır. Dosyaların zaman damgası, güncel olup olmadığını belirlemek için dosya zaman damgasıyla `Outputs` `Target` karşılaştırıldı. Daha fazla bilgi için [bkz. Artımlı derlemeler,](../msbuild/incremental-builds.md) [Nasıl yapılır: Artımlı](../msbuild/how-to-build-incrementally.md)olarak derleme ve [Dönüşümler.](../msbuild/msbuild-transforms.md)|
|`Outputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefe çıkışlar oluşturmak için dosyalar. Birden çok dosya noktalı virgülle ayrılır. Dosyaların zaman damgası, güncel olup olmadığını belirlemek için dosya zaman damgasıyla `Inputs` `Target` karşılaştırıldı. Daha fazla bilgi için [bkz. Artımlı derlemeler,](../msbuild/incremental-builds.md) [Nasıl yapılır: Artımlı](../msbuild/how-to-build-incrementally.md)olarak derleme ve [Dönüşümler.](../msbuild/msbuild-transforms.md)|
|`Returns`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefi çağıran görevler için kullanılabilir olacak öğe kümesi, örneğin, MSBuild. Birden çok hedef noktalı virgülle ayrılır. Dosyada hedeflerde öznitelik `Returns` yoksa, bunun yerine Outputs öznitelikleri kullanılır.|
|`KeepDuplicateOutputs`|İsteğe bağlı Boole özniteliği.<br /><br /> ise, `true` hedefin Dönüşleri'ne aynı öğeye birden çok başvuru kaydedilir.  Varsayılan olarak bu `false` özniteliktir.|
|`BeforeTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların noktalı virgülle ayrılmış listesi.  Belirtiliyorsa, bu hedefin belirtilen hedef veya hedef öncesinde çalışması gerektiğini gösterir. Bu, proje yazarının mevcut hedef kümelerini doğrudan değiştirmeden genişletmesini sağlar. Daha fazla bilgi için [bkz. Hedef derleme sırası.](../msbuild/target-build-order.md)|
|`AfterTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların noktalı virgülle ayrılmış listesi. Belirtilmedikten sonra, bu hedefin belirtilen hedef veya hedef sonrasında çalışması gerektiğini gösterir. Bu, proje yazarının mevcut hedef kümelerini doğrudan değiştirmeden genişletmesini sağlar. Daha fazla bilgi için [bkz. Hedef derleme sırası.](../msbuild/target-build-order.md)|
|`DependsOnTargets`|İsteğe bağlı öznitelik.<br /><br /> Bu hedef yürütülmeden önce yürütülecek hedefler veya üst düzey bağımlılık analizi oluşabilir. Birden çok hedef noktalı virgülle ayrılır.|
|`Label`|İsteğe bağlı öznitelik.<br /><br /> Sistem ve kullanıcı öğelerini belirleyen veya sıralayan bir tanımlayıcı.|

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | Bir görev örneği oluşturur ve MSBuild yürütür. Hedefte sıfır veya daha fazla görev olabilir. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | Kullanıcı tanımlı öğeler kümesi `Property` içerir. 3.5 .NET Framework başlayarak, bir `Target` öğe öğeleri `PropertyGroup` içerebilir. |
| [Itemgroup](../msbuild/itemgroup-element-msbuild.md) | Kullanıcı tanımlı öğeler kümesi `Item` içerir. 3.5 .NET Framework başlayarak, bir `Target` öğe öğeleri `ItemGroup` içerebilir. Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md) |
| [Onerror](../msbuild/onerror-element-msbuild.md) | Öznitelik başarısız bir görev için ErrorAndStop (veya ) ise bir veya daha `ContinueOnError` fazla `false` hedefin yürütülse neden olur. Hedefte sıfır veya `OnError` daha fazla öğe olabilir. Öğeler `OnError` varsa, öğenin son öğeleri olması `Target` gerekir.<br /><br /> özniteliği hakkında bilgi `ContinueOnError` için bkz. [Görev öğesi (MSBuild).](../msbuild/task-element-msbuild.md) |

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Bir proje dosyasının gerekli MSBuild öğesi. |

## <a name="remarks"></a>Açıklamalar

 Yürütülecek ilk hedef çalışma zamanında belirtilir. Hedeflerin diğer hedeflere bağımlılıkları olabilir. Örneğin, dağıtım hedefi derleme hedefine bağlıdır. MSBuild altyapısı, bağımlılıkları öznitelikte görünme sırasına göre `DependsOnTargets` soldan sağa yürütür. Daha fazla bilgi için [bkz. Hedefler.](../msbuild/msbuild-targets.md)

 MSBuild sırasına bağlıdır ve belirli bir özniteliği olan hedefin son `Name` tanımı kullanılan tanımdır.

 Bir hedef, birden fazla hedefin bağımlılığı olsa bile bir derleme sırasında yalnızca bir kez yürütülür.

 Özniteliği değerlendirmesi nedeniyle bir hedef atlanırsa, daha sonra derlemede çağrılsa ve özniteliği o anda olarak değerlendirilirse yine `Condition` `false` de `Condition` `true` yürütülebilirsiniz.

 4 MSBuild `Target` önce, özniteliğinde belirtilen öğeleri `Outputs` döndürüldü.  Bunu yapmak için MSBuild daha sonra derlemedeki görevlerin istenen görevleri kaydetmesi durumunda bu öğeleri kaydetmeniz gerekirdi. Çağıranların ihtiyaç çağıranların hangi hedeflerin çıkışları olduğunu MSBuild tüm çağrılan öğelerde tüm öğeleri `Outputs` `Target` birikti. Bu, çok sayıda çıkış öğeye sahip derlemeler için ölçeklendirme sorunlarına yol açabilir.

 Kullanıcı bir projedeki `Returns` herhangi bir öğe üzerinde bir `Target` belirtirse, yalnızca `Target` öznitelik kaydı olan öğeler bu öğeleri `Returns` kaydeder.

 hem `Target` öznitelik hem de öznitelik `Outputs` `Returns` içerebilir.  `Outputs` hedefin `Inputs` güncel olup olmadığını belirlemek için ile kullanılır. `Returns`varsa, çağıranlara hangi öğelerin `Outputs` döndürüleceklerini belirlemek için değerini geçersiz kılar.  `Returns`yoksa, daha önce `Outputs` açıklanan durum dışında çağrıyı yapanlar tarafından kullanılabilir yapılır.

 4 MSBuild önce, içinde aynı öğeye birden çok başvuru ekli olduğu her durumda `Target` `Outputs` bu yinelenen öğeler kaydedilir. Çok sayıda çıkışa ve birçok proje bağımlılığına sahip olan çok büyük derlemelerde, yinelenen öğeler herhangi bir kullanımdan kaynaklanmazsa bu, büyük miktarda belleğin boşa harcanmalarına neden olur. özniteliği `KeepDuplicateOutputs` olarak `true` ayarlanırsa, bu yinelemeler kaydedilir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, görevi `Target` yürüten bir öğeyi `Csc` gösterir.

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

- [Targets](../msbuild/msbuild-targets.md)
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
