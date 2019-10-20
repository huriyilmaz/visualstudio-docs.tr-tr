---
title: Ifadeyi değerlendir komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657702"
---
# <a name="evaluate-statement-command"></a>Deyimi Değerlendir Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verilen ifadeyi değerlendirir ve görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Arguments
 `text` gerekiyor. Değerlendirilecek olan ifade.

## <a name="remarks"></a>Açıklamalar
 **EvaluateStatement** komutunu girmek için kullanılan pencere, bir eşittir işareti (=) karşılaştırma işleci olarak mı yoksa atama işleci olarak mı yorumlanacağını belirler.

 **Komut** penceresinde, bir eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. Bu nedenle, örneğin, `a` ve `b` değişkenlerinin değerleri farklıysa, komut

```
>Debug.EvaluateStatement(a=b)
```

 `false` bir değer döndürür.

 **Hemen** penceresinde, aksine, bir eşittir işareti (=) bir atama işleci olarak yorumlanır. Bu nedenle, örneğin, komut

```
>Debug.EvaluateStatement(a=b)
```

 , değişken `b` `a` değişkenine atanır.

## <a name="example"></a>Örnek

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Yazdır komutu](../../ide/reference/print-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
