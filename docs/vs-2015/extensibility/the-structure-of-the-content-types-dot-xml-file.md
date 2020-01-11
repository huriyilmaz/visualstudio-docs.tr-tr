---
title: Content_types]. xml dosyasının yapısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3185b70f74478a9a55c4fb918c1535c86d154c76
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846365"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml Dosyasının Yapısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSıX paketindeki içerik türleri hakkında bilgi içerir. Visual Studio, paketi yüklemek için [Content_Types]. xml dosyasını kullanır, ancak dosyanın kendisini yüklemez.  
  
> [!NOTE]
> Bu konu yalnızca VSıX paketlerinde kullanılan [Content_Type]. xml dosyaları için geçerli olsa da, [Content_Types]. xml dosya türü *Açık paketleme kuralları (OPC)* standardının bir parçasıdır. Daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](https://msdn.microsoft.com/magazine/cc163372.aspx) .  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde kök öğe ve öznitelikleri ve alt öğeleri açıklanır.  
  
### <a name="root-element"></a>Kök öğe  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Types`|VSıX paketindeki dosya türlerini numaralandırmanızı sağlayan alt öğeleri içerir.|  
  
### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Xmlns`|(Gerekli.) Bu [Content_Types]. xml dosyası için kullanılan şemanın konumu.|  
  
### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliğe  
  
|                           Değer                           |                Açıklama                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | İçerik türleri şemasının konumu. |
  
### <a name="child-elements"></a>Alt Öğeler  
 `Types` öğesi herhangi bir sayıda `Default` öğesi içerebilir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Default`|VSıX paketindeki bir içerik türünü açıklar. Paketteki her dosya türünün kendi `Default` öğesi olmalıdır.|  
  
### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Extension`|VSıX paketindeki bir dosyanın dosya adı uzantısı.|  
|`ContentType`|Dosya adı uzantısıyla ilişkili içerik türünü açıklar.|  
  
### <a name="attribute-name-attribute"></a>{Öznitelik adı} Özniteliğe  
 Visual Studio, ilişkili `Extension` türleri için aşağıdaki `ContentType` değerlerini tanır.  
  
|Uzantı|contentType|  
|---------------|-----------------|  
|txt|metin/düz|  
|pkgdef|metin/düz|  
|xml|metin/XML|  
|vsixmanifest|metin/XML|  
|htm veya HTML|text/html|  
|biçimindeki|Uygulama/RTF|  
|pdf|uygulama/PDF|  
|gif|resim/GIF|  
|jpg veya JPEG|resim/jpg|  
|tiff|resim/TIFF|  
|vsix|Uygulama/zip|  
|sıkıştırma|Uygulama/zip|  
|dosyasını|application/octet-stream|  
|diğer tüm dosya türleri|application/octet-stream|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Şu [Content_Types]. xml dosyası tipik bir VSıX paketini açıklamaktadır.  
  
### <a name="code"></a>Kod  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSIX paketinin Anatomumu](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: verilerinizi paketlemeye yönelik yeni bir standart](https://msdn.microsoft.com/magazine/cc163372.aspx)
