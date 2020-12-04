---
title: Hata ayıklayıcı Windows kullanarak verileri İnceleme | Microsoft Docs
description: Size bilgi sağlayan birçok hata ayıklayıcı penceresi vardır. Bu makale, türlerin bir listesini sağlar. Her biri için daha fazla bilgi bağlantısı vardır.
ms.custom: SEO-VS-2020, seodec18
ms.date: 04/25/2018
ms.topic: conceptual
ms.assetid: 4c6fe8f1-b015-4989-bb31-72ebac390026
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8caa5f11f4f0501d8b56c308d5336f10d518062
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560739"
---
# <a name="inspect-data-using-debugger-windows-in-visual-studio"></a>Visual Studio 'da hata ayıklayıcı pencerelerini kullanarak verileri İnceleme

Programınızda hata ayıklarken çoğu hata ayıklayıcı penceresini açabilirsiniz. Hata ayıklayıcı pencerelerinin bir listesini görmek için, bir kesme noktası ayarlayın ve hata ayıklamayı başlatın. Kesme noktasına ulaştığınızda ve yürütme durduktan sonra **Windows > hata ayıkla**' ya tıklayın.

|Pencere|Kısayol tuşu|Konuya bakın|
|-|-|-|
|Kesme noktaları|CTRL + ALT + B|[Kesme noktaları kullan](../debugger/using-breakpoints.md)|
|Özel durum ayarları|CTRL + ALT + E|[Hata ayıklayıcı ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md)|
|Çıktı|CTRL + ALT + O|[Çıkış Penceresi](../ide/reference/output-window.md)|
|İzle|CTRL + ALT + W, (1, 2, 3, 4)|[İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)|
|QuickWatch|SHIFT + F9|[İzleme ve Hızlı İzleme Pencereleri](../debugger/watch-and-quickwatch-windows.md)|
|Otolar|CTRL + ALT + V, A|[Otomatikler ve Yereller Pencereleri](../debugger/autos-and-locals-windows.md)|
|Ayarlanmalıdır|CTRL + ALT + V, L|[Otomatikler ve Yereller Pencereleri](../debugger/autos-and-locals-windows.md)|
|Çağrı yığınları|CTRL + ALT + C|[Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma](../debugger/how-to-use-the-call-stack-window.md)|
|Hemen|CTRL + ALT + ı|[Komut penceresi](../ide/reference/immediate-window.md)|
|Paralel Yığınlar|MRK: + SHıFT + D, S|[Paralel Yığınlar Penceresini Kullanma](../debugger/using-the-parallel-stacks-window.md)|
|Paralel Izleme|MRK: + SHıFT + D, (1, 2, 3, 4)|[Çoklu Iş parçacıklı uygulamalarda hata ayıklamaya başlayın](../debugger/get-started-debugging-multithreaded-apps.md)|
|İş Parçacıkları|CTRL + ALT + H|[Iş parçacıkları penceresini kullanarak hata ayıkla](../debugger/how-to-use-the-threads-window.md)|
|Modül|CTRL + ALT + U|[Nasıl Yapılır: Modüller Penceresini Kullanma](../debugger/how-to-use-the-modules-window.md)|
|GPU Iş parçacıkları|-|[Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md)|
|Görevler|MRK: + SHıFT + D, K|[Görevleri Penceresini Kullanma](../debugger/using-the-tasks-window.md)|
|Python hata ayıklama etkileşimli|SHIFT + ALT + ı|[Python etkileşimli REPL](../python/python-interactive-repl-in-visual-studio.md)|
|JavaScript Konsolu|CTRL + ALT + V, C|[Hızlı Başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md)|
|DOM Gezgini|CTRL + ALT + V, D|[DOM Gezgini'ni kullanarak düzen hatalarını ayıklama](quickstart-debug-html-and-css.md)|
|Canlı görsel ağaç|-|[Hata ayıklama sırasında XAML özelliklerini denetleme](../xaml-tools/inspect-xaml-properties-while-debugging.md)|
|Canlı Özellik Gezgini|-|[Hata ayıklama sırasında XAML özelliklerini denetleme](../xaml-tools/inspect-xaml-properties-while-debugging.md)|
|İşlemler|CTRL + ALT + Z|[Hata ayıklama Iş parçacıkları ve süreçler](../debugger/debug-threads-and-processes.md)|
|Bellek|CTRL + ALT + A, (1, 2, 3, 4)|[Bellek Pencereleri](../debugger/memory-windows.md)|
|Ayrıştırılmış kod|CTRL + ALT + D|[Nasıl Yapılır: Ayrıştırılmış Kod Penceresini Kullanma](../debugger/how-to-use-the-disassembly-window.md)|
|Kayıtların|CTRL + ALT + G|[Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)|

## <a name="see-also"></a>Ayrıca bkz.

[Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)