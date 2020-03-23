---
title: Madde Tanımları | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633713"
---
# <a name="item-definitions"></a>Madde tanımları

MSBuild 2.0, [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesini kullanarak proje dosyalarındaki maddelerin statik bildirimini sağlar. Ancak, meta veriler tüm öğeler için aynı olsa bile, meta veriler yalnızca öğe düzeyinde eklenebilir. MSBuild 3.5'ten başlayarak, [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) adlı bir proje öğesi bu sınırlamanın üstesinden gelinir. *ItemDefinitionGroup,* adlandırılmış madde türündeki tüm öğelere varsayılan meta veri değerleri ekleyen bir madde tanımı kümesi tanımlamanıza olanak tanır.

*ItemDefinitionGroup* öğesi, proje dosyasının [Proje](../msbuild/project-element-msbuild.md) öğesinden hemen sonra görüntülenir. Madde tanımları aşağıdaki işlevselliği sağlar:

- Hedef dışındaki öğeler için genel varsayılan meta verileri tanımlayabilirsiniz. Diğer bir diğer olarak, aynı meta veriler belirtilen türden tüm öğeler için geçerlidir.

- Madde türlerinin birden çok tanımı olabilir. Türe ek meta veri belirtimleri eklendiğinde, son belirtim önceliklidir. \(Meta veriler, özellikler aşağıdaki gibi aynı alma siparişi izler.\)

- Meta veriler katkı maddesi olabilir. Örneğin, CDefines değerleri ayarlanan özelliklere bağlı olarak koşullu olarak birikir. Örneğin, `MT;STD_CALL;DEBUG;UNICODE`.

- Meta veriler kaldırılabilir.

- Koşullar meta verilerin dahil edilmesini denetlemek için kullanılabilir.

## <a name="item-metadata-default-values"></a>Madde meta veri varsayılan değerleri

ItemDefinitionGroup'ta tanımlanan madde meta verileri yalnızca varsayılan meta verilerin bir bildirimidir. Meta veri değerlerini içerecek şekilde bir Öğe Grubu kullanan bir Öğe tanımlamadığınız sürece meta veriler geçerli değildir.

> [!NOTE]
> Bu konuyla ilgili örneklerin çoğunda, bir ItemDefinitionGroup öğesi gösterilir, ancak karşılık gelen ItemGroup tanımı netlik için atlanır.

Bir ItemGroup'ta açıkça tanımlanan meta veriler, ItemDefinitionGroup'taki meta verilerden önceliklidir. ItemDefinitionGroup'taki meta veriler yalnızca bir ItemGroup'taki tanımlanmamış meta veriler için uygulanır. Örnek:

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

Bu örnekte, "m" meta verileri Madde "i" olarak uygulanır, çünkü meta veri "m" Madde "i" tarafından açıkça tanımlanmamıştır. Ancak, varsayılan meta veri "n" Madde "i" uygulanmaz, çünkü meta veri "n" zaten Madde "i" tarafından tanımlanır.

> [!NOTE]
> XML Öğesi ve Parametre\-adları büyük/küçük harf duyarlıdır. Madde meta verileri\/ve Madde\-Özelliği adları büyük/küçük harf duyarlı değildir. Bu nedenle, yalnızca duruma göre farklı adları olan ItemDefinitionGroup öğeleri aynı ItemGroup olarak kabul edilmelidir.

## <a name="value-sources"></a>Değer kaynakları

Bir ItemDefinitionGroup'ta tanımlanan meta veriler için değerler aşağıdaki gibi birçok farklı kaynaktan gelebilir:

- PropertyGroup Özelliği

- ItemDefinitionGroup'tan öğe

- ItemDefinitionGroup Öğesinde madde dönüşümü

- Ortam değişkeni

- Genel özellik *(MSBuild.exe* komut satırından)

- Ayrılmış özellik

- Bir ItemDefinitionGroup'tan bir Öğe üzerinde iyi bilinen meta veriler

- CDATA \< \! \[bölümü\[CDATA burada bir şey ayrıştırılmış değil\]\]\>

> [!NOTE]
> ItemDefinitionGroup öğeleri ItemGroup öğelerinden önce işlendiğinden, ItemDefinitionGroup meta veri bildiriminde MaddeGrubu meta verileri kullanışlı değildir.

## <a name="additive-and-multiple-definitions"></a>Katkı ve çoklu tanımlar

Tanımlar eklediğinizde veya birden çok ItemDefinitionGroups kullandığınızda, aşağıdakileri unutmayın:

- Türüne ek meta veri belirtimi eklenir.

- Son belirtim önceliklidir.

Birden çok ItemDefinitionGroups varsa, sonraki her belirtim önceki tanıma kendi meta verilerini ekler. Örnek:

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

Bu örnekte, "o" meta verileri "m" ve "n" eklenir.

Buna ek olarak, daha önce tanımlanmış meta veri değerleri de eklenebilir. Örnek:

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

Bu örnekte, meta \(veri "m" m1\) için daha önce \(tanımlanan\)değer yeni değer m2'ye eklenir, böylece son değer "m1;m2"dir.

> [!NOTE]
> Bu, aynı ItemDefinitionGroup'ta da oluşabilir.

Daha önce tanımlanan meta verileri geçersiz kaldığınızda, son belirtim önceliklidir. Aşağıdaki örnekte, meta veri "m" son değeri "m1" den "m1a" gider.

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

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>ItemDefinitionGroup'taki kullanım koşulları

Meta verilerin eklenmesini denetlemek için itemdefinitiongroup'taki koşulları kullanabilirsiniz. Örnek:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

Bu durumda, "i" öğesindeki varsayılan meta veri "m1" yalnızca "Yapılandırma" özelliğinin değeri "Hata Ayıklama" ise dahil edilir.

> [!NOTE]
> Yalnızca yerel meta veri başvuruları koşullarda desteklenir.

Önceki bir ItemDefinitionGroup'ta tanımlanan meta verilere yapılan başvurular, tanım grubuna değil, öğeye yereldir. Diğer bir diğer olarak, başvuruların kapsamı öğeye özgüdür. Örnek:

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

Yukarıdaki örnekte, "i" öğesi "test" öğesine koşulunda başvurur. MSBuild, bir ÖğeTanımı Grubundaki başka bir öğenin meta verilerine yapılan başvuruyu boş dize olarak yorumladığı için bu durum hiçbir zaman doğru olmayacaktır. Bu nedenle, "m" "m0" olarak ayarlanır.

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Yukarıdaki örnekte, "evet" öğesi için "i"nin meta veri değerine atıfta bulunulan Koşul referansları olarak "m1" değerine "m1" olarak ayarlanır.

## <a name="override-and-delete-metadata"></a>Meta verileri geçersiz kılma ve silme

ItemDefinitionGroup öğesinde tanımlanan meta veriler, meta veri değerini başka bir değere ayarlayarak daha sonraki bir ItemDefinitionGroup öğesinde geçersiz kılınabilir. Ayrıca, bir meta veri öğesini boş bir değere ayarlayarak etkili bir şekilde silebilirsiniz. Örnek:

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

"i" öğesi hala meta veri "m" içerir, ancak değeri artık boştur.

## <a name="scope-of-metadata"></a>Meta verilerin kapsamı

ItemDefinitionGroups tanımlanan ve küresel özellikleri nerede tanımlanırsa tanımlansınlar genel kapsama sahiptir. ItemDefinitionGroup'taki varsayılan meta veri tanımları kendi kendine başvurulabilir. Örneğin, aşağıdaki basit bir meta veri başvurusu kullanır:

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

Ancak, aşağıdakiler geçerli değildir:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

MSBuild 3.5'ten başlayarak, ItemGroups kendi kendine de ifade edilebilir. Örnek:

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
