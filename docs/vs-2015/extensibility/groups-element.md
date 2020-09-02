---
title: Groups öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 740ca4ec-79fa-4b98-8f9a-2a137f9f7f98
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e9199ea7a74f92fec5d26c1b2a3e178224780f9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204257"
---
# <a name="groups-element"></a>Groups Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage 'un komut gruplarını tanımlayan girişleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Groups>  
  <Group>... </Group>  
  <Group>... </Group>  
</Groups>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Group Öğesi](../extensibility/group-element.md)|Tek bir komut grubunu temsil eder.|  
|[Groups Öğesi](../extensibility/groups-element.md)|VSPackage 'un komut gruplarını tanımlayan girişleri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Commands öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğundaki komutların koleksiyonunu temsil eder.|  
  
## <a name="example"></a>Örnek  
  
```  
<Groups>  
  <Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>  
  </Group>  
</Groups>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
