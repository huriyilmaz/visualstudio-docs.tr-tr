---
description: Hata ayıklama nesneleri için sanal DIA SDK ve göreli sanal adreslerin nasıl hesap sağladığı üzerinde denetim sağlar.
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f6e8d8a803f471d6e856da987ea70a1f121bfae5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630518"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Hata ayıklama nesneleri için sanal DIA SDK ve göreli sanal adreslerin nasıl hesap sağladığı üzerinde denetim sağlar.

## <a name="syntax"></a>Syntax

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDiaAddressMap` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Belirli bir oturum için adres eşlemesi oluşturulıp kurulmamış olduğunu gösterir.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Sembol adreslerini çevirmek için adres eşlemesi kullanıp kullanılmay gerektiğini belirtir.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Göreli sanal adreslerin hesaplama ve kullanımının etkin olup olmadığını gösterir.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|İstemcinin göreli sanal adres hesaplamasını etkinleştirmesini veya devre dışı bırakmasını sağlar.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Geçerli görüntü hizalamasını alın.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Görüntü hizalamasını ayarlar.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Göreli sanal adreslerin çevirisini etkinleştirmek için görüntü üst bilgilerini ayarlar.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Görüntü düzeni çevirilerini desteklemek için bir adres haritası sağlar.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim tarafından sağlanan denetim, size sağlanan iki veri kümesinde kapsüllanır: görüntü üst bilgileri ve adres eşlemeleri. Çoğu istemci [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) yöntemini kullanarak bir görüntü için uygun hata ayıklama bilgilerini bulabilir ve yöntemi genellikle tüm gerekli üst bilgileri bulabilir ve verileri eşler. Ancak bazı istemciler özel işleme ve veri arama işlemleri gerçekleştirmektedir. Bu istemciler, arama sonuçlarıyla `IDiaAddressMap` ilgili bilgileri sağlamak DIA SDK yöntemlerini kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim DIA oturum nesnesinden kullanılabilir. İstemci, arabirimi `QueryInterface` almak için DIA oturum nesnesi arabiriminde yöntemini (genellikle [IDiaSession)](../../debugger/debug-interface-access/idiasession.md) `IDiaAddressMap` arar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
