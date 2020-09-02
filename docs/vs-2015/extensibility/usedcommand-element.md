---
title: UsedCommand öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186375"
---
# <a name="usedcommand-element"></a>UsedCommand Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir VSPackage 'ın, başka bir. vsct dosyasında tanımlı bir komuta erişmesine olanak sağlar. Örneğin, VSPackage, kabuk tarafından tanımlanan standart **kopyalama** komutunu kullanıyorsa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , komutu yeniden uygulamadan bir menü veya araç çubuğuna ekleyebilirsiniz.  
  
## <a name="syntax"></a>Syntax  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir. Komutu tanımlayan GUID KIMLIK çiftinin GUID 'SI.|  
|kimlik|Gereklidir. Komutu tanımlayan GUID KIMLIK çiftinin KIMLIĞI.|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Hiçbiri||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[UsedCommands Öğesi](../extensibility/usedcommands-element.md)|Gruplar, UsedCommand öğeleri ve diğer UsedCommands gruplandırmaları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğeye bir komut eklenerek `<UsedCommands>` VSPackage, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage 'ın komutunu gerektirdiğini bildirir. `<UsedCommand>`Paketinizin her bir komut için, Visual Studio 'nun tüm sürümlerine ve yapılandırmalarına dahil edilmemelidir. Örneğin, paketiniz Visual C++ özgü bir komut çağırırsa, komut için bir öğe eklemediğiniz takdirde, komut Visual Web Developer kullanıcıları tarafından kullanılamaz `<UsedCommand>` .  
  
## <a name="example"></a>Örnek  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UsedCommands öğesi](../extensibility/usedcommands-element.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
