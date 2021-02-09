---
title: Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 234bfa31c79fa2c9ef60afd29d655cfc6e585aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853263"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)
Yöntemler, içindekiler tablosundaki her arabirim altında ve vtable sırasındaki arabirim sayfasında alfabetik olarak listelenir.

## <a name="in-this-section"></a>Bu Bölümde

[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)

DIA SDK hata ayıklama nesneleri için sanal ve göreli sanal adresleri nasıl hesaplatığına ilişkin denetim sağlar.

[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

Hata ayıklama sembolleri kaynağına erişimi başlatır.

[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)

Hata ayıklama veri akışındaki kayıtlara erişim sağlar.

[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)

Veri kaynağında bulunan çeşitli hata ayıklama akışlarını numaralandırır.

[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

Veri kaynağında bulunan çeşitli çerçeve verisi öğelerini numaralandırır.

[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

Veri kaynağında yer alan çeşitli eklenen kaynakları numaralandırın.

[IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

Veri kaynağında bulunan çeşitli satır numaralarını numaralandırır.

[IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

Veri kaynağında bulunan çeşitli bölüm katkılarını numaralandırır.

[IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

Veri kaynağında bulunan çeşitli kesimleri numaralandırır.

[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

Veri kaynağında bulunan çeşitli kaynak dosyalarını numaralandırır.

[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)

Kullanılabilir çeşitli yığın çerçevelerini numaralandırır.

[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

Veri kaynağında bulunan çeşitli sembolleri numaralandırır.

[IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

Veri kaynağında bulunan çeşitli sembolleri ele alarak sıralar.

[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

Veri kaynağında bulunan çeşitli tabloları numaralandırır.

[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

Yığın çerçevesinin ayrıntılarını gösterir.

[IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)

Modülün veya görüntünün temel konumunun ve bellek uzaklarının ayrıntılarını gösterir.

[IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

DIA veri kaynağında depolanan program kaynak koduna erişir.

[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

Bir bayt bloğundan bir kaynak dosya satır numarasıyla eşleme işlemini açıklayan bilgilere erişir.

[IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)

DIA sembol konumlandırma yordamının geri çağırmaları alır, böylece bir kullanıcı arabiriminin konum denemesinin ilerlemesini raporlemelerini sağlar.

[IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)

,, Bulma işleminde kısıtlamaların bulunmasına izin veren bir ÇYA sembol yordamının yerini alan geri çağırmaları alır.

[IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

Bir DIA özellik kümesinin kalıcı özelliklerini okumanızı sağlar.

[IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

İstemci uygulamasının dosya konumuyla belirtilen bir yürütülebilir dosya bayt sağlaması için izin sağlar.

[IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)

Bir istemci uygulamanın, göreli bir sanal adresle belirtilen bir yürütülebilir dosya bayt vermesini sağlar.

[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

Bir bölüm katkısını açıklayan verileri alır, diğer bir deyişle, bir compiland tarafından görüntüye katkıda bulunulan bir bellek bloğu.

[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

Bölüm numarasından verileri adres alanının kesimlerine eşler.

[IDiaSession](../../debugger/debug-interface-access/idiasession.md)

Hata ayıklama sembolleri için bir sorgu bağlamı sağlar.

[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

Bir kaynak dosyasını temsil eder.

[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)

Yığın çerçevesinin özelliklerini gösterir.

[IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)

PDB dosyasını kullanarak bir yığın yürüme yöntemi sağlar.

[IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

[IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yönteminin etkinleştirmeleri arasında yığın bağlamını korur.

[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

Program hata ayıklama veritabanı (PDB) dosyasını kullanarak yığını yürüme işlemini kolaylaştırır.

[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

Bir sembol örneğinin özelliklerini açıklar.

[IDiaTable](../../debugger/debug-interface-access/idiatable.md)

Bir DIA veri kaynağı tablosunu numaralandırır.

## <a name="related-sections"></a>İlgili Bölümler
[Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)

DIA SDK çeşitli arabirimleri tarafından kullanılan numaralandırmaları ve yapıları açıklar.

[Sabitler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)

DIA SDK bulunan sabitleri açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)