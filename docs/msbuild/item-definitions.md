---
title: Öğe Tanımları | Microsoft Docs
description: Proje dosyalarında MSBuild için meta verileri bildiren ItemGroup ve ItemDefinitionGroup'ları nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f56772bec8d0e4e62a58976b5c084f99c1e6f6e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136904"
---
# <a name="item-definitions"></a>Öğe tanımları

MSBuild 2.0, ItemGroup öğesini kullanarak proje dosyalarında öğelerin statik [bildirimini](../msbuild/itemgroup-element-msbuild.md) sağlar. Ancak meta veriler tüm öğeler için aynı olsa bile yalnızca öğe düzeyinde eklenebilir. 3.5 MSBuild başlayarak [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) adlı bir proje öğesi bu sınırlamanın üstesinden gelir. *ItemDefinitionGroup,* adlandırılmış öğe türüne tüm öğelere varsayılan meta veri değerleri ekleyerek bir öğe tanımları kümesi tanımlamanıza olanak sağlar.

*ItemDefinitionGroup* öğesi, proje dosyasının [Project](../msbuild/project-element-msbuild.md) hemen sonra görüntülenir. Öğe tanımları aşağıdaki işlevleri sağlar:

- Hedef dışındaki öğeler için genel varsayılan meta veriler tanımlayabilirsiniz. Diğer bir ifadeyle, aynı meta veriler belirtilen türdeki tüm öğeler için geçerlidir.

- Öğe türlerinin birden çok tanımı olabilir. Türe ek meta veri belirtimleri eklenmiştir, son belirtim önceliklidir. \(Meta veriler, özelliklerle aynı içeri aktarma sırasına sahiptir.\)

- Meta veriler eklenebilir. Örneğin, CDefines değerleri, ayarlanmış olan özelliklere bağlı olarak koşullu olarak biriktir. Örneğin, `MT;STD_CALL;DEBUG;UNICODE`.

- Meta veriler kaldırılabilir.

- Meta verilerin eklenmesini kontrol etmek için koşullar kullanılabilir.

## <a name="item-metadata-default-values"></a>Öğe meta verileri varsayılan değerleri

ItemDefinitionGroup içinde tanımlanan öğe meta verileri yalnızca varsayılan meta verilerin bildirimidir. Meta veri değerlerini içeren bir ItemGroup kullanan bir Öğe tanımlamadıkça meta veriler geçerli olmaz.

> [!NOTE]
> Bu konudaki örneklerin çoğunda bir ItemDefinitionGroup öğesi gösterilir, ancak buna karşılık gelen ItemGroup tanımı netlik sağlamak için atlanır.

Bir ItemGroup içinde açıkça tanımlanan meta veriler, ItemDefinitionGroup'ta meta verilere göre önceliklidir. ItemDefinitionGroup'daki meta veriler yalnızca bir ItemGroup'ta tanımlanmamış meta veriler için uygulanır. Örnek:

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

"m" meta verileri "i" Öğesi tarafından açıkça tanımlanmamış olduğundan, bu örnekte varsayılan "m" meta verileri Item "i" değerine uygulanır. Ancak"n" meta verileri "i" Öğesi tarafından zaten tanımlandığı için varsayılan "n" meta verileri "i" öğesine uygulanmaz.

> [!NOTE]
> XML Öğesi ve Parametre adları büyük/büyük/büyük harfe \- duyarlıdır. Öğe meta verileri ve Öğe \/ Özelliği adları büyük/büyük harfe duyarlı \- değildir. Bu nedenle, yalnızca büyük/büyük harfe göre farklı adlara sahip ItemDefinitionGroup öğeleri aynı ItemGroup olarak kabul edilmelidir.

## <a name="value-sources"></a>Değer kaynakları

ItemDefinitionGroup içinde tanımlanan meta verilerin değerleri aşağıdaki gibi birçok farklı kaynaktan gelebilir:

- PropertyGroup Özelliği

- ItemDefinitionGroup öğesinden

- ItemDefinitionGroup Öğesi üzerinde öğe dönüştürme

