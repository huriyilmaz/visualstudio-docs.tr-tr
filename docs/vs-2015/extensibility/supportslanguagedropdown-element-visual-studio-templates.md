---
title: SupportsLanguageDropDown öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53703d6178c81758650fdd00aada0a5952734caa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160483"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web öğesi şablonunun birden çok dil için aynı olup olmadığını ve **Yeni öğe Ekle** Iletişim kutusunda **dil** seçeneğinin etkinleştirilip etkinleştirilmediğini belirtir.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SupportsLanguageDropDown>  
  
## <a name="syntax"></a>Syntax  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir.  
  
 Metin ya da `true` `false` , **dil** seçeneğinin **Yeni öğe Ekle** iletişim kutusundan kullanılıp kullanılamayacağını belirten olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SupportsLanguageDropDown` isteğe bağlı bir öğedir. Varsayılan değer: `false`.  
  
 `SupportsLanguageDropDown`Öğesi yalnızca Web öğesi şablonları için kullanılabilir.  
  
 Bu öğe için değer olarak ayarlanırsa `true` , öğe şablonu tüm programlama dilleri için aynı olur ve **Yeni öğe Ekle** iletişim kutusunda **dil** seçeneği etkinleştirilir. Bu seçenek, şablondan oluşturmak istediğiniz yeni öğenin programlama dilini seçmenizi sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, **dil** açılan seçeneğini göstermek için belirtir.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
