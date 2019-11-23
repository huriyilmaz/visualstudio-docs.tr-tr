---
title: 'Iactivescriptauthor:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f4bbcc694b24ffafd4333f635c7cdf0c67793a7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985335"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Betik için ad alanına bir tür kitaplığı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `rguidTypeLib`  
 'ndaki Eklenecek tür kitaplığının CLSID (sınıf tanımlayıcısı).  
  
 `dwMajor`  
 'ndaki Ana sürüm numarası.  
  
 `dwMinor`  
 'ndaki İkincil sürüm numarası.  
  
 `dwFlags`  
 'ndaki Kullanılmıyor.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, tür kitaplığını yüklemek için `LoadTypeLib` çağırır. Başarılı olduğunda, bu yöntem tür bilgilerini eklemek için `IActiveScriptAuthor::AddNamedItem` çağırır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Iactivescriptauthor arabirimi](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Iactivescriptauthor:: Addnamedidıtem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)