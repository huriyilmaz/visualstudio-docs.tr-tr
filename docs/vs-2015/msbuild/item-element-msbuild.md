---
title: Item öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc3d606bb890b5f95089bfc7b1e83b2d34cd56ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192612"
---
# <a name="item-element-msbuild"></a>Öğe Unsuru (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı tanımlı bir öğe ve onun meta verilerini içerir. Bir projede kullanılan her öğe, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bir öğesinin alt öğesi olarak belirtilmelidir `ItemGroup` .  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Include`|Gerekli öznitelik.<br /><br /> Öğe listesine dahil edilecek dosya veya joker karakter.|  
|`Exclude`|İsteğe bağlı öznitelik.<br /><br /> Öğe listesinden dışlanacak dosya veya joker karakter.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
|`Remove`|İsteğe bağlı öznitelik.<br /><br /> Öğe listesinden kaldırılacak dosya veya joker karakter.<br /><br /> Bu öznitelik yalnızca içindeki bir öğesi için belirtilmişse geçerlidir `ItemGroup` `Target` .|  
|`KeepMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğelere eklenecek kaynak öğelerinin meta verileri. Yalnızca adları noktalı virgülle ayrılmış listede belirtilen meta veriler bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca içindeki bir öğesi için belirtilmişse geçerlidir `ItemGroup` `Target` .|  
|`RemoveMetadata`|İsteğe bağlı öznitelik.<br /><br /> Hedef öğelere aktarılamayan kaynak öğelerinin meta verileri. Tüm meta veriler, adları noktalı virgülle ayrılmış ad listesinde yer alan meta veriler hariç bir kaynak öğeden hedef öğeye aktarılır. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca içindeki bir öğesi için belirtilmişse geçerlidir `ItemGroup` `Target` .|  
|`KeepDuplicates`|İsteğe bağlı öznitelik.<br /><br /> Bir öğenin, var olan bir öğenin tam yinelemesi olması halinde, hedef gruba eklenip eklenmeyeceğini belirtir. Kaynak ve hedef öğe aynı `Include` değere ancak farklı meta verilere sahip ise, olarak ayarlanmış olsa bile öğe eklenir `KeepDuplicates` `false` . Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).<br /><br /> Bu öznitelik yalnızca içindeki bir öğesi için belirtilmişse geçerlidir `ItemGroup` `Target` .|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Öğe meta veri değerini içeren Kullanıcı tanımlı öğe meta verileri anahtarı. Bir öğede sıfır veya daha fazla `ItemMetadata` öğe olabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Öğeler için gruplandırma öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Item` öğeler Yapı sistemine giriş tanımlar ve Kullanıcı tanımlı koleksiyon adlarına göre öğe koleksiyonları halinde gruplandırılır. Bu öğe koleksiyonları, yapı işlemi adımlarını gerçekleştirmek için koleksiyonlardaki ayrı öğeleri kullanan [Görevler](../msbuild/msbuild-tasks.md)için parametre olarak kullanılabilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).  
  
 `@(` *MyType* gösterimini kullanmak `)` *MyType* türünde bir öğe koleksiyonunun noktalı virgülle ayrılmış bir dize listesine genişletilmesini ve bir parametreye geçirilmesini sağlar. Parametresi tür ise `string` , parametrenin değeri noktalı virgülle ayırarak öğelerin listesidir. Parametresi bir dizeler diziyse ( `string[]` ), her öğe noktalı virgül konumunu temel alarak diziye eklenir. Görev parametresi tür ise <xref:Microsoft.Build.Framework.ITaskItem> `[]` , bu değer, eklenen tüm meta verilerle birlikte öğe koleksiyonunun içeriğidir. Noktalı virgül dışında bir karakter kullanarak her öğeyi sınırlandırmak için `@(` *MyType* `, '` *ayırıcı*sözdizimini kullanın `')` .  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Motor ve gibi joker karakterleri ve gibi `*` `?` özyinelemeli joker karakterleri değerlendirebilir `/**/*.cs` . Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, türünde iki öğenin nasıl bildirilemeyeceğini gösterir `CSFile` . Belirtilen ikinci öğe, olarak ayarlanmış meta verileri içerir `MyMetadata` `HelloWorld` .  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğeler](../msbuild/msbuild-items.md)   
 [MSBuild özellikleri](msbuild-properties1.md)   
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
