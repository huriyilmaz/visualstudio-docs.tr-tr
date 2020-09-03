---
title: 'Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d388d32b288e47a7e92f5d0f727230ffa00a2621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178329"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl Yapılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birkaç [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası oluşturduysanız, farklı proje dosyalarında aynı görevleri ve hedefleri kullanmanız gerektiğini fark edebilirsiniz. Her proje dosyasındaki bu görevlerin veya hedeflerin tüm açıklamalarını eklemek yerine, bir hedefi ayrı bir proje dosyasında kaydedebilir ve sonra bu projeyi, hedefi kullanmak için gereken diğer bir projeye içeri aktarabilirsiniz.  
  
## <a name="using-the-import-element"></a>Içeri aktarma öğesini kullanma  
 Öğesi, başka bir proje dosyasına `Import` bir proje dosyası eklemek için kullanılır. İçeri aktarılmakta olan proje dosyası geçerli bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Proje dosyası olmalıdır ve iyi BIÇIMLENDIRILMIŞ XML içermelidir. `Project`Öznitelik, içeri aktarılan proje dosyasının yolunu belirtir. Öğesi hakkında daha fazla bilgi için `Import` bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Bir projeyi içeri aktarmak için  
  
1. İçeri aktarılan projedeki Özellikler ve öğeler için parametre olarak kullanılan proje dosyasını içeri aktarma, tüm özellikler ve öğeler ' i tanımlayın.  
  
2. `Import`Projeyi içeri aktarmak için öğesini kullanın. Örneğin:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3. Öğesini takip `Import` eden tüm özellikleri ve içeri aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken öğeleri tanımlayın.  
  
## <a name="order-of-evaluation"></a>Değerlendirme Sırası  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Bir öğeye ulaştığında `Import` , içeri aktarılan proje, öğe konumundaki içeri aktarma projesine etkin bir şekilde eklenir `Import` . Bu nedenle, `Import` öğesinin konumu Özellikler ve öğelerin değerlerini etkileyebilir. İçeri aktarılan proje tarafından ayarlanan özellikleri ve öğeleri ve içeri aktarılan projenin kullandığı özellikleri ve öğeleri anlamak önemlidir.  
  
 Proje oluşturulduğunda tüm özellikler önce değerlendirilir ve ardından öğeler gelir. Örneğin, aşağıdaki XML içeri aktarılan proje dosyasını MyCommon. targets olarak tanımlar:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Aşağıdaki XML, MyCommon. targets içeri aktaran MyApp. proj öğesini tanımlar:  
  
```  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Proje oluşturduğunda, aşağıdaki ileti görüntülenir:  
  
 `Name="MyCommon"`  
  
 Proje, özelliği `Name` MyApp. proj içinde tanımlandıktan sonra içeri aktarıldığından `Name` MyCommon. targets içindeki tanımı, MyApp. proj içindeki tanımı geçersiz kılar. Eğer proje, özellik adı tanımlanmadan önce içeri aktarıldıysa, yapı aşağıdaki iletiyi görüntüler:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri içeri aktarırken aşağıdaki yaklaşımı kullanın  
  
1. Proje dosyasında, içeri aktarılan projedeki Özellikler ve öğeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.  
  
2. Projeyi içeri aktarın.  
  
3. Proje dosyasında, içeri aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken tüm özellikleri ve öğeleri tanımlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ikinci kod örneği içe aktardığı MyCommon. targets dosyasını gösterir. . Targets dosyası, derlemeyi yapılandırmak için içeri aktarma projesinden özellikleri değerlendirir.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği MyCommon. targets dosyasını içeri aktarır.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Targets](../msbuild/msbuild-targets.md)
