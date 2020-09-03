---
title: 'IDebugContainerField:: EnumFields | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 485de4bdc9ff5b17c056c0db4e2930f5c6986fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205310"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kapsayıcının alanları için bir Numaralandırıcı oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwKindFilter`  
 'ndaki Numaralandırılacak alanları seçerek [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sabitlerin birleşimi. Alan türleri, sınıf veya temel gibi depolama türlerini veya yerel, parametre veya "This" işaretçisi gibi belirli bilgileri tanımlayabilir.  
  
 `dwModifiersFilter`  
 'ndaki Numaralandırılacak alanları seçerek [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) sabitlerin birleşimi. Alan değiştiricileri, genel veya özel gibi erişim izinleri veya sanal, statik veya son gibi depolama bilgileri olabilir.  
  
 `pszNameFilter`  
 'ndaki Numaralandırılacak alanın adı. Tüm alanlar döndürülürsünüz bu null bir değer olabilir.  
  
 `nameMatch`  
 'ndaki Aramanın büyük/küçük harfe duyarlı olup olmadığını denetleyen [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) numaralandırmasından bir değer.  
  
 `ppEnum`  
 dışı Alan listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Alan yoksa null değeri döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, alan yoksa S_OK veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwKindFilter`, `dwModifiersFilter` Ve `pszNameFilter` parametreleri birleştirilebilir, örneğin, "MyMethod" adlı tüm ortak sanal yöntemleri seçmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
