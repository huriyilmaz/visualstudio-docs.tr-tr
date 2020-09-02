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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657702"
---
# <a name="evaluate-statement-command"></a>Deyimi Değerlendir Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verilen ifadeyi değerlendirir ve görüntüler.

## <a name="syntax"></a>Söz dizimi

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Bağımsız değişkenler
 `text` Gerekli. Değerlendirilecek olan ifade.

## <a name="remarks"></a>Açıklamalar
 **EvaluateStatement** komutunu girmek için kullanılan pencere, bir eşittir işareti (=) karşılaştırma işleci olarak mı yoksa atama işleci olarak mı yorumlanacağını belirler.

 **Komut** penceresinde, bir eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. Bu nedenle, örneğin, değişkenlerin değerleri `a` ve `b` farklıysa, komut

```
>Debug.EvaluateStatement(a=b)
```

 , bir değeri döndürür `false` .

 **Hemen** penceresinde, aksine, bir eşittir işareti (=) bir atama işleci olarak yorumlanır. Bu nedenle, örneğin, komut

```
>Debug.EvaluateStatement(a=b)
```

 değişkenin değeri değişkene atanır `a` `b` .

## <a name="example"></a>Örnek

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Yazdır komutu](../../ide/reference/print-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