- Ortam değişkeni

- Genel özellik *(MSBuild.exe* komut satırı)

- Ayrılmış özellik

- ItemDefinitionGroup öğesinden bir Öğede iyi bilinen meta veriler

- CDATA bölümü \<\!\[CDATA\[anything here is not parsed\]\]\>

> [!NOTE]
> ItemDefinitionGroup öğeleri ItemGroup öğelerinden önce işlendiğinden ItemGroup öğesi meta verileri bir ItemDefinitionGroup meta veri bildiriminde kullanışlı değildir.

## <a name="additive-and-multiple-definitions"></a>Eklenebilir ve birden çok tanım

Tanımları eklerken veya birden çok ItemDefinitionGroups kullanırsanız, şunları unutmayın:

- Türe ek meta veri belirtimi eklenir.

- Son belirtim önceliklidir.

Birden çok ItemDefinitionGroup'uz olduğunda, izleyen her belirtim, meta verilerini önceki tanıma ekler. Örnek:

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

Bu örnekte "o" meta verileri "m" ve "n" ifadelerine eklenir.

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

Bu örnekte, yeni m2 değerine "m1;m2" meta verileri için önceden tanımlanmış değer eklenmiştir. Böylece son değer \( \) \( \) "m1;m2" olur.

> [!NOTE]
> Bu aynı ItemDefinitionGroup içinde de oluşabilir.

Önceden tanımlanmış meta verileri geçersiz kılarak son belirtim önceliklidir. Aşağıdaki örnekte "m" meta verilerinin son değeri "m1" ile "m1a" arasındadır.

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

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>ItemDefinitionGroup içinde koşulları kullanma

Meta verilerin dahil edilmesini kontrol etmek için ItemDefinitionGroup içinde koşulları kullanabilirsiniz. Örnek:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

Bu durumda, "i" öğesinde varsayılan "m1" meta verileri yalnızca "Configuration" özelliğinin değeri "Debug" ise dahil edilir.

> [!NOTE]
> Koşullarda yalnızca yerel meta veri başvuruları de desteklemektedir.

Önceki bir ItemDefinitionGroup içinde tanımlanan meta verilere yapılan başvurular, tanım grubu için değil öğe için yereldir. Başka bir ifadeyle başvuruların kapsamı öğeye özgü olur. Örnek:

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

Yukarıdaki örnekte , "i" öğesi Koşulda "test" öğesine başvurur. Bir ItemDefinitionGroup MSBuild başka bir öğenin meta verilerine yapılan bir başvuru boş dize olarak yorumlanması nedeniyle bu koşul hiçbir zaman true olmayacaktır. Bu nedenle, "m" "m0" olarak ayarlanır.

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Yukarıdaki örnekte, Koşul "evet" öğesi için "i" öğesinin meta veri değerine başvurarak "m1" değerine ayarlanır.

## <a name="override-and-delete-metadata"></a>Meta verileri geçersiz kılma ve silme

Bir ItemDefinitionGroup öğesinde tanımlanan meta veriler, meta veri değeri başka bir değere ayarlandığı için sonraki bir ItemDefinitionGroup öğesinde geçersiz kılınabilir. Bir meta veri öğesini boş bir değere ayarerek de etkili bir şekilde silebilirsiniz. Örnek:

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

"i" öğesi hala "m" meta verilerini içerir, ancak değeri artık boştur.

## <a name="scope-of-metadata"></a>Meta verilerin kapsamı

ItemDefinitionGroups, tanımlandığı her yerde tanımlı ve genel özellikler üzerinde genel kapsama sahiptir. ItemDefinitionGroup'ta varsayılan meta veri tanımları kendi kendine başvurul olabilir. Örneğin, aşağıda basit bir meta veri başvurusu kullanılır:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Tam meta veri başvurusu da kullanılabilir:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Ancak, aşağıdakiler geçerli değildir:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

3.5 MSBuild den itibaren ItemGroups da kendi kendine başvurul olabilir. Örnek:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Toplu İşleme](../msbuild/msbuild-batching.md)
