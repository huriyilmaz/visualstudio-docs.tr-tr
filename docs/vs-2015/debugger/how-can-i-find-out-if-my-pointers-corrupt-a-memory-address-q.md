---
title: Kendi İşaretçilerimin Bellek Adresini Bozup Bozmadığını Nasıl Anlarım? | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d4f23b885b2e72e53d288946df18e038d9d956d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476776"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Kendi İşaretçilerimin Bellek Adresini Bozup Bozmadığını Nasıl Anlarım?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun Açıklaması  
 İşaretçilerimin bir birinin 0x00408000 adresindeki belleği bozuyor olabileceğini düşünüyorum. Ne olduğunu öğrenmek için ne olduğunu nasıl anlarım?  
  
## <a name="solution"></a>Çözüm  
  
#### <a name="check-for-heap-corruption"></a>Yığın bozulmasını denetle  
  
- Çoğu bellek bozulması aslında yığın bozulması nedeniyle olur. Genel Bayraklar yardımcı programını (gflags.exe) veya pageheap.exe kullanmayı deneyin. [Microsoft Visual C++ projesindeki bellek hatalarını algılamak Için](https://support.microsoft.com/help/264471/how-to-use-the-pageheap-utility-to-detect-memory-errors-in-a-microsoft) [Gflags ve PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap) ve PageHeap yardımcı programını kullanma bölümüne bakın.
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Bellek adresinin değiştirildiğini bulmak için  
  
1. 0x00408000 konumunda bir veri kesme noktası ayarlayın. Bkz. [veri değişikliği kesme noktası ayarlama (yalnızca yerel C++)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2. Kesme noktasına ulaştığınızda, 0x00408000 ' dan başlayan bellek içeriğini görüntülemek için **bellek** penceresini kullanın. Daha fazla bilgi için bkz. [bellek pencereleri](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
