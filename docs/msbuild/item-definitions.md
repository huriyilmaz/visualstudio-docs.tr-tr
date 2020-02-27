---
title: Öğe tanımları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18d6a2a30af4fb29a8d9e924c44c1570ff1efe29
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633713"
---
# <a name="item-definitions"></a>Öğe tanımları

MSBuild 2,0, [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesini kullanarak proje dosyalarındaki öğelerin statik bildirimini sunar. Ancak meta veriler, tüm öğeler için özdeş olsa bile yalnızca öğe düzeyinde eklenebilir. MSBuild 3,5 ' den başlayarak, [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) adlı bir proje öğesi bu sınırlamaya sahiptir. *ItemDefinitionGroup* , adlandırılmış öğe türündeki tüm öğelere varsayılan meta veri değerleri ekleyen bir öğe tanımları kümesi tanımlamanızı sağlar.

*ItemDefinitionGroup* öğesi proje dosyasının [Proje](../msbuild/project-element-msbuild.md) öğesinden hemen sonra görünür. Öğe tanımları aşağıdaki işlevleri sağlar:

- Bir hedefin dışındaki öğeler için genel varsayılan meta verileri tanımlayabilirsiniz. Diğer bir deyişle, aynı meta veriler belirtilen türdeki tüm öğeler için geçerlidir.

- Öğe türlerinde birden çok tanım olabilir. Türe ek meta veri belirtimleri eklendiğinde, son belirtim öncelik kazanır. meta veriler, Özellikler takip eden aynı alma sırasını izler \(.\)

- Meta veriler eklenebilir. Örneğin, Ctanımlıyor değerleri, ayarlanmakta olan özelliklere bağlı olarak koşullu olarak toplanır. Örneğin, `MT;STD_CALL;DEBUG;UNICODE`.

- Meta veriler kaldırılabilir.

- Koşullar, meta verilerin eklenmesini denetlemek için kullanılabilir.

## <a name="item-metadata-default-values"></a>Öğe meta verileri varsayılan değerleri

Bir ItemDefinitionGroup içinde tanımlanan öğe meta verileri yalnızca varsayılan meta verilerin bir bildirimidir. Meta veri değerlerini içeren bir ItemGroup kullanan bir öğe tanımlamadığınız takdirde meta veriler uygulanmaz.

> [!NOTE]
> Bu konudaki örneklerin çoğunda, bir ItemDefinitionGroup öğesi gösteriliyor ancak karşılık gelen ItemGroup tanımı açıklık için atlandı.

Bir ItemGroup içinde açıkça tanımlanan meta veriler, ItemDefinitionGroup içindeki meta verilerden önceliklidir. ItemDefinitionGroup içindeki meta veriler yalnızca bir ItemGroup içindeki tanımsız meta veriler için uygulandı. Örnek:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

Bu örnekte, "m" meta verileri "i" öğesi tarafından açıkça tanımlanmadığından "m" varsayılan meta verileri "i" öğesine uygulanır. Ancak, "n" meta verileri "i" öğesi tarafından zaten tanımlandığından "i" varsayılan meta verileri "i" öğesine uygulanmıyor.

> [!NOTE]
> XML öğesi ve parametre adları büyük/küçük harfe\-duyarlıdır. Öğe meta verileri ve öğe\/Özellik adları, büyük/küçük harfe duyarlı\-. Bu nedenle, yalnızca büyük/küçük harfe göre farklı adlara sahip olan ItemDefinitionGroup öğeleri aynı ItemGroup olarak değerlendirilmelidir.

## <a name="value-sources"></a>Değer kaynakları

Bir ItemDefinitionGroup içinde tanımlanan meta verilerin değerleri, aşağıdaki gibi birçok farklı kaynaktan gelebilir:

- PropertyGroup özelliği

- ItemDefinitionGroup 'tan öğe

- Bir ItemDefinitionGroup öğesinde öğe dönüştürme

- Ortam değişkeni

- Global özelliği ( *MSBuild. exe* komut satırından)

- Ayrılmış Özellik

- ItemDefinitionGroup 'tan bir öğe üzerinde iyi bilinen meta veriler

- CDATA bölümü \<\!\[CDATA\[hiçbir şey ayrıştırılmaz\]\]\>

> [!NOTE]
> ItemDefinitionGroup öğeleri ItemGroup öğelerinden önce işlendiğinden, ItemGroup 'tan öğe meta verileri bir ItemDefinitionGroup meta veri bildiriminde yararlı değildir.

## <a name="additive-and-multiple-definitions"></a>Eklenebilir ve birden çok tanım

Tanımlar eklediğinizde veya birden çok ItemDefinitionGroups kullandığınızda, aşağıdakileri unutmayın:

- Ek meta veri belirtimi türe eklenir.

- Son belirtim öncelik kazanır.

Birden çok ItemDefinitionGroups varsa, izleyen her belirtim meta verilerini önceki tanımına ekler. Örnek:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

Bu örnekte, "o" meta verileri "m" ve "n" öğesine eklenir.

Ayrıca, önceden tanımlanmış meta veri değerleri de eklenebilir. Örnek:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Bu örnekte, en son değerin "M1; m2" olması için, "d" \(M1\) meta verileri için önceden tanımlanmış değer \(m2\)yeni değerine eklenir.

> [!NOTE]
> Bu, aynı ItemDefinitionGroup içinde de gerçekleşebilir.

Önceden tanımlanmış meta verileri geçersiz kıldığınızda, son belirtim öncelik kazanır. Aşağıdaki örnekte, "m" meta verisinin son değeri "M1" öğesinden "M1A" öğesine gider.

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Bir ItemDefinitionGroup içindeki koşulları kullanma

Meta verilerin eklenmesini denetlemek için bir ItemDefinitionGroup içindeki koşulları kullanabilirsiniz. Örnek:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

Bu durumda, "i" öğesinde "M1" varsayılan meta verileri yalnızca "Configuration" özelliğinin değeri "Debug" ise dahil edilir.

> [!NOTE]
> Koşullarda yalnızca yerel meta veri başvuruları desteklenir.

Önceki bir ItemDefinitionGroup içinde tanımlanan meta verilere yapılan başvurular, tanım grubuna değil, öğe için yereldir. Diğer bir deyişle, başvuruların kapsamı öğeye özgüdür. Örnek:

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

Yukarıdaki örnekte, "i" öğesi "test" öğesine başvuruyor. MSBuild bir ItemDefinitionGroup içindeki başka bir öğenin meta verilerine bir başvuruyu boş dize olarak yorumladığı için bu durum hiçbir şekilde doğru olmaz. Bu nedenle "d", "M0" olarak ayarlanır.

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Yukarıdaki örnekte "m", "Evet" öğesi için "i" öğesinin meta veri değerine başvurduğundan "M1" değerine ayarlanır.

## <a name="override-and-delete-metadata"></a>Meta verileri geçersiz kıl ve Sil

Bir ItemDefinitionGroup öğesinde tanımlanan meta veriler, meta veri değeri başka bir değere ayarlanarak sonraki bir ItemDefinitionGroup öğesinde geçersiz kılınabilir. Ayrıca, bir meta veri öğesini boş bir değere ayarlayarak etkin bir şekilde silebilirsiniz. Örnek:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

"İ" öğesi "m" meta verilerini hala içeriyor, ancak değeri artık boş.

## <a name="scope-of-metadata"></a>Meta veri kapsamı

ItemDefinitionGroups tanımlandıklarında, tanımlı ve genel özelliklerde genel kapsama sahiptir. Bir ItemDefinitionGroup içindeki varsayılan meta veri tanımları kendi kendine başvuru olabilir. Örneğin, aşağıdaki bir basit meta veri başvurusu kullanır:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Nitelikli bir meta veri başvurusu da kullanılabilir:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Ancak, şunlar geçerli değildir:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

MSBuild 3,5 ' den başlayarak, ItemGroups da kendine başvuran olabilir. Örnek:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
