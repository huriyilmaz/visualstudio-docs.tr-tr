---
title: 'Nasıl yapılır: paralel Izleme penceresini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697489"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Nasıl Yapılır: Paralel İzleme Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Paralel izleme penceresi, bir ifadenin birden çok iş parçacığında tuttuğu değerleri aynı anda görüntüleyebilirsiniz. Her satır bir uygulamada çalışan bir iş parçacığını temsil eder, ancak bir iş parçacığı birden çok satırda gösterilebilir. Daha belirgin olarak, her satır, işlev imzası geçerli yığın çerçevesindeki işlevle eşleşen bir işlev çağrısını temsil eder. Sütunlardaki öğeleri sıralayabilir, yeniden sıralayabilir, kaldırabilir ve gruplandırabilirsiniz. İş parçacıklarını bayrak, unbayrak, dondurma (askıya al) ve çözme (devam etme). **Paralel izleme** penceresinde aşağıdaki sütunlar görüntülenir:  
  
- Özel dikkat etmek istediğiniz bir iş parçacığını işaretleyecek bayrak sütunu.  
  
- Bir okun seçili çerçeveyi gösterdiği çerçeve sütunu.  
  
- Makine, işlem, kutucuk, görev ve iş parçacığını görüntüleyebilen yapılandırılabilir bir sütun.  
  
  > [!TIP]
  > Görev bilgilerini **paralel izleme** penceresinde göstermek Için **paralel görev** penceresini açmanız gerekir.  
  
- **\<Add Watch>** İçinde izlenecek ifadeler girebileceğiniz sütun.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Paralel izleme penceresi görüntüleme  
  
1. Kodda bir kesme noktası ayarlayın.  
  
2. Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin. Uygulamanın kesme noktasına ulaşmasını bekleyin.  
  
3. Menü çubuğunda **Hata Ayıkla**, **Windows**, **paralel izleme**' yi seçin ve ardından bir Gözcü penceresi seçin. Dört tane pencere açabilirsiniz.  
  
### <a name="to-add-a-watch-expression"></a>Bir Gözcü ifadesi eklemek için  
  
- **\<Add Watch>** Bir Gözcü ifadesi seçin ve sonra belirtin.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Bir iş parçacığını işaretlemek veya bayrak kaldırmak için  
  
- Satır için bayrak sütununu seçin veya iş parçacığının kısayol menüsünü açın ve **bayrak** ya da **Unflag**' ı seçin.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için  
  
- **Paralel izleme** penceresinin sol üst köşesindeki yalnızca bayraklı seçeneği göster düğmesini seçin.  
  
### <a name="to-switch-frames"></a>Çerçeveleri değiştirmek için  
  
- Çerçeve sütununa çift tıklayın. (Klavye: satırı seçin ve ENTER tuşuna basın.)  
  
### <a name="to-sort-a-column"></a>Bir sütunu sıralamak için  
  
- Sütun başlığını seçin.  
  
### <a name="to-group-threads"></a>İş parçacıklarını gruplandırmak için  
  
- Paralel izleme penceresi için kısayol menüsünü açın, **Gruplandır**' ı seçin ve ardından uygun alt menü öğesini seçin.  
  
### <a name="to-freeze-or-thaw-threads"></a>İş parçacıklarını dondurmak veya çözme  
  
- Satır için kısayol menüsünü açın ve **dondurma** veya **çözme**seçeneğini belirleyin.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Verileri paralel izleme penceresi dışarı aktarmak için  
  
- **Excel 'de aç** düğmesini seçin ve sonra **Excel 'de aç** veya **CSV 'ye aktar**' ı seçin.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Boole ifadesine göre filtrelemek için  
  
- **Boole ifadesine göre filtrele** kutusuna bir Boole ifadesi girin. Hata ayıklayıcı, her bir iş parçacığı bağlamı için ifadeyi değerlendirir. Yalnızca değerin `true` görüntülendiği satırlar görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md)   
 [İzlenecek yol: C++ AMP uygulamasında hata ayıklama](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
