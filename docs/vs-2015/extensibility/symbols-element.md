---
title: Symbols öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8d28d225bd3a8d5c105bf54b9c63574002aed15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160454"
---
# <a name="symbols-element"></a>Symbols Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diğer VSCT öğeleri tarafından kullanılan GUID 'Leri ve kimlikleri tanımlar. Yönetilmeyen kod için bu bilgiler genellikle [extern öğesi](../extensibility/extern-element.md)tarafından belirtilen başlık dosyalarından gelir. Yönetilen kod, bu bilgileri tanımlamak için semboller öğesinin alt öğelerini kullanır.  
  
 Var olan bir. CTO dosyasından bir. vsct dosyası oluşturursanız, semboller semboller öğesinin alt öğesi olarak oluşturulur. Daha fazla bilgi için bkz [. nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTO dosyası](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Sembol öğesi, Önişlemci tarafından kullanılmak üzere ad-değer çiftlerini tanımlayan [define öğesiyle](../extensibility/define-element.md)karıştırılmamalıdır.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Hiçbiri||  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|GuidSymbol|Bir GUID sembolünü tanımlar. GuidSymbol iki gerekli özniteliğe sahiptir: ad ve değer. Ad, simgenin adıdır ve değer, GUID 'in bir dize olarak değeridir.<br /><br /> Örneğin:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|  
|IDSymbol|Bir sembol tanımlar. IDSymbol iki gerekli özniteliğe sahiptir: ad ve değer. Ad, simgenin adıdır ve değer, sembolün bir dize olarak değeridir.<br /><br /> Örneğin:\<IDSymbol name="MyMenuGroup" value="0x1020" />|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|. Vsct dosyasının kök öğesi.|  
  
## <a name="example"></a>Örnek  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
