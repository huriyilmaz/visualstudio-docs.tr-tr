---
title: Hedef öğe (MSBuild) | Microsoft Docs
description: MSBuild sırayla yürütülecek bir görev kümesi içeren MSBuild Target öğesi hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142864"
---
# <a name="target-element-msbuild"></a>Target öğesi (MSBuild)

MSBuild sırayla yürütebilmesi için bir görev kümesi içerir.

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
|`Name`|Gerekli öznitelik.<br /><br /> Hedefin adı. Hedef adı, dışında herhangi bir karakter içerebilir `$@()%*?.` .|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Koşul olarak değerlendirilirse `false` , hedef hedefin gövdesini veya özniteliğinde ayarlanan tüm hedefleri yürütmez `DependsOnTargets` . Koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`Inputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefte girdileri oluşturan dosyalar. Birden çok dosya noktalı virgülle ayrılır. Dosyaların zaman damgaları, ' ın `Outputs` güncel olup olmadığını belirlemekte içindeki dosyaların zaman damgalarına göre karşılaştırılır `Target` . Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md), [nasıl yapılır: artımlı](../msbuild/how-to-build-incrementally.md)ve [dönüşümler](../msbuild/msbuild-transforms.md)oluşturma.|
|`Outputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefte çıktı oluşturan dosyalar. Birden çok dosya noktalı virgülle ayrılır. Dosyaların zaman damgaları, ' ın `Inputs` güncel olup olmadığını belirlemekte içindeki dosyaların zaman damgalarına göre karşılaştırılır `Target` . Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md), [nasıl yapılır: artımlı](../msbuild/how-to-build-incrementally.md)ve [dönüşümler](../msbuild/msbuild-transforms.md)oluşturma.|
|`Returns`|İsteğe bağlı öznitelik.<br /><br /> bu hedefi çağıran görevler için kullanılabilir hale getirilen öğeler kümesi, örneğin MSBuild görevleri. Birden çok hedef noktalı virgülle ayrılır. Dosyadaki hedeflerin hiçbir `Returns` özniteliği yoksa, bu amaçla bunun yerine çıkışlar öznitelikleri kullanılır.|
|`KeepDuplicateOutputs`|İsteğe bağlı Boolean özniteliği.<br /><br /> Eğer `true` , hedefin dönüşteki aynı öğeye birden fazla başvuru kaydedilir.  Varsayılan olarak, bu öznitelik `false` .|
|`BeforeTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların noktalı virgülle ayrılmış listesi.  Belirtildiğinde, bu hedefin belirtilen hedeften veya hedeflerden önce çalışması gerektiğini gösterir. Bu, proje yazarının varolan bir hedef kümesini doğrudan değiştirmeden genişletmesine imkan tanır. Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md).|
|`AfterTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların noktalı virgülle ayrılmış listesi. Belirtildiğinde, bu hedefin belirtilen hedeften veya hedeflerden sonra çalıştırılması gerektiğini gösterir. Bu, proje yazarının varolan bir hedef kümesini doğrudan değiştirmeden genişletmesine imkan tanır. Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md).|
|`DependsOnTargets`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefin yürütülebilmesi veya en üst düzey bağımlılık Analizi gerçekleşebilmesi için yürütülmesi gereken hedefler. Birden çok hedef noktalı virgülle ayrılır.|
|`Label`|İsteğe bağlı öznitelik.<br /><br /> Sistem ve Kullanıcı öğelerini tanımlayan veya sırabilen bir tanımlayıcı.|

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | MSBuild bir görevin örneğini oluşturur ve yürütür. Hedefte sıfır veya daha fazla görev olabilir. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Kullanıcı tanımlı öğelerin bir kümesini içerir `Property` . .NET Framework 3,5 ' den başlayarak bir `Target` öğe öğe içerebilir `PropertyGroup` . |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Kullanıcı tanımlı öğelerin bir kümesini içerir `Item` . .NET Framework 3,5 ' den başlayarak bir `Target` öğe öğe içerebilir `ItemGroup` . Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | `ContinueOnError`Başarısız bir görevin özniteliği Errportadstop (veya) ise, bir veya daha fazla hedefin yürütülmesine neden olur `false` . Hedefte sıfır veya daha fazla `OnError` öğe olabilir. `OnError`Öğeler varsa, bu öğelerin öğesindeki son öğeler olması gerekir `Target` .<br /><br /> Özniteliği hakkında daha fazla bilgi için `ContinueOnError` bkz. [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar

 Yürütülecek ilk hedef çalışma zamanında belirtilir. Hedeflerin diğer hedeflere bağımlılıkları olabilir. Örneğin, dağıtım hedefi, derleme için bir hedefe bağlıdır. MSBuild altyapısı, bağımlılıkları öznitelikte göründükleri sırada `DependsOnTargets` , soldan sağa yürütür. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md).

 MSBuild içeri aktarma siparişi bağımlıdır ve belirli bir özniteliğe sahip bir hedefin son tanımı `Name` kullanılan tanımdır.

 Bir hedef, birden fazla hedefin buna bağımlılığı olsa bile, bir derleme sırasında yalnızca bir kez yürütülür.

 `Condition`Özniteliği olarak değerlendirildiğinden bir hedef atlanırsa `false` , derleme içinde daha sonra çağrılırsa ve `Condition` özniteliği o anda olarak değerlendirilirse, hala yürütülür `true` .

 4 MSBuild önce, `Target` özniteliğinde belirtilen herhangi bir öğeyi döndürdü `Outputs` .  bunu yapmak için, MSBuild bu öğeleri, bu öğelerin daha sonra istekte bulunan görevlere kaydetmeniz gerekiyordu. hangi hedeflerin, arayanlara gereken çıkışları olduğunu belirtmenin bir yolu olmadığından, tüm çağrılan tüm öğeleri MSBuild `Outputs` `Target` . Bu, çok sayıda çıkış öğesi olan derlemeler için ölçeklendirme sorunlarına yol açabilir.

 Kullanıcı bir projedeki herhangi bir öğe için bir belirtiyorsa `Returns` `Target` , `Target` `Returns` Bu öğeleri yalnızca bir özniteliği kaydeder.

 `Target`, Hem bir özniteliği hem de `Outputs` bir özniteliği içerebilir `Returns` .  `Outputs` , `Inputs` hedefin güncel olup olmadığını belirlemekte kullanılır. `Returns`varsa, `Outputs` çağıranlara hangi öğelerin döndürüleceğini belirleyen değerini geçersiz kılar.  `Returns`Mevcut değilse, `Outputs` daha önce açıklanan durum dışında çağıranlar için kullanılabilir hale getirilir.

 MSBuild 4 ' den önce, `Target` içindeki aynı öğeye birden çok başvuru eklendiğinde `Outputs` , bu yinelenen öğeler kaydedilir. Çok sayıda çıkış ve birçok proje bağımlılığı bulunan çok büyük derlemelerde, yinelenen öğeler hiçbir kullanım olmadığından büyük miktarda bellek harcanmasına neden olur. `KeepDuplicateOutputs`Özniteliği olarak ayarlandığında `true` , bu yinelemeler kaydedilir.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneğinde, `Target` görevi yürüten bir öğe gösterilmektedir `Csc` .

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
- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
