---
title: CustomParameter öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59bfec972750a4f893d1cb8b7cf08710bcca761a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555979"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel bir parametre adı ve değeri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gereklidir. Parametrenin adı. Parametrelerin biçimi $*Name*$ olur.|  
|`Value`|Gereklidir. Parametrenin değiştirme değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Sihirbaz parametre değişiklikleri yaptığında şablon sihirbazına geçirilecek özel parametreleri gruplandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şablon `CustomParameter` öğeleri içerdiğinde, her örnek `Name` özniteliği `Value` oluşturulan proje veya öğe dosyalarındaki özniteliğiyle değiştirilmiştir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir şablonda birkaç özel parametrenin nasıl kullanılacağını gösterir. Bir şablon veya öğe, aşağıdaki özel parametrelerle bir şablondan oluşturulduğunda, `$color1$` `$color2$` şablon dosyalarındaki ve içindeki tüm örnekleri sırasıyla ve ile yerine geçer `Red` `Blue` .  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Şablon parametreleri](../ide/template-parameters.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
