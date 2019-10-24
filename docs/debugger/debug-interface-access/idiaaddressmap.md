---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744986"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
DIA SDK hata ayıklama nesneleri için sanal ve göreli sanal adresleri nasıl hesaplatığına ilişkin denetim sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda `IDiaAddressMap` yöntemleri gösterilmektedir.

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
 Bu arabirim tarafından sunulan denetim, sağladığınız iki veri kümesinde kapsüllenir: görüntü üstbilgileri ve adres eşlemeleri. Çoğu istemci, bir görüntüyle ilgili doğru hata ayıklama bilgilerini bulmak için [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu kullanır ve yöntem genellikle gerekli tüm üst bilgileri ve haritalar verilerini bulabilir. Ancak bazı istemciler özelleştirilmiş işleme ve veri aramayı uygular. Bu istemciler, arama sonuçlarıyla DIA SDK sağlamak için `IDiaAddressMap` arabiriminin yöntemlerini kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, DIA oturum nesnesinden kullanılabilir. İstemci, `IDiaAddressMap` arabirimini almak için genellikle [IDiaSession](../../debugger/debug-interface-access/idiasession.md)nesne arabirimindeki `QueryInterface` yöntemini çağırır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)