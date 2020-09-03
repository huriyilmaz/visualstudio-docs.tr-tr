---
title: 'Idebugsymbolproviderdirect:: Getmethodfromadkıya| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 16ba628887f1910738df825a0965959715c5d250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155110"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Belirtilen hata ayıklama adresinde yöntemi hakkındaki bilgileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAddress`  
 'ndaki [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi tarafından temsil edilen hata ayıklama adresi.  
  
 `pGuid`  
 dışı Modülün benzersiz tanıtıcısı.  
  
 `pAppID`  
 dışı Uygulama etki alanının tanımlayıcısı.  
  
 `pTokenClass`  
 dışı Kapsayan sınıfı temsil eden belirteç.  
  
 `pTokenMethod`  
 dışı Modülünü temsil eden belirteç.  
  
 `pdwOffset`  
 dışı Parametrenin başından itibaren bayt cinsinden bir konum `pAddress` .  
  
 `pdwVersion`  
 dışı Metodun sürüm numarası.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
