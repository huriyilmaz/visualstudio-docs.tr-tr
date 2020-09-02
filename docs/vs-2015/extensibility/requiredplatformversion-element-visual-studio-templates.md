---
title: RequiredPlatformVersion öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e5ba8cfef6674b5603cf03c73619f686338af3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159279"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje şablonunun doğru çalışması için gereken en düşük işletim sistemi sürümünü belirtir. Bu öğe, uygulama oluşturan proje şablonları için kullanılır [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
 `RequiredPlatformVersion`Değer, işletim sisteminin sürümü ile doğrudan karşılaştırılır. , `RequiredPlatformVersion` İşletim sistemi sürümünden daha yüksekse, şablon **Yeni proje** iletişim kutusunda görünmez. Veya üzeri bir şablon belirtmek için [!INCLUDE[win8](../includes/win8-md.md)] , `RequiredPlatformVersion` 6.2.0 olarak ayarlayın. Veya üzeri bir şablon belirtmek için [!INCLUDE[win81](../includes/win81-md.md)] RequiredPlatformVersion değerini 6.3.0 olarak ayarlayın.  
  
 = 8 ' i belirten şablonlar `RequiredPlatformVersion` önceki müşteri şablonlarıyla uyumludur [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Yok.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Proje şablonunun hedeflediği platformu belirtir.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu metin, şablonun gerektirdiği en düşük işletim sistemi sürümünü belirtir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, proje şablonunun hedeflediği [!INCLUDE[win8](../includes/win8-md.md)] veya daha sonraki bir sürümünü belirtir.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TargetPlatformName öğesi (Visual Studio şablonları)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
