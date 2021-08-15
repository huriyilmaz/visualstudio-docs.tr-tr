---
title: İş Parçacıklarına Bayrak | Microsoft Docs
description: İş parçacıklarını tek tek bayrakla bayrakla Visual Studio. Bir iş parçacığına, birkaç iş parçacığına veya tüm iş parçacıklarına bayrak bayrak veya bayrağını açma. Yalnızca kodunuz veya bir modülle ilişkilendirilmiş olanları bayrakla bayrakla girin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 62b3b57e7932ac44a24a0d4946f38be6f1b5d9502dabc6a3bc8a8070414831b8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379080"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Nasıl bilinir: İş Parçacıklarını Bayrakla BayrakLa ve Bayrakla Asma (C#, Visual Basic, C++)

İş **Parçacıkları,** Paralel Yığınlar **(iş** parçacığı **görünümü),** Paralel İzleme ve GPU İş Parçacıkları pencerelerini bir simgeyle işaretleyerek özel olarak dikkat vermek istediğiniz bir iş parçacığını **işaretleyerek işaretleyerek** işaretlenir. Bu simge, sizin ve başkalarının bayraklı iş parçacıklarını diğer iş parçacıklarından ayırmanıza yardımcı olabilir.

Bayraklı iş parçacıkları ayrıca  Hata Ayıklama  Konumu araç çubuğundaki İş Parçacığı listesinde ve diğer çok iş parçacıklı hata ayıklama pencerelerde özel işlem alır. Tüm iş parçacıklarını veya yalnızca işaretlenen iş parçacıklarını **İş** Parçacığı listesinde veya diğer pencerelerde gösterebilirsiniz.

### <a name="to-flag-or-unflag-a-thread"></a>Bir iş parçacığını bayrakla bayrakla bayraklama veya bayrağını açma

- İş Parçacıkları **veya** **Paralel İzleme** penceresinde ilgilendiğinizi iş parçacığını bulun ve bayrağı seçmek veya temizlemek için bayrak simgesine tıklayın.
- Paralel **Yığınlar penceresinde** bir iş parçacığına veya iş parçacığı grubuna sağ tıklayın ve Bayrak / veya Bayrağını **Aç \<thread> /** seçeneğini **seçin. \<thread>**

### <a name="to-unflag-all-threads"></a>Tüm iş parçacıklarının bayrağını geri alama

- İş Parçacıkları **penceresinde** herhangi bir iş parçacığına sağ tıklayın ve ardından Tüm İş **Parçacıklarını Bayrağını Aç'a tıklayın.**
- Paralel İzleme **penceresinde tüm** bayraklı iş parçacıklarını seçin, ardından sağ tıklayın ve Bayrağını **aç'ı seçin.**

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için

- Çok iş **parçacıklı hata ayıklama pencerelerinden** birinin Yalnızca Bayraklı İş Parçacıklarını Göster düğmesini seçin.

### <a name="to-flag-just-my-code"></a>Bir Yalnızca kendi kodum

1. İş Parçacıkları penceresinin en üstündeki **araç** çubuğunda bayrak simgesine tıklayın.

2. Açılan listede Bayrak ekle'ye **tıklayın Yalnızca kendi kodum.**

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Seçili modüllerle ilişkili iş parçacıklarını bayrakla bayrakla bayrakla bayrakla

1. İş Parçacıkları penceresinin **araç** çubuğunda bayrak simgesine tıklayın.

2. Açılan listede Özel Modül Seçimi **bayrağına tıklayın.**

3. Modülleri **Seç iletişim** kutusunda istediğiniz modülleri seçin.

4. (İsteğe bağlı) Ara **kutusuna** belirli modülleri aramak için bir dize yazın.

5. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Çok iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md)
- [Adım adım kılavuz: İş Parçacıkları penceresini kullanarak çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/how-to-use-the-threads-window.md)