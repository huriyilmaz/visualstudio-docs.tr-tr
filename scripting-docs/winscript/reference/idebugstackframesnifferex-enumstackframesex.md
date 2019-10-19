---
title: 'Idebugstackframesnifferex:: EnumStackFramesEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576702"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Geçerli iş parçacığı için yığın çerçevelerinin bir Numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwSpMin`  
 'ndaki Yığın çerçevelerini listelemek için daha düşük adres sınırı.  
  
 `ppedsf`  
 dışı Geçerli iş parçacığı için yığın çerçevelerinin numaralandırıcısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntemi bir `HRESULT` döndürür. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın çerçeve numaralandırıcısı, en son gönderilen kareyle birlikte yığının en üstünde başlayan kareleri döndürür. Numaralandırıcı yalnızca `dwSpMin` eşit veya daha büyük adreslere sahip yığın çerçeveleri içeriyor.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugStackFrameSnifferEx Arabirimi](../../winscript/reference/idebugstackframesnifferex-interface.md)