---
title: CommandTable öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477044"
---
# <a name="commandtable-element"></a>CommandTable Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable,. vsct dosyasının kök öğesidir. Bu, bir VSPackage 'ın IDE 'ye sağladığı komutların gerçek düzen ve türünü tanımlayan dosyadır. Komutlar Menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları içerebilir. Daha fazla bilgi için bkz [. Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
| Öznitelik |                                                                                                                   Açıklama                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   özniteliði   |                                   Gereklidir. XML ad alanları:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| language  | İsteğe bağlı. Language özniteliği, komut tablosundaki tüm öğelerin varsayılan dilini belirtmek için kullanılabilir \<Strings> .  Dil belirtilmezse, geçerli işlemin dili kullanılacaktır:<br /><br /> Language = "en-US" |
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Extern Öğesi](../extensibility/extern-element.md)|İsteğe bağlı. Derleyici için önişlemci yönergelerini içerir.|  
|[Include Öğesi](../extensibility/include-element.md)|İsteğe bağlı. Derlemeye dahil edilecek herhangi bir dosyanın yolunu içerir.|  
|[Define Öğesi](../extensibility/define-element.md)|İsteğe bağlı. Adı ve değeri verilen bir sembol tanımlar.|  
|[Commands öğesi](../extensibility/commands-element.md)|İsteğe bağlı. Tüm diğer öğeleri içeren VSPackage için tüm komutları tanımlayan üst öğe.|  
|[CommandPlacements Öğesi](../extensibility/commandplacements-element.md)|İsteğe bağlı. Komut çubuğundaki komutların nereye yerleştirileceğini tanımlar.|  
|[VisibilityConstraints Öğesi](../extensibility/visibilityconstraints-element.md)|İsteğe bağlı. Komutların ve araç çubuklarının statik görünürlüğünü belirler.|  
|[KeyBindings Öğesi](../extensibility/keybindings-element.md)|İsteğe bağlı. Varsa, komutlar için kısayol tuş bileşimlerini belirtir.|  
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|İsteğe bağlı. Bir VSPackage 'ın, özgün olarak diğer VSPackages tarafından desteklenen kendi işlev sürümünü kullanmasına izin verir.|  
|[Symbols Öğesi](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|İsteğe bağlı. Derleyici için herhangi bir sembol verisi (--Guid, kimlik vb.) içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Hiçbiri||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
