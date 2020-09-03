---
title: IDSymbol öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4e686b5e105b0ea0aa80783137093679d4cad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203962"
---
# <a name="idsymbol-element"></a>IDSymbol Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol`Öğesi, bir menü, Grup veya komutu temsil eden GUID: ID ÇIFTININ kimliğini içerir. GUID üst `GuidSymbol` öğeden gelir. `IDSymbol`Öğesi, `name` özniteliğinde yer alan ID için kolay bir ad sağlayan bir özniteliğe sahiptir `value` .  
  
## <a name="syntax"></a>Syntax  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Gereklidir. KIMLIK sembolünün adı.|  
|değer|Gereklidir. KIMLIK sembolünün sayısal KIMLIK değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[GuidSymbol Öğesi](../extensibility/guidsymbol-element.md)|Bir menü, Grup veya komutu temsil eden GUID: ID çiftinin GUID 'sini içerir. `IDSymbol`Öğeleri gruplandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IDSymbol`Verilen bir öğe içindeki her öğenin `GuidSymbol` benzersiz olması gerekir `value` . Ancak, `IDSymbol` aynı değerlere sahip öğeler farklı üst öğeleri oldukları sürece bir pakette bulunabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
