---
title: Etkin komut dosyası profil oluşturucu sabitleri, numaralandırmalar ve yapılar | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572684"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Etkin Komut Dosyası Profil Oluşturucu Sabitleri, Numaralandırmaları ve Yapıları
Aşağıdaki numaralandırmalar etkin betik profil oluşturucu arabirimleri tarafından kullanılır.  
  
## <a name="constants-enumerations-and-structures"></a>Sabitler, Listelemeler ve Yapılar  
  
|Sabitler|Açıklama|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS Türü](../../winscript/reference/profiler-external-object-address-type.md)|Profil oluşturucunun dış nesne adresi. [PROFILER_HEAP_OBJECT yapısı](../../winscript/reference/profiler-heap-object-structure.md) ve [PROFILER_HEAP_OBJECT_RELATIONSHIP yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md)içinde kullanılır.|  
|[PROFILER_HEAP_OBJECT_ID Türü](../../winscript/reference/profiler-heap-object-id-type.md)|Yığın nesnesinin KIMLIĞI. [PROFILER_HEAP_OBJECT Structure](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST yapısı](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER_HEAP_OBJECT_OPTIONAL_INFO yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md)ve [PROFILER_HEAP_OBJECT_RELATIONSHIP yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md)içinde kullanılır.|  
|[PROFILER_HEAP_OBJECT_NAME_ID Türü](../../winscript/reference/profiler-heap-object-name-id-type.md)|Yığın nesnesinin adının KIMLIĞI. [PROFILER_HEAP_OBJECT yapısı](../../winscript/reference/profiler-heap-object-structure.md)içinde kullanılır.|  
  
|Numaralandırmalar|Açıklama|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK Sabit Listesi](../../winscript/reference/profiler-event-mask-enumeration.md)|Profili oluşturulacak olay türlerini gösterir.|  
|[PROFILER_HEAP_ENUM_FLAGS Sabit Listesi](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Bir nesne ilişkisinde işaret eden bir yığın nesnesi hakkındaki ek bilgilerin açığa çıkmadığını temsil eden bayraklar. [IActiveScriptProfilerControl5:: EnumHeap2 yönteminde](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)kullanılır.|  
|[PROFILER_HEAP_OBJECT_FLAGS Sabit Listesi](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Yığın nesnesiyle ilgili temel bilgileri temsil eden bayraklar. [PROFILER_HEAP_OBJECT yapısında](../../winscript/reference/profiler-heap-object-structure.md)kullanılır.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE Sabit Listesi](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|İsteğe bağlı bilgilerin farklı türlerini temsil eder. [PROFILER_HEAP_OBJECT_OPTIONAL_INFO yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md)içinde kullanılır.|  
|[PROFILER_RELATIONSHIP_INFO Sabit Listesi](../../winscript/reference/profiler-relationship-info-enumeration.md)|İlişkideki nesneyle ilgili bilgileri temsil eder. [PROFILER_HEAP_OBJECT_RELATIONSHIP yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md)içinde kullanılır.|  
|[PROFILER_SCRIPT_TYPE Sabit Listesi](../../winscript/reference/profiler-script-type-enumeration.md)|Betiğin türünü belirtir.|  
  
|Yapılar|Açıklama|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT Yapısı](../../winscript/reference/profiler-heap-object-structure.md)|[Iactivescriptprofilercontrol3:: Enumheap yöntemi](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)tarafından toplanan yığın nesnelerini temsil eder.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO Yapısı](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Yığın nesneleriyle ilgili isteğe bağlı bilgileri temsil eder.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP Yapısı](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Yığın nesnesinin ilişkisini temsil eder.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST Yapısı](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Yığın nesnesine ait olan ilişkilerin listesini temsil eder.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST Yapısı](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Bu yapı yalnızca işlev nesneleriyle ilişkili. Kapsam listesi, her kapsamın belirli bir kapsamdaki değişkenleri temsil eden ilişkili bir özellik listesi olan bir yığın nesnesi olduğu bir kapsam listesi olarak işlevin kapanışını temsil eder. Bazı durumlarda, bu kapsamdaki nesne adları, yalnızca kimlikleri için kullanılabilir olmayabilir.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO Yapısı](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Alt dizenin türü hakkındaki bilgileri temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Profil Oluşturucu Arabirimleri](../../winscript/reference/active-script-profiler-interfaces.md)