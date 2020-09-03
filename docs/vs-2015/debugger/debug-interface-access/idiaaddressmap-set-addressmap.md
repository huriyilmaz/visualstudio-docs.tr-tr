---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198657"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Görüntü düzeni çevirilerini desteklemek için bir adres haritası sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cbData`  
 'ndaki Parametresindeki öğelerin sayısı `data` .  
  
 `data[]`  
 'ndaki Çeviri eşlemesini tanımlayan [DiaAddressMapEntry yapı](../../debugger/debug-interface-access/diaaddressmapentry.md) yapılarının dizisi.  
  
 `imagetoSymbols`  
 [in] `TRUE` `data` parametresi yeni görüntü düzeninden özgün düzene (hata ayıklama sembolleri tarafından açıklandığı gibi) bir harita tanımlıyorsa. `FALSE` , `data` özgün düzenden alınan yeni görüntü düzenine bir haritadır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu, genellikle, program veritabanı (. pdb) dosyasındaki adres çevirisi haritalarını alır. Bu değerler eksikse, [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) yöntemi iki kez çağrılır; parametresi olarak ayarlanmış `imagetoSymbols` `TRUE` parametresi ile bir kez olarak ayarlanır `imagetoSymbols` `FALSE` . Her iki çeviri eşlemesi sağlanmamışsa, [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) yöntemi kullanılarak adres Haritası çevirileri etkinleştirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DiaAddressMapEntry yapısı](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
