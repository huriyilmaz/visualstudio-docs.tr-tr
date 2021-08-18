---
title: İş Parçacıkları Görünümünde İş Parçacığı Arama | Microsoft Docs
description: Spy++ aracının İş Parçacıkları görünümünde belirli bir iş parçacığını, hata ayıklama sırasında iş parçacığı kimliğini veya modül dizesini arama ölçütü olarak Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 38db1aa0af80b8c2c1769c6acf864f577a1d7a2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052050"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Nasıl Yapılır: İş Parçacıkları Görünümünde İş Parçacığı Arama
İş parçacığı kimliğini veya modül dizesini arama ölçütü olarak kullanarak İş Parçacıkları görünümünde belirli bir iş parçacığını arayabilirsiniz. Ayrıca aramanın başlangıç yönünü de belirtsiniz. İletişim kutusundaki alanlar, iş parçacığı ağacında seçili iş parçacığının özniteliklerini gösterir.

### <a name="to-search-for-a-thread-in-threads-view"></a>İş Parçacıkları görünümünde bir iş parçacığını aramak için

1. Spy++ ve etkin bir İş Parçacıkları Görünümü penceresinin görünür [olması için](../debugger/threads-view.md) pencerelerinizi düzenleme.

2. Arama menüsünde **İş** Parçacığı **Bul'a tıklayın.**

    İş [Parçacığı Arama İletişim Kutusu](../debugger/thread-search-dialog-box.md) açılır.

3. Arama ölçütü olarak iş parçacığı kimliğini veya modül dizesini yazın.

4. Değerlerini belirtmek istemeyebilirsiniz.

   > [!TIP]
   > Bir modülün sahip olduğu tüm iş parçacıklarını bulmak için İş Parçacığı **metin** kutusunu temizleyin ve Modül kutusuna modül **adını** yazın. Ardından, iş **parçacıklarını aramaya** devam etmek için Sonrakini Bul'ı kullanın.

5. **Aramanın** ilk **yönü** için Yukarı veya Aşağı'ya seçin.

6. **Tamam**'a tıklayın.

   Eşleşen bir iş parçacığı bulunursa, İş Parçacıkları görünüm penceresinde vurgulanır.