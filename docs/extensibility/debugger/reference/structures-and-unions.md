---
title: Yapılar ve | Microsoft Docs
description: Bu makale, Visual Studio Hata Ayıklama SDK'sında yapıların ve Visual Studio açıklamalarına bağlantı verir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a5ac418731fc3676c4813ff3e346f452342f7df9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057401"
---
# <a name="structures-and-unions"></a>Yapılar ve Birleşimler
Hata Ayıklama SDK'sı'nın Visual Studio ve unions aşağıda velanmıştır.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Sistem kimliği veya GUID olabilir işlem kimliğini belirtir.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Bir kesme noktası hangi koşulların altında sıyaklanacaklarını açıklar.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Konum, program ve iş parçacığı dahil olmak üzere bir hata kesme noktası çözümlemesi açıklar.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Kesme noktası konumunu açıklamak için kullanılan yapı türünü belirtir.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Kodda bir adreste kesme noktası konumunu açıklayan bileşenleri tanımlar.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Hata ayıklarken programda doğrudan bir adrese bağlı olan bir kesme noktası konumunu açıklar.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Kod kaynağı dosyasında satır içinde kesme noktası konumunu açıklar.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Kodda bir işlevde kesme noktası uzaklığı konumunu açıklar.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Kullanıcının IDE'den girebilirsiniz bir dizeye dayalı olarak kod kesme noktaları ayarlama için kullanılır.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Kullanıcının IDE'den girebilirsiniz bir dizeye dayalı veri kesme noktaları ayarlama için kullanılır.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Belirli bir konumdaki bir kesme noktası çözümlemesi açıklar.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Bir kesme noktası daha önce geçirildikten sonra hangi sayı ve koşullar üzerinde işten atılacağı açıklar.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Bir kesme noktası uygulamak için gereken bilgileri içerir.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Bir kesme noktası uygulamak için gereken bilgileri içerir (aynı BP_REQUEST_INFO [ancak](../../../extensibility/debugger/reference/bp-request-info.md) satıcı GUID'si, kısıtlama ve izleme noktası bilgilerini içerir).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Bir kod kesme noktası konumunu açıklar.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Bir veri kesme noktası bağlamanın sonucundan açıklar.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Bir kod kesme noktası veya veri kesme noktası için bağlı kesme noktası bilgilerini açıklar.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Kesme noktası çözümleme konumunun yapısını belirtir.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Bir dize dizisini açıklar.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Meta verilerden alınan alan türüyle ilgili bilgileri belirtir.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Bir işleve veya yönteme yapılan çağrıyı açıklar.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Hata ayıklayıcının üzerinde çalıştır olduğu bilgisayarı açıklar.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) GUID'ler listesini açıklar.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Bellek bağlamını veya kod bağlamını açıklar.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Hata ayıklaması yapılan programda bir adresi açıklar.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Bir dizi farklı adres türüne sahip birini temsil eder.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Özel görüntüleyiciyi veya tür görselleştiriciyi tanımlar.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Buna karşılık ad, tür ve değere sahip hiyerarşik bir nesnenin hata ayıklama özelliğini açıklar.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Bir başvuru açıklar.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Görüntü için IDE'ye ayrımını açıklar.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Hata ayıklaması yapılan program tarafından bir özel durum veya çalışma zamanı hatasının neden olduğunu açıklar.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Yerel bir değişkeni, parametreyi veya başka bir alanı açıklar.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Bir yığın çerçevesini açıklar.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Kullanılabilir hata ayıklama altyapıları için bir dizi benzersiz tanımlayıcıyı açıklar.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Bir modülün JustMyCode bilgilerini ayarlamak için kullanılır.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Belirli bir makineyi açıklar.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Bir dizi içindeki bir dizi öğesini açıklar.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Bir sınıfın veya yapının bir alanın adresini açıklar.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Bir kapsam içindeki yerel değişkenin adresini açıklar (genellikle bir işlev veya yöntem).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Bir sınıfın yönteminin adresini açıklar.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Bir yöntemin veya işlevin parametresini açıklar.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Bir yöntem veya işlevden dönüş değerini açıklar.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Meta verilerden alınan bir alan türünü açıklar.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Belirli bir modülü (DLL, EXE veya derleme) açıklar.

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Aranan sembol arama yolları hakkında durum bilgilerini açıklar.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Yerel bir adresi açıklar.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) PDB simgesinden alınan alan türünü açıklar.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Bir kod konumu bağlamaya hazır bir kesme noktası durumunu açıklar.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Bir işlemi açıklar.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Program düğümlerini temsil eden [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnelerinin listesini açıklar.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Bir makinede çalışan işlemleri açıklar.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Verilen metinde satır ve sütun konumunu açıklar.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Bir iş parçacığının özelliklerini açıklar.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Bir alanın türünü açıklar.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Fiziksel adresi açıklar.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Bir işaretçiye göreli bir adresi `this` açıklar ( `Me` Visual Basic).

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h, sh.h veya ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
