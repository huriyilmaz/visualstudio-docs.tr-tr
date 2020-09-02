---
title: 'Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7b97c346cc933e14292fbb1198bfb69ecf59717
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696172"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Nasıl Yapılır: GPU İş Parçacıkları Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

GPU Iş parçacıkları penceresinde, hata ayıklaması yaptığınız uygulamadaki GPU üzerinde çalışan iş parçacıklarını inceleyebilir ve bunlarla çalışabilirsiniz. GPU üzerinde çalışan uygulamalar hakkında daha fazla bilgi için bkz. [C++ amp genel bakış](https://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 GPU Iş parçacıkları penceresi, her bir satırın tüm sütunlarda aynı değerlere sahip olan bir GPU iş parçacığı kümesini temsil ettiği bir tablo içerir. Sütunlardaki öğeleri sıralayabilir, yeniden sıralayabilir, kaldırabilir ve gruplandırabilirsiniz. GPU Iş parçacıkları penceresinden bayrak, unbayrak, dondurma (askıda) ve çözme (devam etme) iş parçacıklarını işaretleyebilirsiniz. Aşağıdaki sütunlar, GPU Iş parçacıkları penceresinde görüntülenir:  
  
- Özel dikkat etmek istediğiniz bir iş parçacığını işaretleyecek bayrak sütunu.  
  
- Sarı okun etkin bir iş parçacığını gösterdiği etkin iş parçacığı sütunu. Bir ok, yürütmenin hata ayıklayıcıya bölünmesinin gerçekleştiği bir iş parçacığını gösterir.  
  
- Aynı konumdaki iş parçacığı sayısını görüntüleyen **Iş parçacığı sayısı** sütunu.  
  
- Her iş parçacığı grubunun bulunduğu kod satırını görüntüleyen **satır** sütunu.  
  
- Her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen **Adres** sütunu. Bu sütun varsayılan olarak gizlidir.  
  
- Kaynak kodundaki **konum sütunu.**  
  
- İş parçacığının etkin, engellenen, başlatılmamış veya tamamlanmamış olduğunu gösteren **durum** sütunu.  
  
- Satırdaki iş parçacıkları için kutucuk dizinini gösteren **döşeme** sütunu.  
  
  Tablonun üst bilgisinde, gösterilen kutucuk ve iş parçacığı gösterilmektedir.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>GPU Iş parçacıkları penceresini görüntüleme  
  
1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. Projenin **Özellik sayfaları** penceresinde, **yapılandırma özellikleri**altında **hata ayıklama**öğesini seçin.  
  
3. **Başlatmak Için hata ayıklayıcı** listesinde, **yerel Windows hata ayıklayıcısı**' nı seçin. **Hata ayıklayıcı türü** listesinde **yalnızca GPU**' yı seçin. GPU üzerinde çalışan koddaki kesme noktalarına bölmek için bu hata ayıklayıcıyı seçmeniz gerekir.  
  
4. **Tamam** düğmesini seçin.  
  
5. GPU kodunda bir kesme noktası ayarlayın.  
  
6. Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin. Uygulamanın kesme noktasına ulaşmasını bekleyin.  
  
7. Bir menü çubuğu, **Hata Ayıkla**, **Windows**, **GPU iş parçacıkları**' nı seçin.  
  
### <a name="to-change-to-a-different-active-thread"></a>Farklı bir etkin iş parçacığına geçiş yapmak için  
  
- Sütuna çift tıklayın. (Klavye: satırı seçin ve ENTER ' u seçin.)  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Belirli bir kutucuğu ve iş parçacığını görüntüleme  
  
1. GPU Iş parçacıkları penceresinde **Iş parçacığı değiştiricisini Genişlet** düğmesini seçin.  
  
2. Metin kutularına kutucuk ve iş parçacığı değerlerini girin.  
  
3. Üzerine okuna sahip düğmeyi seçin.  
  
### <a name="to-display-or-hide-a-column"></a>Bir sütunu göstermek veya gizlemek için  
  
- GPU Iş parçacıkları penceresi için kısayol menüsünü açın, **sütunlar**' ı seçin ve ardından göstermek veya gizlemek istediğiniz sütunu seçin.  
  
### <a name="to-sort-by-a-column"></a>Bir sütuna göre sıralamak için  
  
- Sütun başlığını seçin.  
  
### <a name="to-group-threads"></a>İş parçacıklarını gruplandırmak için  
  
- GPU Iş parçacıkları penceresi için kısayol menüsünü açın, **Gruplandır**' ı seçin ve ardından görünen sütun adlarından birini seçin. İş parçacıklarının grubunu çözmek için **hiçbiri** ' ni seçin.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>İş parçacığı satırını dondurmak veya çözme  
  
- Satır için kısayol menüsünü açın ve **dondurma** veya **çözme**seçeneğini belirleyin.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>İş parçacıklarının bir satırına bayrak eklemek veya bayrak kaldırmak için  
  
- İş parçacığının Bayrak sütununu seçin veya iş parçacığının kısayol menüsünü açın ve **bayrak** ya da **Unflag**' ı seçin.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için  
  
- GPU Iş parçacıkları penceresinde bayrak düğmesini seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl yapılır: paralel Izleme penceresini kullanma](../debugger/how-to-use-the-parallel-watch-window.md)   
 [İzlenecek yol: C++ AMP uygulamasında hata ayıklama](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
