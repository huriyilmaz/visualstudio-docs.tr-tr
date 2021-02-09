---
title: Sembol sağlayıcısı arabirimleri | Microsoft Docs
description: Bu makale, kesme modundaki bir çağrı yığınındaki değişkenleri değerlendiren Visual Studio SDK 'Sı için sembol Işleme arabirimlerinin açıklamalarını bağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5c2204a1f8c4bef17256e98ed04dcf4b195c3aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850827"
---
# <a name="symbol-provider-interfaces"></a>Sembol Sağlayıcısı Arabirimleri
Aşağıdakiler için sembol Işleme arabirimlerdir [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Tartışma
 Bu arabirimler, kesme modunda bir çağrı yığınında değişkenleri değerlendirmek için kullanılır. Yalnızca ortak dil çalışma zamanı sembol sağlayıcıları (SP) için uygulanır.

|Arabirim|Uygulayan|Description|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP2|Bir öğenin adresini temsil eder.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP2|İşlem KIMLIĞINE erişim sağlayan bir öğenin adresini temsil eder.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP2|Bir dizi sembolünü veya dizi türünü temsil eder.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP2|Bir sınıf sembolünü veya sınıf türünü temsil eder.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP2|Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP2|Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder ve **IDebugComPlusSymbolProvider**'ı genişletir.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP2|Diğer semboller veya türler için kapsayıcı olan bir simgeyi veya türü temsil eder.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP2|Bir simgeye iliştirilebilecek özel bir özniteliği temsil eder.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP2|Bir yöntem veya tür üzerindeki özel öznitelikler için bir sorgu temsil eder.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP2|Bir sembolde özel özniteliklere erişim sağlar.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP2|Çalışma zamanında belirlenebileceği her tür için temel arabirim.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP2|Bir [ıdebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi için dinamik alanı temsil eder.|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP2|Bir sabit listesi türünü temsil eder.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP2|Yönetilen kod genel türlerini desteklemek için kullanılabilir alan türlerini genişletir.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP2|Tüm alanlar için temel sınıf; bir simgenin veya türün açıklamasını temsil eder.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP2|Yönetilen kod genel türü için bir alanın tanımını temsil eder.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP2|Yönetilen kod genel türü için bir alan örneğini temsil eder.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP2|Yönetilen kod genel türü için bir parametreyi temsil eder.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP2|Bir yöntemi temsil eder.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP2|Bir hata ayıklama isteğe bağlı değiştiricisini temsil eder.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP2|Bir işaretçiyi temsil eder.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP2|Bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden bir basit tür numaralandırma değeri temsil eder.|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP2|Bir yönetilen kod sınıfının, Get veya ayarlanabilir bir özelliğini temsil eder.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP2|Semboller ve türler sağlayan bir sembol sağlayıcısını temsil eder.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP2|Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişim sağlayan bir sembol sağlayıcısını temsil eder.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP2|Bir türü temsil eden alan oluşturma yeteneğini temsil eder.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP2|Dizi türleri oluşturabilmeniz için **ıdebugtypefieldbuilder** 'ı genişletir.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP2|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnelerinin bir koleksiyonunu temsil eder.|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP2|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) nesnelerinin bir koleksiyonunu temsil eder.|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP2|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnelerinin bir koleksiyonunu temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
