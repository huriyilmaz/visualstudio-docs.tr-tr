---
title: Öğe tanımları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7097311c3d1aae718096c3bf74ec04c3e5ea8818
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779616"
---
# <a name="item-definitions"></a>Öğe Tanımları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2,0, [ItemGroup](../msbuild/itemgroup-element-msbuild.md) öğesini kullanarak proje dosyalarındaki öğelerin statik bildirimini sunar. Ancak meta veriler, tüm öğeler için özdeş olsa bile yalnızca öğe düzeyinde eklenebilir. 3,5 ' den başlayarak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) adlı bir proje öğesi bu sınırlamaya sahiptir. *ItemDefinitionGroup* , adlandırılmış öğe türündeki tüm öğelere varsayılan meta veri değerleri ekleyen bir öğe tanımları kümesi tanımlamanızı sağlar.  
  
 *ItemDefinitionGroup* öğesi proje dosyasının [Proje](../msbuild/project-element-msbuild.md) öğesinden hemen sonra görünür. Öğe tanımları aşağıdaki işlevleri sağlar:  
  
- Bir hedefin dışındaki öğeler için genel varsayılan meta verileri tanımlayabilirsiniz. Diğer bir deyişle, aynı meta veriler belirtilen türdeki tüm öğeler için geçerlidir.  
  
- Öğe türlerinde birden çok tanım olabilir. Türe ek meta veri belirtimleri eklendiğinde, son belirtim öncelik kazanır. \(Meta veriler, Özellikler takip eden içeri aktarma sırasını izler.\)  
  
- Meta veriler eklenebilir. Örneğin, Ctanımlıyor değerleri, ayarlanmakta olan özelliklere bağlı olarak koşullu olarak toplanır. Örneğin, `MT;STD_CALL;DEBUG;UNICODE`.  
  
- Meta veriler kaldırılabilir.  
  
- Koşullar, meta verilerin eklenmesini denetlemek için kullanılabilir.  
  
## <a name="item-metadata-default-values"></a>Öğe meta verileri varsayılan değerleri  
 Bir ItemDefinitionGroup içinde tanımlanan öğe meta verileri yalnızca varsayılan meta verilerin bir bildirimidir. Meta veri değerlerini içeren bir ItemGroup kullanan bir öğe tanımlamadığınız takdirde meta veriler uygulanmaz.  
  
> [!NOTE]
> Bu konudaki örneklerin çoğunda, bir ItemDefinitionGroup öğesi gösteriliyor ancak karşılık gelen ItemGroup tanımı açıklık için atlandı.  
  
 Bir ItemGroup içinde açıkça tanımlanan meta veriler, ItemDefinitionGroup içindeki meta verilerden önceliklidir. ItemDefinitionGroup içindeki meta veriler yalnızca bir ItemGroup içindeki tanımsız meta veriler için uygulandı. Örneğin:  
  
```  
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
> XML öğesi ve parametre adları büyük/küçük harfe \- duyarlıdır. Öğe meta verileri ve öğe \/ özelliği adları büyük/küçük harfe \- duyarlı değildir. Bu nedenle, yalnızca büyük/küçük harfe göre farklı adlara sahip olan ItemDefinitionGroup öğeleri aynı ItemGroup olarak değerlendirilmelidir.  
  
## <a name="value-sources"></a>Değer kaynakları  
 Bir ItemDefinitionGroup içinde tanımlanan meta verilerin değerleri, aşağıdaki gibi birçok farklı kaynaktan gelebilir:  
  
- PropertyGroup özelliği  
  
- ItemDefinitionGroup 'tan öğe  
  
- Bir ItemDefinitionGroup öğesinde öğe dönüştürme  
  
- Ortam değişkeni  
  
- \(MSBuild.exe komut satırındaki genel özellik\)  
  
- Ayrılmış Özellik  
  
- \-ItemDefinitionGroup 'tan bir öğe üzerinde iyi bilinen meta veriler  
  
- CDATA bölümü \<\!\[CDATA\[anything here is not parsed\]\]\>  
  
> [!NOTE]
> ItemDefinitionGroup öğeleri ItemGroup öğelerinden önce işlendiğinden, ItemGroup 'tan öğe meta verileri bir ItemDefinitionGroup meta veri bildiriminde yararlı değildir.  
  
## <a name="additive-and-multiple-definitions"></a>Eklenebilir ve birden çok tanım  
 Tanımlar eklediğinizde veya birden çok ItemDefinitionGroups kullandığınızda, aşağıdakileri unutmayın:  
  
- Ek meta veri belirtimi türe eklenir.  
  
- Son belirtim öncelik kazanır.  
  
  Birden çok ItemDefinitionGroups varsa, izleyen her belirtim meta verilerini önceki tanımına ekler. Örneğin:  
  
```  
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
  
 Ayrıca, önceden tanımlanmış meta veri değerleri de eklenebilir. Örneğin:  
  
```  
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
  
 Bu örnekte, "d" M1 için önceden tanımlanmış değer, \( \) Yeni \( bir değer olan m2 için eklenmiştir \) , böylece son değer "M1; m2" olur.  
  
> [!NOTE]
> Bu, aynı ItemDefinitionGroup içinde de gerçekleşebilir.  
  
 Önceden tanımlanmış meta verileri geçersiz kıldığınızda, son belirtim öncelik kazanır. Aşağıdaki örnekte, "m" meta verisinin son değeri "M1" öğesinden "M1A" öğesine gider.  
  
```  
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
  
## <a name="using-conditions-in-an-itemdefinitiongroup"></a>Bir ItemDefinitionGroup içindeki koşulları kullanma  
 Meta verilerin eklenmesini denetlemek için bir ItemDefinitionGroup içindeki koşulları kullanabilirsiniz. Örneğin:  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Bu durumda, "i" öğesinde "M1" varsayılan meta verileri yalnızca "Configuration" özelliğinin değeri "Debug" ise dahil edilir.  
  
> [!NOTE]
> Koşullarda yalnızca yerel meta veri başvuruları desteklenir.  
  
 Önceki bir ItemDefinitionGroup içinde tanımlanan meta verilere yapılan başvurular, tanım grubuna değil, öğe için yereldir. Diğer bir deyişle, başvuruların kapsamı öğeye \- özeldir. Örneğin:  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Bu örnekte, "i" öğesi koşuldaki "test" öğesine başvuruyor.  
  
## <a name="overriding-and-deleting-metadata"></a>Meta verileri geçersiz kılma ve silme  
 Bir ItemDefinitionGroup öğesinde tanımlanan meta veriler, meta veri değeri boş olarak ayarlanarak sonraki bir ItemDefinitionGroup öğesinde geçersiz kılınabilir. Ayrıca, bir meta veri öğesini boş bir değere ayarlayarak etkin bir şekilde silebilirsiniz. Örneğin:  
  
```  
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
 ItemDefinitionGroups tanımlandıklarında, tanımlı ve genel özelliklerde genel kapsama sahiptir. Bir ItemDefinitionGroup içindeki varsayılan meta veri tanımları kendine \- başvuru yapabilir. Örneğin, aşağıdaki bir basit meta veri başvurusu kullanır:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Nitelikli bir meta veri başvurusu da kullanılabilir:  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Ancak, şunlar geçerli değildir:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 3,5 ' den başlayarak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , ItemGroups da kendine \- başvuru yapabilir. Örneğin:  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Toplu İşleme](../msbuild/msbuild-batching.md)
