---
title: Iş parçacıklarını işaretle ve bayrak kaldır | Microsoft Docs
description: Visual Studio 'da iş parçacıklarını bayrakla işaretlemeyi veya bayrak kaldırmalarını öğrenin. Bir iş parçacığını, birkaç iş parçacığını veya tüm iş parçacıklarını bayrak veya işaretini kaldır. Yalnızca kendi kodunuzu veya bir modülle ilişkili olanları bayrakla işaretle.
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
ms.workload:
- multiple
ms.openlocfilehash: d5f31bb73b4a22a11235e471dfa1fa99545e422e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877609"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Nasıl yapılır: bayrak ve Unflag Iş parçacıkları (C#, Visual Basic, C++)

**Iş parçacıkları**, **Paralel Yığınlar** (iş parçacığı görünümü), **paralel izleme** ve **GPU iş parçacıkları** pencerelerinin bir simgesi ile işaretleyerek özel dikkat sağlamak istediğiniz bir iş parçacığına bayrak atayabilirsiniz. Bu simge, ve diğer iş parçacıklarından işaretlenen iş parçacıklarını ayırt etmenize yardımcı olabilir.

Bayraklı iş parçacıkları Ayrıca **hata ayıklama konumu** araç çubuğundaki **iş parçacığı** listesinde ve diğer çok iş parçacıklı hata ayıklama penceresinde özel bir işlem alır. Tüm iş parçacıklarını veya yalnızca bir **Iş parçacığı** listesindeki veya diğer pencerelerin bayraklı iş parçacıklarını gösterebilirsiniz.

### <a name="to-flag-or-unflag-a-thread"></a>Bir iş parçacığını işaretlemek veya bayrak kaldırmak için

- **Iş parçacıkları** veya **paralel izleme** penceresinde ilgilendiğiniz iş parçacığını bulun ve bayrağı seçmek veya temizlemek için bayrak simgesine tıklayın.
- **Paralel Yığınlar** penceresinde iş parçacığı veya iş parçacığı grubuna sağ tıklayın ve **bayrak/ \<thread>** veya **unbayrak/ \<thread>** seçeneğini belirleyin.

### <a name="to-unflag-all-threads"></a>Tüm iş parçacıklarının bayrağını kaldır

- **Iş parçacıkları** penceresinde, herhangi bir iş parçacığına sağ tıklayın ve sonra **Tüm Iş parçacıklarının bayrağını kaldır**' a tıklayın.
- **Paralel izleme** penceresinde, bayraklı tüm iş parçacıkları ' nı seçin, ardından sağ tıklayıp **unbayrak**' ı seçin.

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için

- Çok iş parçacıklı hata ayıklama pencerelerinin birinde **yalnızca bayraklı Iş parçacıklarını göster** düğmesini seçin.

### <a name="to-flag-just-my-code"></a>Yalnızca kendi kodum işaretlemek için

1. **Iş parçacıkları** penceresinin en üstündeki araç çubuğunda, bayrak simgesine tıklayın.

2. Aşağı açılan listede, **yalnızca kendi kodum işaretle**' ye tıklayın.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Seçili modüllerle ilişkili iş parçacıklarını işaretlemek için

1. **Iş parçacıkları** penceresinin araç çubuğunda bayrak simgesine tıklayın.

2. Açılan listede, **özel modül seçimini işaretle**' ye tıklayın.

3. **Modül Seç** iletişim kutusunda, istediğiniz modülleri seçin.

4. Seçim **Arama** kutusuna belirli modülleri aramak için bir dize yazın.

5. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Çok iş parçacıklı uygulamalarda hata ayıklamaya başlama](../debugger/get-started-debugging-multithreaded-apps.md)
- [İzlenecek yol: Iş parçacıkları penceresini kullanarak çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/how-to-use-the-threads-window.md)