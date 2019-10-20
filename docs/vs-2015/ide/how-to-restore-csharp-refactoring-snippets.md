---
title: 'Nasıl yapılır: yeniden C# düzenleme parçacıklarını geri yükleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ae3f1d74a482192d3782aaa87baa816694abcf4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670793"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Nasıl Yapılır: C# Yeniden Düzenleme Kod Parçacıklarını Geri Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C#yeniden düzenleme işlemleri aşağıdaki dizinde bulunan kod parçacıklarını kullanır:

 *Yükleme dizini*\Microsoft Visual Studio 14,0 \VC#\PARÇACıKLAR \\*dil kimliği*\ yeniden düzenleme

 Bu yeniden düzenleme dizini veya bu dizindeki herhangi bir dosya silinirse veya bozuksa, yeniden C# düzenleme işlemleri IDE 'de çalışmayabilir. Aşağıdaki yordamlar yeniden düzenleme kod parçacıklarını geri C# yüklemenize yardımcı olabilir.

### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Yeniden düzenleme C# kod parçacıklarının kod parçacığı Yöneticisi aracılığıyla kullanılabilir olduğunu doğrulamak için

1. **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ni seçin.

2. **Kod parçacığı Yöneticisi** iletişim kutusunda, **dil** açılır listesinden **görsel C#**  ' i seçin.

     Ağaç görünümü klasör listesinde bir yeniden **düzenleme** klasörü görünmelidir.

### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Yeniden düzenlemeyi geri yüklemek için bkz. kod parçacığı yöneticisinde açıklama

1. Yeniden **düzenleme** klasörü kod parçacığı yöneticisinin ağaç görünümü klasörü listesinde görünmezse, kod parçacığı yöneticisine yeniden düzenleme parçacıkları eklemek için bu yordamı kullanın.

2. **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ni seçin.

3. **Kod parçacığı Yöneticisi** iletişim kutusunda, **dil** açılır listesinden **görsel C#**  ' i seçin.

4. **Ekle**'yi tıklatın. Kod parçacığı yöneticisine geri eklenecek dizini bulmanıza ve belirtmenize yardımcı olan **kod parçacıkları dizini** iletişim kutusu görüntülenir.

5. Dizin yolu şu olan yeniden **düzenleme** klasörünü bulun:

     *Yükleme dizini*\Microsoft Visual Studio 14,0 \VC#\PARÇACıKLAR \\*dil kimliği*\ yeniden düzenleme

     Asıl yol, varsayılan yükleme için aşağıdakine benzerdir:

     C:\Program Files\Microsoft Visual Studio 14,0 \VC#\Snippets\1033\Refactoring.

6. **Kod parçacıkları dizini** Iletişim kutusunda **Aç** ' a tıklayın ve ardından kod parçacıkları yöneticisinde **Tamam** ' a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Görsel C# kod parçacıkları](../ide/visual-csharp-code-snippets.md) yeniden [düzenlemeC#()](../csharp-ide/refactoring-csharp.md) [kod parçacıkları](../ide/code-snippets.md)
