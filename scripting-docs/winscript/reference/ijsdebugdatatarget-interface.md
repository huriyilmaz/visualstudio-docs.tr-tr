---
title: IJsDebugDataTarget arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572456"
---
# <a name="ijsdebugdatatarget-interface"></a>IJsDebugDataTarget Arabirimi
Hata ayıklayıcı tarafından, hedef hata ayıklayıcı işleminin durumunu erişim ve değiştirme işlevlerini sağlamak için uygulanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="public-methods"></a>Ortak Yöntemler  
  
|Name|Açıklama|  
|----------|-----------------|  
|[IJsDebugDataTarget::AllocateVirtualMemory Metodu](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Hedef işlemin sanal adres alanı içindeki bir bellek bölgesini ayırır ve/veya kaydeder.|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator Metodu](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Yığın çerçeveleri için bir Numaralandırıcı oluşturur.|  
|[IJsDebugDataTarget::FreeVirtualMemory Metodu](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Hedef işlemin sanal adres alanı içindeki bir bellek bölgesini serbest bırakır ve/veya kaydeder.|  
|[IJsDebugDataTarget::GetThreadContext Metodu](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Verilen iş parçacığının bağlamını alır.|  
|[IJsDebugDataTarget::GetTlsValue Metodu](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Hata ayıklanan iş parçacığı için, belirtilen TLS dizini için iş parçacığı yerel depolaması (TLS) yuvasındaki değeri alır.|  
|[IJsDebugDataTarget::ReadBSTR Metodu](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Hata ayıklama hedefinden bir BSTR okur.|  
|[IJsDebugDataTarget::ReadMemory Metodu](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Hedef işlemin belleğini okur.|  
|[IJsDebugDataTarget::ReadNullTerminatedString Metodu](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Hedeften belirtilen sayıda karakteri okur.|  
|[IJsDebugDataTarget::WriteMemory Metodu](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Hedef işlemin belleğini okur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Üstbilgi:** jscript9diag. h  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Betik Arabirimleri Başvurusu](../../winscript/reference/windows-script-interfaces-reference.md)