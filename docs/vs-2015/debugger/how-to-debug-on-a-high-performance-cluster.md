---
title: 'Nasıl yapılır: yüksek performanslı bir kümede hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4487b168c3d405b2449bcfb9515e60f0ea67ed1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702687"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Nasıl Yapılır: Yüksek Performanslı Kümede Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yüksek performanslı bir kümede çok İşlemsiz bir programın hata ayıklaması, uzak bir bilgisayardaki sıradan bir programın hata ayıklamasına benzer. Ancak bazı ek hususlar vardır. Genel uzaktan kurulum gereksinimleri için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
 Yüksek performanslı bir kümede hata ayıklarken, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Uzaktan hata ayıklama için kullanılabilen tüm hata ayıklama pencerelerini ve tekniklerini kullanabilirsiniz. Ancak uzaktan hata ayıklaması yaptığınız için dış konsol penceresi kullanılamaz.  
  
 **Iş parçacıkları** penceresi ve **süreçler** penceresi özellikle paralel uygulamalarda hata ayıklamak için faydalıdır. Bu pencereleri kullanma hakkında ipuçları için bkz. [nasıl yapılır: Işlem penceresini kullanma](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) ve [nasıl yapılır: Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-threads-window.md).  
  
 Aşağıdaki yordamlarda, özellikle yüksek performanslı bir kümede hata ayıklama için yararlı olan bazı teknikler gösterilmektedir.  
  
 Paralel bir uygulamada hata ayıklarken, belirli bir iş parçacığı, süreç veya bilgisayarda bir kesme noktası ayarlamak isteyebilirsiniz. Bunu, normal bir kesme noktası oluşturarak ve sonra bir kesme noktası filtresi ekleyerek yapabilirsiniz.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Kesme noktası filtresi iletişim kutusunu açmak için  
  
1. Kaynak penceresinde, **ayrıştırma** penceresinde, **çağrı yığını** penceresinde veya **kesme noktaları** penceresinde bir kesme noktası glifi ' ne sağ tıklayın.  
  
2. Kısayol menüsünde **filtre**' ye tıklayın. Bu seçenek en üst düzeyde veya **kesme noktaları**altındaki alt menüde görünebilir.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Belirli bir bilgisayarda bir kesme noktası ayarlamak için  
  
1. **İşlem** penceresinden bilgisayar adını alın.  
  
2. Bir kesme noktası seçin ve önceki yordamda açıklandığı gibi **kesme noktası filtresi** iletişim kutusunu açın.  
  
3. **Kesme noktası filtresi** iletişim kutusunda şunu yazın:  
  
     MachineName =*yourmachinename*  
  
     Daha karmaşık bir filtre oluşturmak için, yan tümceleri, `&` and işlecini, `||` , or işlecini, `!` , Not işleci ve parantezleri kullanarak birleştirebilirsiniz.  
  
4. **Tamam**’a tıklayın.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Belirli bir işlemde bir kesme noktası ayarlamak için  
  
1. **İşlemler** penceresinden işlem adını veya işlem kimliği numarasını alın.  
  
2. Bir kesme noktası seçin ve ilk yordamda olduğu gibi **kesme noktası filtresi** iletişim kutusunu açın.  
  
3. **Kesme noktası filtresi** iletişim kutusunda şunu yazın:  
  
     `ProcessName =`  *yourprocessname*  
  
     —veya—  
  
     `ProcessID =`*Yourprocessıdnumber*  
  
     Daha karmaşık bir filtre oluşturmak için, yan tümceleri, `&` and işlecini, `||` , or işlecini, `!` , Not işleci ve parantezleri kullanarak birleştirebilirsiniz.  
  
4. **Tamam**’a tıklayın.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Belirli bir iş parçacığında bir kesme noktası ayarlamak için  
  
1. İş parçacığı adı veya iş parçacığı KIMLIĞI numarasını iş **parçacıkları** penceresinden alın.  
  
2. Bir kesme noktası seçin ve ilk yordamda açıklandığı gibi **kesme noktası filtresi** iletişim kutusunu açın.  
  
3. **Kesme noktası filtresi** iletişim kutusunda şunu yazın:  
  
     `ThreadName =`*yourthreadname*  
  
     —veya—  
  
     `ThreadID =`*Yourthreadıdnumber*  
  
     Daha karmaşık bir filtre oluşturmak için, yan tümceleri, `&` and işlecini, `||` , or işlecini, `!` , Not işleci ve parantezleri kullanarak birleştirebilirsiniz.  
  
4. **Tamam**’a tıklayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, adlı bir bilgisayar ve adlı bir iş parçacığı için bir kesme noktası için bir filtre oluşturmayı gösterir `marvin` `fourier1` .  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)   
 [Nasıl yapılır: süreçler penceresini kullanma](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Nasıl yapılır: Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-threads-window.md)   
 [İş parçacıkları ve süreçler](https://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Kesme Noktalarını Kullanma](../debugger/using-breakpoints.md)
