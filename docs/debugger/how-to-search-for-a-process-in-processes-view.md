---
title: Işlemler görünümünde bir Işlem arayın | Microsoft Docs
description: Visual Studio 'da hata ayıklarken işlem KIMLIĞI veya modül dizesini arama ölçütü olarak kullanarak, Spy + + aracının Işlemler görünümünde belirli bir işlemi arayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f6c51276bea76fe77455d13e011aa85efa8f6fd
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148565"
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