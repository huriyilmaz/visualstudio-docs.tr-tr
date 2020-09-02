---
title: İçeri aktarma öğesi (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f8edefc8e097f7ada67041b807231f594774548
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833527"
---
# <a name="import-element-msbuild"></a>İçeri Aktarma Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir proje dosyasının içeriğini başka bir proje dosyasına aktarır.  
  
 \<Project>  
 \<Import>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Project`|Gerekli öznitelik.<br /><br /> İçeri aktarılacak proje dosyasının yolu. Yol joker karakterler içerebilir. Eşleşen dosyalar sıralanmış sırada içeri aktarılır. Bu özelliği kullanarak, kod dosyasını bir dizine ekleyerek bir projeye kod ekleyebilirsiniz.|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Proje dosyasının gerekli kök öğesi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|[ImportGroup](../msbuild/importgroup-element.md)|`Import`İsteğe bağlı bir koşul altında gruplanmış bir öğe koleksiyonu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Import`Öğesini kullanarak, birçok proje dosyası için ortak olan kodu yeniden kullanabilirsiniz. Bu, paylaşılan kodda yaptığınız tüm güncelleştirmeler tarafından içeri aktarılan tüm projelere yayıldığından, kodun korunmasını kolaylaştırır.  
  
 Kurala göre, paylaşılan içe aktarılan proje dosyaları. targets dosyaları olarak kaydedilir, ancak bunlar standart [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proje dosyalarıdır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , farklı bir dosya adı uzantısına sahip bir projeyi içeri aktarmaya engel olmaz, ancak. targets uzantısını tutarlılık için kullanmanızı öneririz.  
  
 İçeri aktarılan projelerdeki göreli yollar, içeri aktarılan projenin dizinine göre yorumlanır. Bu nedenle, bir proje dosyası farklı konumlarda birkaç proje dosyasına aktarılmışsa, içeri aktarılan proje dosyasındaki göreli yollar, içeri aktarılan her proje için farklı şekilde yorumlanacak.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]İçeri aktarılan bir projede başvurulan, ve gibi proje dosyası ile ilgili tüm ayrılmış özelliklere, `MSBuildProjectDirectory` `MSBuildProjectFile` içeri aktarma projesi dosyasına göre değerler atanır.  
  
 İçeri aktarılan projenin bir `DefaultTargets` özniteliği yoksa, içeri aktarılan projeler içeri aktarıldıkları sırada incelenir ve ilk keşfedilen `DefaultTargets` özniteliğin değeri kullanılır. Örneğin, ProjectA, ProjectB ve ProjectC 'yi (Bu sırada) içeri aktardığında ve ProjectB, ProjectD 'yi içeri aktardığında, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] önce `DefaultTargets` ProjectA, sonra ProjectB, sonra ProjectD ve finally ProjectC ' de belirtilen öğesine bakar.  
  
 İçeri aktarılan projenin şeması, standart bir proje ile aynıdır. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]İçeri aktarılan bir proje oluşturabiliyor olsa da, içeri aktarılan bir proje genellikle hangi özelliklerin ayarlanacağı veya hedeflerin çalıştırılacağı sıra hakkında bilgi içermediği için olası bir olasılıktır. İçeri aktarılan proje, bu bilgileri sağlamak için içeri aktarıldığı projeye bağlıdır.  
  
> [!NOTE]
> Koşullu içeri aktarma deyimleri Komut satırı Msderlemeleriyle çalışırken, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik geliştirme ortamında (IDE) MSBuild ile çalışmaz. Koşullu içeri aktarmalar, proje yüklendiğinde ayarlanan yapılandırma ve platform değerleri kullanılarak değerlendirilir. Proje dosyasındaki conditionalların yeniden değerlendirilmesini gerektiren değişiklikler yapıldıktan sonra, örneğin, platformu değiştirme, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Özellikler ve öğeler üzerindeki koşulları yeniden değerlendirerek içeri aktarmaları üzerinde değil. İçeri aktarma koşulu yeniden değerlendirilmediği için içeri aktarma atlanır.  
>   
> Bu sorunu geçici olarak çözmek için. targets dosyalarına koşullu içeri aktarmalar koyun veya kodu bir [seçim öğesi (MSBuild)](../msbuild/choose-element-msbuild.md) bloğu gibi bir koşullu bloğa koyun.  
  
## <a name="wildcards"></a>Joker karakterler  
 .NET Framework 4 ' te, MSBuild proje özniteliğinde Joker karakterlere izin verir. Joker karakterler olduğunda, bulunan tüm eşleşmeler sıralanır (reproducibility için) ve ardından sipariş açıkça ayarlanmış gibi bu sırayla içeri aktarılır.  
  
 Bu, başka birinin dosya adını içeri aktarma dosyasına açıkça eklemenize gerek kalmadan bir dosyayı içeri aktarabilmesi için bir genişletilebilirlik noktası sunmak istiyorsanız yararlıdır. Bu amaçla, Microsoft. Common. targets dosyanın en üstünde aşağıdaki satırı içerir.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birkaç öğe ve özellik içeren ve genel bir proje dosyasını içeri aktaran bir projeyi gösterir.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  
  
        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs" />  
  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  
  
    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Nasıl Yapılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
