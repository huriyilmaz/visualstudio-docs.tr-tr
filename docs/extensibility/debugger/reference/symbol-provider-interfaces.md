---
title: Sembol Sağlayıcı Arayüzleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715846"
---
# <a name="symbol-provider-interfaces"></a>Sembol Sağlayıcısı Arabirimleri
Aşağıdaki ler için [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]Sembol İşleme Arabirimleri.

## <a name="discussion"></a>Tartışma
 Bu arabirimler, kesme modu sırasında bir çağrı yığınındaki değişkenleri değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı sembol sağlayıcıları (SP) için uygulanır.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|Sp|Bir öğenin adresini temsil eder.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|Sp|İşlem kimliğine erişim sağlayan bir öğenin adresini temsil eder.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|Sp|Bir dizi simgesini veya dizi türünü temsil eder.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|Sp|Bir sınıf simgesini veya sınıf türünü temsil eder.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|Sp|Yönetilen koda özgü yöntemlerle com+ sembol sağlayıcısını temsil eder.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|Sp|Yönetilen koda özgü yöntemlerle com+ sembol sağlayıcısını temsil eder ve **IDebugComPlusSymbolProvider'ı**genişletir.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|Sp|Diğer semboller veya türler için bir kapsayıcı olan bir sembolü veya türü temsil eder.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|Sp|Bir simgeye eklenebilecek özel bir özniteliği temsil eder.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|Sp|Bir yöntem veya türdeki özel öznitelikler için bir sorgutemsil eder.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|Sp|Bir semboldeki özel özniteliklere erişim sağlar.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|Sp|Çalışma zamanında belirlenebilen herhangi bir tür için temel arabirim.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|Sp|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi için dinamik bir alanı temsil eder.|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|Sp|Numaralandırma türünü temsil eder.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Yönetilen kod jeneriklerini desteklemek için kullanılabilir alan türlerini genişletir.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|Sp|Tüm alanlar için taban sınıf; bir sembol veya türün açıklamasını temsil eder.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|Sp|Yönetilen kod genel türü için alan tanımını temsil eder.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|Sp|Yönetilen kod genel türü için bir alan örneğini temsil eder.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|Sp|Yönetilen kod genel türü için bir parametreyi temsil eder.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|Sp|Bir yöntemi temsil eder.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|Sp|Hata ayıklama isteğe bağlı değiştiriyi temsil eder.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|Sp|Bir işaretçiyi temsil eder.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|Sp|[Bir IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden ilkel bir tür numaralandırma değerini temsil eder.|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|Sp|Alınabilen veya ayarlanabilen yönetilen kod sınıfının özelliğini temsil eder.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|Sp|Semboller ve türler sağlayan bir sembol sağlayıcısını temsil eder.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|Sp|Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|Sp|Bir türü temsil eden bir alan oluşturma yeteneğini temsil eder.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|Sp|Dizi türleri oluşturabilmek için **IDebugTypeFieldBuilder** genişletir.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|Sp|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnelerinin bir koleksiyonunu temsil eder.|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|Sp|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) nesnelerin bir koleksiyon temsil eder.|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|Sp|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnelerinin bir koleksiyonunu temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
