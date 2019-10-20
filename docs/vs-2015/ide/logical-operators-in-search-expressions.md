---
title: Arama Ifadelerindeki mantıksal Işleçler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651434"
---
# <a name="logical-operators-in-search-expressions"></a>Arama İfadelerindeki Mantıksal İşleçler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mantıksal işleçleri kullanarak, daha karmaşık arama ifadelerini daha basit bir şekilde oluşturarak içerik aramanızı geliştirebilirsiniz. Aşağıdaki tabloda gösterildiği gibi mantıksal işleçler, birden çok arama terimlerinin bir arama sorgusunda nasıl birleştirilmesi gerektiğini belirtir.

> [!IMPORTANT]
> Arama altyapısının bunları tanıması için tüm büyük harflerle mantıksal işleçler girmeniz gerekir.

|Arama yapmak için|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Aynı konunun her iki terimi|AND|DIB ve palet|Hem "DIB" hem de "palet" içeren konular.|
|Konu başlığında iki terim|VEYA|Raster veya vektör|"Tarama" ya da "vektör" içeren konular.|
|Aynı konu başlığında ikinci terim olmadan ilk terim|BAŞLATıLMADı|"işletim sistemi" DOS DEĞIL|"İşletim sistemi" ("DOS" değil) içeren konular.|
|Her iki terim de bir konu başlığında birlikte kapat|KALEMIN|çekirdeğin YAKıNıNDA Kullanıcı|"Kernel" öğesinin yakın yakınına "user" içeren konular.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Tam metin arama Ipuçları](../ide/full-text-search-tips.md) [bilgileri bulma](../ide/locate-information.md)
