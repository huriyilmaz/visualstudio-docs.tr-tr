---
title: High-Performance kümesinde hata ayıklama | Microsoft Docs
description: Yüksek performanslı bir kümede çok işlemli bir programda hata ayıklamanın ne olduğunu öğrenin. İki pencere özellikle yararlıdır ve özel teknikler vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c4e6bffa006fac3408bc3b5459cdeee92c9a636f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052063"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Nasıl yapılır: High-Performance kümesinde hata ayıklama (C#, Visual Basic, C++)

Yüksek performanslı bir kümede çok İşlemsiz bir programın hata ayıklaması, uzak bir bilgisayardaki sıradan bir programın hata ayıklamasına benzer. Ancak bazı ek hususlar vardır. Genel uzaktan kurulum gereksinimleri için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

 Yüksek performanslı bir kümede hata ayıklarken, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Uzaktan hata ayıklama için kullanılabilen tüm hata ayıklama pencerelerini ve tekniklerini kullanabilirsiniz. Ancak uzaktan hata ayıklaması yaptığınız için dış konsol penceresi kullanılamaz.

 **Iş parçacıkları** penceresi ve **süreçler** penceresi özellikle paralel uygulamalarda hata ayıklamak için faydalıdır. Bu pencereleri kullanma hakkında ipuçları için bkz. [nasıl yapılır: Işlem penceresini kullanma](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) ve [Izlenecek yol: iş parçacıkları penceresini kullanarak hata ayıklama](../debugger/how-to-use-the-threads-window.md).

 Aşağıdaki yordamlarda, özellikle yüksek performanslı bir kümede hata ayıklama için yararlı olan bazı teknikler gösterilmektedir.

 Paralel bir uygulamada hata ayıklarken, belirli bir iş parçacığı, süreç veya bilgisayarda bir kesme noktası ayarlamak isteyebilirsiniz. Bunu, normal bir kesme noktası oluşturarak ve sonra bir kesme noktası filtresi ekleyerek yapabilirsiniz.

### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Kesme noktası filtresi iletişim kutusunu açmak için

1. Kaynak penceresinde, **ayrıştırma** penceresinde, **çağrı yığını** penceresinde veya **kesme noktaları** penceresinde bir kesme noktası glifi ' ne sağ tıklayın.

2. Kısayol menüsünde **filtre**' ye tıklayın. Bu seçenek en üst düzeyde veya **kesme noktaları** altındaki alt menüde görünebilir.

### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Belirli bir bilgisayarda bir kesme noktası ayarlamak için

1. **İşlem** penceresinden bilgisayar adını alın.

2. Bir kesme noktası seçin ve önceki yordamda açıklandığı gibi **kesme noktası filtresi** iletişim kutusunu açın.

3. **Kesme noktası filtresi** iletişim kutusunda şunu yazın:

     MachineName =*yourmachinename*

     Daha karmaşık bir filtre oluşturmak için, yan tümceleri, `&` and işlecini, `||` , or işlecini, `!` , Not işleci ve parantezleri kullanarak birleştirebilirsiniz.

4. **Tamam**'a tıklayın.

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Belirli bir işlemde bir kesme noktası ayarlamak için

1. **İşlemler** penceresinden işlem adını veya işlem kimliği numarasını alın.

2. Bir kesme noktası seçin ve ilk yordamda olduğu gibi **kesme noktası filtresi** iletişim kutusunu açın.

3. **Kesme noktası filtresi** iletişim kutusunda şunu yazın:

     `ProcessName =`  *yourprocessname*

     —veya—

     `ProcessID =`*Yourprocessıdnumber*

     Daha karmaşık bir filtre oluşturmak için, yan tümceleri, `&` and işlecini, `||` , or işlecini, `!` , Not işleci ve parantezleri kullanarak birleştirebilirsiniz.

4. **Tamam**'a tıklayın.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Belirli bir iş parçacığında bir kesme noktası ayarlamak için

1. İş parçacığı adı veya iş parçacığı KIMLIĞI numarasını iş **parçacıkları** penceresinden alın.

2. Bir kesme noktası seçin ve ilk yordamda açıklandığı gibi **kesme noktası filtresi** iletişim kutusunu açın.

3. **Kesme noktası filtresi** iletişim kutusunda şunu yazın:

     `ThreadName =`*yourthreadname*

     —veya—

     `ThreadID =`*Yourthreadıdnumber*

     Daha karmaşık bir filtre oluşturmak için, yan tümceleri, `&` and işlecini, `||` , or işlecini, `!` , Not işleci ve parantezleri kullanarak birleştirebilirsiniz.

4. **Tamam**'a tıklayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, adlı bir bilgisayar ve adlı bir iş parçacığı için bir kesme noktası için bir filtre oluşturmayı gösterir `marvin` `fourier1` .

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
- [Nasıl yapılır: süreçler penceresini kullanma](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Başlarken Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/get-started-debugging-multithreaded-apps.md)
- [İş parçacıkları ve süreçler](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Kesme noktaları kullanma](../debugger/using-breakpoints.md)