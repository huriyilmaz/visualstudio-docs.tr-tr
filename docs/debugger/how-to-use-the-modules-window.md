---
title: Dll 'Leri ve yürütülebilir dosyaları görüntüleme
description: Visual Studio 'da hata ayıklama oturumu sırasında uygulamanızın modüller penceresinde kullandığı dll 'Leri ve yürütülebilir dosyaları (. exe dosyaları) görüntüleyin.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 8add274d74d9d8d7d72f2808a2b0100c66a19717
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912207"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Modüller penceresinde dll 'Leri ve yürütülebilir dosyaları görüntüleme (C#, C++, Visual Basic, F #)

Visual Studio hata ayıklaması sırasında **modüller** penceresi, uygulamanızın kullandığı dll 'ler ve yürütülebilir dosyalar (*. exe* dosyaları) hakkındaki bilgileri listeler ve gösterir.

> [!NOTE]
> Modüller penceresi SQL veya betik hata ayıklaması için kullanılamaz.

## <a name="use-the-modules-window"></a>Modüller penceresini kullanma

Modüller penceresini açmak için hata ayıklama sırasında Windows modülleri **Hata Ayıkla**' yı seçin  >    >   (veya **Ctrl + Alt + U** tuşlarına basın).

Varsayılan olarak **modüller** penceresi modülleri yükleme sırasına göre sıralar. Herhangi bir pencere sütununa göre sıralamak için sütunun en üstündeki üstbilgiyi seçin.

## <a name="load-symbols"></a>Sembolleri yükle

**Modüller** penceresindeki **sembol durumu** sütununda, hangi modüllerin hata ayıklama sembolleri yüklü olduğunu gösterir. Durum, **sembolleri yükleme Işleminin atlandığı** takdirde **pdb dosyasını bulamaz veya açamaz**, ya da **Include/exclude ayarı tarafından devre dışı** olarak yükleyebilirsiniz. sembolleri el ile yükleyebilirsiniz. Sembolleri yükleme ve kullanma hakkında daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Sembolleri el ile yüklemek için:**

1. **Modüller** penceresinde, simgelerin yüklenmediği modüle sağ tıklayın.

   - Simgelerin neden yüklenmediğini ilgili ayrıntılar için **sembol yükleme bilgileri** ' ni seçin.

   - Sembolleri el ile yüklemek için **sembolleri yükle** ' yi seçin.

1. Semboller yüklenmediğinde, **sembol ayarları** ' nı seçerek **Seçenekler** iletişim kutusunu açın ve sembol yükleme konumlarını belirtin veya değiştirin.

   Sembolleri ortak Microsoft sembol sunucularından veya diğer sunuculardan indirebilir veya bilgisayarınızdaki bir klasörden sembolleri yükleyebilirsiniz. Ayrıntılar için bkz. [simge konumlarını ve yükleme davranışını belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Sembol yükleme davranışı ayarlarını değiştirmek için:**

1. **Modüller** penceresinde herhangi bir modüle sağ tıklayın.

1. **Sembol ayarları**' nı seçin.

1. **Tüm sembolleri yükle**' yi seçin veya dahil edilecek veya hariç tutulacak modülleri seçin.

1. **Tamam**’ı seçin. Değişiklikler bir sonraki hata ayıklama oturumunda etkili olur.

**Belirli bir modülün sembol yükleme davranışını değiştirmek için:**

1. **Modüller** penceresinde modüle sağ tıklayın.

1. Sağ tıklama menüsünde, **her zaman otomatik olarak yükle**' yi seçin veya seçimini kaldırın. Değişiklikler bir sonraki hata ayıklama oturumunda etkili olur.

## <a name="see-also"></a>Ayrıca bkz.
- [Son yürütme](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)