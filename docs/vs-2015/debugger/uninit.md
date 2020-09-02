---
title: Başlatma geri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197932"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik günlük dosyasını sonlandırır, kapatır ve uygulama grafik bilgilerini etkin bir şekilde kaydederken kullanılan kaynakları serbest bırakır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `UnInit` , sınıfının bir örneği yok edildiğinde otomatik olarak çağrılır `VsgDbg` . Örnek, `VsgDbg` grafik bilgilerini etkin bir şekilde kaydetmediği takdirde bu bir etkiye sahip değildir.  
  
 `UnInit`Sınıfının bir örneği üzerinde çağrıldıktan sonra `VsgDbg` , çağırarak çağırarak ve sonlandırıldığında yeni bir grafik günlük dosyası oluşturulabilir `Init` `UnInit` . `VsgDbg`Birkaç bağımsız grafik günlük dosyası oluşturmak için aynı örneği kullanmak istediğiniz kadar bu adı tekrarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dengeleyici](../debugger/init.md)
