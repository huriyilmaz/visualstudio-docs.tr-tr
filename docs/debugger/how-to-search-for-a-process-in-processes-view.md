---
title: Işlemler görünümünde bir Işlem arayın | Microsoft Docs
description: Visual Studio 'de hata ayıklarken işlem KIMLIĞINI veya modül dizesini arama ölçütü olarak kullanarak, Spy + + aracının Işlemler görünümünde belirli bir işlemi arayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9f5ff80257a3f3708d2de517e38fbc6abf6a77f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128175"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Nasıl Yapılır: İşlemler Görünümünde İşlem Arama
İşlem KIMLIĞINI veya modül dizesini arama ölçütü olarak kullanarak, Işlemler görünümündeki belirli bir işlemi arayabilirsiniz. Aramanın başlangıç yönünü de belirtebilirsiniz. İletişim kutusundaki alanlar, işlem ağacındaki seçili işlemin özniteliklerini gösterir.

### <a name="to-search-for-a-process-in-processes-view"></a>Işlemler görünümünde bir işlem aramak için

1. Windows 'larınızı Spy + + ve etkin [süreçler görünümü](../debugger/processes-view.md) penceresi görünür olacak şekilde düzenleyin.

2. **Arama** menüsünde **işlemi bul** ' u seçin.

    [Işlem arama Iletişim kutusu](../debugger/process-search-dialog-box.md) açılır.

3. İşlem KIMLIĞINI veya bir modül dizesini arama ölçütü olarak yazın.

4. Değerlerini belirtmek istemediğiniz tüm alanları temizleyin.

   > [!TIP]
   > Bir modülün sahip olduğu tüm işlemleri bulmak için, **işlem** kutusunu temizleyin ve **Modül kutusuna Modül** adını yazın. Sonra, işlem aramaya devam etmek için **Sonrakini Bul** ' u kullanın.

5. Aramanın ilk yönü için **yukarı** veya **aşağı** seçeneğini belirleyin.

6. **Tamam**'a tıklayın.

   Eşleşen bir işlem bulunursa, **işlem görünümü** penceresinde vurgulanır.