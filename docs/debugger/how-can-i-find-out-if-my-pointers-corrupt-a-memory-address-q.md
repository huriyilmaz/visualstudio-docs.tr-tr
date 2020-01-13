---
title: Kendi işaretçilerimin bozuk bellek adresi kaydolmadığı | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc178675e6d2423336c38e69691f081bf4b447a4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916169"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Kendi İşaretçilerimin Bellek Adresini Bozup Bozmadığını Nasıl Anlarım?
## <a name="problem-description"></a>Sorun açıklaması
 İşaretçilerimden birinin 0x00408000 adresinde belleği bozabileceğini düşünüyorum. Nasıl öğrenebilirim orada neler olduğunu kullanıma?

## <a name="solution"></a>Çözüm

#### <a name="check-for-heap-corruption"></a>Yığın bozulmasını denetleme

- Çoğu Bellek Bozulması gerçekten Öbek Bozulması nedeniyledir ' dir. Genel bayraklar yardımcı programı'nı (gflags.exe) veya pageheap.exe'yi kullanmayı deneyin. Bkz. [/Windows-Hardware/Drivers/Debugger/Gflags-and-PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>Bellek adresinin nerede değiştirildiğini bulmak için

1. 0x00408000 veri kesme noktası ayarlayın. Bkz: [veri değişikliği kesme noktası (yalnızca yerel C++'da) ayarla](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Kesme noktasına ulaştığınızda kullanın **bellek** bellek görüntülemek için pencere içeriği 0x00408000 başlatılıyor. Daha fazla bilgi için [bellek Windows](../debugger/memory-windows.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
