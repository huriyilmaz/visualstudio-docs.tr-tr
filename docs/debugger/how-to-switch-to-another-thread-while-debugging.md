---
title: Hata ayıklarken başka bir iş parçacığına geçme
description: İş parçacığında çok iş parçacıklı bir uygulamada hata ayıklarken başka bir iş parçacığına geçmek için Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/27/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7521218b895371127d4389ce2456a8c0f9274f6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128110"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Nasıl bilinir: Visual Studio'da Hata Ayıklama Sırasında Başka Bir İş Parçacığına Geçiş (C#, Visual Basic, C++)
Çok iş parçacıklı bir uygulamada hata ayıklarken, üzerinde çalışmakta olduğu iş parçacığından başka bir iş parçacığına geçmek için çeşitli yöntemlerden herhangi birini kullanabilirsiniz.

> [!NOTE]
> İş parçacıklarının yürütülme sıralarını kontrol etmek için iş parçacıklarını dondurmanız [ve çözmeniz gerekir.](../debugger/get-started-debugging-multithreaded-apps.md)

Kod düzenleyicisinde iş parçacıklarını ve farklı çok iş parçacıklı hata ayıklama pencerelerini incelerken, sarı ok geçerli iş parçacığını gösterir. Kuyruklu yeşil ok, geçerli olmayan bir iş parçacığının geçerli hata ayıklayıcı bağlamına sahip olduğunu gösterir.

### <a name="to-switch-to-any-thread-that-appears"></a>Görüntülenen herhangi bir iş parçacığına geçmek için

- İş Parçacıkları **veya** **Paralel İzleme** penceresinde iş parçacığına çift tıklayın.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Kaynak penceresinde iş parçacığına geçmek için

- Sol oluk içinde bir iş parçacığı işaretçisi simgesine sağ ![tıklayın,](../debugger/media/dbg-thread-marker.png "ThreadMarker")İş Parçacığı İşaretçisi'nin üzerine gelin ve ardından geçiş yapmak istediğiniz iş parçacığının adına tıklayın. Kısayol menüsünde yalnızca ilgili konumdaki iş parçacıkları görüntülenir.

     İş parçacığı işaretçisi görünmüyorsa İş Parçacıkları penceresine sağ **tıklayın** ve Kaynakta İş **Parçacıklarını Göster'in seçili** olduğunu doğrulayın.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Hata Ayıklama Konumu araç çubuğunda bir iş parçacığına geçmek için

1. Hata Ayıklama **Konumu araç çubuğunda** İş Parçacığı **listesine** tıklayın.

2. Listede, geçiş yapmak istediğiniz iş parçacığına tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
