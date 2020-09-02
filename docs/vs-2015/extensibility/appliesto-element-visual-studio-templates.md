---
title: AppliesTo öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6622c4774be5188aced606ce4b73dffe544aea1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698934"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo Öğesi (Visual Studio Şablonları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veya daha fazla yeteneği karşılamak için isteğe bağlı bir ifade belirtir. (bkz <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> .). Özellikler, bir özellik olarak hiyerarşi aracılığıyla proje türleri tarafından gösterilir <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> . Bu sayede, şablon ortak uygulanabilir yeteneklere sahip birden fazla proje türü tarafından paylaşılabilir.  
  
 Bu öğe isteğe bağlıdır. Bir şablon dosyasında en fazla bir örnek olabilir. Bu öğe yalnızca, o anda seçili etkin projenin yeteneklerine göre bir öğe şablonunun uygulanabilir olarak tercih edilmesini sağlar. Bir öğe şablonunu uygulanamaz yapmak için kullanılamaz. Yoksa `AppliesTo` veya ifade başarılı bir şekilde kabul etmediğinde, `TemplateID` `TemplateGroupID` ürünün önceki sürümlerinde olduğu gibi, şablonu uygulanabilir hale getirmek için veya kullanılır.  
  
 Visual Studio 2013 güncelleştirme 2 ' de kullanıma sunulmuştur. Doğru sürüme başvurmak için, bkz. [VISUAL STUDIO 2013 SDK güncelleştirme 2 ' de sunulan derlemelere başvuru](https://msdn.microsoft.com/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<AppliesTo>  
  
## <a name="syntax"></a>Syntax  
  
```  
<AppliesTo>Capability1</AppliesTo>   
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablon kategorilere ayırır.|  
  
## <a name="text-value"></a>Metin Değeri  
 Bir metin değeri gereklidir. Bu metin projenin yeteneklerini belirtir.  
  
 Geçerli ifade sözdizimi şu şekilde tanımlanır:  
  
- "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)" gibi yetenek ifadesi.  
  
- "&#124;", OR işleçtir.  
  
- "&" ve "+" karakterleri hem hem de işleçleridir.  
  
- "!" karakteri NOT işlecidir.  
  
- Parantezler değerlendirme-öncelik sırasını zorlar.  
  
- Null veya boş ifade bir eşleşme olarak değerlendirilir.  
  
- Proje özellikleri şu ayrılmış karakterler dışında herhangi bir karakter olabilir: "' ':;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>? \t\b\n\r  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç farklı şablonu göstermektedir. `Template1` Tüm C# proje türlerine veya özelliğini destekleyen diğer proje türlerine uygulanır `WindowsAppContainer` . `Template2` her türlü C# projesi için geçerlidir. `Template3` Proje olmayan C# projelerine uygulanır `WindowsAppContainer` .  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
