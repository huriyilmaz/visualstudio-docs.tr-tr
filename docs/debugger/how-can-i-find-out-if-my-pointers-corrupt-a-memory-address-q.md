---
title: İşaretçilerimin bir bellek adresinin bozuk olup | Microsoft Docs
description: İşaretçinizin belleği bozarak olup olmadığını belirlemek için yığın bozulması olup olmadığını bulabilir ve bir değerin nasıl değiştirildiğinden emin olmak için bir veri kesme noktası kurabilirsiniz.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 30cd06e52314d2daac3d3e9ce73216ec70b424ba
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969755"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Kendi İşaretçilerimin Bellek Adresini Bozup Bozmadığını Nasıl Anlarım?
## <a name="problem-description"></a>Sorun Açıklaması
 İşaretçilerimin birinin adreste belleği boztu olduğunu 0x00408000. Orada neler olduğunu nasıl bulamıyorum?

## <a name="solution"></a>Çözüm

#### <a name="check-for-heap-corruption"></a>Yığın bozulmayı denetleme

- Çoğu bellek bozulması aslında yığın bozulmasına neden olur. Genel Bayraklar Yardımcı Programı'nı (gflags.exe) veya pageheap.exe. Bkz. [/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Bellek adresinin değiştiril olduğu yeri bulmak için

1. Veri kesme noktası ayarlama 0x00408000. Bkz. [Veri değişikliği kesme noktası ayarlama (yalnızca yerel C++ )](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Kesme noktasıyla başlayarak bellek **içeriğini görüntülemek** için Bellek penceresini 0x00408000. Daha fazla bilgi için [bkz. Bellek Windows.](../debugger/memory-windows.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
