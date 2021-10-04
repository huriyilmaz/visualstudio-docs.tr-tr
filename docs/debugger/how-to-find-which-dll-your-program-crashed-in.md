---
title: "|'de Programınız Hangi DLL'nin | Microsoft Docs"
description: Modüller penceresini kullanarak, uygulamanın kilitlenmesi nedeniyle hangi dış DLL'nin etkin olduğunu belirleme. Bunu bir sistem DLL'si veya başka birinin kodu için de yapabiliriz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a1a76976dc630074768bb14bc39fc480278962fa
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431360"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Nasıl: Programınız Hangi DLL'de Kilitlenmeli Olduğunu Bulma (C#, C++, Visual Basic, F#)

 Bir sistem DLL'sinde veya başka birinin kodunda bir çağrı sırasında uygulama kilitleniyorsa, kilitlenmenin meydana geldiği zaman hangi DLL'nin etkin olduğunu bulmanız gerekir. Kendi programınız dışındaki bir DLL'de kilitlenmeyle karşınıza çıkarsanız, Modüller penceresini kullanarak **konumu tanımlayabilirsiniz.**

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Modüller penceresini kullanarak kilitlenmenin nerede olduğunu bulmak için

1. Kilitlenmenin meydana geldiği adresi not olun.

    Adres hata iletisinde gösterilmezse, DLL'i tanımlamak için alternatif yöntemlerden birini kullanabilirsiniz. Bir sistem DLL'lerinden şüpheleniyorsanız, hata [ayıklama sırasında](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Microsoft Sembol Sunucularından semboller yükleyebilirsiniz. Aksi takdirde, bunun yerine [yığın bilgileriyle bir döküm](../debugger/using-dump-files.md) dosyası oluşturmanız gerekir. Döküm dosyaları oluşturmak için çeşitli araçlar kullanılabilir.

2. Hata **Ayıkla menüsünde,** **Windows'ı seçin** ve **Modüller'e tıklayın.**

3. Modüller **penceresinde** Adres **sütununu** bulun. Bunu görmek için kaydırma çubuğunu kullanmanız gerekir.

4. **URL'leri** adrese göre sıralamak için sütunun en üstünde yer alan Adres düğmesine tıklayın.

5. Adres aralığı kilitlenme konumunu içeren DLL'i bulmak için sıralanmış listeyi tarayın.

6. DLL adını **ve yolunu** **görmek** için Ad ve Yol sütunlarına bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [DLL Projelerinde Hata Ayıklama](../debugger/debugging-dll-projects.md)
- [Nasıl Yapılır: Modüller Penceresini Kullanma](../debugger/how-to-use-the-modules-window.md)