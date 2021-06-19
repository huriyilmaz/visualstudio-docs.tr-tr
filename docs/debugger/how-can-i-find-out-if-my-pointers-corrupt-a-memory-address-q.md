---
title: İşaretçilerimin bir bellek adresinin bozuk olup | Microsoft Docs
description: İşaretçinizin belleği bozarak olup olmadığını belirlemek için yığın bozulması olup olmadığını bulabilir ve bir değerin nasıl değiştirildiğinden emin olmak için bir veri kesme noktası kurabilirsiniz.
ms.custom: SEO-VS-2020
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
ms.workload:
- multiple
ms.openlocfilehash: 836cc0363da0e20c45d83e1b2c13081e480fa919
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386975"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Kendi İşaretçilerimin Bellek Adresini Bozup Bozmadığını Nasıl Anlarım?
## <a name="problem-description"></a>Sorun Açıklaması
 İşaretçilerimin birinin adreste belleği boztu olduğunu 0x00408000. Orada neler olduğunu nasıl bulamıyorum?

## <a name="solution"></a>Çözüm

#### <a name="check-for-heap-corruption"></a>Yığın bozulmayı denetleme

- Çoğu bellek bozulması aslında yığın bozulmasına neden olur. Genel Bayraklar Yardımcı Programı'nı (gflags.exe) veya pageheap.exe. Bkz. [/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Bellek adresinin değiştiril olduğu yeri bulmak için

1. Veri kesme noktası ayarlama 0x00408000. Bkz. [Veri değişikliği kesme noktası ayarlama (yalnızca yerel C++ )](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Kesme noktasıyla başlayarak bellek **içeriğini görüntülemek** için Bellek penceresini 0x00408000. Daha fazla bilgi için bkz. [Bellek Pencereleri.](../debugger/memory-windows.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
