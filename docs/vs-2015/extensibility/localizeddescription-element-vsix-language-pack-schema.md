---
title: LocalizedDescription öğesi (VSıX dil paketi şeması) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b4eb077ba8c957466568967804487929254117e
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114230"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>LocalizedDescription öğesi (VSıX dil paketi şeması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gereklidir. Uzantının yerelleştirilmiş açıklamasını sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
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
 Gereklidir. Hedef dilde uzantının metin açıklaması.  
  
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
