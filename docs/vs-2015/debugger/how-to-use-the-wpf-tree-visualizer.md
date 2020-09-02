---
title: 'Nasıl yapılır: WPF Ağacı Görselleştiricisini Kullanma | Microsoft Docs'
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
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825429"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Nasıl Yapılır: WPF Ağacı Görselleştiricisini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WPF nesnesinin görsel ağacını araştırmak ve söz konusu ağaçta yer alan nesneler için WPF bağımlılık özelliklerini görüntülemek için WPF ağacı görselleştiricisi ' ni kullanabilirsiniz. Görsel ağaçlar hakkında daha fazla bilgi için bkz. [WPF Içindeki ağaçlar](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 WPF ağaç görselleştiricisi öğesini açtığınızda, iki bölme _görürsünüz: sol_taraftaki **görsel ağaç** ve sağdaki **Özellikler** **:**_tür_ bölmesi. **Görsel ağaç** bölmesindeki herhangi bir nesneyi seçin ve _ad_**:**_tür_ bölmesi **özellikleri** , bu nesnenin özelliklerini gösterecek şekilde otomatik olarak güncelleştirilir.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>WPF Ağacı Görselleştiricisini açmak için  
  
1. Bir veri Ipucunda, bir WPF nesnesi adının yanındaki bir veri **İpucu, bir** **pencere penceresi veya** **Yereller** penceresinde, büyüteç simgesine bitişik olan oka tıklayın.  
  
     Görselleştiricilerin bir listesi görüntülenir.  
  
2. **WPF ağaç görselleştiricisi**öğesine tıklayın.  
  
### <a name="to-search-the-visual-tree"></a>Görsel ağacı aramak için  
  
- **Görsel ağaç** bölmesinde, **arama** kutusuna arama yapmak istediğiniz dizeyi yazın.  
  
  WPF ağacı görselleştiricisi, görsel ağaçtaki yazdığınız dizeyle eşleşen ilk nesneyi hemen bulur. Daha doğru bir eşleşme bulmak için daha fazla karakter yazın.  

  - Görsel ağaç içindeki bir sonraki eşleştirmeye gitmek için **İleri**' ye tıklayın.  

  - Önceki eşleştirmeye geri dönmek **için önceki ' ye tıklayın.**  

  - Arama ölçütlerini temizlemek için **Temizle**' ye tıklayın.  

### <a name="to-search-the-properties-list"></a>Özellikler listesinde arama yapmak için  
  
- _Ad_**:**_tür_ **bölmesine,** **filtre** kutusunda arama yapmak istediğiniz dizeyi yazın.  
  
  WPF ağaç görselleştiricisi, yazdığınız dizeyle eşleşen özellikleri hemen bulur; artık listede, yalnızca yazdığınız dizeyle eşleşen özellikler görüntülenir. Daha doğru bir eşleşme bulmak için daha fazla karakter yazın.  

  - Arama ölçütlerini temizlemek için **Temizle**' ye tıklayın.  
  
### <a name="to-close-the-visualizer"></a>Görselleştiriciyi kapatmak için  
  
- İletişim kutusunun sağ üst köşesindeki **Kapat** simgesine tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Görselleştirici kullanma](../misc/how-to-use-a-visualizer.md)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [WPF içinde ağaçlar](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Bağımlılık Özelliklerine Genel Bakış](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
