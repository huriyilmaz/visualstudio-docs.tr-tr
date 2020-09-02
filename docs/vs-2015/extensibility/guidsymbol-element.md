---
title: GuidSymbol öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204217"
---
# <a name="guidsymbol-element"></a>GuidSymbol Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`Öğesi, bir menü, Grup veya komutu temsil eden GUID: ID ÇIFTININ GUID 'sini içerir. KIMLIĞI `IDSymbol` , öğesindeki bir öğeden gelir `GuidSymbol` . `GuidSymbol`Öğesi, `name` özniteliğinde yer alan GUID için kolay bir ad sağlayan bir özniteliğe sahiptir `value` .  
  
## <a name="syntax"></a>Syntax  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Gereklidir. GUID sembolünün adı.|  
|değer|Gereklidir. GUID sembolünün GUID 'SI.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[IDSymbol Öğesi](../extensibility/idsymbol-element.md)|Bir menü, Grup veya komutu temsil eden GUID: ID çiftinin KIMLIĞINI içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Symbols Öğesi](../extensibility/symbols-element.md)|`GuidSymbol`. Vsct dosyasındaki öğeleri gruplandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genellikle, bir. vsct dosyası kendi bölümünde, biri paketin kendisi için, biri `GuidSymbol` `Symbols` komut kümesi için (menülerin, grupların ve paketin kullanılabilir hale getiren komutlar koleksiyonu) ve düğmeler ve diğer görsel bileşenlere simgeler sağlayan bit eşlemler için olmak üzere üç öğesi içerir. `IDSymbol`Verilen bir öğe içindeki her öğenin `GuidSymbol` benzersiz olması gerekir `value` . Ancak, `IDSymbol` aynı değerlere sahip öğeler farklı üst öğeleri oldukları sürece bir pakette bulunabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
