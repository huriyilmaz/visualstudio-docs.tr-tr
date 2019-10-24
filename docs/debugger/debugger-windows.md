---
title: Hata ayıklayıcı Windows kullanarak verileri İnceleme | Microsoft Docs
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: conceptual
ms.assetid: 4c6fe8f1-b015-4989-bb31-72ebac390026
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91df84c92761ae75ce9f26bddefad57c6dc8bc2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738306"
---
# <a name="inspect-data-using-debugger-windows-in-visual-studio"></a>Visual Studio 'da hata ayıklayıcı pencerelerini kullanarak verileri İnceleme

Programınızda hata ayıklarken çoğu hata ayıklayıcı penceresini açabilirsiniz. Hata ayıklayıcı pencerelerinin bir listesini görmek için, bir kesme noktası ayarlayın ve hata ayıklamayı başlatın. Kesme noktasına ulaştığınızda ve yürütme durduktan sonra **Windows > hata ayıkla**' ya tıklayın.

|Pencere|Kısayol tuşu|Konuya bakın|
|-|-|-|
|Kesme noktaları|CTRL + ALT + B|[Kesme noktaları kullan](../debugger/using-breakpoints.md)|
|Özel durum ayarları|CTRL + ALT + E|[Hata ayıklayıcı ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md)|
|Çıkış|CTRL + ALT + O|[Çıktı Penceresi](../ide/reference/output-window.md)|
|Servisi|CTRL + ALT + W, (1, 2, 3, 4)|[İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)|
|QuickWatch|SHIFT + F9|[İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)|
|Otolar|CTRL + ALT + V, A|[Otomatikler ve Yereller Pencereleri](../debugger/autos-and-locals-windows.md)|
|Ayarlanmalıdır|CTRL + ALT + V, L|[Otomatikler ve Yereller Pencereleri](../debugger/autos-and-locals-windows.md)|
|Çağrı yığınları|CTRL + ALT + C|[Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma](../debugger/how-to-use-the-call-stack-window.md)|
|Hemen|CTRL + ALT + ı|[Komut Penceresi](../ide/reference/immediate-window.md)|
|Paralel Yığınlar|MRK: + SHıFT + D, S|[Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)|
|Paralel Izleme|MRK: + SHıFT + D, (1, 2, 3, 4)|[Çoklu Iş parçacıklı uygulamalarda hata ayıklamaya başlayın](../debugger/get-started-debugging-multithreaded-apps.md)|
|İş Parçacıkları|CTRL + ALT + H|[Iş parçacıkları penceresini kullanarak hata ayıkla](../debugger/how-to-use-the-threads-window.md)|
|Modüller|CTRL + ALT + U|[Nasıl Yapılır: Modüller Penceresini Kullanma](../debugger/how-to-use-the-modules-window.md)|
|GPU Iş parçacıkları|-|[Nasıl Yapılır: GPU İş Parçacıkları Penceresini Kullanma](../debugger/how-to-use-the-gpu-threads-window.md)|
|Görevler|MRK: + SHıFT + D, K|[Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)|
|Python hata ayıklama etkileşimli|SHIFT + ALT + ı|[Python etkileşimli REPL](../python/python-interactive-repl-in-visual-studio.md)|
|JavaScript Konsolu|CTRL + ALT + V, C|[Hızlı Başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md)|
|DOM Gezgini|CTRL + ALT + V, D|[DOM Gezgini'ni kullanarak düzen hatalarını ayıklama](/visualstudio/debugger/quickstart-debug-html-and-css)|
|Canlı görsel ağaç|-|[Hata ayıklama sırasında XAML özelliklerini denetleme](../xaml-tools/inspect-xaml-properties-while-debugging.md)|
|Canlı Özellik Gezgini|-|[Hata ayıklama sırasında XAML özelliklerini denetleme](../xaml-tools/inspect-xaml-properties-while-debugging.md)|
|İşlemler|CTRL + ALT + Z|[İş Parçacıklarında ve İşlemlerde Hata Ayıklama](../debugger/debug-threads-and-processes.md)|
|Bellek|CTRL + ALT + A, (1, 2, 3, 4)|[Bellek Pencereleri](../debugger/memory-windows.md)|
|Ayrıştırılmış kod|CTRL + ALT + D|[Nasıl Yapılır: Ayrıştırılmış Kod Penceresini Kullanma](../debugger/how-to-use-the-disassembly-window.md)|
|Kayıtların|CTRL + ALT + G|[Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)|

## <a name="see-also"></a>Ayrıca bkz.

[Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)