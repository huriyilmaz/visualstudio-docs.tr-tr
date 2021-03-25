---
title: Yapılar ve birleşimler | Microsoft Docs
description: Bu makale, Visual Studio hata ayıklama SDK 'sında yapıların ve birleşimlerin başvuru açıklamalarına bağlantı sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 055c8972643a94bd8f13aa6e5e6bc5dde600140b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061478"
---
# <a name="structures-and-unions"></a>Yapılar ve Birleşimler
Visual Studio hata ayıklama SDK 'sında yapılar ve birleşimler aşağıda verilmiştir.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Bir sistem KIMLIĞI ya da bir GUID olabilecek işlem KIMLIĞINI belirtir.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Bir kesme noktasının tetikleneceği koşulları açıklar.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Konum, program ve iş parçacığı dahil bir hata kesme noktası çözünürlüğünü açıklar.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Kesme noktasının konumunu anlatmak için kullanılan yapının türünü belirtir.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Kod içindeki bir kesme noktasının konumunu tanımlayan bileşenleri tanımlar.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Hata ayıklanan programdaki bir adrese doğrudan bağlanan bir kesme noktasının konumunu açıklar.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Bir kod kaynağı dosyasında satır içindeki bir kesme noktasının konumunu açıklar.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Koddaki işlevdeki bir kesme noktasının konum konumunu açıklar.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Kullanıcının IDE 'den girebileceği bir dizeye göre kod kesme noktaları ayarlamak için kullanılır.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Kullanıcının IDE 'den girebileceği bir dizeyi temel alan veri kesme noktaları ayarlamak için kullanılır.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Belirli bir konumda bir kesme noktasının çözünürlüğünü açıklar.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Daha önce geçtikten sonra bir kesme noktasının tetikleneceği sayı ve koşulları açıklar.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Kesme noktası uygulamak için gereken bilgileri içerir.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Bir kesme noktası uygulamak için gereken bilgileri içerir ( [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapısıyla aynı ancak satıcı GUID, kısıtlama ve izleme noktası bilgilerini içerir).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Bir kod kesme noktasının konumunu açıklar.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Veri kesme noktası bağlamanın sonucunu açıklar.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Bir kod kesme noktası ya da bir veri kesme noktası için, bağlantılı kesme noktası bilgisini açıklar.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Kesme noktası çözümleme konumunun yapısını belirtir.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Dizelerin dizisini açıklar.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Meta verilerden alınan bir alan türü hakkında bilgi belirtir.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Bir işlev veya yöntem çağrısını açıklar.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Hata ayıklayıcının çalıştığı bilgisayarı tanımlar.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) GUID 'lerin bir listesini açıklar.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Bellek bağlamını veya kod bağlamını açıklar.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Hata ayıklamakta olan bir programdaki bir adresi açıklar.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Birçok farklı türde adresten birini temsil eder.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Özel bir Görüntüleyici veya tür görselleştiricisi tanımlar.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Sırasıyla ad, tür ve değer içeren hiyerarşik yapıdaki bir nesneyi tanımlayan bir hata ayıklama özelliğini açıklar.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Bir başvuruyu açıklar.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Görüntüleme için IDE 'ye ayrıştırılmış derlemeyi açıklar.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Hata ayıklamakta olan program tarafından oluşturulan bir özel durumu veya çalışma zamanı hatasını açıklar.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Yerel bir değişken, parametre veya başka bir alan tanımlar.

- [FrameInfo](../../../extensibility/debugger/reference/frameinfo.md) Yığın çerçevesini açıklar.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Kullanılabilir hata ayıklama motorları için benzersiz tanımlayıcıların dizisini açıklar.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Bir modül için Adatmycode bilgilerini ayarlamak için kullanılır.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Belirli bir makineyi açıklar.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Dizi içinde bir dizi öğesi tanımlar.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Bir sınıf veya yapının alanının adresini açıklar.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Kapsam içindeki yerel bir değişkenin adresini açıklar (genellikle bir işlev veya yöntem).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Bir sınıfın yönteminin adresini açıklar.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Bir yöntemin veya işlevin parametresini açıklar.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Bir yöntem veya işlevden dönüş değeri tanımlar.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Meta verilerden alınan bir alan türünü açıklar.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Belirli bir modülü (DLL, EXE veya derleme) açıklar.

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Aranan sembol arama yolları hakkında durum bilgilerini açıklar.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Yerel bir adres tanımlar.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) PDB simgesinden alınan alan türünü açıklar.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Bir kod konumuna bağlanmaya yönelik bir kesme noktasının durumunu açıklar.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Bir işlemi açıklar.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Program düğümlerini temsil eden [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnelerinin bir listesini açıklar.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Bir makinede çalışan işlemlerin açıklar.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Verilen metindeki satır ve sütun konumunu açıklar.

- [Threadproperties](../../../extensibility/debugger/reference/threadproperties.md) Bir iş parçacığının özelliklerini açıklar.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Bir alanın türünü açıklar.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Fiziksel bir adres tanımlar.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Bir `this` işaretçiye (Visual Basic) göre bir adres tanımlar `Me` .

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg. h, sh. h veya Ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
