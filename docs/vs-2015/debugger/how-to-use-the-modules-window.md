---
title: 'Nasıl yapılır: modüller penceresini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696123"
---
# <a name="how-to-use-the-modules-window"></a>Nasıl Yapılır: Modüller Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Bu özellik SQL veya betik hata ayıklaması için kullanılamaz.  
  
 **Modüller** penceresi, programınız tarafından kullanılan dll 'LERI ve exe 'yi listeler ve her biri için ilgili bilgileri gösterir.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Modül penceresini kesme modunda veya çalışma modunda görüntüleme  
  
- **Hata Ayıkla** menüsünde **Windows**' u seçin ve ardından **modüller**' i tıklatın.  
  
     Varsayılan olarak **modüller** penceresi modülleri yükleme sırasına göre sıralar. Ancak, herhangi bir sütuna göre sıralamayı seçebilirsiniz.  
  
### <a name="to-sort-by-any-column"></a>Herhangi bir sütuna göre sıralamak için  
  
- Sütunun en üstündeki düğmeye tıklayın.  
  
     Kısayol menüsünü kullanarak, sembolleri yükleyebilir veya **modüller** penceresinden bir sembol yolu belirtebilirsiniz.  
  
## <a name="loading-symbols"></a>Semboller yükleniyor  
 **Modüller** penceresinde, hangi modüllerin hata ayıklama sembolleri yüklendiğini görebilirsiniz. Bu bilgiler **sembol durumu** sütununda görüntülenir. Durum **atlandı Load, pdb dosyasını bulamıyor veya açamıyor**ya da **içerme/hariç tutma ayarı ile devre dışı olarak yüklemeyi**, Microsoft ortak sembol sunucularından sembolleri indirmek veya bilgisayarınızdaki bir sembol dizininden sembolleri yüklemek için hata ayıklayıcıyı yönlendirebilirsiniz. Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Sembolleri el ile yüklemek için  
  
1. **Modüller** penceresinde, simgelerin yüklenmediği bir modüle sağ tıklayın.  
  
2. **Sembolleri yükle** ' nin üzerine gelin ve ardından **Microsoft sembol sunucuları** veya **sembol yolu**' na tıklayın.  
  
#### <a name="to-change-symbol-load-settings"></a>Sembol yükleme ayarlarını değiştirmek için  
  
1. **Modüller** penceresinde herhangi bir modüle sağ tıklayın.  
  
2. **Sembol ayarları**' na tıklayın.  
  
     Artık sembol [konumları belirtin ve yükleme davranışı](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)bölümünde açıklandığı gibi sembol yükleme ayarlarını değiştirebilirsiniz. Değişiklikler hata ayıklama oturumu yeniden başlatılana kadar etkili olmaz.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Belirli bir modülün sembol yükleme davranışını değiştirmek için  
  
1. **Modüller** penceresinde modüle sağ tıklayın.  
  
2. **Otomatik sembol yükleme ayarları** ' nın üzerine gelin ve ardından **her zaman el ile** veya **varsayılan**olarak yükle ' Değişiklikler hata ayıklama oturumu yeniden başlatılana kadar etkili olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Son yürütme](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
