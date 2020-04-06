---
title: Yapılar ve Sendikalar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713490"
---
# <a name="structures-and-unions"></a>Yapılar ve Birleşimler
Aşağıdaki yapılar ve sendikalar Visual Studio Hata Ayıklama SDK vardır.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Sistem kimliği veya GUID olabilecek işlem kimliğini belirtir.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Bir kırılma noktasının hangi koşullar altında ateş edeceğini açıklar.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Konum, program ve iş parçacığı da dahil olmak üzere bir hata kesme noktasının çözümünü açıklar.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Kesme noktasının konumunu açıklamak için kullanılan yapı türünü belirtir.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Koddaki bir adreste kesme noktasının konumunu açıklayan bileşenleri tanımlar.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Programda doğrudan bir adrese bağlanan bir kesme noktasının konumunu açıklar.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Kod kaynağı dosyasında satırdaki bir kesme noktasının konumunu açıklar.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Koddaki bir işlevdeki kesme noktasının mahsup konumunu açıklar.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Kullanıcının IDE'den girebileceği bir dizeyi temel alan kod kesme noktalarını ayarlamak için kullanılır.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Kullanıcının IDE'den girebileceği bir dizeyi temel alan veri kesme noktalarını ayarlamak için kullanılır.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Belirli bir konumdaki bir kesme noktasının çözünürlüğünü açıklar.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Daha önce geçtikten sonra bir kesme noktasının hangi sayıve koşullarla ateşlendiğini açıklar.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Kesme noktası uygulamak için gereken bilgileri içerir.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Bir kesme noktası uygulamak için gereken bilgileri içerir [(BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) yapısıyla aynıdır, ancak satıcı GUID, kısıtlama ve izleme noktası bilgilerini içerir).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Kod kesme noktasının konumunu açıklar.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Veri kesme noktasını bağlamanın sonucunu açıklar.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Kod kesme noktası veya veri kesme noktası için bağlı kesme noktası bilgilerini açıklar.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Kesme noktası çözümlü konumuyapısını belirtir.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Bir dizi dize açıklar.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Meta verilerden alınan bir alan türü hakkındaki bilgileri belirtir.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Bir işlev veya yönteme yapılan çağrıyı açıklar.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Hata ayıklamanın çalıştırıldığı bilgisayarı açıklar.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) GUID'lerin listesini açıklar.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Bellek bağlamı veya kod bağlamı açıklar.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Debugged olan bir programdaki bir adresi açıklar.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Farklı türde adreslerden birini temsil eder.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Özel bir görüntüleyici veya tür görselleştiricisi tanımlar.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Sırayla ad, tür ve değer olan hiyerarşik bir doğa nesnesi açıklayan bir hata ayıklama özelliği açıklar.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Bir başvuru açıklar.

- [DesassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Görüntülenmek üzere IDE'ye sökmeyi açıklar.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Hata ayıklanan program tarafından atılan bir özel durum veya çalışma zamanı hatasını açıklar.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Yerel bir değişkeni, parametreyi veya başka bir alanı açıklar.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Yığın çerçeveyi açıklar.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Kullanılabilir hata ayıklama motorları için bir dizi benzersiz tanımlayıcıyı açıklar.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Bir modül için JustMyCode bilgilerini ayarlamak için kullanılır.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Belirli bir makineyi tanımlar.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Dizi içindeki bir dizi öğesini açıklar.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Bir sınıfın veya yapının alanının adresini açıklar.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Bir kapsamdaki yerel değişkenin adresini (genellikle bir işlev veya yöntem) açıklar.

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Bir sınıfın yönteminin adresini açıklar.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Bir yöntemin veya işlevin parametresini açıklar.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Bir yöntem veya işlevden gelen bir geri dönüş değerini açıklar.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Meta verilerden alınan bir alan türünü açıklar.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Belirli bir modülü (DLL, EXE veya montaj) açıklar.

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Aranan sembol arama yolları hakkındaki durum bilgilerini açıklar.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Yerel bir adresi açıklar.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) PDB simgesinden alınan alan türünü açıklar.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Kod konumuna bağlanmaya hazır bir kesme noktasının durumunu açıklar.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Bir işlemi açıklar.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Program düğümlerini temsil eden [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnelerinin listesini açıklar.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Makinede çalışan işlemleri açıklar.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Verilen metindeki satır ve sütun konumunu açıklar.

- [KONU ÖZELLİkLerİ](../../../extensibility/debugger/reference/threadproperties.md) İş parçacığının özelliklerini açıklar.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Bir alanın türünü açıklar.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Fiziksel bir adresi açıklar.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) `this` İşaretçiye göre (Visual`Me` Basic'te) bir adresi açıklar.

## <a name="requirements"></a>Gereksinimler
 Başlık: msdbg.h, sh.h veya ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
