---
title: Property öğesi (MSBuild) | Microsoft Docs
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
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eefe0160328f1eb6b3fe841742547efe8be50ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158271"
---
# <a name="property-element-msbuild"></a>Özellik Öğesi (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı tanımlı özellik adı ve değeri içerir. Bir projede kullanılan her özellik [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bir öğesinin alt öğesi olarak belirtilmelidir `PropertyGroup` .  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Özellikler için gruplandırma öğesi.|  
  
## <a name="text-value"></a>Metin Değeri  
 Metin değeri isteğe bağlıdır.  
  
 Bu metin, özellik değerini belirtir ve XML içerebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Özellik adları yalnızca ASCII karakterleri ile sınırlıdır. Özellik değerleri, " `$(` " ve "" arasında özellik adı girilerek projede başvurulur `)` . Örneğin, `$(builddir)\classes` özelliğinde değer varsa, "build\classes" olarak çözümlenir `builddir` `build` . Özellikler hakkında daha fazla bilgi için bkz. [MSBuild özellikleri](msbuild-properties1.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, özelliği `Optimization` boş ise özelliğini `false` ve özelliğini `DefaultVersion` olarak ayarlar `1.0` `Version` .  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.
[MSBuild özellikleri](msbuild-properties1.md)  
 [Proje Dosyası Şema Başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
