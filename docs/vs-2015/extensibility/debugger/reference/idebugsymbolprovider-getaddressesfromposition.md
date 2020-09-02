---
title: 'IDebugSymbolProvider:: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27349cfdc438da133c4cea05077649ebb4df376c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547162"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem bir belge konumunu hata ayıklama adresleri dizisiyle eşler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pDocPos`  
 'ndaki Belge konumu.  
  
 `fStatmentOnly`  
 'ndaki TRUE ise, hata ayıklama adreslerini tek bir deyimle sınırlandırır.  
  
 `ppEnumBegAddresses`  
 dışı Bu deyimle veya satırla ilişkili başlangıç hata ayıklama adresleri için bir Numaralandırıcı döndürür.  
  
 `ppEnumEndAddresses`  
 dışı Bu deyimle veya satırla ilişkili bitiş hata ayıklama adresleri için bir [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) numaralandırıcısı döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Belge konumu genellikle kaynak satır aralığını gösterir. Bu yöntem, bu satırlarla ilişkili hata ayıklama adreslerini başlatma ve sonlandırma sağlar. Bazı diller birden çok satırı kapsayan deyimlere veya birden fazla deyim içeren satırlara izin verir. Bu yöntem, hata ayıklama adreslerini tek bir deyimle sınırlamak için bir bayrak sağlar.  
  
 Tek bir deyimin, şablonlar söz konusu olduğunda olduğu gibi birden çok hata ayıklama adresi olması mümkündür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
