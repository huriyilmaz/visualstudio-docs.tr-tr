---
title: Content_types Yapısı].xml Dosyası | Microsoft Dokümanlar
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
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395367"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>[Content_types].xml Dosyasının Yapısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX paketindeki içerik türleri hakkında bilgi içerir. Visual Studio paketi yüklemek için [Content_Types].xml dosyasını kullanır, ancak dosyanın kendisini yüklemez.  
  
> [!NOTE]
> Bu konu yalnızca VSIX paketlerinde kullanılan [Content_Type].xml dosyaları için geçerli olsa da, [Content_Types].xml dosya türü *Açık Ambalaj Sözleşmeleri (OPC)* standardının bir parçasıdır. Daha fazla bilgi için, MsDN Web sitesinde [Verilerinizi Paketlemek için Yeni Bir Standart Olan OPC:](https://msdn.microsoft.com/magazine/cc163372.aspx)  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde kök öğesi ve öznitelikleri ve alt öğeleri açıklayınız.  
  
### <a name="root-element"></a>Kök Öğesi  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Types`|VSIX paketinde dosya türlerini sayısala bilen alt öğeler içerir.|  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Xmlns`|(Gerekli.) Bu [Content_Types].xml dosyası için kullanılan şema konumu.|  
  
### <a name="attribute-name-attribute"></a>{Öznitelik adı} Öznitelik  
  
|                           Değer                           |                Açıklama                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | İçerik türlerinin konumu şema. |
  
### <a name="child-elements"></a>Alt Öğeler  
 Öğe `Types` herhangi bir sayıda `Default` öğe içerebilir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Default`|VSIX paketindeki içerik türünü açıklar. Paketteki her dosya türünün `Default` kendi öğesi olmalıdır.|  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Extension`|VSIX paketindeki bir dosyanın dosya adı uzantısı.|  
|`ContentType`|Dosya adı uzantısı ile ilişkili içerik türünü açıklar.|  
  
### <a name="attribute-name-attribute"></a>{Öznitelik adı} Öznitelik  
 Visual Studio ilişkili `ContentType` `Extension` türleri için aşağıdaki değerleri tanır.  
  
|Dahili numara|Contenttype|  
|---------------|-----------------|  
|Txt|metin/düz|  
|pkgdef|metin/düz|  
|xml|metin/xml|  
|vsixmanifest|metin/xml|  
|htm veya html|text/html|  
|Rtf|uygulama/rtf|  
|pdf|uygulama/pdf|  
|Gıf|resim/gif|  
|jpg veya jpeg|resim/jpg|  
|tiff|resim/tiff|  
|vsix|uygulama/zip|  
|Zip|uygulama/zip|  
|Dll|uygulama/sekizli-akarsu|  
|diğer tüm dosya türleri|uygulama/sekizli-akarsu|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki [Content_Types].xml dosyası tipik bir VSIX paketini açıklar.  
  
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
 [VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX Uzatma Şeması 1.0 Referans](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Verilerinizi Paketlemek için Yeni Bir Standart](https://msdn.microsoft.com/magazine/cc163372.aspx)
