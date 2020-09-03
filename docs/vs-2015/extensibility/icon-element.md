---
title: Icon öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5ced87596b5e40ae70e3faa06e58493da3d8ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203988"
---
# <a name="icon-element"></a>Icon Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Simge etiketinin GUID özniteliği, tanımlı bir bit eşlemin GUID 'sidir.  ID özniteliği, bit eşlem şeridinde yuva seçer. Bu öğe isteğe bağlıdır.  Bu öğe atlanırsa **guidOfficeIcon değeri: Msotcıdnoıcon** dahil edilir.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir. Tanımlı bir bit eşlemin GUID 'si.|  
|kimlik|Gereklidir. Bit eşlem şeridinde yuva seçer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Yok.|Yok.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Buttons Öğesi](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
