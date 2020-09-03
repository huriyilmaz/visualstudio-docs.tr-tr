---
title: ButtonText öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184575"
---
# <a name="buttontext-element"></a>ButtonText Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu alan, çeşitli menülerde görüntülenen metni belirtmenize olanak tanır. Varsayılan olarak, `ButtonText` öğesi menü denetleyicileri ' nde görünür. `ButtonText`Diğer metin alanları boşsa, öğesi de varsayılan olarak olur. `ButtonText`Diğer metin alanları belirtilmiş olsa bile öğe boş bırakılamaz.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Dizeler öğesi](../extensibility/strings-element.md)|Ve gibi metin öğelerini gruplandırır `ButtonText` `CommandName` .|  
  
## <a name="text-value"></a>Metin Değeri  
 Öğesinin metin değeri, `ButtonText` menü öğeleri, combos ve görünür metne sahip diğer kullanıcı arabirimi (UI) öğeleri için görüntülenen metni sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
