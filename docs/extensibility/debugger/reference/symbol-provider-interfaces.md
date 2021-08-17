---
title: Sembol Sağlayıcısı Arabirimleri | Microsoft Docs
description: Bu makale, kesme modu sırasında bir çağrı yığınında değişkenleri değerlendiren Visual Studio SDK'sı için Sembol İşleme Arabirimleri açıklamalarına bağlantı sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 14cb7be76bc941fd04eba217f0708ae94817821034b0dd1999ce194e090105a4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389013"
---
# <a name="symbol-provider-interfaces"></a>Sembol Sağlayıcısı Arabirimleri
Aşağıdakiler için Sembol İşleme Arabirimleri'dir. [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]

## <a name="discussion"></a>Tartışma
 Bu arabirimler kesme modu sırasında bir çağrı yığınında değişkenleri değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı sembol sağlayıcıları (SP) için uygulanır.

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|Sp|Bir öğenin adresini temsil eder.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|Sp|İşlem kimliğine erişim sağlayan bir öğenin adresini temsil eder.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|Sp|Bir dizi sembolünü veya dizi türünü temsil eder.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|Sp|Bir sınıf sembolünü veya sınıf türünü temsil eder.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|Sp|Yönetilen koda özgü yöntemlerle bir COM+ sembol sağlayıcısını temsil eder.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|Sp|Yönetilen koda özgü yöntemlerle bir COM+ sembol sağlayıcısını temsil eder ve **IDebugComPlusSymbolProvider'ı genişleter.**|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|Sp|Diğer semboller veya türler için kapsayıcı olan bir simgeyi veya türü temsil eder.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|Sp|Bir simgeye ekli olan özel bir özniteliği temsil eder.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|Sp|Bir yöntem veya tür üzerinde özel öznitelikler için bir sorguyu temsil eder.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|Sp|Bir sembolde özel özniteliklere erişim sağlar.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|Sp|Çalışma zamanında belirlenecek herhangi bir tür için temel arabirim.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|Sp|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi için dinamik bir alanı temsil eder.|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|Sp|Bir numaralama türünü temsil eder.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Yönetilen kod genel türlerini desteklemek için kullanılabilir alan türlerini genişletmektedir.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|Sp|Tüm alanlar için temel sınıf; , bir simgenin veya türün açıklamasını temsil eder.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|Sp|Yönetilen kod genel türü için bir alanın tanımını temsil eder.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|Sp|Yönetilen kod genel türü için bir alanın örneğini temsil eder.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|Sp|Yönetilen kod genel türü için bir parametreyi temsil eder.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|Sp|Bir yöntemi temsil eder.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|Sp|Hata ayıklama isteğe bağlı değiştiricisini temsil eder.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|Sp|Bir işaretçiyi temsil eder.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|Sp|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden bir temel tür numaralama değerini temsil eder.|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|Sp|Al veya ayarlan bir yönetilen kod sınıfının özelliğini temsil eder.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|Sp|Simgeler ve türler sağlayan bir sembol sağlayıcısını temsil eder.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|Sp|Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|Sp|Bir türü temsil eden bir alan oluşturma yeteneğini temsil eder.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|Sp|Dizi türleri **oluşturabilecek şekilde IDebugTypeFieldBuilder'ı** genişleter.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|Sp|[IDebugAddress nesneleri koleksiyonunu temsil](../../../extensibility/debugger/reference/idebugaddress.md) eder.|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|Sp|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) nesneleri koleksiyonunu temsil eder.|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|Sp|[IDebugField nesneleri koleksiyonunu temsil](../../../extensibility/debugger/reference/idebugfield.md) eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
