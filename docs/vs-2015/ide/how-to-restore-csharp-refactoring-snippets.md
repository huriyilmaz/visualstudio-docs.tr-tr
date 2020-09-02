---
title: 'Nasıl yapılır: C# yeniden düzenleme parçacıklarını geri yükleme | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670793"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Nasıl Yapılır: C# Yeniden Düzenleme Kod Parçacıklarını Geri Yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C# yeniden düzenleme işlemleri aşağıdaki dizinde bulunan kod parçacıklarını kullanır:

 *Yükleme dizini*\Microsoft Visual Studio 14.0 \ VC # \parçacıklar \\ *dil kimliği*\ yeniden düzenleme

 Bu yeniden düzenleme dizini veya bu dizindeki herhangi bir dosya silinirse veya bozuksa, C# yeniden düzenleme işlemleri IDE 'de çalışmayabilir. Aşağıdaki yordamlar, C# yeniden düzenleme kod parçacıklarını geri yüklemenize yardımcı olabilir.

### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>C# yeniden düzenleme parçacıkları kod parçacığı Yöneticisi aracılığıyla kullanılabilir olduğunu doğrulamak için

1. **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ni seçin.

2. **Kod parçacığı Yöneticisi** iletişim kutusunda, **dil** açılan listesinden **Visual C#** ' yi seçin.

     Ağaç görünümü klasör listesinde bir yeniden **düzenleme** klasörü görünmelidir.

### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Yeniden düzenlemeyi geri yüklemek için bkz. kod parçacığı yöneticisinde açıklama

1. Yeniden **düzenleme** klasörü kod parçacığı yöneticisinin ağaç görünümü klasörü listesinde görünmezse, kod parçacığı yöneticisine yeniden düzenleme parçacıkları eklemek için bu yordamı kullanın.

2. **Araçlar** menüsünde **kod parçacığı Yöneticisi**' ni seçin.

3. **Kod parçacığı Yöneticisi** iletişim kutusunda, **dil** açılan listesinden **Visual C#** ' yi seçin.

4. **Ekle**'ye tıklayın. Kod parçacığı yöneticisine geri eklenecek dizini bulmanıza ve belirtmenize yardımcı olan **kod parçacıkları dizini** iletişim kutusu görüntülenir.

5. Dizin yolu şu olan yeniden **düzenleme** klasörünü bulun:

     *Yükleme dizini*\Microsoft Visual Studio 14.0 \ VC # \parçacıklar \\ *dil kimliği*\ yeniden düzenleme

     Asıl yol, varsayılan yükleme için aşağıdakine benzerdir:

     C:\Program Files\Microsoft Visual Studio 14.0 \ VC # \Snippets\1033\Refactoring.

6. **Kod parçacıkları dizini** Iletişim kutusunda **Aç** ' a tıklayın ve ardından kod parçacıkları yöneticisinde **Tamam** ' a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual C# kod parçacıkları](../ide/visual-csharp-code-snippets.md) yeniden [düzenleme (C#)](../csharp-ide/refactoring-csharp.md) [kod parçacıkları](../ide/code-snippets.md)
