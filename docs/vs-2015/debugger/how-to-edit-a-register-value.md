---
title: 'Nasıl yapılır: yazmaç değerini düzenleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f0cd04b054d51119f6f6c1b0275c4f781656bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811946"
---
# <a name="how-to-edit-a-register-value"></a>Nasıl Yapılır: Yazmaç Değerini Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazmaçları penceresi yalnızca, **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünde adres düzeyi hata ayıklama etkinse kullanılabilir.  
  
### <a name="to-change-the-value-of-a-register"></a>Bir kaydın değerini değiştirmek için  
  
1. **Yazmaçları** penceresinde, ekleme noktasını değiştirmek istediğiniz değere TAŞıMAK için sekme tuşunu veya fareyi kullanın. Yazmaya başladığınızda, imlecin üzerine yazmak istediğiniz değerin önünde bulunması gerekir.  
  
2. Yeni değeri yazın.  
  
    > [!CAUTION]
    > Kayıt değerlerini değiştirme (özellikle EıP ve EBP yazmaçlarında) program yürütmesini etkileyebilir.  
  
    > [!CAUTION]
    > Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Bir anlık zararsız düzenleme bile, kayan nokta kaydındaki en az önemli bitlerin bazılarında değişikliklere yol açabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)
