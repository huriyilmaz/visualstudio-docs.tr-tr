---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198677"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Adres eşlemesinin sembol adreslerini çevirmek için kullanılıp kullanılmayacağını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 NewVal  
 'ndaki `TRUE` Simgelerin çevirisini etkinleştirmek veya devre dışı bırakmak için olarak ayarlayın `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Yürütülebilir son işlemciler bazen yürütülebilir dosyayı güncelleştirebilir. DIA, sembollerin yeni düzene çevirisini desteklemek için bir mekanizma içerir.  
  
 Bir PDB dosyası yüklendiğinde, dosyada depolanan adres eşlemesi etkinleştirilir. Ancak, bir istemci uygulamanın [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) yöntemini çağırarak kendi adres haritasını sağlaması gerekebilecek durumlar vardır. `set_addressMap`Yöntem başarılı olursa, istemci uygulamanın `put_addressMapEnabled` `NewVal` `TRUE` Bu adres eşlemesinin kullanımını etkinleştirmek için parametresiyle yöntemini çağırması gerekir.  
  
 Etkin olan adres eşlemesinin geçerli durumu [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) yöntemi çağrısıyla alınabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
