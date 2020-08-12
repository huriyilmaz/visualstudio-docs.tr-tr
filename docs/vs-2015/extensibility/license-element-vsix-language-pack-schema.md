---
title: License öğesi (VSıX dil paketi şeması) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91f0792f64e09292836a3b2d60f669c67903b3a7
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114190"
---
# <a name="license-element-vsix-language-pack-schema"></a>License öğesi (VSıX dil paketi şeması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İsteğe bağlı. Uzantı için lisans dosyasının yerelleştirilmiş bir sürümünün yolu.  
  
## <a name="syntax"></a>Syntax  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Yok||  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Yok||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[VSIX LanguagePack Öğesi](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Gereklidir. VSıX dil paketi için kök öğesi sağlar.|  
  
## <a name="text-value"></a>Metin Değeri  
 Görüntülenecek yerelleştirilmiş lisans dosyasının göreli yolu.  
  
## <a name="remarks"></a>Açıklamalar  
 `License`Öğe tanımlanmışsa, belirlenen lisans dosyasının metni kurulum sırasında görüntülenir ve kullanıcının devam etmesi için lisansı kabul etmesi gerekir.  
  
## <a name="element-information"></a>Öğe Bilgisi  

:::row:::
    :::column:::
        Ad Alanı  
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Şema adı
    :::column-end:::
    :::column:::
        VSıX dil paketi şeması
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Doğrulama dosyası
    :::column-end:::
    :::column:::
        Valtlanguagepackschema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Boş olabilir
    :::column-end:::
    :::column:::
        Uygulanamaz
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSX dil paketi şema başvurusu](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSıX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)   
 [VSıX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110))
