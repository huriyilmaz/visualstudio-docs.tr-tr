---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c7d2263642c2ff8a2c36f274d2c7b80745ed845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179489"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, Bir [VsgDbg Class](../debugger/vsgdbg-class.md) sınıfının, Programlı yakalama arabirimini sağlayan varsayılan bir örneğinin sağlanmış olup olmadığı, kendi varlığına göre tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Değer  
 Varlığı veya devamsızlığı tarafından kullanılan bir ön işlemci sembolü, sınıfının varsayılan bir örneğinin sağlandığını belirler `VsgDbg` . Bu simge tanımlanmışsa, sınıfın varsayılan örneği `VsgDbg` sağlanmaz; Aksi takdirde, programınız çalıştırılmadan önce varsayılan bir örnek sağlanır ve başlatılır.  
  
 Programlı yakalama arabirimi, genel kapsama sahip bir işaretçi aracılığıyla sağlanır `g_pVsgDbg` .  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan örnek genellikle yeterlidir, ancak D3D cihazı bu DLL dışında oluşturulduğunda, bir DLL içinde programlı yakalama arabirimini kullanmak için, kendi sınıf örneğinizi oluşturmanız ve yönetmeniz gerekir `VsgDbg` . Bu şekilde kendi arabiriminizi Programlı yakalama API 'sine yönetiyorsanız, ek yükün önüne geçmek için tanımlayarak varsayılan örneği devre dışı bırakın `VSG_NODEFAULT_INSTANCE` .  
  
 Varsayılan örnek devre dışı bırakılmışsa, programınız çalıştırılmadan önce otomatik olarak başlatılır ve programınız sona erdiğinde otomatik olarak yok edilir. Bu örneği açıkça başlatmak veya Uninitialize için gerekmez.  
  
 Varsayılan örneği devre dışı bırakmak için, `VSG_NODEFAULT_INSTANCE` programınıza dahil etmeden önce tanımlamanız gerekir `vsgcapture.h` .  
  
## <a name="example"></a>Örnek  
 Bu örnekte, varsayılan örneği devre dışı bırakma gösterilmektedir:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
