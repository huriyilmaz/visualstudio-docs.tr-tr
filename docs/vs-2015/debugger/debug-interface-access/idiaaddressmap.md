---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547513"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA SDK hata ayıklama nesneleri için sanal ve göreli sanal adresleri nasıl hesaplatığına ilişkin denetim sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaAddressMap` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Belirli bir oturum için bir adres eşlemesinin yapılıp yapılmayacağını belirtir.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Adres eşlemesinin sembol adreslerini çevirmek için kullanılıp kullanılmayacağını belirtir.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Göreli sanal adreslerin hesaplanması ve kullanılması etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|İstemcinin göreli sanal adreslerin hesaplamasını etkinleştirmesine veya devre dışı bırakmasına izin verir.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Geçerli resim hizalamasını alır.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Resim hizalamasını ayarlar.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Göreli sanal adreslerin çevirisini etkinleştirmek için görüntü üst bilgilerini ayarlar.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Görüntü düzeni çevirilerini desteklemek için bir adres haritası sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim tarafından sunulan denetim, sağladığınız iki veri kümesinde kapsüllenir: görüntü üstbilgileri ve adres eşlemeleri. Çoğu istemci, bir görüntüyle ilgili doğru hata ayıklama bilgilerini bulmak için [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu kullanır ve yöntem genellikle gerekli tüm üst bilgileri ve haritalar verilerini bulabilir. Ancak bazı istemciler özelleştirilmiş işleme ve veri aramayı uygular. Bu istemciler, `IDiaAddressMap` arama sonuçlarıyla DIA SDK sağlamak için arabirimin yöntemlerini kullanır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, DIA oturum nesnesinden kullanılabilir. İstemci, `QueryInterface` arabirimi almak için genellikle [IDiaSession](../../debugger/debug-interface-access/idiasession.md)olan DIA oturum nesne arabirimindeki yöntemi çağırır `IDiaAddressMap` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
