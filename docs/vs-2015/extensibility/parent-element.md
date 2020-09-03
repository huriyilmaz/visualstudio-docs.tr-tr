---
title: Üst öğe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2086473bc484fed4e8e351f0c3838074557586c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194083"
---
# <a name="parent-element"></a>Üst Öğe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir düğme veya Birleşik giriş kutusunun üst öğesi yalnızca bir grup olabilir. Bir menünün veya grubun üstü başka bir menü veya grup olabilir. [Commandyerleştirme öğesinde](../extensibility/commandplacement-element.md)bu öğe gereklidir; diğer tüm örneklerde, bu isteğe bağlıdır. Bu öğe atlanırsa, üst öğesi de `Group_Undefined:0` kapsanır.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.|  
|kimlik|Gereklidir. GUID/ID komut tanımlayıcısının KIMLIĞI.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[CommandTable Öğesi](../extensibility/commandtable-element.md)|Bir VSPackage 'ın tümleşik geliştirme ortamına (IDE) sağladığı komutları temsil eden tüm öğeleri tanımlar. Örneğin, menü öğeleri, menüler, araç çubukları ve Birleşik giriş kutuları.|  
|[Buttons Öğesi](../extensibility/buttons-element.md)|Gruplar [düğme öğesi](../extensibility/button-element.md) öğeleri.|  
|[Menus Öğesi](../extensibility/menus-element.md)|VSPackage 'ın uyguladığı tüm menüleri tanımlar.|  
|[Groups Öğesi](../extensibility/groups-element.md)|VSPackage 'un komut gruplarını tanımlayan girişleri içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
