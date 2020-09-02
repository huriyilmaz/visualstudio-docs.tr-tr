---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160769"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik günlük dosyasının varsayılan dosya adını tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parametreler  
 `filename`  
 Grafik bilgileri programlı olarak yakalanarak grafik günlük dosyasına varsayılan olarak verilen dosya adı.  
  
## <a name="value"></a>Değer  
 Grafik günlük dosyasının dosya adını temsil eden bir dize sabit değeri. Varsayılan olarak, L "default. vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Önişlemci sembolü `DONT_SAVE_VSGLOG_TO_TEMP` tanımlanmışsa, dosya adı yakalanan uygulamanın geçerli dizinine göre değişir veya mutlak bir yoldur; Aksi takdirde, kullanıcının geçici dosyalar dizinine göredir ve mutlak bir yol olamaz.  
  
 Tanımlı dosya adını değiştirmek için, programınıza dahil etmeden önce yeniden tanımlamanız gerekir `vsgcapture.h` .  
  
## <a name="example"></a>Örnek  
 Bu örnek, yakalama dosyasının varsayılan dosya adının nasıl değiştirileceğini gösterir:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)
