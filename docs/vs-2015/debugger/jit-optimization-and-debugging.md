---
title: JıT Iyileştirme ve hata ayıklama | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690531"
---
# <a name="jit-optimization-and-debugging"></a>JIT İyileştirmesi ve Hata Ayıklaması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen bir uygulamada hata ayıklarken, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Varsayılan olarak tam zamanında (JIT) kodun iyileştirmesini bastırır. JıT iyileştirmesini gizleme, en iyi duruma getirilmemiş koddan hata ayıklaması yaptığınız anlamına gelir. Kod, iyileştirilmediği için biraz daha yavaş çalışır, ancak hata ayıklama deneyiminiz çok daha geniş. İyileştirilmiş kodda hata ayıklama işlemi daha zordur ve yalnızca iyileştirilmiş kodda oluşan ancak en iyi duruma getirilmemiş sürümde yeniden oluşturulamayacağından bir hata yaşarsanız önerilir.  
  
 JıT iyileştirmesi, modül yüklemesinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **JIT Iyileştirmesini bastır** seçeneğinde içinde denetlenir. Bu seçeneği, **Seçenekler** Iletişim kutusundaki **hata ayıklama** düğümünün altındaki **genel** sayfasında bulabilirsiniz.  
  
 **Modül YÜKLEMESINDE JIT iyileştirmesini önle** seçeneğini temizlerseniz, iyileştirilmiş JIT kodunda hata ayıklaması yapabilirsiniz, ancak en iyi duruma getirilmiş kod Kaynak kodla eşleşmediğinden hata ayıklama olanağınız sınırlı olabilir. Sonuç olarak, **Yereller** ve **oto** 'ler penceresi gibi hata ayıklayıcı pencereleri, en iyi duruma getirilmemiş koddan hata ayıklaması yaptığınız için çok daha fazla bilgi görüntülemeyebilir.  
  
 Diğer önemli fark, Yalnızca kendi kodum ile hata ayıklamaya karşı ilgilidir. Yalnızca kendi kodum ile hata ayıklaması yapıyorsanız, hata ayıklayıcı iyileştirilmiş kodu kullanıcı olmayan kod olarak değerlendirir ve hata ayıklarken görüntülenmemelidir. Sonuç olarak, JıT ile iyileştirilmiş kodda hata ayıklaması yapıyorsanız muhtemelen Yalnızca kendi kodum kapatmak istersiniz. Daha fazla bilgi için bkz.  [yalnızca kendi kodum adımlamayı kısıtla](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 **Modül yükleme SEÇENEĞINDE JIT iyileştirmesini gösterme** seçeneğinin modüller yüklendiğinde kodun iyileştirmesini bastırır olduğunu unutmayın. Zaten çalışmakta olan bir işleme eklerseniz, önceden yüklenmiş, JıT olarak derlenen ve optimize edilmiş bir kod içerebilir. **Modül YÜKLEMESINDE JIT iyileştirmesini gösterme** seçeneğinin Bu kod üzerinde hiçbir etkisi yoktur, ancak iliştirdikten sonra yüklenen modülleri etkiler. Ayrıca, modül yüklemesinde **JIT iyileştirmesini bastır** SEÇENEĞI, Ngen ile oluşturulan WinForms.dll gibi modülleri etkilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Hata ayıklayıcı ile kod arasında gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Yönetilen yürütme Işlemi](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
