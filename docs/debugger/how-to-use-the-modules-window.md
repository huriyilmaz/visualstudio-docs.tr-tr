---
title: DLL'leri ve yürütülebilir dosyaları görüntüleme
description: Uygulamanın modüllerde hata ayıklama oturumu .exe modüller penceresinde kullandığı DLL'leri ve yürütülebilir dosyaları (Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385415"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Modüller penceresinde DLL'leri ve yürütülebilir dosyaları görüntüleme (C#, C++, Visual Basic, F#)

Hata Visual Studio sırasında **Modüller penceresi,** uygulamanın kullandığı DLL'ler ve yürütülebilir dosyalar *(.exe* dosyaları) hakkında bilgi listeler ve gösterir.

> [!NOTE]
> Modüller penceresi SQL veya betik hata ayıklama için kullanılamaz.

## <a name="use-the-modules-window"></a>Modüller penceresini kullanma

Hata ayıklama sırasında Modüller penceresini açmak için Windows Modüllerde Hata Ayıkla'ya  >    >   tıklayın (veya **Ctrl + Alt + U tuşlarına basın).**

Modüller penceresi **varsayılan olarak** modülleri yük sırasına göre sıralar. Herhangi bir pencere sütununa göre sıralamak için sütunun üst kısmından üst bilgi seçin.

## <a name="load-symbols"></a>Sembolleri yükleme

Modüller **penceresindeki** Sembol **Durumu sütunu,** hangi modüllerin hata ayıklama simgelerinin yük olduğunu gösterir. Durum Sembollerin yüklenmesi **atlandı**, **PDB** dosyası bulunamıyor veya açılamaz veya **Dahil/dışlama** ayarı tarafından devre dışı yükleniyor ise, sembolleri el ile yükleyebilirsiniz. Sembolleri yükleme ve kullanma hakkında daha fazla bilgi için [bkz. Sembol belirtme (.pdb) ve kaynak dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

**Sembolleri el ile yüklemek için:**

1. Modüller **penceresinde** sembollerin yüklenmemiş olduğu modüle sağ tıklayın.

   - Sembollerin **neden yüklenmedi?** hakkında ayrıntılı bilgi için Sembol Yükleme Bilgileri'ne tıklayın.

   - Sembolleri **el ile yüklemek** için Sembolleri Yükle'yi seçin.

1. Semboller yüklenmezseniz, Seçenekler iletişim **kutusunu** açmak  ve sembol yükleme konumlarını belirtmek veya değiştirmek için Sembol Ayarları'ı seçin.

   Sembolleri genel Microsoft Sembol Sunucularından veya diğer sunuculardan indirebilir veya bilgisayarınıza bir klasörden semboller indirebilirsiniz. Ayrıntılar için [bkz. Sembol konumlarını belirtme ve yükleme davranışı.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)

**Sembol yükleme davranışı ayarlarını değiştirmek için:**

1. Modüller **penceresinde** herhangi bir modüle sağ tıklayın.

1. Sembol **Ayarları'ı seçin.**

1. Tüm **sembolleri yükle'yi** seçin veya hangi modüllerin dahil veya hariç tutulacaklarını seçin.

1. **Tamam**’ı seçin. Değişiklikler bir sonraki hata ayıklama oturumunda etkili olur.

**Belirli bir modül için sembol yükleme davranışını değiştirmek için:**

1. Modüller **penceresinde** modüle sağ tıklayın.

1. Sağ tıklama menüsünde Her Zaman Otomatik Olarak Yükle'yi **seçin veya seçimini kaldırın.** Değişiklikler bir sonraki hata ayıklama oturumunda etkili olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütmeyi durdurma](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)