---
title: '&lt;RelatedProducts &gt; öğesi (önyükleyici) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202539"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts &gt; öğesi (önyükleyici)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`RelatedProducts`Öğesi, geçerli ürüne dahil olan veya üzerine bağlı olan diğer ürünleri tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `RelatedProducts`Öğesi, öğesinin bir alt öğesidir `Product` . Hiç özniteliği yok.  
  
## <a name="dependsonproduct"></a>Bağımlı ürün  
 `DependsOnProduct`Öğesi, geçerli ürünün adlandırılan ürüne bağlı olduğunu ve adlandırılan ürünün geçerli bir uygulamadan önce yüklü olması gerektiğini belirtir. Bu, öğesinin bir alt `RelatedProducts` öğesidir. Bir `RelatedProducts` öğenin bir veya daha fazla öğesi olabilir `DependsOnProduct` .  
  
 `DependsOnProduct` aşağıdaki özniteliğe sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Code`|Öğenin özniteliğiyle belirtilen şekilde, dahil edilen ürünün kod adı `ProductCode` `Product` . Daha fazla bilgi için bkz. [ \<Product> öğesi](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>Etheri ürünleri  
 `EitherProducts`Öğesi sıfır veya daha fazla `DependsOnProduct` öğe tanımlar ve özniteliği yoktur. Bu küme içindeki en az bir tane `DependsOnProduct` , geçerli ürünün önüne yüklenmelidir. Bir `RelatedProducts` öğede sıfır veya daha fazla `EitherProducts` öğe olabilir.  
  
## <a name="includesproduct"></a>Includesürünü  
 `IncludesProduct`Öğesi, bir ürünün geçerli yüklemeye dahil edildiğini ve ayrı bir yükleme gerektirmeyeceğini belirtir. Bu, öğesinin bir alt `RelatedProducts` öğesidir. Bir `RelatedProducts` öğenin bir veya daha fazla öğesi olabilir `IncludesProduct` .  
  
 `IncludesProduct` aşağıdaki özniteliğe sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Code`|Öğenin özniteliğiyle belirtilen şekilde, dahil edilen ürünün kod adı `ProductCode` `Product` . Daha fazla bilgi için bkz. [ \<Product> öğesi](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Microsoft yükleyicisi ile birlikte yüklendiğini [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ve bu nedenle ayrı bir yüklemeye ihtiyaç duymayacak olduğunu belirtir.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Product> Dosyalarında](../deployment/product-element-bootstrapper.md)
