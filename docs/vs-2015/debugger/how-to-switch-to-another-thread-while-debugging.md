---
title: 'Nasıl yapılır: hata ayıklarken başka bir Iş parçacığına geçme | Microsoft Docs'
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
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176517"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Nasıl Yapılır: Hata Ayıklarken Başka Bir İş Parçacığına Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çok iş parçacıklı bir uygulamada hata ayıklarken, çalışan iş parçacığından başka bir iş parçacığına geçiş yapmak için birkaç yöntemden birini kullanabilirsiniz.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Iş parçacıkları penceresinde görüntülenen herhangi bir iş parçacığına geçiş yapmak için  
  
- İş parçacığına çift tıklayın.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Kaynak penceredeki bir iş parçacığına geçiş yapmak için  
  
- Sol cilt payındaki bir iş parçacığı göstergesini sağ tıklatın, **geçiş yap**' ın üzerine gelin ve ardından değiştirmek istediğiniz iş parçacığının adına tıklayın. Kısayol menüsü yalnızca ilgili konumdaki iş parçacıklarını gösterir.  
  
     Hiçbir gösterge görünmezse, **Iş parçacıkları** penceresinde sağ tıklayın ve **Iş parçacıklarını kaynakta göster** ' in seçili olduğunu doğrulayın.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Hata ayıklama konumu araç çubuğunda bir iş parçacığına geçiş yapmak için  
  
1. **Hata ayıklama konumu** araç çubuğunda, **iş parçacığı** kutusuna tıklayın.  
  
2. Listede, değiştirmek istediğiniz iş parçacığına tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok İş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
