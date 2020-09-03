---
title: Commandyerleştirmesini öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43fd417c4d54c0ab57133cf6dbff2c770c1ffc45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184329"
---
# <a name="commandplacement-element"></a>CommandPlacement Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Commandyerleştirme öğesi düğmelerin, grupların ve menülerin birden fazla gruba veya menüye dahil edilmesini sağlar. Commandyerleştirme öğesini kullanarak, Kullanıcı arabiriminin görünümünü değiştirmek için bu öğeleri tamamen yeniden tanımlamanız gerekmez.  
  
 Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir. [Sembol öğesinde](../extensibility/symbols-element.md)tanımlandığı şekilde, komut kümesinin GUID 'si.|  
|kimlik|Gereklidir. İçinde tanımlandığı şekilde, yerleştirilecek menü, Grup veya komutun kimliği `Symbols Element` .|  
|Priority|Gereklidir. Öğenin üst öğesinde görsel konumunu belirler.|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Üst|Gereklidir. Yerleştirilecek öğeyi barındıran menü veya grup.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandPlacements Öğesi](../extensibility/commandplacements-element.md)|CommandPlacements ve Commandyerleştirme öğelerinin gruplarını belirtir.|  
  
## <a name="example"></a>Örnek  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CommandPlacements öğesi](../extensibility/commandplacements-element.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
