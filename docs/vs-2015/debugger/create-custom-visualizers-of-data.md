---
title: Özel Görselleştiriciler oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
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
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50df868f0e01d49d4c49bccae32d743d5291a066
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820653"
---
# <a name="create-custom-visualizers-of-data"></a>Özel Görselleştiriciler oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştiriciler, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hata ayıklayıcı Kullanıcı arabiriminin bileşenleridir. *Görselleştirici* , bir değişken veya nesneyi veri türüne uygun şekilde göstermek için bir iletişim kutusu veya başka bir arabirim oluşturur. Örneğin, bir HTML Görselleştiricisini bir HTML dizesini yorumlar ve bir tarayıcı penceresinde görüneceği şekilde sonucu görüntüler; bit eşlem görselleştiricisi bir bit eşlem yapısını Yorumlar ve temsil ettiği grafiği görüntüler. Bazı Görselleştiriciler, verileri görüntülemenizi ve değiştirmenizi sağlar.  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]Hata ayıklayıcı altı standart Görselleştiriciler içerir. Bunlar, hepsi dize nesnelerinde çalışan metin, HTML, XML ve JSON görselleştiricilerini gösterir; WPF nesne görsel ağacının özelliklerini görüntülemek için WPF ağaç görselleştiricisi; Veri kümesi, DataView ve DataTable nesneleri için de kullanılabilir olan veri kümesi görselleştiricisi. Ek Görselleştiriciler gelecekte Microsoft Corporation 'dan indirilebilir ve üçüncü taraflar ve topluluk tarafından kullanılabilir. Ayrıca, kendi görselleştiricilerini yazabilir ve [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hata ayıklayıcıya yükleyebilirsiniz.  
  
> [!NOTE]
> **Mağaza** uygulamalarında yalnızca standart metın, HTML, XML ve JSON Görselleştiriciler desteklenir. Özel (Kullanıcı tarafından oluşturulan) Görselleştiriciler desteklenmez.  
  
 Görselleştiriciler, hata ayıklayıcıda büyüteç simgesiyle gösterilir. Bir veri **ipucunda**büyüteç simgesini, bir hata ayıklayıcı değişkenleri penceresinde veya **QuickWatch** iletişim kutusunda gördüğünüzde, ilgili nesnenin veri türüne uygun bir Görselleştirici seçmek için Büyüteç Camı ' ne tıklayabilirsiniz.  
  
 Görselleyiciler Compact Framework 'te desteklenmez.  
  
> [!NOTE]
> Hata ayıklayıcı Görselleştiriciler kısmi güven uygulaması tarafından izin verilenden daha fazla ayrıcalık gerektiriyor. Sonuç olarak, kısmi güvenle kodda durdurulduğunda Görselleştiriciler yüklenmez. Görselleştirici kullanarak hata ayıklamak için, kodu tam güvenle çalıştırmanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl Yapılır: Görselleştirici Yazma](../debugger/how-to-write-a-visualizer.md)  
  
 [İzlenecek Yol: C# ile Görselleştirici Yazma](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Nasıl yapılır: Görselleştirici yüklemesi](../debugger/how-to-install-a-visualizer.md)  
  
 [Nasıl yapılır: Görselleştiriciyi test etme ve hata ayıklama](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Görselleştirici API Başvurusu](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
