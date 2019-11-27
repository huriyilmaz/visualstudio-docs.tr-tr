---
title: Target öğesi (MSBuild) | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1748064482e13eba95e9aa83e9cb04c93b8066f
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491624"
---
# <a name="target-element-msbuild"></a>Target öğesi (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sırayla yürütebilmesi için bir görev kümesi içerir.

 \<Proje > \<hedefi >

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

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli öznitelik.<br /><br /> Hedefin adı.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Koşul `false`olarak değerlendirilirse hedef, hedefin gövdesini veya `DependsOnTargets` özniteliğinde ayarlanan tüm hedefleri yürütmez. Koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`Inputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefte girdileri oluşturan dosyalar. Birden çok dosya noktalı virgülle ayrılır. `Target` güncel olup olmadığını anlamak için, dosyaların zaman damgaları `Outputs` içindeki dosyaların zaman damgalarına göre karşılaştırılır. Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md), [nasıl yapılır: artımlı](../msbuild/how-to-build-incrementally.md)ve [dönüşümler](../msbuild/msbuild-transforms.md)oluşturma.|
|`Outputs`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefte çıktı oluşturan dosyalar. Birden çok dosya noktalı virgülle ayrılır. `Target` güncel olup olmadığını anlamak için, dosyaların zaman damgaları `Inputs` içindeki dosyaların zaman damgalarına göre karşılaştırılır. Daha fazla bilgi için bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md), [nasıl yapılır: artımlı](../msbuild/how-to-build-incrementally.md)ve [dönüşümler](../msbuild/msbuild-transforms.md)oluşturma.|
|`Returns`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefi çağıran görevler için kullanılabilir hale getirilen öğelerin kümesi, örneğin MSBuild görevleri. Birden çok hedef noktalı virgülle ayrılır. Dosyadaki hedeflerin `Returns` özniteliği yoksa, bu amaçla çıkış öznitelikleri kullanılır.|
|`KeepDuplicateOutputs`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`, hedefin dönüşteki aynı öğeye birden fazla başvuru kaydedilir.  Varsayılan olarak, bu öznitelik `false`.|
|`BeforeTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların noktalı virgülle ayrılmış listesi.  Belirtildiğinde, bu hedefin belirtilen hedeften veya hedeflerden önce çalışması gerektiğini gösterir. Bu, proje yazarının varolan bir hedef kümesini doğrudan değiştirmeden genişletmesine imkan tanır. Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md).|
|`AfterTargets`|İsteğe bağlı öznitelik.<br /><br /> Hedef adların noktalı virgülle ayrılmış listesi. Belirtildiğinde, bu hedefin belirtilen hedeften veya hedeflerden sonra çalıştırılması gerektiğini gösterir. Bu, proje yazarının varolan bir hedef kümesini doğrudan değiştirmeden genişletmesine imkan tanır. Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md).|
|`DependsOnTargets`|İsteğe bağlı öznitelik.<br /><br /> Bu hedefin yürütülebilmesi veya en üst düzey bağımlılık Analizi gerçekleşebilmesi için yürütülmesi gereken hedefler. Birden çok hedef noktalı virgülle ayrılır.|
|`Label`|İsteğe bağlı öznitelik.<br /><br /> Sistem ve Kullanıcı öğelerini tanımlayan veya sırabilen bir tanımlayıcı.|

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| [Görevinin](../msbuild/task-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bir görevin örneğini oluşturur ve yürütür. Hedefte sıfır veya daha fazla görev olabilir. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Kullanıcı tanımlı `Property` öğeleri kümesi içerir. .NET Framework 3,5 ' den başlayarak `Target` bir öğe `PropertyGroup` öğeleri içerebilir. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Kullanıcı tanımlı `Item` öğeleri kümesi içerir. .NET Framework 3,5 ' den başlayarak `Target` bir öğe `ItemGroup` öğeleri içerebilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Başarısız bir görevin `ContinueOnError` özniteliği Errportadstop (veya `false`) ise, bir veya daha fazla hedefin yürütülmesine neden olur. Bir hedefte sıfır veya daha fazla `OnError` öğe olabilir. `OnError` öğeler varsa, bu öğelerin `Target` öğesindeki son öğeler olması gerekir.<br /><br /> `ContinueOnError` özniteliği hakkında daha fazla bilgi için bkz. [görev öğesi (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasının gerekli kök öğesi. |

## <a name="remarks"></a>Açıklamalar
 Yürütülecek ilk hedef çalışma zamanında belirtilir. Hedeflerin diğer hedeflere bağımlılıkları olabilir. Örneğin, dağıtım hedefi, derleme için bir hedefe bağlıdır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] altyapısı, bağımlılıkları `DependsOnTargets` özniteliğinde göründükleri sırada (soldan sağa) yürütür. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md).

 MSBuild içeri aktarma-sipariş bağımlıdır ve belirli bir `Name` özniteliğiyle bir hedefin son tanımı kullanılan tanımdır.

 Bir hedef, birden fazla hedefin buna bağımlılığı olsa bile, bir derleme sırasında yalnızca bir kez yürütülür.

 `Condition` özniteliği `false`olarak değerlendirildiğinden bir hedef atlanırsa, hala derlemede çağrılırsa çalıştırılabilir ve `Condition` özniteliği o anda `true` olarak değerlendirilir.

 MSBuild 4 ' ten önce, `Target` `Outputs` özniteliğinde belirtilen herhangi bir öğeyi döndürdü.  Bunu yapmak için, MSBuild 'in bu öğeleri, daha sonra yapı içinde talep eden görevlere kaydı gerekiyordu. Çağıranların gerektirdiği hangi hedeflerin çıkış olduğunu belirtmenin bir yolu olmadığından, tüm çağrılan `Target`s üzerinde tüm `Outputs` MSBuild birikmiş tüm öğeleri. Bu, çok sayıda çıkış öğesi olan derlemeler için ölçeklendirme sorunlarına yol açabilir.

 Kullanıcı bir projedeki herhangi bir `Target` öğesinde bir `Returns` belirtiyorsa, bu öğeleri yalnızca bir `Returns` özniteliğine sahip olan `Target`ler kaydeder.

 `Target`, hem `Outputs` özniteliği hem de `Returns` özniteliği içerebilir.  `Outputs`, hedefin güncel olup olmadığını belirlemede `Inputs` ile birlikte kullanılır. varsa `Returns`, çağıranlara hangi öğelerin döndürüldüğünü belirleyen `Outputs` değerini geçersiz kılar.  `Returns` yoksa, daha önce açıklanan durum dışında çağıranlar için `Outputs` kullanılabilir hale getirilir.

 MSBuild 4 ' den önce, bir `Target` `Outputs`aynı öğeye birden fazla başvuru eklendiğinde, bu yinelenen öğeler kaydedilir. Çok sayıda çıkış ve birçok proje bağımlılığı bulunan çok büyük derlemelerde, yinelenen öğeler hiçbir kullanım olmadığından büyük miktarda bellek harcanmasına neden olur. `KeepDuplicateOutputs` özniteliği `true`olarak ayarlandığında, bu yinelemeler kaydedilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `Csc` görevini yürüten bir `Target` öğesini gösterir.

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
- [Hedefler](../msbuild/msbuild-targets.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
