---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12945998b215e9082591fad514bd9c16ab789405
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203887"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense ana bilgisayar bayraklarını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Üyeler|Açıklama|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Bağlam arabelleği salt okunurdur.|  
|`IHF_NOSEPARATESUBJECT`|Konu metni yok. Bağlam arabelleği IntelliSense-target (anlamına gelir `!IHF_READONLYCONTEXT` ) içerir.|  
|`IHF_SINGLELINESUBJECT`|Konu metni çok satırlı özellikli değil.|  
|`IHF_FORCECOMMITTOCONTEXT`|Aynı `CanCommitIntoReadOnlyBuffer` .|  
|`IHF_OVERTYPE`|Düzenlemenin (konu veya bağlamda) üzerine yazma modunda yapılması gerekir.|  
  
## <a name="requirements"></a>Gereksinimler  
 SingleFileeditor. IDL  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
