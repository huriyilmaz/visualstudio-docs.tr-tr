---
title: İş parçacığı görünümünde Iş parçacığı arama | Microsoft Docs
description: Visual Studio 'de hata ayıklarken iş parçacığı KIMLIĞINI veya modül dizesini arama ölçütü olarak kullanarak, Spy + + aracının Iş parçacıkları görünümünde belirli bir iş parçacığını arayın.
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
ms.openlocfilehash: 7eff224614fb2a0be28258217e7d6e06a5ba7ea9d0898aeb58957e9a25610813
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378989"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Nasıl Yapılır: İş Parçacıkları Görünümünde İş Parçacığı Arama
İş parçacığı KIMLIĞINI veya modül dizesini arama ölçütü olarak kullanarak Iş parçacıkları görünümünde belirli bir iş parçacığını arayabilirsiniz. Aramanın başlangıç yönünü de belirtebilirsiniz. İletişim kutusundaki alanlar, iş parçacığı ağacındaki seçili iş parçacığının özniteliklerini gösterir.

### <a name="to-search-for-a-thread-in-threads-view"></a>İş parçacıkları görünümünde iş parçacığı aramak için

1. Windows 'larınızı, Spy + + ve etkin bir [Iş parçacığı görünümü](../debugger/threads-view.md) penceresi görünür olacak şekilde düzenleyin.

2. **Arama** menüsünden **iş parçacığı bul**' u seçin.

    [Iş parçacığı arama Iletişim kutusu](../debugger/thread-search-dialog-box.md) açılır.

3. İş parçacığı KIMLIĞINI veya bir modül dizesini arama ölçütü olarak yazın.

4. Değerlerini belirtmek istemediğiniz tüm alanları temizleyin.

   > [!TIP]
   > Bir modülün sahip olduğu tüm iş parçacıklarını bulmak için, **Iş parçacığı** **metin kutusunu temizleyin ve modül kutusuna Modül** adını yazın. Sonra iş parçacığı aramaya devam etmek için **Sonrakini Bul** ' u kullanın.

5. Aramanın ilk yönü için **yukarı** veya **aşağı** seçeneğini belirleyin.

6. **Tamam**'a tıklayın.

   Eşleşen bir iş parçacığı bulunursa, Iş parçacıkları görünümü penceresinde vurgulanır.