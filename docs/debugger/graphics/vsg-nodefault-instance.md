---
description: ', Bir VsgDbg Class sınıfının, Programlı yakalama arabirimini sağlayan varsayılan bir örneğinin sağlanmış olup olmadığı, kendi varlığına göre tanımlar.'
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 75bb54adb5667f3e8246034eca1075d339755785
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232420"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
, Bir [VsgDbg Class](vsgdbg-class.md) sınıfının, Programlı yakalama arabirimini sağlayan varsayılan bir örneğinin sağlanmış olup olmadığı, kendi varlığına göre tanımlar.

## <a name="syntax"></a>Syntax

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>Değer
 Varlığı veya devamsızlığı tarafından kullanılan bir ön işlemci sembolü, sınıfının varsayılan bir örneğinin sağlandığını belirler `VsgDbg` . Bu simge tanımlanmışsa, sınıfın varsayılan örneği `VsgDbg` sağlanmaz; Aksi takdirde, programınız çalıştırılmadan önce varsayılan bir örnek sağlanır ve başlatılır.

 Programlı yakalama arabirimi, genel kapsama sahip bir işaretçi aracılığıyla sağlanır `g_pVsgDbg` .

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>Açıklamalar
 Varsayılan örnek genellikle yeterlidir, ancak D3D cihazı bu DLL dışında oluşturulduğunda, bir DLL içinde programlı yakalama arabirimini kullanmak için, kendi sınıf örneğinizi oluşturmanız ve yönetmeniz gerekir `VsgDbg` . Bu şekilde kendi arabiriminizi Programlı yakalama API 'sine yönetiyorsanız, ek yükün önüne geçmek için tanımlayarak varsayılan örneği devre dışı bırakın `VSG_NODEFAULT_INSTANCE` .

 Varsayılan örnek devre dışı bırakılmışsa, programınız çalıştırılmadan önce otomatik olarak başlatılır ve programınız sona erdiğinde otomatik olarak yok edilir. Bu örneği açıkça başlatmak veya Uninitialize için gerekmez.

 Varsayılan örneği devre dışı bırakmak için, `VSG_NODEFAULT_INSTANCE` programınıza dahil etmeden önce tanımlamanız gerekir `vsgcapture.h` .

## <a name="example"></a>Örnek
 Bu örnekte, varsayılan örneği devre dışı bırakma gösterilmektedir:

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
