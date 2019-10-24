---
title: Hata ayıklarken başka bir iş parçacığına geçme
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11ad6280ad1213008bbb8ca8f6311ca34231d308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732436"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Nasıl yapılır: Visual Studio 'da hata ayıklarken başka bir Iş parçacığına geçmeC#(, Visual Basic C++,)
Çok iş parçacıklı bir uygulamada hata ayıklarken, çalışmakta olduğunuz iş parçacığından başka bir iş parçacığına geçiş yapmak için birkaç yöntemden birini kullanabilirsiniz.

> [!NOTE]
> İş parçacıklarının yürütme sırasını denetlemek isterseniz, [iş parçacıklarını dondurmanız ve bunları çözme](../debugger/get-started-debugging-multithreaded-apps.md)yapmanız gerekir.

Kod düzenleyicisinde iş parçacıklarını ve farklı çok iş parçacıklı hata ayıklama pencerelerini incelediğinizde, sarı ok geçerli iş parçacığını gösterir. Küme kuyruklu yeşil ok, geçerli olmayan bir iş parçacığının geçerli hata ayıklayıcı bağlamına sahip olduğunu gösterir.

### <a name="to-switch-to-any-thread-that-appears"></a>Görüntülenen herhangi bir iş parçacığına geçiş yapmak için

- **Iş parçacıkları** veya **paralel izleme** penceresinde iş parçacığına çift tıklayın.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Kaynak penceredeki bir iş parçacığına geçiş yapmak için

- Sol cilt payındaki bir iş parçacığı işaretleyici simgesi ![Iş parçacığı işaretleyicisi](../debugger/media/dbg-thread-marker.png "Threadişaretleyici")' ne sağ tıklayın, **geçiş**' in üzerine gelin ve ardından değiştirmek istediğiniz iş parçacığının adına tıklayın. Kısayol menüsü yalnızca ilgili konumdaki iş parçacıklarını gösterir.

     Hiçbir iş parçacığı işaretleyicisi görünmezse, **Iş parçacıkları** penceresinde sağ tıklayın ve **Iş parçacıklarını kaynakta göster** ' in seçili olduğunu doğrulayın.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Hata ayıklama konumu araç çubuğunda bir iş parçacığına geçiş yapmak için

1. **Hata ayıklama konumu** araç çubuğunda, **iş parçacığı** listesine tıklayın.

2. Listede, değiştirmek istediğiniz iş parçacığına tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok İş Parçacıklı Uygulamaların Hatalarını Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
