---
title: 'Nasıl yapılır: Iş parçacıklarını bayrak ve işaretini kaldır | Microsoft Docs'
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
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189437"
---
# <a name="how-to-flag-and-unflag-threads"></a>Nasıl Yapılır: İş Parçacıklarını Bayrakla İşaretleme ve İşareti Geri Alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Iş parçacıklarında**, **paralel yığınlarda**, **paralel**bildirimde ve **GPU iş parçacıkları** penceresinde bir simge ile işaretleyerek özel dikkat sağlamak istediğiniz bir iş parçacığına bayrak atayabilirsiniz. Bu simge, ve diğer iş parçacıklarından işaretlenen iş parçacıklarını ayırt etmenize yardımcı olabilir.  
  
 Bayraklı iş parçacıkları Ayrıca **hata ayıklama konumu** araç çubuğunda **iş parçacığı** listesinde özel bir işlem alır. Bu liste, tüm iş parçacıklarını veya yalnızca bayraklı iş parçacıklarını gösterebilir. Bir iş parçacığını bayrakla belirlediğinizde, **Iş parçacığı** listesi otomatik olarak yalnızca bayraklı iş parçacıklarını gösterecek şekilde geçer, ancak tüm iş parçacıklarını uygun şekilde göstermek için geri dönebilirsiniz.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>İş parçacığı penceresini kullanarak bir iş parçacığına bayrak eklemek veya bayrak kaldırmak için  
  
- **Iş parçacıkları** penceresinde ilgilendiğiniz iş parçacığını bulun ve bayrağı seçmek veya temizlemek için bayrak simgesine tıklayın.  
  
### <a name="to-unflag-all-threads"></a>Tüm iş parçacıklarının bayrağını kaldır  
  
- **Iş parçacıkları** penceresinde, herhangi bir iş parçacığına sağ tıklayın ve sonra **Tüm Iş parçacıklarının bayrağını kaldır**' a tıklayın.  
  
### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için  
  
- Hata ayıklama penceresinde bayrak düğmesini seçin.  
  
### <a name="to-flag-just-my-code"></a>Yalnızca kendi kodum işaretlemek için  
  
1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, bayrak simgesine tıklayın.  
  
2. Aşağı açılan listede, **yalnızca kendi kodum işaretle**' ye tıklayın.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Seçili modüllerle ilişkili iş parçacıklarını işaretlemek için  
  
1. **Iş parçacıkları** penceresinin araç çubuğunda bayrak simgesine tıklayın.  
  
2. Açılan listede, **özel modül seçimini işaretle**' ye tıklayın.  
  
3. **Modül Seç** iletişim kutusunda, istediğiniz modülleri seçin.  
  
4. Seçim **Arama** kutusuna belirli modülleri aramak için bir dize yazın.  
  
5. **Tamam**’a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [İzlenecek Yol: Çok İş Parçacıklı Uygulamada Hata Ayıklama](../debugger/walkthrough-debugging-a-multithreaded-application.md)
