---
title: Kopyala (Programlı yakalama) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161508"
---
# <a name="copy-programmatic-capture"></a>Kopyalama (Programlı Yakalama)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etkin grafik günlüğü (. vsglog) dosyasının içeriğini yeni bir dosyaya kopyalar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szNewVSGLog`  
 Yeni grafik günlük dosyasının dosya adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Grafik bilgilerini yeni bir dosyaya kopyalamak için bazı grafik bilgilerini zaten yakalamış olmanız gerekir; Aksi takdirde hiçbir şey olmaz.
